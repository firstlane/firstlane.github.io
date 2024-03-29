---
title: "Buwwshit Part1"
date: 2021-06-18T21:30:42-06:00
author: "firstlane"
---

I work at a company that was acquired about a year and a half ago. Prior to this event, we were an employee-owned company. With the purchase, the company stock that many long-time employees held suddenly multiplied in value. This was a fantastic opportunity for older and loyal employees to see a return on their time invested into the company, so I understand why the decision was made to sell.

For those of us who had been recently hired, this felt a bit like a punch in the gut. We came into the company with promises of employee ownership and a rapidly growing stock, and all of that disappeared.

Fast forward a little over a year. COVID restrictions started to relax and people came back into the office. With coworkers all back in the office together, the memery started once again. Of course, the CEO of our new parent company was a frequent subject of our jokes. One of the individuals in our group would take emails from the CEO, run them through [this uwuifier](https://uwuifier.com/), and forward the modified version to us with the email's existing formatting. There were several times where we would be gathered in one office reading the email, heaving with silent laughter.

In completely unrelated events, I had previously stumbled across [bullshit.js](https://mourner.github.io/bullshit.js/) in a HackerNews comment section (I don't remember what the context was anymore). We also experimented with using this tool on our CEO's emails, leading to similar laughing sessions.

A thought dawned on us: what if we combined Uwuifier and bullshit.js? We discussed how we could go about this, to the extent that we even considered the possibility of making a custom Outlook extension. That evening when I got home, I pulled down Uwuifier and bullshit.js and started creating a React app to make our dreams come true.

It didn't take very long to make an initial cut at the tool, and I got it put up on my GitHub Pages site [here](https://firstlane.github.io/buwwshit/). It had no styling or anything, but it did something. Once I showed it to my coworkers, one of them hopped on board with the development to help me squash some bugs and start thinking about future improvements for the tool.

I haven't touched buwwshit in several weeks now. I still need to get some GitHub Actions setup so that every successful build on master will be pushed to my GitHub Pages site. After that's working, it will be easier to iterate on new features to the tool.
