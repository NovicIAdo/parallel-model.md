# The parallel model

An association that does not sell anything, funded by the people who belong to
it, which recognises what they give it instead of charging them for what they
take.

This is a working document. It is public so that it can be argued with. If you
think a part of it is wrong, or unlawful, or merely naive, that is the most
useful thing you can tell us — open an issue.

Written by Noviciado, a members' association in Madrid with a venue, a bar and
an events programme. Everything here is what we intend to build, not a
description of a finished thing. Section 9 says exactly how far along it is.

---

## 1. The idea in one paragraph

A member does not buy a drink. A member supports the association, and the
association keeps a record of that support. Later, the member takes a drink,
and the record goes down. Nothing is priced, nothing is sold, and no money
moves between the two events — the second is not a purchase, it is the
association giving something to somebody who has given to it.

Whether that survives contact with tax law is a real question and we are asking
a lawyer. See section 8, which is honest about where it is weakest.

---

## 2. Contribution

A member makes a **voluntary contribution** to the association. It can be:

- **Money.** Cash or card at the venue, or stablecoins on a public chain.
- **A thing.** A sofa for the lounge, a painting for a wall, a set of
  photographs of the venue.
- **Work.** Three hours of DJing. Fixing the plumbing. Running a workshop.
- **Attention.** Sharing an announcement so that more people see it.

All four are contributions and all four are recognised. That is the point of
the model: an association is not only funded by the people with money in it.

### It is not refundable

A contribution cannot be asked back. This is stated at the moment of giving,
and again in the terms a person accepts when they apply to join, and accepting
it is a condition of membership.

We think the honesty is load-bearing. A contribution you can reclaim is a
deposit, and a deposit is a balance, and a balance is the thing this model is
trying not to be. Better to say plainly that the money is gone than to build
something that looks like a wallet and is called something else.

---

## 3. Points

Every contribution is recognised in **points**.

### Getting them

| Contribution | Points |
|---|---|
| Money | 1 point per €1 |
| Anything else | Decided by a manager or an administrator, case by case |

The second row is doing a lot of work and we are not going to pretend
otherwise. A sofa is worth what somebody says it is worth. What makes it
tolerable is that the decision is never automatic, never made by ordinary
staff, and never made without a record: who decided, for whom, for what — in
words, "accepted a sofa from —, 40 points" — how many, and when.

A manager's decision can be overturned by an administrator. An administrator's
cannot be overturned, because the administrator is the association's owner and
how the association develops is theirs to decide.

### Spending them

| What | Points |
|---|---|
| Any drink — water, cola, beer, all the same | 7 |
| A month of membership | 50 |
| A day of membership | 20 |
| A month of membership, student rate | 30 |
| A t-shirt with the association's mark | *to be set* |
| A ticket to an association event | *to be set* |
| A fresh random pseudonym | 2 |
| A pseudonym you choose | 10 |

Every drink costs the same, deliberately, so that the number is not a price.
Our bar already charges €7 flat for all twelve of its drinks, so this changes
nothing about what happens at the counter — only what it is called.

### They do not turn back into money

There is no withdrawal, no transfer between members, no cash value. Somebody
who leaves takes nothing with them. This is the same decision as
non-refundability and for the same reason: the moment points can be cashed out
they are money, and everything else in this document becomes decoration.

---

## 4. The ledger

Every movement is a line: what changed, by how much, why, and who authorised
it. Nothing adjusts a total without leaving one, and there is no path in the
software that changes a total silently.

This matters more than it sounds. The whole model rests on members trusting a
number that only the association can compute. The number has to be explicable
to the person it belongs to, line by line, years later.

---

## 5. Pseudonyms and the ranking

The association publishes a ranking of members by points. Those who have given
most are visible at the top of it. At the end of each month the top three
receive something commemorative.

Nobody is ranked by name. Each member gets a three-word pseudonym —
`TigerHuntingAlone`, `DragonFlyHigh`, `OwlLiveNight`.

- You see your own pseudonym. You do not see anybody else's.
- **Staff cannot see pseudonyms at all** and cannot connect one to a person.
- Only managers and administrators can.
- Members are told this when they apply.

If you dislike yours you can change it, by asking or by spending points, and
the change is logged with who made it and why.

