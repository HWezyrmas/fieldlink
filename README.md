# Fieldlink

A concept prototype of a field app for crews who work with gloves on, lights off and no signal: fire and rescue, event security, utility field operations.

- **Landing page:** `index.html`
- **The app:** `app/index.html`. Open it on a phone.

## Live voice between phones

Voice messages travel peer to peer over WebRTC. No accounts and no server of our own are needed. Phones find each other through public Nostr relays using [Trystero](https://github.com/dmotz/trystero), then audio goes directly between devices.

1. Open `app/` on two phones.
2. Use the same team code on both. Either open `app/?team=yourcode`, or set it in Setup (the gear icon) and use **Copy invite link**.
3. Tap the screen once on each phone to allow sound, and allow the microphone when asked.
4. Hold the green button to talk and release to send. The other phone plays it as a radio message.

Notes:
- Audio is compressed to 8 kHz radio quality (about 4 KB per second, 30 s maximum per message).
- Messages are not stored. A phone that isn't open when you send misses that message.
- Some corporate or carrier networks block peer-to-peer connections. If phones don't see each other, try both on mobile data or the same Wi-Fi.
- Anyone who knows a team code can join it. Use an unguessable code for anything private.

## Real map and live location

Inside an organization the app switches to a real street map ([MapLibre GL JS](https://maplibre.org) 5.24, bundled in `app/vendor/`, with the free [OpenFreeMap](https://openfreemap.org) dark style; map data © OpenStreetMap contributors). Your GPS position and every other device's position in the organization appear live, with callsigns, accuracy and age. Allow location when the browser asks.

## What's simulated

Outside an organization (the solo demo and guided tour): map data, positions, sensors (air, heart rate, gas), drone and body-cam video, translation and network conditions are simulated for the demo. Live voice between devices is real.

## Hosting

Static files only. On GitHub: Settings → Pages → Deploy from a branch → `main` / root.
