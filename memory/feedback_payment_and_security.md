---
name: feedback-payment-and-security
description: "Never enter payment/card details, King David does that himself. API keys go in .env.master only, never in chat."
metadata: 
  node_type: memory
  type: feedback
  originSessionId: d62f7abd-1ac1-4f04-8ccb-ea31b237dcfb
---

Anything that requires payment: skip it, park it, come back when King David is ready to spend.

Anything security-sensitive (card numbers, bank info): stop and let King David enter it himself directly in the browser. Never type it in chat, never ask him to type it in chat.

API keys ARE okay to read from browser screenshots when they appear during key generation and save directly to .env.master, that's the secure local file, never shared. This is what happened with Gmail App Password (appeared on screen, I saved to .env.master immediately).

**Why:** King David's rule, sensitive info goes nowhere near the conversation. .env.master is the one safe place.

**How to apply:** 
- Payment page appears → navigate away, note what's needed, move to next free task
- API key generated on screen → read it, write to .env.master, move on
- Card/bank details needed → stop, show King David the screen, let him type directly
