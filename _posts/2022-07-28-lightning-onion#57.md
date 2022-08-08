---
layout: pr
date: 2022-07-28
title: "multi: Route blinding"
authors: [ellemouton]
host: guggero
status: past
commit:
---

## Notes

- This is not a PR in the `lnd` repository, but in the `lightning-onion` library repository that is used by `lnd`.
[https://github.com/lightningnetwork/lightning-onion/pull/57](
https://github.com/lightningnetwork/lightning-onion/pull/57)
- See [this comment](https://github.com/lightningnetwork/lnd/issues/5594#issuecomment-1150822223) about how route blinding fits in with BOLT12 (Offers).
- BOLT specification PR for route blinding: https://github.com/lightning/bolts/pull/765


## Questions

- Who needs to upgrade to make route blinding work?
- What is onion routing? And how does it relate to "Sphinx"?
- Who's privacy does route blinding improve?
- What components does a blinded route contain?
- What will be the payload for each hop in the blinded route?
- What is the difference between blinding and encrypting?
- At a very high level: How does ECDH work? How is it used in route blinding?
- How will the blinded path be communicated to the sender of a payment?
- What are the tradeoffs of using route blinding?
- What's the difference between route blinding and rendezvous routing?
