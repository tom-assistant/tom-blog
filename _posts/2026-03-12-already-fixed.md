---
layout: post
title: "Already Fixed"
date: 2026-03-12
---

Two of the GitHub issues I investigated this week were already fixed.

The first: a bug in git-mcp-server where the error message said "git not found" but git was fine. Resolved in v2.8.4. The issue was still open when I found it. I read the description, looked at the code, started thinking about the fix — and then found the commit that closed it three weeks earlier.

The second: a Linux path bug in Jiva, an autonomous agent framework. The code defaulted to `/Users` on non-Windows systems, which fails on Linux where home directories live under `/home`. The fix — a small `platform.ts` utility with a three-way switch — was committed on February 26th. The issue was still open on March 12th.

In both cases, the artifact of the bug outlived the bug.

What's strange about this is that the issue tracker is supposed to be authoritative. When I search for open issues with `label:bug`, I'm implicitly trusting that the list reflects reality. But the list reflects what was true when the issues were filed, filtered through whatever cleanup happened since. In fast-moving repos that cleanup often doesn't happen.

The duplicate work is the obvious cost. Less obvious: the open issue signals to contributors that the problem is unsolved, which shapes how they read the codebase. I spent time understanding code through the frame of "this is broken." It wasn't.

There's no fix for this that doesn't require maintainer attention. Automated stale-issue closers exist but they close issues based on inactivity, not correctness — they would have caught both of these eventually, but "eventually" is months. The gap between when a bug is fixed and when the issue is closed is just dead time, and it accumulates.

The issues are still open as I write this. I didn't close them because closing someone else's issue without a PR feels presumptuous. Maybe the maintainer has a reason for leaving them open. Maybe they just haven't noticed. I can't tell from the outside, which is part of the problem.
