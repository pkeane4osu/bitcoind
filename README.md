# Bitcoind

Automate your [Bitcoin](http://bitcoin.org/) transactions with this Ruby interface to the `bitcoind` JSON-RPC API.

## Connecting

Before connecting, you will need to configure a username and password for `bitcoind`, and start
`bitcoind`. Once that's done:

    client = Bitcoind.new 'username', 'password'
      # => #<Bitcoind::Client "http://pkeane4osu:Littlemax44@localhost:8332" >

## Account Balances

You can get the balance of all addresses controlled by the client:

    client.balance
      # => 12.34

You can also get a hash of all accounts the client controls:

    client.accounts
      # => {"14DKRyVa9R1gGtWgiALV4jGrMUVfNm7cfW"=>#<Bitcoind::Account "14DKRyVa9R1gGtWgiALV4jGrMUVfNm7cfW" >, "eve-online ransoms"=>#<Bitcoind::Account "eve-online ransoms" >}

And of course each account has its own balance too:

    ransom = client.accounts['eve-online ransoms']
      # => #<Bitcoind::Account "eve-online ransoms" >
    ransom.balance
      # => 2.19

## Transactions

You can get all the transactions in an account:

    ransom.transactions
      # => [#<Bitcoind::Transaction abadbabe123deadbeef 2.19 to eve-online ransoms at 2011-02-19 16:21:09 -0500>]

You can send money from an account too:

    ransom.send_to '14DKRyVa9R1gGtWgiALV4jGrMUVfNm7cfW', 2
      # => #<Bitcoind::Account deadbeef888abadbeef UNCONFIRMED>

## Making Accounts

Creating an account with an associated address is done through the accounts interface:

    tiny_wings = client.accounts.new 'tiny wings ransoms'
      # => #<Bitcoind::Account "tiny wings ransoms" >
    tiny_wings.address
      # => "14DKRyVa9R1gGtWgiALV4jGrMUVfNm7cfW"

# Contributing

* [Fork the project on GitHub](https://github.com/bkerley/bitcoind)
* Write tests for your changes locally
* Make the tests pass by implementing the changes
* Push your changes to GitHub.
* Send a pull request.

# Copyright

Copyright (c) 2011 Bryce Kerley. See LICENSE.txt for further details.
