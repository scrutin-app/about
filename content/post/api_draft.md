---
title: "API (draft)"
date: 2023-02-22T19:03:41+05:45
---

## election
```json
{
  "event": {
    "type": "election",

    "params": election.params,
    "trustees": election.trustees,
    "credentials": election.credentials,

    // This is unrelated to trustees, it's used to manage the ballot/voter list
    "publicKey": orgUser.publicKey
  },
  "eventHash": hash(event)
}
```

## ballot
```json
{
  "event": {
    "type": "election.ballot",

    "election.eventHash": election.eventHash,
    "election.publicKey": election.publicKey,

    // This is here to authenticate the uer when he wants to vote. The user is the only owner of the secretKey.
    "election.ballot.publicKey": user.publicKey,
    // or ballot.token, but a publicKey can always be used instead of a hashed-token by sending the secretKey in place of the hash preimage (by mail, email, other...)
    "election.ballot.ciphertext": ""
  },
  "eventHash": hash(event),
  "auth.publicKey": election.publicKey,
  "auth.signature": sig(election.privateKey, hash(event))
}
```

## ballot.update
```json
{
  "event": {
    "type": "election.ballot.update",
    "election.eventHash": election.eventHash,
    "election.publicKey": election.publicKey,
    "election.ballot.eventHash": ballot.eventHash,
    "election.ballot.publicKey": user.publicKey || newUser.publicKey,
    "election.ballot.ciphertext": null || ciphertext,
  },
  "eventHash": hash(event),
  "auth.publicKey": election.publicKey,
  "auth.signature": sig(election.privateKey, hash(event))

  orgSig: sig(orgSecretKey, eventHash)
}
```

## ballot.delete
TODO

## ballot.pubkey
```json
{
  "event": {
    "type": "election.ballot.pubkey",
    "election.ballot.eventHash": ballot.eventHash,
    "election.ballot.publicKey": ballot.eventHash,
    previousBallot: ballot.eventHash,
    ballot: {
      publicKey,
      ciphertext # empty or unchanged
    }
  },
  eventHash: hash(event),
  orgSig: sig(orgSecretKey, eventHash)
}
```
// To update pubkey key when creating/recovering account
// /!\ Done by the organisation

## ballot.ciphertext
```json
{
  event: {
    type: "election.ballot.ciphertext",
    previousBallot: ballot.eventHash,
    ballot: {
      publicKey, # unchanged
      ciphertext
    }
  },
  eventHash: hash(event),
  sig: sig(secretKey, eventHash)
}
```
// To vote
// /!\ Done by the user
// /!\ When aknowledged, could be locked (not allowing revotes) so that the voter has peace of mind /!\


# Annexe 1: Auth server API
// /!\ Org should maintain their own authentication database (associated for exemple with email or phone number) [not yet 3.0]

POST /users
```json
{
  email
}
```
=> Send an email with a token

POST /user/confirm
```json
{
  pubkey
  email
  token
}
```


# Annexe 2: Web-of-trust part (will not be implemented)

## org
```json
{
  event: {
    type: "org",
    orgPublicKey,
    ...
  }
  eventHash: hash(event),
  sig: sig(orgSecretKey, eventHash)
}
```

## member
```json
{
  event: {
    type: "member",
    org: org.eventHash,
    member: {
      memberPublicKey
    }
  },
  eventHash: hash(event),
  sig: sig(orgSecretKey, eventHash)
}
```

## member.pubkey
TODO

## member.delete
TODO
