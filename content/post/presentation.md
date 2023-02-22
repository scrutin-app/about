---
title: "Presentation (draft)"
date: 2023-01-01
---

# What

The most secure voting app in the world.

Everything is made on the device: encryption of the vote, collaborative decryption of the tally (using partial decryption from different entities), verification of the vote

# How

Using the [Helios protocol](https://www.usenix.org/legacy/events/sec08/tech/full_papers/adida/adida.pdf) and INRIA's [Belenios](https://www.belenios.org/) voting library.

# Why

It is useful

# Roadmap

## First version

A minimal server. A one-time-password will be sent to participants by phone or email, removing the need of user accounts.

## Decentralized storage and user accounts

## Auditing interface

- For anyone to verify that their vote has been counted

- For anyone to verify that the result of an election corresponds to the ballots in the ballot box (voting urn)

## Quorum of trustees

The private key of the election is shared between multiple trustees.

They have to get together to decrypt the result of the election, which improves security.

## Persistent organisations

Organisations can choose to manage a list of users (identified by their public keys).

This way they will be able to organise multiple elections with the same set of participants.