The reason for pseudonyms is not modesty. A public list of who gives the most
money to a private members' club is a list of who has money, attached to a
place they physically go, and publishing it under real names would be a
careless thing to do to your own members.

---

## 6. Where the money arrives

Contributions in money reach the association three ways: cash at the venue,
card at the venue, and stablecoins — USDC and USDT — on public chains.

The stablecoin path is the only one worth describing here because it is the
only one with a design decision in it. The association shows the contributor
an exact amount to send and fixes the euro rate at that moment; a service
watches the public chain, finds the transfer, and records it against the
member. Every contribution keeps its transaction hash, so any line in the
ledger can be checked against a public chain by anybody who doubts it.

The intended shape is one receiving address per member, so a contribution is
identified by where it arrived rather than by how much it was. We began with a
single shared address and matched on the amount, which works and is worse: it
fails exactly when somebody sends a round number, and it fails silently.

---

## 7. The vocabulary

The model is mostly a change of language, and the language is not decoration —
it is the difference between an association and a shop. What the software says
today, and what it should say:

| Today | Under this model |
|---|---|
| Wallet | Contribution / Your contribution |
| Balance | Points |
| €20.01 | 20 points |
| Top up | Contribute · Support the association |
| Add money | Make a contribution |
| Pay at the door | Hand it to staff at the desk |
| Payment method | How you are contributing |
| Price | Points |
| €50 /mo | 50 points per month |
| Buy a membership | Renew with points |
| Purchase | Redeem |
| Charge | Deduct |
| Receipt | Record of contribution |
| Refund | *does not exist* |
| Customer | Member |

Two words are deliberately absent from the whole vocabulary: **price** and
**buy**. If a screen needs one of them, the screen is describing a shop and
should be rewritten rather than translated.

### A note for whoever implements it

Points and euro cents are the same integer with the decimal moved: 1 point =
100 stored units. The existing ledger can stay exactly as it is and be
displayed as points, which means the rename is a language change and not a
migration, and it leaves room for half-points if the association ever wants
them. Rename what members read first. Rename the database when there is a
reason beyond tidiness.

---

## 8. Where this is weakest

The parts we would attack first if we were reading somebody else's version of
this.

**It may be a shop with extra steps.** Contribute money, receive points,
points obtain a drink. Fixed point costs and non-monetary contributions push
against that reading, but they do not settle it, and a tax authority is
entitled to look at substance. This is with a lawyer.

**Points for work is payment for work.** Granting a DJ 100 points for a set,
where points obtain goods and membership, looks like payment in kind however
it is labelled — with everything that follows about employment and social
security. We think this is the sharpest edge in the whole model and it is not
solved by calling it a contribution.

**A points grant is a mint.** Somebody with the right login can create value
out of nothing. Logging every grant and restricting who may make one is
necessary and is not the same as sufficient.

**The ranking is a leaderboard for spending.** We built it to recognise
generosity. It can equally reward compulsion, and a private club is not the
place to find out which. The pseudonyms help. A points-and-prizes ladder aimed
at the same people every month may not be a good idea at all, and we would
rather hear that now.

**Pseudonymised is not anonymous.** Managers and administrators can
re-identify anybody in the ranking, which is right operationally and means the
ranking is personal data under the GDPR whatever it displays.

---

## 9. Status

**Working today:** membership and in-person verification, cash and card at the
venue, stablecoin receipts on Solana and Near with the matching and the ledger
described in section 6, and a member wallet **denominated in euros** — the
thing section 7 replaces.

**Not built:** points, the ranking, pseudonyms, redemption, per-member
addresses, and everything in section 2 about contributions being
non-refundable.

No member has ever held a euro balance with the association. The wallet has
been used only by the owner, testing it, and those records were removed on
1 September 2026. The model can therefore be adopted without unwinding
anything, which is a good position to be in and will not last.

---

## 10. What would help

- Tell us where this is unlawful in your jurisdiction, and what the nearest
  lawful shape is. The second half is the useful half.
- Tell us if you have run something like it and what went wrong.
- Tell us if the ranking is a mistake.
- Argue with the vocabulary. If a word in section 7 still smells like a shop,
  it will end up on a screen and undo the rest.

Issues and pull requests welcome.
