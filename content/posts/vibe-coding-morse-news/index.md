+++
title = "Vibe Coding a Morse Code News Practice Page"
date = 2026-06-01T11:45:00-07:00
draft = false
img = "morse-news.png"
tags = ["projects", "web", "morse-code", "vibe-coding", "ai"]
summary = "I vibe coded a small Morse code practice page that turns current news headlines into CW audio, then linked it up with a couple of older Morse code reference tools: a cheat sheet and a decoder tree."
+++

I have been playing with Morse code again, and one thing I wanted was a
practice source that changes every day. Random practice text is fine, but
copying something with real words and real context feels more like listening to
an actual transmission. So I vibe coded a small web app that sends current news
headlines as Morse code.

The result is here:

> [Morse News practice page](https://morse-news.mckoss.com)

{{< figure src=morse-news.png title="Morse News: current headlines as CW practice" >}}

The page fetches a small set of headlines, then sends them as CW audio in the
browser. It uses Farnsworth timing, so the characters are sent at a steady 20
WPM while the spacing stretches out for slower effective copy speeds. That
makes the rhythm of the characters sound right even when practicing at 5, 10,
or 15 WPM.

Each headline is treated as its own message. At the end of a headline the page
sends the `AR` end-of-message prosign (`.-.-.`), then waits five seconds before
starting the next headline. That little bit of structure matters; otherwise the
headlines run together in a way that is not very pleasant to copy.

The source is also on GitHub:

> [mckoss/morse-news](https://github.com/mckoss/morse-news)

## Vibe Coding It

This was a good example of the kind of coding I have been doing lately: I
describe the experience I want, iterate on the details, and let the AI assistant
do most of the mechanical code changes. The interesting work is not just
"generate a web page." It is the back-and-forth: make the tone adjustable, add
session lengths, keep the UI usable on a phone, separate one headline from the
next, add a visible version number, and push each revision through GitHub so the
host can deploy it.

That style works especially well for small, self-contained tools. The app is
plain HTML, CSS, JavaScript, and a tiny Node/Express server. No build system, no
framework, no complicated deployment machinery.

## Older Morse Tools

This is not my first little Morse code tool. A while back I made a couple of
static references as part of my Morse Keyer project.

The first is a compact cheat sheet for learning the code:

> [Morse Code Cheat Sheet](https://mckoss.com/morse-keyer/cheat-sheet.html)

The second is a decoder tree. It is a visual way to decode Morse by walking left
or right through a binary tree: dot one way, dash the other.

> [Morse Code Decoder Tree](https://mckoss.com/morse-keyer/morse-tree.html)

Those pages are simple, but I still like them. The cheat sheet is useful when
learning the alphabet, and the tree is useful when hearing a character and
trying to decode it on the fly.

Together, the cheat sheet, decoder tree, and Morse News page make a nice little
practice loop: learn the symbols, decode unfamiliar characters, then copy real
headlines by ear.
