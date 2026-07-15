# Product

## Register

product

## Users

Working cinematographers and gaffers on active film sets, plus film students learning lighting. Context: standing on a dark stage or location, phone in one hand (the other holds a flag, a meter, or coffee), ambient light is the thing being measured so the screen must not pollute it. Glances last 2 to 5 seconds between fixture adjustments. The job to be done: read a contrast ratio, a color temperature, or a separation value fast enough to call an adjustment to the crew without breaking rhythm.

## Product Purpose

DoP Meter turns a phone camera into a lighting measurement instrument: face key:fill contrast ratio (auto via face detection), subject-to-background separation, spot stop-offsets, false color exposure, CCT with gel correction suggestions, and relative EV. It exists because real light meters cost $400+ and don't measure ratios from the camera's point of view. Success: a gaffer trusts a reading enough to trim a fixture from it, and the app is worth a one-time pro-unlock price.

## Brand Personality

Precision instrument. Calm, exact, technical. Authority through restraint: the numbers are the interface, everything else recedes. Reference feel: Blackmagic / DaVinci Resolve panel density; muted greys with strictly functional color coding where each hue means one measurement channel. The confidence of gear that belongs on a set, not an app that visits one.

## Anti-references

- SaaS dashboard: KPI card grids, identical rounded tiles, hero metrics. The readouts are instrument channels, not analytics widgets.
- Consumer camera/filter apps: pastel chips, social polish, playful copy.
- Sci-fi HUD cosplay: glows, scanlines, decorative overlays on the viewfinder.

## Design Principles

- Dark is functional, not aesthetic: the screen is used beside calibrated light; every surface must stay near-black so the phone doesn't become a fill source. Brightness is reserved for data.
- One glance, one number: each measurement must be readable at arm's length in under a second; hierarchy tuned for the primary value, context in the small print.
- Color = channel: every hue in the UI is bound to exactly one measurement (key yellow, fill blue, BG purple, spot pink, CCT orange, face green, EV ice). No decorative color, ever.
- Thumb-reachable, glove-tolerant: all controls in the bottom third, targets at least 44px, no gesture-only affordances.
- Never lie about confidence: estimated values are labeled as estimates; failure states say why and what to do, in set language.

## Accessibility & Inclusion

One-handed use is a hard requirement. Touch targets 44px minimum. Readouts must survive bright exteriors (contrast) and pitch-dark stages (no white surfaces). Channel colors chosen to remain distinguishable with deuteranopia (yellow/blue/pink primary distinctions, never red/green pairs alone). Respect prefers-reduced-motion. Text values always accompany color coding.
