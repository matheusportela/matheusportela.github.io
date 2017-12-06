---
layout: post
status: publish
published: true
title: "Compilando Tensorflow 1.4 com suporte a GPU"
date: '2017-12-05 23:55:00 -0200'
categories:
- Programming
tags:
- machine-learning
- tensorflow
comments: []
---

Recentemente, montei um PC novo com a intenção de rodar jogos mais pesados, que não podem ser executados no meu laptop, e poder utilizar a sua GPU em algoritmos de Deep Learning. Após instalar o [Ubuntu 16.04](http://releases.ubuntu.com/16.04/), a distribuição Linux mais simples para iniciar qualquer tipo de trabalho, escolhi utilizar o [Tensorflow](https://www.tensorflow.org/) como framework para implementação de algoritmos de ML uma vez que, além de ser desenvolvido em Python, tornou-se o framework mais popular na indústria. Outra opção seria o [Torch](http://torch.ch/), que é bastante utilizado em trabalhos acadêmicos.

[Instalar o Tensorflow](https://www.tensorflow.org/install/install_linux) com suporte a GPU é super simples, trabalho feito em um único comando:

```
$ pip install tensorflow-gpu
```

Entretanto, para minha surpresa, os pacotes pré-compilados do Tensorflow estão *desatualizados*. Embora, o CUDA esteja na versão 9.0 e o cuDNN, na 7.0, o pacote pré-compilado do Tensorflow 1.4 requer CUDA 8.0 e cuDNN 6.0. Mais ainda, esse pacote não faz uso dos conjuntos de instruções [SSE 4.1 e SSE 4.2](https://en.wikipedia.org/wiki/SSE4), [AVX e AVX2](https://en.wikipedia.org/wiki/Advanced_Vector_Extensions) e [FMA](https://en.wikipedia.org/wiki/Multiply%E2%80%93accumulate_operation#Fused_multiply%E2%80%93add), que aceleram a execução de algumas operações na CPU.

```
W tensorflow/core/platform/cpu_feature_guard.cc:95] The TensorFlow library wasn't compiled to use SSE4.1 instructions, but these are available on your machine and could speed up CPU computations.
W tensorflow/core/platform/cpu_feature_guard.cc:95] The TensorFlow library wasn't compiled to use SSE4.2 instructions, but these are available on your machine and could speed up CPU computations.
W tensorflow/core/platform/cpu_feature_guard.cc:95] The TensorFlow library wasn't compiled to use AVX instructions, but these are available on your machine and could speed up CPU computations.
W tensorflow/core/platform/cpu_feature_guard.cc:95] The TensorFlow library wasn't compiled to use AVX2 instructions, but these are available on your machine and could speed up CPU computations.
W tensorflow/core/platform/cpu_feature_guard.cc:95] The TensorFlow library wasn't compiled to use FMA instructions, but these are available on your machine and could speed up CPU computations.
```

Para não desperdiçar o potencial da CPU e GPU, **resolvi compilar o Tensorflow a partir do código-fonte**. Apesar de poder intimidar à primeira vista, garanto que não há grandes dificuldades e que você também pode fazê-lo.

Portanto, escrevi esse passo a passo para fins de documentação própria, caso precise realizar essa instalação novamente no futuro. Disponibilizo os passos aqui para ajudar quem tenha encontrado o mesmo problema na sua máquina.

# Tensorflow: Do código-fonte ao Python

## Instalando drivers da GPU

Antes de mais nada, é necessário instalar os drivers gráficos da NVIDIA no seu Ubuntu. Para isso, vamos adicionar o PPA que contém esses drivers - que são proprietários.

```
$ sudo add-apt-repository ppa:graphics-drivers/ppa
$ sudo apt update
$ sudo apt upgrade
```

Em seguida, vá em `System Settings > Software and updates > Aditional drivers` e selecione a versão mais recente do driver que houver disponível. [Esse tutorial](http://www.edivaldobrito.com.br/recentes-drivers-graficos-proprietarios-no-ubuntu/) possui screenshots mostrando exatamente como fazer isso.

## Instalando o ambiente de desenvolvimento

Primeiro, devemos garantir que temos os headers mais atualizados para desenvolver em Linux:

```
$ sudo apt install linux-headers-$(uname -r)
```

Para trabalhar com Python, vamos utilizar o [pip](https://pypi.python.org/pypi/pip) como gerenciador de pacotes.

```
$ sudo apt install python-pip python-dev
$ pip install --upgrade pip
```

Além disso, o [virtualenv](https://virtualenv.pypa.io/en/stable/) é extremamente recomendável para isolar dependências de maneira saudável. Também recomendo fortemente o uso do [virtualenvwrapper](https://virtualenvwrapper.readthedocs.io/en/latest/), que facilita o uso do virtualenv.

```
$ pip install virtualenv --user
$ pip install virtualenvwrapper --user
$ source /usr/local/bin/virtualenvwrapper.sh
$ echo "" >> ~/.bashrc
$ echo "# Virtualenv" >> ~/.bashrc
$ echo "source ~/.local/bin/virtualenvwrapper.sh" >> ~/.bashrc
```

Por fim, para quem desejar um interpretador Python um pouco mais amigável e com funcionalidades extras, o [IPython](https://ipython.org/) é a minha sugestão.

```
$ sudo apt install ipython ipython-notebook
```

## Instalando CUDA e cuDNN

Com o ambiente instalado, podemos instalar as bibliotecas mais importantes para trabalhar com a GPU: [CUDA](https://developer.nvidia.com/cuda-toolkit) - um toolkit para programação em placas gráficas com a linguagem CUDA C - e [cuDNN](https://developer.nvidia.com/cudnn) - o framework para acelerar a execução Deep Neural Networks e GPUs da NVIDIA.

### Instalando CUDA

Inicialmente, é necessário fazer o download dos arquivos `.deb` do CUDA diretamente do [site da NVIDIA](https://developer.nvidia.com/cuda-downloads).

```
$ cd ~/Downloads/
$ sudo dpkg -i cuda-repo-ubuntu1604-9-0-local_9.0.176-1_amd64.deb
```

Agora, podemos instalar o CUDA a partir do pré-compilado disponibilizado pela NVIDIA.

```
$ sudo apt-key add /var/cuda-repo-9-0-local/7fa2af80.pub
$ sudo apt update
$ sudo apt install cuda
```

Também é necessário configurar duas variáveis de ambiente: `PATH` e `LD_LIBRARY_PATH` com os caminhos de instalação do CUDA. Vamos colocar essas informações no `~/.bashrc`.

```
$ echo "" >> ~/.bashrc
$ echo "# CUDA" >> ~/.bashrc
$ echo "export PATH=\"\$PATH:/usr/local/cuda-9.0/bin\"" >> ~/.bashrc
$ echo "export LD_LIBRARY_PATH=\"/usr/local/cuda-9.0/lib64\"" >> ~/.bashrc
```

Após esses passos, já é possível instalar o CUDA toolkit, o último passo necessário para executar o ambiente do CUDA no seu computador:

```
$ sudo apt install nvidia-cuda-toolkit
```

Para testar a instalação do CUDA até aqui, o comando `nvidia-smi` pode ser utilizado. Ele apresenta na tela dados da GPU detectada e vários status, como percentual de memória de vídeo livre. Caso seja necessário, reinicie o terminal ou o computador para aplicar as alterações realizadas nos passos anteriores.

```
$ nvidia-smi
```

### Instalando cuDNN

O processo para instalação do cuDNN é ainda mais fácil do que o do CUDA. Começamos baixando três arquivos `.deb` do [site da NVIDIA](https://developer.nvidia.com/rdp/cudnn-download): `libcudnn7_<version>.deb`, `libcudnn7-dev_<version>.deb` e `libcudnn7-doc_<version>.deb`. Note que é necessário preencher um formulário antes de conseguir baixá-los.

```
$ cd ~/Downloads/
$ sudo dpkg -i libcudnn7_7.0.4.31-1+cuda9.0_amd64.deb
$ sudo dpkg -i libcudnn7-dev_7.0.4.31-1+cuda9.0_amd64.deb
$ sudo dpkg -i libcudnn7-doc_7.0.4.31-1+cuda9.0_amd64.deb
$ sudo apt install libcupti-dev
```

Pronto!

Para testar a instalação, vamos compilar o exemplo de classificação de dígitos com Deep Neural Networks usando a base de dados do [MNIST](http://yann.lecun.com/exdb/mnist/).

```
$ mkdir /tmp/cudnn
$ cd /tmp/cudnn
$ cp -r /usr/src/cudnn_samples_v7/ /tmp/cudnn/
$ cd /tmp/cudnn/cudnn_samples_v7/mnistCUDNN/
$ make clean
$ make
$ ./mnistCUDNN
```

Se tudo der certo, o script deve mostrar uma mensagem de sucesso.

## Instalando MKL

Uma das bibliotecas que iremos instalar será a [MKL](https://software.intel.com/en-us/mkl), Math Kernel Library, desenvolvida pela Intel. Segundo a empresa, utilizar tal biblioteca em CPUs da Intel provê um ganho significativo de performance para Deep Neural Networks. A parte boa é que o Tensorflow integra com a MKL de forma transparente!

Iremos compilar a MKL a partir do código-fonte [disponível no GitHub](https://github.com/01org/mkl-dnn.git). O processo é simples e segue o padrão `cmake > make > make install`.

```
$ sudo apt install git curl cmake doxygen graphviz
$ mkdir ~/git
$ cd git
$ git clone https://github.com/01org/mkl-dnn.git
$ cd mkl-dnn/scripts/
$ ./prepare_mkl.sh
$ mkdir build
$ cd build/
$ cmake ..
$ make
$ make test
$ make doc
$ sudo make install
$ sudo ldconfig
```

## Instalando TensorFlow

Finalmente chegamos na parte que todos estávamos esperando. Compilar o Tensorflow!

Antes de mais nada, vamos criar um virtualenv para o Tensorflow e instalar alguns pacotes necessários para compilar o framework.

```
$ mkvirtualenv tensorflow
$ pip install numpy wheel
```

Também vamos instalar o Java 8 da Oracle e o [Bazel](https://bazel.build/), o sistema de build criado pela Google e utilizado pelo Tensorflow.

```
$ sudo add-apt-repository ppa:webupd8team/java
$ sudo apt install oracle-java8-installer
$ echo "deb [arch=amd64] http://storage.googleapis.com/bazel-apt stable jdk1.8" | sudo tee /etc/apt/sources.list.d/bazel.list
$ curl https://bazel.build/bazel-release.pub.gpg | sudo apt-key add -
$ sudo apt update
$ sudo apt install bazel
```

Agora, podemos clonar o repositório do Tensorflow para a nossa máquina.

```
$ cd ~/git/
$ git clone https://github.com/tensorflow/tensorflow
$ cd tensorflow/
```

Utilizando o `git`, podemos fazer o checkout da branch contendo a versão exata do Tensorflow que será instalada ao invés de pegar a versão da branch `master`. No caso, iremos com a versão 1.4.

```
$ git checkout r1.4
```

Agora, vamos gerar os arquivos de build a partir do script `configure`. **Atenção:** nesse momento, você terá que escolher as opções de compilação que forem adequadas para a sua máquina. Não se esqueça de selecionar o suporte à GPU!

```
$ ./configure
```

Esse é o momento que iremos gerar o pacote do Tensorflow para ser instalado com o pip. Repare que, nesse momento, passamos como argumento as opções para suporte de SSE 4.1, SSE 4.2, AVX, AVX2, FMA e MKL.

```
$ bazel build -c opt --copt=-msse4.1 --copt=-msse4.2 --copt=-mavx --copt=-mavx2 --copt=-mfma --copt=-mfpmath=both --config=mkl //tensorflow/tools/pip_package:build_pip_package
$ bazel-bin/tensorflow/tools/pip_package/build_pip_package ~/git/tensorflow
```

Quando terminarem de serem executados, esses comandos gerarão um arquivo do tipo `tensorflow-<version>.whl`. Basta instalar esse arquivo na nossa virtualenv para podermos utilizar o Tensorflow.

```
$ pip install --upgrade ~/git/tensorflow/tensorflow-*.whl
```

Vamos aproveitar esse momento para atualizar o `protobuf` também:

```
$ pip install --upgrade https://storage.googleapis.com/tensorflow/linux/cpu/protobuf-3.0.0b2.post2-cp27-none-linux_x86_64.whl
```

**Parabéns, você instalou o Tensorflow a partir do código-fonte!**. Você pode testar sua instalação em uma sessão do Python que utilize GPU:

```python
import tensorflow as tf

with tf.device('/gpu:0'):
    a = tf.constant([1.0, 2.0, 3.0, 4.0, 5.0, 6.0], shape=[2, 3], name='a')
    b = tf.constant([1.0, 2.0, 3.0, 4.0, 5.0, 6.0], shape=[3, 2], name='b')
    c = tf.matmul(a, b)

with tf.Session() as sess:
    print (sess.run(c))
```

Se tudo der certo, você verá na saída do seu programa as informações da GPU utilizada. Lembre-se que você pode utilizar o comando `nvidia-smi` para verificar o status da sua placa gráfica enquanto estiver executando um script com Tensorflow.

# Conclusão

Ao final desse processo, você terá uma instalação fresquinha do Tensorflow com todos os avanços disponibilizados pela NVIDIA e pela Intel na sua máquina. Agora, é hora de botar a mão na massa e treinar alguns modelos para fazer o esforço compensar.

Em um futuro, quero comparar o ganho de desempenho com as otimizações de SEE, AVX, FMA e MKL em relação à versão padrão do Tensorflow disponível no `pip`.

Espero que você tenha gostado e até a próxima!
