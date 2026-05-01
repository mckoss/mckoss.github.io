+++
title = "Whidbey Island Dashboard"
date = 2026-05-01T07:00:00-07:00
draft = false
img = "whidbey-dashboard.png"
tags = ["projects", "web", "vibe-coding", "ai"]
summary = """
    We recently bought a vacation home on Whidbey Island — and I turned a
    spare TV into an ambient dashboard showing tides, weather, and ferry
    schedules. It's free to use at dashboard.mckoss.com.
    """
+++

Debbie and I recently bought a vacation home on Whidbey Island. The house had
a couple of unused TVs, and I wanted something useful on them — tides, weather,
ferry times. So I built a dashboard.

## What It Shows

{{< figure src=whidbey-dashboard.png title="TV view (960×540) — fits on one screen with no scrolling" >}}

- **Clock & date**
- **Sunrise & sunset**
- **Moon phase** — SVG, no images, pure geometry
- **3-day weather forecast** — current conditions + highs/lows/wind (Clinton, WA)
- **Tide predictions** — hi/lo table, sparkline, and gauge (NOAA Hansville station)
- **Ferry schedules** — both directions (Clinton ↔ Mukilteo) with live space availability

Everything refreshes automatically and shows a staleness indicator per data source.

## Works on TV, Phone, and Tesla

{{< figure src=whidbey-dashboard-tesla.png title="Tesla screen (1050×700) — vh-scaled fonts make the ferry times larger and easier to read from the driver's seat" >}}

{{< figure src=whidbey-dashboard-mobile.png title="Mobile (390×844) — single column" >}}

The layout is fully responsive. Font sizes are `vh`-scaled, so the Tesla's
taller screen genuinely renders larger text — not just more whitespace. A phone
gets a single-column stacked layout.

On one trip I was sitting in the ferry line at Clinton and noticed the departure
times were hard to read on the Tesla screen. I opened a chat with my AI
assistant ([OpenClaw](https://openclaw.ai)) and described the problem. A few
exchanges later the fix was committed to GitHub and deployed. By the time I
drove off the ferry at Mukilteo the display was fixed.

## Vibe Coded with OpenClaw

The project was built entirely through conversation with AI — describing what I
wanted, iterating on layout and features, without writing much code directly.

The ferry schedule requires an API token from the Washington State Department of
Transportation. When the AI flagged this, I told it to register for one itself
using its email account. It navigated to the WSDOT developer portal, filled out
the form, received the confirmation, and added the key to the config.

## Use It Yourself

The dashboard is live at **[dashboard.mckoss.com](https://dashboard.mckoss.com)**
— free for anyone to use. The
[source is on GitHub](https://github.com/mckoss/whidbey-dashboard).

## Running It on Your TV

For a clean full-screen display with no browser chrome, I use
[Fully Kiosk Browser](https://www.fully-kiosk.com/) on a Google TV. It's an
Android app, so it installs directly from the Play Store on any Google TV or
Android TV device.

1. Install **Fully Kiosk Browser** from the Play Store on your Google TV
2. Open it and enter `https://dashboard.mckoss.com` as the start URL
3. Enable **Kiosk Mode** in the settings to hide all browser controls

That's it. The dashboard fills the screen with no address bar, no tabs, no
extra UI — just the display. It auto-refreshes on its own, so you can leave
it running indefinitely.
