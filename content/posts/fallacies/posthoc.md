---
title: "Post Hoc Fallacy"
date: 2021-07-06
categories:
  - fallacies
draft: false
---

## Overview

---

This logical fallacy comes from assuming sequential events cause one another. 

It should be noted that this fallacy is highly similar to two other fallacies. First, the fallacy of the inverse. If the latter half of the statement is negated, the post hoc fallacy becomes a fallacy of the inverse. Second, the fallacy of affirming the consequent, if A then B; B, therefore A.

## Fallacy Names

---

- False attribution fallacy
- Post hoc fallacy
This name comes from a Latin phrase 'post hoc ergo propter hoc' which translates to 'after this, therefore because of this'.  Commonly called the post hoc fallacy.

## Structure

---

If A, then B. Therefore, A caused B.

## Examples

---

The user provided an authenticated cookie. If a user has an authenticated cookie, then they were authenticated by the system. Therefore, the user has the authenticated cookie because they were authenticated.
- The assumption of past authentication fails if the authenticated session is hijacked.

The timestamp of the authenticated session comes after the authentication request was sent. Therefore, the authentication request verified the user's identity.
- This may not be true. Timestamps can be manipulated and the sequence of events does imply causality. 

## Avoidance

---

In security, this fallacy can arise frequently due to timestamps. Remember that due to timezone and system clock differences, there may be issues with log timestamps. Generally, avoid the assumption that time-series sequential events cause one another.