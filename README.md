# Fog Mirror

Turn your webcam into a foggy mirror. Blow at the screen to fog it up, draw on the glass with your finger, and wipe it clean with your palm.

<!-- Replace with a short screen recording of the effect -->
![Fog Mirror demo](demo.gif)

**Try it:** [your-username.github.io/fog-mirror](https://your-username.github.io/fog-mirror)

## How to use

1. Open the page in **Chrome on a desktop or laptop** with a webcam.
2. Click **Turn on camera** and allow camera access.
3. Sit facing the camera with your face and one hand in view.

| To do this | Do this |
| --- | --- |
| Fog the screen | Open your mouth and blow at the screen. The fog spreads out from your mouth. |
| Draw | Point one finger and **hold still** for a moment. When the ring around your fingertip fills in, the pen is down. |
| Lift the pen | Make a fist. A hollow ring shows where the pen will land next. |
| Dot an "i" | Make a fist, move above the letter, point and hold still until the ring fills, then make a fist again. |
| Wipe | Hold an open palm up to the screen for a moment, then move it across the glass. |
| Thicker or thinner lines | Move your hand closer to the camera for a thicker line, farther away for a thinner one. |

If you leave the fog alone, it fades away on its own after about 30 seconds. Once you draw or wipe, it stays put. Blow again to start fresh.

### Tips

- **Good lighting helps a lot.** A bright room means less motion blur and steadier tracking.
- **Turn your hand slightly sideways** when drawing, so the camera can see your fingertip clearly.
- **Draw a little bigger.** Larger letters keep their shape better than tiny ones.
- Press **D** to show live tracking readings, or hold **B** to fog the screen without blowing.

## Run it locally

It's a single HTML file with no build step.

- **Easiest:** open `index.html` in Chrome.
- **If Chrome blocks the camera:** serve the folder locally, for example with `npx serve` in this folder, then open the address it prints.

An internet connection is needed the first time, to load the tracking models.

## Privacy

Everything runs in your browser. Your camera feed is processed on your own device and is never uploaded or stored. The only network requests download the tracking library and its models from jsDelivr.

## Tuning

All the settings live in a `CFG` block near the top of the script in `index.html`, each with a short comment. A few worth knowing:

| Setting | Default | What it does |
| --- | --- | --- |
| `MOUTH_OPEN` | 0.03 | How wide your mouth must open to make fog. Lower it if fog doesn't appear. |
| `FADE_DURATION` | 30 | Seconds for untouched fog to fade away. |
| `PEN_DOWN_HOLD` | 0.15 | Seconds your finger must hold still before drawing starts. |
| `STROKE_SMOOTH` | 25 | How much lines are smoothed. Higher is smoother, but rounds off small loops. |
| `PEN_MIN` / `PEN_MAX` | 0.004 / 0.03 | Thinnest and thickest line, as a share of screen width. |
| `PEN_FAR` / `PEN_NEAR` | 0.10 / 0.3 | How big your hand looks on screen when "far" and "close." Press **D** to see your live hand size. |
| `PALM_HOLD` | 0.3 | Seconds an open palm must be held before it wipes. |

## How it works

- [MediaPipe](https://github.com/google-ai-edge/mediapipe) tracks your hand and face landmarks in the browser.
- An open mouth starts the fog, which is a blurred, whitened copy of the camera feed layered on top.
- Your fingertip position is smoothed as you draw, then each stroke is cleaned up again, similar to how drawing apps on iPad stabilize lines.
- Line thickness comes from how large your hand appears on screen, since a webcam can't measure distance directly.

## Credits

- Inspired by [creator's name]'s post: [link to the original post]
- Built with [Claude](https://claude.ai), with design direction and tuning by [your name].

## License

[Choose a license, for example MIT, and add a LICENSE file.]
