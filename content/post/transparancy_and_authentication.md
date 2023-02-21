---
title: "Privacy and transparancy: A real-world use case of decentralized authentication"
date: 2023-02-21T17:34:45+05:45
---

# Privacy and transparancy

## Everything encrypted

Every vote is encrypted. Not even us can see the content of your vote. 

## Everything monitorable

A log of the election would be made publicly available (either during or shortly after the election depending of the policy) to everyone to monitor that their vote is being counted

## Everything verifiable

Everyone can verify that the result is the sum of all votes, even though no one can know who has voted for what

<small>(Open, replayable, but encrypted and anonymous. The underlying data structures is a CRDT append-only log)</small>

# Authentication

## Decentralized IDentities (DID)

Users should be able to interact to the network without the need for a central authority.

When selecting a good decentralized authentication scheme, bitcoin-like cryptography is the first thing that came to mind.

In bitcoin people can directly interact with the network without the need of a third party, using only the knowledge of their wallet's secret key.

**The ballot.cipertext events are managed by users**

## Authentication Organisations (AO)

By definition Decentralized Identities can be generated at will.

We need a mechanism to manage the member list, so every real-world member has exactly one identity, one voice.

Autentication organisation are also necessaries when someone loose access to his DID (by loosing access to his device for exemple).

**The ballot.create and ballot.pubkey events are managed by organisations**

## Decentralized Authenticaton

Different organisations can co-organize an election.

Each AO add their own members to the election (**ballot** event).

The election rules could set a maximum to the number of ballot an organisation could provide.

If the election rules allows it, the AO is able to help a user recover his identity if necessary (using the **ballot.pubkey** event), by verifing him by email/phone-number for exemple, or by having him coming to the registration office with his ID card.
