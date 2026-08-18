---
title: Pakka
date: 2026-08-17T12:00:00-07:00
draft: false
projects: artificialintelligence
featuredImage: /images/pakka.svg
---
## WhatsApp bookings that collect an advance and post the payment themselves

Pakka is a WhatsApp bot for small businesses in India that take bookings and
an advance payment. Built for sports venues first, though the same pattern
fits any shop that takes an appointment and a deposit. A customer books in
Hindi, the owner approves with one tap, and the advance goes straight to the
owner's own UPI id. The moment their bank texts them that the money arrived,
Pakka reads that message and confirms the booking automatically, no payment
gateway and no human re-typing anything.

Pakka is RCM (Revenue Cycle Management) in the US sense: schedule, approve,
collect, post payment. The same loop extends naturally into healthcare RCM
too, since a clinic collecting a copay before a visit runs on the same
mechanism.

## Why payment posting, not just booking

Booking bots are common. The gap is the last step: matching a payment that
already happened to a slot that's still just a maybe. Most merchants here
either can't qualify for a payment gateway or won't pay the fee, so they post
the payment by eyeballing a bank SMS. Pakka reads that same SMS.

| | |
|---|---|
| **Trigger** | owner forwards their own bank/UPI payment message |
| **Match** | amount + timing against bookings on hold |
| **Never settles on** | a customer's screenshot — a claim, not proof |
| **Ambiguous match** | settles nothing, asks the owner instead |

## Running it

```bash
git clone https://github.com/asaraog/pakka
cd pakka
node test.js       # 21 tests, no WhatsApp account or network needed
```

Node 18+, zero dependencies. See the [GitHub repo](https://github.com/asaraog/pakka)
for the full setup, or [pakka.online](https://pakka.online) for the hosted version.
