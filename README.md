# DualProof — QR + Acoustic Code (Web Proof of Concept)

A Hebrew RTL, mobile-friendly static web demo. A lecturer creates a short-lived QR link and broadcasts an eight-symbol acoustic challenge through the laptop speakers. A student opens the link on a phone, grants microphone access, and the browser decodes the sound locally. The app compares a SHA-256 commitment in the QR to the received acoustic code.

## Run on Mac and phone

**Recommended:** Publish `index.html` using GitHub Pages (Settings → Pages → Deploy from a branch → main / root). Open the HTTPS URL on the Mac and create a session. Scan the QR on the phone. Click **התחלת האזנה** on the phone, then **שידור קוד קולי** on the Mac. Keep the phone close to the Mac speaker for the first test. You do not need Node.js, a phone app, or a backend.

**Local laptop-only check:** Double-click `index.html`. Browsers may restrict microphone access and clipboard when opened as a file, so GitHub Pages HTTPS is recommended for the phone test.

## Caveats

- This is an educational **proof of concept**, not a production attendance system. It has no authentication, backend, persistent attendance, or database.
- QR and audio can both be relayed in real time. The acoustic signal is not reliable proof of physical presence.
- Audio decoding is experimental and may fail on some phone models, browsers, or noisy classrooms. It is deliberately audible (900–2200 Hz). Keep volume comfortable. For first tests, use a quiet room and 0.5–1 m distance.
- The QR code image is loaded from `api.qrserver.com`, a third-party service; it receives the session URL (which contains a public commitment and expiry, not the raw acoustic code). Do not include private student information in the link.
- The QR expires after ten minutes. Device clocks must be reasonably synchronized.
- The demo uses Web Crypto and microphone access; use HTTPS for phone testing.
- No audio is uploaded; it is analyzed in the student's browser.

## Suggested next steps

1. Test on iPhone Safari and Android Chrome at increasing distances.
2. Improve acoustic framing/error correction and verify multiple consecutive frames.
3. Add a backend, authenticated course roster, server-side sessions and expiry, and an attendance dashboard.
4. Add instructor-approved fallback for inaccessible/unsupported microphones.
5. Never publish the real student roster or Israeli ID numbers in a public repository.
