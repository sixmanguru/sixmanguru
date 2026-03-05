---
title: "I Built a NCAA Division I Indoor Track & Field Meet Simulator — Here's What It's Telling Me"
date: 2026-03-05T00:00:00+00:00
slug: "ncaa-indoor-simulator-post"
author: "granger"
draft: false
---

If you follow this site, you know I love digging into numbers. For this year's NCAA Division I Indoor Track & Field Championships, I wanted to go further than projections on a spreadsheet — so I built a full web app that actually simulates the meet.

You can check it out yourself right here: [https://web-production-55f65.up.railway.app/](https://web-production-55f65.up.railway.app/)

*Note: Variable adjustment is currently password protected — I'm hoping to open that up to everyone next week.*

Here's how it works, what I found, and why you should temper your expectations of any simulation — including mine.

---

## How the App Works

The app pulls in every NCAA Division I Indoor qualifier across all events, then fetches their actual results. From there, it simulates the meet — scoring it exactly the way the NCAA does — and runs that simulation **5,000 times by default**.

To generate marks for each simulated race or field event, the app uses a random mark derived from each athlete's **top-N results** (defaulting to their top 3). It can look back anywhere from **30 days to 1,000 days** for those marks, with **365 days as the default**. These variables are currently password protected, but I'm planning to open them up to everyone next week. Importantly, those marks are used to create some order and competitive structure, not to predict exact outcomes. Distance events especially can be tactical, and a time on paper doesn't always reflect what happens when the gun goes off.

For multi-section events, the app randomly splits athletes into heats (I'm hoping to update this once actual heat assignments are released, which will make the simulation sharper).

The simulation scores every event, accumulates team points, and does that 5,000 times to build a picture of the probability space — who's likely to score, where, and how often.

---

## What the Numbers Are Saying

### Both Team Races Are Razor-Thin

The first thing that jumps out: **the team races on both the men's and women's sides are extraordinarily close.** This isn't a case where one team runs away with it. The simulations are distributing outcomes across multiple programs in a way that makes a definitive pick feel dishonest.

### The Relays Could Decide Everything

The relays are so evenly distributed across the field in these simulations that **relay points could easily be the swing factor** for multiple teams on both sides. If you're picking a winner, pay close attention to relay lineups and form heading into the meet.

---

### Women's Side: Illinois Has a Path That Involves Zero Track Points

One of the more surprising findings: **Illinois — a field-event heavy program — has a realistic path to the team title without scoring a single track point.** That's a wild statement, but the depth they've shown in the field events makes it plausible in the simulations.

That said, **Georgia, Oregon, and BYU** all have legitimate shots if things break their way. This women's race is genuinely wide open.

---

### Men's Side: Can Penn State Score 20 Points in the 800?

The Penn State men's distance program has been strong, and **the simulation keeps flashing the possibility of Penn State putting up a massive points haul in the 800 meters** — potentially in the range of 20 points from that one event. Whether that actually happens depends on tactical racing, health, and a hundred other factors. But the talent is there.

**Kansas State** emerges as another fascinating storyline — the simulations suggest they could grab a significant chunk of field event points. Can they deliver?

On the balance side, **Arkansas and Oregon** both show up as the most well-rounded men's programs, capable of accumulating points across the full range of track events rather than relying on one or two disciplines.

---

## The Gary Martin Problem (Or Feature)

Here's something fun to try in the app: expand the mark window to include **all-time results**. When you do that, Gary Martin's **3:48 mile from last year's Millrose Games** — which is substantially faster than anything run indoors this season — pushes him to the very front of the Mile projections.

That's not a flaw in the app, it's just math. It's also a reminder of how the mark window you select changes the story the simulation tells. Stick to recent results and you're modeling current form. Open it up and you're weighting a different kind of talent ceiling.

---

## The Altitude Conversion Question

One thing I want to dig into more after the meet: **how do altitude-converted qualifying marks actually translate to sea-level competition?** The app includes those converted marks as submitted, and I've been curious whether athletes who qualified with altitude-converted times outperform or underperform their paper marks at the championships. I'll be revisiting this once the results are in.

---

## Honest Disclaimer: This Is a Simulation

I want to be straight with you: **this is a guess.** A well-constructed, data-driven, 5,000-iteration guess — but still a guess. Track and field at this level is full of tactical decisions, upsets, injuries, and variables no model can fully account for.

My plan is to update the app at least twice more:

1. **After heat sheets are released** — assigning athletes to real heats rather than random ones will improve the accuracy meaningfully.
2. **After Friday's results** — once we have actual outcomes from the first day of competition, we'll only have a handful of field events and finals left to simulate, and the picture will get much clearer.

---

Go explore the app, play with the settings, and see what scenarios you can construct. I'd love to hear what you find — especially if you uncover a combination of settings that surfaces something interesting.

More to come once heat sheets drop.
