# DoP Light Meter

Single-file web app for cinematographers:

- **FACE auto** — detects the face (MediaPipe), splits at the nose, and reads the key:fill contrast ratio of the face automatically (median luminance per half, shown as ratio + stops + key side)
- **KEY/FILL taps** — manual two-point contrast ratio
- **CCT spot** — color temperature (Kelvin, McCamy) + green/magenta tint hint
- **Exposure** — relative EV vs 18% grey

No build step — static `index.html`. Requires HTTPS (or localhost) for camera access; FACE auto loads its model from jsdelivr CDN on first use.

Verified in headless Chromium (fake camera): ratio math exact (4.2:1 expected = 4.2:1 shown), CCT of pure white = 6504K, zero console errors.
