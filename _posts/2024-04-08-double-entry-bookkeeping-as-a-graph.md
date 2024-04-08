---
layout: post
status: publish
published: true
title: 'Double-Entry Bookkeeping is a Directed Graph'
date: '2024-04-08 00:00:00 -0500'
categories:
- Business
tags:
- accounting
- graphs
comments: []
---

## My Journey into Accounting

In the past couple of years, I've been working in billing and payments at [Justworks](https://www.justworks.com). This experience exposed me to the world of bookkeeping and accounting in a way that I didn't expect: I took a [course](https://www.udemy.com/course/accounting-fsa-a-solid-foundation-for-a-career-in-finance/) and [read a textbook](https://link.springer.com/book/10.1007/978-1-349-20618-6) in accounting, adopted [plain text accounting](https://plaintextaccounting.org/) for my personal finances, and worked in a double-entry ledger system.

Being such a fundamental part of the human experience, accounting has been around for literally millenia. It fostered mathematical and language development. In some cultures, it even predates [written language](https://en.wikipedia.org/wiki/Quipu). For this reason, it's not surprising that accounting uses a very particular vocabulary and set of concepts that can be intimidating to a newcomer. Credits and debits. Assets and liabilities. Balance sheet. Ledgers and journals.

It took me a while to get used to these things. But once I did, I realized they aren't _that_ difficult. Maybe it is just a matter of finding the right way to explain them.

This series of articles is my attempt to capture some of my "a-ha" moments while learning accounting. Hopefully, it will help someone out there grasp these ideas in a more intuitive and modern way.

In this first article, we'll start with the basics: bookkeeping.

## Bookkeeping Without Ledgers

At its core, accounting is about keeping track of countable things over time. It can be anything: food, animals, people, money. Some of the oldest documents archelogists have found register these quantities in old societies. Nowadays, accounting is usually interested in tracking money whereas other areas (such as inventory management or the census bureau) count other things. For the rest of this article, we'll focus on money.

Let's start with a simple example. Imagine you're in a small town with two people: Alice and Bob. Alice has $100 in her pocket and Bob has $50 as of January 1st, 2024.

```
Date: January 1st, 2024

| Person | Amount |
| ------ | ------ |
| Alice  | $100   |
| Bob    | $50    |
```

If nothing changes, our job is done. We just need to go around town and ask each person how much money they have, tabulate the data, and store it in a safe place. Badabing, badaboom.

But money is meant to be spent. Alice is studying for her finals needs to buy a book. She notices Bob has one copy and proposes to buy it from him for $20. Bob is happy to sell her the book he hasn't used in a while and cash in the extra $20. Great deal!

Now that money has changed hands, we need to update our records. Alice spent $20 and Bob received the same amount. Let's update our table.

```
Date: February 1, 2024

| Person | Amount |
| ------ | ------ |
| Alice  | $80    |
| Bob    | $70    |
```

Before proceeding, let's name a few things. In our records, Alice and Bob are _accounts_, i.e., places where money is stored. The amount of money in each account is called a _balance_. Saying that Alice has $80 is the same as saying that the Alice account's balance is $80 as of February 1st, 2024.

> **Definition 1: Account**
>
> A place where money is stored.

> **Definition 2: Balance**
>
> The amount of money in an account at a given point in time.

Our records are simple and useful. We can go around town every month, ask people how much money they have and write it down. We're basically creating a snapshot of the town's financial situation monthly. (Surely, most people will be annoyed by this breach of privacy and I would probably be arrested for stalking but let's ignore this for now.)

What kinds of questions can we answer with this data? Actually, many!
- How much money does each person have?
- How much money has each person spent or gained over time?
- Who has the most money?
- Who has the least money?
- How much money is there in total in the town?

Now, consider Alice comes to us one day and asks "How come I have $80? I thought I had more!" Unfortunately, all we can answer is "That's what I have written down" with our current data. We can't tell, for instance, whether Alice initially had $0 and received $80 or if she had $10,000 and spent $9,920.

Why is this so?

Well, we're only keeping track of the current balance of each account. We don't know exactly what happened to get to that balance and all the changes that happened between snapshots are lost.

Of course, accountants have dealt with this problem for centuries. And they have a solution: _ledgers_.

## Bookkeeping with Single-Entry Ledgers

Let's now think how we could keep track of the changes in a more systematic way. One way to do this is to write down each update as it happens, not only the balance in a certain date.

To do this, we'll add more information to the table. For example, we write down that on January 1st, 2024, Alice had $100.

```
| Account | Description     | Date       | Amount | Balance |
| ------- | --------------- | ---------- | ------ | ------- |
| Alice   | Opening balance | 2024-01-01 | $100   | $100    |
```

We added a few new columns to the table:
- **Description**: A human-readable explanation of the transaction (e.g. what it is about, who got paid, a reference number, etc).
- **Date**: When the transaction happened. Besides ordering transactions, this field can be used to group transactions by period (e.g. monthly reports). It can be enhanced with time information (e.g. hour, minute, second) if needed.
- **Balance**: The balance of the account after the transaction. This field is redundant but it's useful when inspecting the data.

So far, so good. Now, let's take a look at how we can write down that Alice bought the book from Bob.

```
| Account | Description     | Date       | Amount | Balance |
| ------- | --------------- | ---------- | ------ | ------- |
| Alice   | Opening balance | 2024-01-01 | $100   | $100    |
| Alice   | Bought book     | 2024-02-01 | -$20   | $80     |
```

This is different. Instead of just updating the existing balance, we're adding a new row with the transaction details. The new columns we added are helpful in understanding what happened and when it happened. We know that Alice had $100, spent $20 when buying the book, and now has $80.

Time for more definitions: each row in this table is called an _entry_ and the whole table is called a _ledger_.

> **Definition 3: Entry**
>
> A record of a transaction that happened to an account.

> **Definition 4: Ledger**
>
> A collection of entries for an account.

This is the core of a [_single-entry bookkeeping_](https://en.wikipedia.org/wiki/Single-entry_bookkeeping) system.

So far, we've updated only Alice's ledger. Let's take a look at Bob's:

```
| Account | Description     | Date       | Amount | Balance |
| ------- | --------------- | ---------- | ------ | ------- |
| Bob     | Opening balance | 2024-01-01 | $50    | $50     |
| Bob     | Sold book       | 2024-02-01 | $20    | $70     |
```

Now we have a ledger for each account. Great!

Ledgers are sometimes called _journal_ or _book_ because, in the past, they were physical books where accountants would write down transactions. In the modern world, they're usually stored in a database.

An important characteristic of a ledger is that the data is **immutable**. Once an entry is written, it cannot be changed at all because we want to preserve the ledger's full history. This raises the question: what happens if we make a mistake?

Here's an example. Say the correct price for the book is $30 but we wrote down $20. If we were in a mutable system, we could just update the amount in the original entry.

```
| Account | Description     | Date       | Amount | Balance |
| ------- | --------------- | ---------- | ------ | ------- |
| Alice   | Opening balance | 2024-01-01 | $100   | $100    |
| Alice   | Bought book     | 2024-02-01 | -$30   | $70     |
```

There are problems with this approach though. For example, we lose the history of the original amount. We can't tell that we made a mistake and corrected it. We also can't tell if the original amount was correct and we made a mistake in the correction.

Could we do better?

In a ledger system, we can't change the amount in the original entry. Instead, we write a new entry to cancel the old one and write a new one with the correct amount.

```
| Account | Description        | Date       | Amount | Balance |
| ------- | ---------------    | ---------- | ------ | ------- |
| Alice   | Opening balance    | 2024-01-01 | $100   | $100    |
| Alice   | Bought book        | 2024-02-01 | -$20   | $80     |
| Alice   | Correct book price | 2024-02-01 | $20    | $100    |
| Alice   | Bought book        | 2024-02-01 | -$30   | $70     |
```

The end result is the same as updating an entry in-place: the balance is $70. However, we can now see that we made a mistake and corrected it. We can also see the original amount and the reason for the correction. This gives us an audit trail of changes.

In a way, a ledger is similar to [_event sourcing_](https://martinfowler.com/eaaDev/EventSourcing.html). In event sourcing, we store events that happened in the system and use them to calculate the current state of the system. This is in contrast to storing the current state of the system and updating it in-place. Event sourcing has many benefits, like being able to replay events or to rebuild the state of the system at any point in time.

If our system only cares about a single account at a time, a single-entry ledger system is enough. Think of a personal finance app that you use to keep track of your money or a gym that tracks how much their members paid for the service. However, financial systems are usually more complex than that and transactions typically involve multiple accounts at once.

It turns out accountants have a solution for this too: [_double-entry bookkeeping_](https://en.wikipedia.org/wiki/Double-entry_bookkeeping).

## Bookkeeping with Double-Entry Ledgers

Let's revisit the example of Alice buying the book from Bob and see the ledgers for both accounts:

```
| Account | Description        | Date       | Amount | Balance |
| ------- | ------------------ | ---------- | ------ | ------- |
| Alice   | Opening balance    | 2024-01-01 | $100   | $100    |
| Alice   | Bought book        | 2024-02-01 | -$20   | $80     |

| Account | Description        | Date       | Amount | Balance |
| Bob     | Opening balance    | 2024-01-01 | $50    | $50     |
| Bob     | Sold book          | 2024-02-01 | $20    | $70     |
```

Did you notice how the transactions are related to each other? The $20 Alice spent is the same $20 Bob received. Nonetheless, we're not explicitly stating this relationship in our ledgers. It could be the case the Alice bought the book from Bob and Bob received the money from Charlie. We can't tell from the ledgers alone.

A first step in making this relationship explicit is to group related entries into a _transaction_. Let's add the `Transaction` column to our table:

```
| Account | Transaction | Description        | Date       | Amount | Balance |
| ------- | ----------  | ------------------ | ---------- | ------ | ------- |
| Alice   | 1           | Opening balance    | 2024-01-01 | $100   | $100    |
| Alice   | 3           | Book sale          | 2024-02-01 | -$20   | $80     |

| Account | Transaction | Description        | Date       | Amount | Balance |
| Bob     | 2           | Opening balance    | 2024-01-01 | $50    | $50     |
| Bob     | 3           | Book sale          | 2024-02-01 | $20    | $70     |
```

In this example, we have the following transactions:
- Transaction 1: Alice's opening balance.
- Transaction 2: Bob's opening balance.
- Transaction 3: Alice bought a book from Bob.

Now, we explicitly state that the $20 Alice spent is the same $20 Bob received. Let's define a _transaction_ formally:

> **Definition 5: Transaction**
>
> A group of related entries that affect different accounts.

The difference between our current system and the previous one is that we're now grouping related entries into transactions. Since each transaction affects multiple accounts, we can now see how money flows between accounts. This is called a _double-entry ledger_ system.

Traditionally, accountants would use two columns to represent the flow of money between accounts: _credits_ and _debits_. When money leaves an account, the amounts goes in the credit column. Incoming money appears in the debit column.

> **Definition 6: Credit**
>
> An entry that represents money leaving an account.

> **Definition 7: Debit**
>
> An entry that represents money entering an account.

(Pro-tip: for now, ignore what you know about credit and debit cards. It's a different concept.)

When Alice pays Bob $20, we say Alice's account is credited $20 and Bob's account is debited $20. Let's represent this in our table:

```
| Account | Transaction | Description        | Date       | Debit | Credit |
| ------- | ----------  | ------------------ | ---------- | ----- | ------ |
| Alice   | 1           | Opening balance    | 2024-01-01 | $100  |        |
| Alice   | 3           | Bought book        | 2024-02-01 |       | $20    |

| Account | Transaction | Description        | Date       | Debit | Credit |
| Bob     | 2           | Opening balance    | 2024-01-01 | $50   |        |
| Bob     | 3           | Sold book          | 2024-02-01 | $20   |        |
```

I wanted to make a few of points before continuing our journey.

First, history is the reason again on why it's common to use different columns for debits and credits. Remember that accounts were doing this work with physical books and pens. The whole goal of the double-entry system is to reduce mistakes, especially the ones that are hard to notice. Old accounting journals were symmetrical: the left side was for debits and the right side was for credits. A simplified version would look like this:

```
Debit                          Alice's account                           Credit
-------------------------------------------------------------------------------
-------------------------------------------------------------------------------
| Date       | Description     | $    | | Date       | Description     | $    |
| ---------- | --------------- | ---- | | ---------- | --------------- | ---- |
| 2024-01-01 | Opening balance | $100 | |            |                 |      |
|            |                 |      | | 2024-02-01 | Bought book     | $20  |
```

This format is commonly referred to as a [_T-account_](https://en.wikipedia.org/wiki/Debits_and_credits#T-accounts) because of its shape. Having a physical distinction between debits and credits made it easier to reduce accounting mistakes. For this reason, many accountants will refer to debits as entries that go on the left side and credits as the ones that go on the right side.

Computer systems don't need to use this format, though, as it doesn't necessary prevent software bugs. Instead, it is common to have a single amount column and only have another column to indicate whether the amount is a debit or a credit. For example:

```
| Account | Transaction | Description        | Date       | Type   | Amount |
| ------- | ----------  | ------------------ | ---------- | ------ | ------ |
| Alice   | 1           | Opening balance    | 2024-01-01 | Debit  | $100   |
| Alice   | 3           | Bought book        | 2024-02-01 | Credit | $20    |
```

Second, notice how we're using a positive number even when money is leaving Alice's account. Historically, accountants don't like negative numbers in the books as they only became popular much later in Europe. Computer systems are very good with negative numbers, though. Instead of having two columns, we could just use a single column and adopt the convention that credits are negative and debits are positive, or vice-versa. For example:

```
| Account | Transaction | Description        | Date       | Amount |
| ------- | ----------  | ------------------ | ---------- | ------ |
| Alice   | 1           | Opening balance    | 2024-01-01 | $100   |
| Alice   | 3           | Bought book        | 2024-02-01 | -$20   |
```

This is exactly what we were doing before but now we understand that the amount is negative because it's a credit. (Technically, using negative numbers for credits might be a limitation if we're trying to undo a credit entry without creating a debit entry but we don't need to be that picky for now.)

Finally, I'm not a big fan of old nomenclature for tradition's sake. We could rename credits as _outgoing_ money and debits as _incoming_ money without losing precision. In my opinion, this is more intuitive and less confusing.

```
| Account | Transaction | Description        | Date       | Incoming | Outgoing |
| ------- | ----------  | ------------------ | ---------- | -------- | -------- |
| Alice   | 1           | Opening balance    | 2024-01-01 | $100     |          |
| Alice   | 3           | Bought book        | 2024-02-01 |          | $20      |

| Account | Transaction | Description        | Date       | Incoming | Outgoing |
| ------- | ----------  | ------------------ | ---------- | -------- | -------- |
| Bob     | 2           | Opening balance    | 2024-01-01 | $50      |          |
| Bob     | 3           | Sold book          | 2024-02-01 | $20      |          |
```

An fundamental principle of a double-entry bookkeeping is that the total amount of money in the system remains the same after each transaction. A particular account can increase or decrease its balance over time but the sum of _all_ balances must remain constant. Nothing is lost, nothing is created, everything is _transacted_. It is a closed system.

> **Definition 6: Double-Entry Ledger**
>
> A system of accounting where each transaction is recorded one or more entries. The amount of money leaving accounts is equal to the amount of money entering other accounts in every transaction.

Ok, you might be thinking: "Wait a minute, these opening balances go against what you just said!" and you're right. Transactions 1 and 2 change the total amount of money in the system from $0 to $150. We should do better than stating a rule only to break it in the next sentence.

Let's assume all of the money that Alice and Bob have comes from a bank. Then, we can create an account for the bank and make it the other side of the opening balances.

```
| Account | Transaction | Description                | Date       | Incoming | Outgoing |
| ------- | ----------  | -------------------------- | ---------- | -------- | -------- |
| Bank    | 1           | Alice's opening balance    | 2024-01-01 |          | $100     |
| Bank    | 2           | Bob's opening balance      | 2024-01-01 |          | $50      |

| Account | Transaction | Description                | Date       | Incoming | Outgoing |
| Alice   | 1           | Opening balance            | 2024-01-01 | $100     |          |
| Alice   | 3           | Bought book                | 2024-02-01 |          | $20      |

| Account | Transaction | Description                | Date       | Incoming | Outgoing |
| Bob     | 2           | Opening balance            | 2024-01-01 | $50      |          |
| Bob     | 3           | Sold book                  | 2024-02-01 | $20      |          |
```

In this example, we don't care where the opening balances come from exactly. We just need to make sure money is coming from somewhere. The bank account is a kind of phony account that is there just to help us follow the rules. In accounting terms, it is a [_contra account_](https://en.wikipedia.org/wiki/Debits_and_credits#Contra_account) to the other accounts. The important thing is that all transactions are _balanced_, i.e., "credits equal debits".

> **Definition 7: Contra Account**
>
> An account that is used to offset another account. It is used to keep the accounting equation in balance.

Let's consider a more complex example. When Alice buys the book, she accidentally uses the wrong credit card and needs to pay $2 in foreign exchange fees. Bob, on the other hand, pays $2 in sales taxes, $1 in credit card fees. How do we keep track of this?

As we did before, we model this flow by creating new accounts: one for the credit card company and another for the tax authority. Then, when creating the transaction, we add new entries as necessary.

```
| Account | Transaction | Description                | Date       | Incoming | Outgoing |
| ------- | ----------  | -------------------------- | ---------- | -------- | -------- |
| Bank    | 1           | Alice's opening balance    | 2024-01-01 |          | $100     |
| Bank    | 2           | Bob's opening balance      | 2024-01-01 |          | $50      |

| Account | Transaction | Description                | Date       | Incoming | Outgoing |
| ------- | ----------  | -------------------------- | ---------- | -------- | -------- |
| Alice   | 1           | Opening balance            | 2024-01-01 | $100     |          |
| Alice   | 3           | Bought book                | 2024-02-01 |          | $20      |
| Alice   | 3           | Foreign exchange fee       | 2024-02-01 |          | $2       |

| Account | Transaction | Description                | Date       | Incoming | Outgoing |
| ------- | ----------  | -------------------------- | ---------- | -------- | -------- |
| Bob     | 2           | Opening balance            | 2024-01-01 | $50      |          |
| Bob     | 3           | Sold book                  | 2024-02-01 | $20      |          |
| Bob     | 3           | Sales tax                  | 2024-02-01 |          | $2       |
| Bob     | 3           | Credit card fee            | 2024-02-01 |          | $1       |

| Account | Transaction | Description                | Date       | Incoming | Outgoing |
| ------- | ----------  | -------------------------- | ---------- | -------- | -------- |
| CC      | 3           | Alice's credit card fee    | 2024-02-01 | $2       |          |
| CC      | 3           | Bob's credit card fee      | 2024-02-01 | $1       |          |

| Account | Transaction | Description                | Date       | Incoming | Outgoing |
| ------- | ----------  | -------------------------- | ---------- | -------- | -------- |
| Tax     | 3           | Bob's sales tax            | 2024-02-01 | $2       |          |
```

Once again, we aren't modelling the real world exactly since Alice and Bob most likely use different credit cards and pay different taxes. However, we're creating balanced transactions and representing the correct balances for each account.

Notice that transaction 3 has more than two entries. This is perfectly fine! We can have as many entries as we need to represent the flow of money between accounts as long as the transaction is balanced. It is a common mistake to think that _double_-entry bookkeeping limits transactions to two entries at a time. In fact, the technique is called "double-entry" because each transaction has two sides: one side where money leaves an account and another side where money enters another account.

## Double-Entry Bookkeeping is a Directed Graph

After using double-entry bookkeeping for a while in for my personal finances and trying to find a way to visualize the data, it finally clicked: we're modeling money flow as a [_directed graph_](https://en.wikipedia.org/wiki/Directed_graph).

Think about this: An account is a _node_ in the graph, a credit entry is an _outgoing edge_ with an amount of money leaving this node whereas a debit is an _incoming edge_ with money flowing to another node. A transaction, then, enforces a condition on a set of edges: the outgoing edges must have the same sum of money as the incoming edges.

Let's take a look at the example we've been using so far. First, we fund Alice's and Bob's accounts with money from the bank:

![Graph for the first example: Alice's and Bob's initial balances with the Bank as a source](<../assets/images/double-entry-bookkeeping/Picture 1.drawio.svg>)

A few comments on this graph:
- An account is a round node with the account name.
- A transaction is a square node with the transaction number.
- A credit entry goes from an account to a transaction.
- A debit entry goes from a transaction to an account.
- The entry's amount of money is written on the edge.

We can see that transaction 1 moves $100 from the bank to Alice. Transaction 2 moves $50 from the bank to Bob. The total amount of money in the system is $150.

Then, Alice buys a book from Bob:

![Graph for the second example: Alice buys a book from Bob](<../assets/images/double-entry-bookkeeping/Picture 2.drawio.svg>)

We can see that transaction 3 moves $20 from Alice to Bob. An account's balances is simply the sum of the amounts of the incoming edges minus the sum of the amounts of the outgoing edges. Hence, Alice has $80 and Bob, $70.

We haven't added fees and taxes yet. Let's do this:

![Graph for the third example: fees and taxes](<../assets/images/double-entry-bookkeeping/Picture 3.drawio.svg>)

Granted, transaction 3 is more complex as it conflates what Alice is paying Bob with the fees and taxes. We could split this transaction into two:


```
| Account | Transaction | Description                | Date       | Incoming | Outgoing |
| ------- | ----------  | -------------------------- | ---------- | -------- | -------- |
| Bank    | 1           | Alice's opening balance    | 2024-01-01 |          | $100     |
| Bank    | 2           | Bob's opening balance      | 2024-01-01 |          | $50      |

| Account | Transaction | Description                | Date       | Incoming | Outgoing |
| ------- | ----------  | -------------------------- | ---------- | -------- | -------- |
| Alice   | 1           | Opening balance            | 2024-01-01 | $100     |          |
| Alice   | 3           | Bought book                | 2024-02-01 |          | $22      |

| Account | Transaction | Description                | Date       | Incoming | Outgoing |
| ------- | ----------  | -------------------------- | ---------- | -------- | -------- |
| Bob     | 2           | Opening balance            | 2024-01-01 | $50      |          |
| Bob     | 3           | Sold book                  | 2024-02-01 | $19      |          |
| Bob     | 4           | Sales tax                  | 2024-02-01 |          | $2       |

| Account | Transaction | Description                | Date       | Incoming | Outgoing |
| ------- | ----------  | -------------------------- | ---------- | -------- | -------- |
| CC      | 3           | Transaction fee            | 2024-02-01 | $3       |          |

| Account | Transaction | Description                | Date       | Incoming | Outgoing |
| ------- | ----------  | -------------------------- | ---------- | -------- | -------- |
| Tax     | 4           | Bob's sales tax            | 2024-02-01 | $2       |          |
```

And as a graph:

![Graph for the fourth example: simplified transactions](<../assets/images/double-entry-bookkeeping/Picture 4.drawio.svg>)

We simplified the transactions a little bit:
- Alice sees $22 leaving her account but Bob only receives $19. The remaining $3 goes to the credit card company.
- Bob pays sales taxes in a different transaction.

Regardless of how we model the transactions, the account balances are the same. Alice has $78, Bob has $68, the tax authority has $2, and the credit card company has $3. It is the accountant's job to decide how to group transactions and entries in a way that makes sense for the business as the bookkeeping system is flexible enough to accommodate different needs.

These simple examples show how we can visualize money flow in a double-entry bookkeeping system. The graph grows over time as new transactions are added but it's properties remain the same. In my opinion, understanding bookkeeping as a graph is a powerful way to reason about accounting concepts. Suddenly, things as _balance sheets_, _income statements_, and _cash flow statements_ are just visualizations of this graph. Categories such as _assets_, _liabilities_, _equity_, _income_, and _expenses_ are just groups of nodes in the graph and it is quite easy to understand whether credits or debits increase their balances. It's a way to make accounting more intuitive and less intimidating to me!

## Takeaways

In this article, we've covered the basics of bookkeeping. We started with a simple system that only kept track of balances and evolved it into a single-entry and, later, a double-entry ledger system that models money flow between accounts. We've seen how to represent transactions as entries in a ledger and how to group related entries into transactions. Finally, we've seen how to visualize a double-entry ledger as a directed graph.

In the next article, we'll dive deeper into basic accounting concepts and see how they relate to the graph representation we've seen here.

## Resources

When studying these concepts, I found the following resources particularly helpful:
- [Beancount's documentation](https://beancount.github.io/docs/the_double_entry_counting_method.html) has a great explanation of accounting as a graph over time. It was a big inspiration for this article.
- [Modern Treasury](https://www.moderntreasury.com/journal/accounting-for-developers-part-i) has a great series of articles that explain accounting concepts for developers. It is another big inspiration.
- [This particular thread on Hacker News](https://news.ycombinator.com/item?id=32495724). Some comments are gold!
- [Plain text accounting](https://plaintextaccounting.org/) is a small but engaged community that uses plain text files and command-line tools to keep track of their finances. I use [hledger](https://hledger.org/) for my personal finances.
