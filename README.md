# DoP Light Meter

Single-file web app for cinematographers:

- **FACE auto** — detects the face (MediaPipe), splits at the nose, and reads the key:fill contrast ratio of the face automatically (median luminance per half, shown as ratio + stops + key side)
- **Key : Background** — subject-to-background separation: how many stops the set behind the subject sits under the key side of the face (auto in FACE mode via median luminance of the scene outside the face/body region, or manual KEY→BG taps)
- **KEY/FILL/BG taps** — manual point sampling
- **SPOT map** — pin up to 8 points on sources/areas; each shows its live offset in stops from KEY (or from the first pin). Tap a pin to remove it
- **False color (FC)** — live exposure bands over the image: clip / 99% / hi-light / skin (+1 stop) / 18% grey / shadow / crushed, at sRGB signal positions so it agrees with the EV card
- **Gel calculator** — tap the Color Temp card: measured CCT → target (3200/4300/5600/6500/custom) → mired shift → nearest Lee CTO/CTB gel + resulting CCT, plus ±green correction from tint
- **CCT spot** — color temperature (Kelvin, McCamy) + green/magenta tint hint (offset from the CIE daylight locus)
- **Exposure** — relative EV vs 18% grey

No build step — static `index.html`. Requires HTTPS (or localhost) for camera access; FACE auto loads its model from jsdelivr CDN on first use.

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
