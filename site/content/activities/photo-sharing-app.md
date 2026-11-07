---
title: "Instagram-style photo sharing app (Android)"
summary: "Individual Android app project for the Mobile Programming course"
ShowToc: true
---

- **Period:** Spring 2026 (Mobile Programming course)
- **Status:** Completed
- **Type:** Individual course project
- **My role:** Everything — design, implementation, and testing

## Goal {#goal}

Build a working social app where users can post photos, follow each other, and talk one-on-one, using a real backend instead of local data.

## What I did {#role}

This was a solo project. I built:

- Sign-in and a main screen with four tabs: feed, upload, map, and profile
- Likes and comments on posts
- A follow system and a follower/following list
- One-on-one chat that updates in real time, and a chat list showing all conversations
- A map tab that shows where photos were posted

## Process and why {#process}

I used Kotlin with Firebase Authentication and Firestore, so I didn't have to run my own server.

Images are compressed and stored as text (Base64) inside Firestore instead of in a separate file storage service. This kept the whole app on Firebase's free plan and in a single database, without setting up another service.

For chat rooms, I made the room ID by sorting the two users' IDs and joining them. That way both users always get the same room without looking it up first.

## Results {#results}

- A working Android app with all the features above, tested on a real device (Samsung Galaxy S22+), not just the emulator
- A project report and a short demo video, both submitted for the course
