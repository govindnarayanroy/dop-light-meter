# DoP Light Meter

Single-file web app for cinematographers:

- **FACE auto** — MediaPipe Face Landmarker (478 landmarks): skin luminance is sampled at cheek/forehead/chin/nose landmarks only (eyes, brows, lips and the face-oval edge excluded), split along the true forehead-to-chin midline, so hair, background and head tilt can't skew the key:fill ratio
- **Key-light direction** — Lambertian fit of skin luminance against ellipsoid surface normals from the landmark cloud; reports the key's horizontal/vertical angle (e.g. "KEY 35°L · 20°↑") with an on-screen arrow when the fit is confident
- **Key : Background** — subject-to-background separation: how many stops the set behind the subject sits under the key side of the face (auto in FACE mode via MediaPipe person segmentation: background = every pixel not in the subject mask; or manual KEY→BG taps)
- **KEY/FILL/BG taps** — manual point sampling
- **SPOT map** — pin up to 8 points on sources/areas; each shows its live offset in stops from KEY (or from the first pin). Tap a pin to remove it
- **False color (FC)** — live exposure bands over the image: clip / 99% / hi-light / skin (+1 stop) / 18% grey / shadow / crushed, at sRGB signal positions so it agrees with the EV card
- **Histogram (in FC mode)** — DaVinci Resolve-style YRGB/RGB parade histogram: stacked per-channel lanes on the scopes' 10-bit full-range 0–1023 scale (Percentage as the alternate scale style), graticule every 128 code values, legal-video reference markers at 64/940, Y lane colored by the FC bands. Readouts: Y 2nd–98th percentile in code values, % below 64 / above 940, and in RGB mode the mean channel balance vs green in stops. Tap the panel to cycle YRGB/RGB and 10-bit/%
- **Gel calculator** — tap the Color Temp card: measured CCT → target (3200/4300/5600/6500/custom) → mired shift → nearest Lee CTO/CTB gel + resulting CCT, plus ±green correction from tint
- **CCT spot** — color temperature (Kelvin, McCamy) + green/magenta tint hint (offset from the CIE daylight locus)
- **Exposure** — relative EV vs 18% grey

No build step — static `index.html`. Requires HTTPS (or localhost) for camera access; All models (face landmarker, selfie segmenter, WASM runtime) are bundled in `www/mediapipe-tasks/` so the app runs fully offline.

Verified against known cinematography references (fake-camera stills piped into the live app):

| Scene | Documented look | Meter reading |
|---|---|---|
| Kimmy Schmidt trailer | high-key sitcom ≈2:1 | 1.1:1 flat |
| Casablanca, Bergman CU | classic glamour ≈2:1 | 2.5:1 soft |
| Citizen Kane rally | hard stage light ≈4:1 | 3.9:1 classic |
| Double Indemnity, Robinson | film noir 8:1+ | 11.9:1 dramatic |
| TDK interrogation, dark→lights-on | Pfister: "overexposed like five stops" | measured EV jump 5.6 stops |
| TDK interrogation dark, BG | face vs black void | Key:BG 54:1 "night/void" |

Synthetic checks: known 4.03:1 patches → 4.0:1 shown (key:fill and key:BG), pure white → 6500K, tint neutral.
