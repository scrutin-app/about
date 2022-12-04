---
title: <(^.^)>
---

# First version

A minimalistic mobile voting app leveraging on the [Belenios](https://www.belenios.org/) voting library.

A minimal server will be also built to store elections and votes [(here)](https://gitlab.com/technostructures/scrutin_server). One-time-password will be sent by email to vote for the election, removing the need of user accounts.

<!-- 
For every vote, an email will be sent with a one-time-password to cast a vote.

Only one guardian (the person allowed to tally, i.e. compute the result of the election) is supported.
-->

# Next steps

## Users account and decentralized authentication

Authentication will be done using public-key cryptography.

Organizer can add users by public key directly instead of relying on email. It is the default when the user already has an account.

## Auditing interface

- For anyone to verify that their vote has been counted

- For anyone to verify that the result of an election corresponds to the the ballots in the ballot box (voting urn)

## Quorum of trustees

The private key of the election is shared between multiple trustees.

They have to get together to decrypt the result of the election, improving security.

## Persistent organisations

Manage a list of persistant users (identified by their public keys).

Can organise multiple elections.

## Decentralization

Moving to a decentralized (distributed) architecture.

- Using distributed storage (ex: IPFS) and decentralized identities (public keys)
- Using digital signatures for authenticated actions
  - Creating an election, with a list of voters (when organisations are implemented)
  - Sending a vote
- Publishing the result doesn't require digital signature as it can be verified.
