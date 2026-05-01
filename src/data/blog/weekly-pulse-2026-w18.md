---
title: "Weekly Pulse — Week 18, 2026"
pubDatetime: 2026-05-01T12:00:00Z
description: "Four stories about AI stopping being a pilot and starting to compound: OptumRx, Morgan Stanley, FedEx, and Jamie Dimon's benchmark."
type: weekly-pulse
tags:
  - weekly-pulse
  - ai-adoption
  - healthcare
  - financial-services
  - supply-chain
draft: false
---

Four stories this week about AI stopping being a pilot and starting to compound.

---

## This Week's AI at Work

**UnitedHealth / OptumRx — Healthcare — Prior authorizations in 30 seconds instead of 8 hours**

OptumRx's PreCheck AI processes prior authorizations at intake — before a human reviewer sees it. The previous average was over eight hours; the new average is under 30 seconds. Complex cases still route to human oversight. Denials from missing information dropped 68%. Appeals dropped 88%. The shift isn't faster review — it's no review. PreCheck decides at intake; humans only see the cases the model flags.

[UnitedHealth Q1 2026 Earnings Call, April 21, 2026](https://www.fool.com/earnings/call-transcripts/2026/04/21/unitedhealth-unh-q1-2026-earnings-transcript/)

---

**Morgan Stanley — Financial Services — 9 million lines of legacy code that no commercial AI tool could read**

Morgan Stanley built DevGen.AI internally because they had no other option: their legacy codebase — mostly COBOL and proprietary banking languages — predates every commercial AI coding assistant. The tool translates legacy code into plain English specifications so any developer can rewrite it. Nine million lines processed in 2025. What looked like a talent problem — COBOL expertise is disappearing — turned out to be a translation problem. AI dissolved the bottleneck without replacing the developers.

[WSJ / Slashdot, January 2026](https://developers.slashdot.org/story/25/06/04/1233253/)

---

**FedEx — Supply Chain — $10M/year saved by predicting equipment failures before they happen**

FedEx's MOBIUS platform reads sensor data from sortation equipment across 41 surface operations facilities and generates proactive maintenance work orders before failures occur. Result: 17,000 hours of sortation downtime prevented, $10 million saved annually. They built it internally — commercial predictive maintenance tools trained on generic equipment are materially worse than a model trained on FedEx's specific machines. MOBIUS is currently deployed to 41 of FedEx's surface operations facilities. FedEx has said publicly the goal is the full network. The $10M is what 41 looks like.

[Supply Chain Dive, April 1, 2026](https://www.supplychaindive.com/news/fedex-ai-usage-rfid-robotics-network-2/816220/)

---

**JPMorgan Chase — Financial Services — Jamie Dimon just gave every enterprise AI program a benchmark to measure against**

"Our $2 billion AI investment has already matched its cost in savings." That's Dimon, Q1 2026, saying publicly what most CEOs won't. GenAI is now deployed across all 240,000 JPMorgan employees. Over 1 million automated code reviews completed this year. Most enterprise AI programs are still in the "investing for the long term" phase of board presentation. JPMorgan just posted the number that ends that conversation.

[Business Insider, April 21, 2026](https://www.businessinsider.com/wall-street-banks-ai-strategy-jpmorgan-goldman-citi-bofa-2026)

---

## The Throwback

**Capital One — 1994 to 2015 — Building a bank on the thesis that credit is a data problem**

In 1994, Rich Fairbank and Nigel Morris convinced Signet Bank to spin out a credit card company built around a single contrarian idea: that credit approval — universally treated as a judgment call by experienced underwriters — was actually a data problem. If you had enough history on how borrowers behaved, a model would outperform the rules committee. Signet backed them. Most of the industry thought it was eccentric.

Capital One spent the next two decades being right. By 2015, gradient-boosted ML models and neural networks were running real-time credit decisions for approximately 65 million customers — not assisting underwriters, running the decisions. Built entirely on a data asset compounded over 20 years of lending history. Fairbank described Capital One in shareholder letters as a technology company that happened to have a banking charter.

The transformation was invisible while it happened. No press release in 2003 announced the replacement of the underwriting rules committee with gradient boosting. Capital One just ran the models, compounded the data advantage, and let the credit performance speak. The "judgment" that everyone said couldn't be systematised was pattern recognition on historical data all along.

---

## From the Blog

**[Stop Automating the Wrong Thing](/stop-automating-the-wrong-thing/)** — Ford didn't speed up invoice processing. FedEx didn't make deliveries faster. Each one noticed a technology had opened a new door and walked through it. The FedEx MOBIUS story is this pattern happening right now.

**[The Data Moat Playbook: How Non-Tech Incumbents Won the Internet Era](/internet-era-quiet-winners/)** — Morgan Stanley built DevGen.AI because no commercial tool could read their code. Capital One built their own credit models because no external dataset matched theirs. The pattern isn't new — and it keeps winning.

---

*Four signals this week: healthcare's most hated bottleneck eliminated, a legacy code backlog finally moving, FedEx predicting failures instead of fixing them, and Dimon giving everyone a benchmark to measure against.*
