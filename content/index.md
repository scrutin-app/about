---
title: <(^.^)>
---

# First version

A minimalistic mobile voting app based on the [Belenios](https://www.belenios.org/) voting library.

A minimal server will be built to store elections and votes [(here)](https://gitlab.com/technostructures/scrutin_server). A one-time-password will be sent to participants by email, removing the need of user accounts.

<!-- 
For every vote, an email will be sent with a one-time-password to cast a vote.

Only one guardian (the person allowed to tally, i.e. compute the result of the election) is supported.
-->

# Next steps

## Decentralized user accounts

A keypair is generated in the app and is used to link users to elections and ballots. It is a decentralized account because the account is stored on the app, not on a server. It replaces sending a token by email.

## Auditing interface

- For anyone to verify that their vote has been counted

- For anyone to verify that the result of an election corresponds to the ballots in the ballot box (voting urn)

## Quorum of trustees

The private key of the election is shared between multiple trustees.

They have to get together to decrypt the result of the election, which improves security.

## Persistent organisations

Organisations can choose to manage a list of users (identified by their public keys).

This way they will be able to organise multiple elections with the same set of participants.

## Decentralization

Moving to a decentralized (distributed) architecture.

- Using distributed storage (ex: IPFS) and decentralized identities
- Using digital signatures for authenticated actions
  - Managing the list of voters (adding or removing)
  - Creating an election
  - Casting a vote
- Publishing the result doesn't require digital signature as it can be verified.
