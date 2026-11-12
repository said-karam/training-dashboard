# Training dashboard

> Proof of concept, not a commercial product. This repository is a write-up only; the source code is private.

## Problem

I wanted my Garmin training data in one simple dashboard I control, without handing my account key to a third-party service.

## What I built

- A sync script on my Mac that pulls my training data from Garmin and keeps only the training numbers (no GPS, no IDs, no profile)
- A private cloud storage bucket that holds that file
- A password-protected website that reads it and shows my training
- An automatic weekly sync: the Mac checks once a day and syncs when the data is a week old and it is on Wi-Fi, with a notification if a sync fails

## Key decisions

- **The Garmin key never leaves my Mac.** The website only ever sees the cleaned numbers.
- **Data minimisation.** Location and personal details are dropped before anything is uploaded.
- **Security basics done properly.** Secure session cookie (only a hash is stored), lockout after 10 wrong passwords, same-origin checks, a strict Content-Security-Policy, and the site is hidden from search engines. Covered by tests.

## Stack

JavaScript (Node.js), Cloudflare Pages and R2, macOS launchd.

## Status

In personal use. Not offered to anyone else.

Built with AI-assisted development (Claude Code).
