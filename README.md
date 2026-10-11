# Counterpane website

Everything is in `index.html`: the 3D viewer, the charts, the copy and the simulation data. There is no build step.

## Put it online tonight (about 5 minutes)

**Netlify Drop (fastest):** go to https://app.netlify.com/drop, sign in, and drag this whole `counterpane-site` folder onto the page. You get a live link in seconds. Rename it under Site settings (for example `counterpane.netlify.app`).

**GitHub Pages:** create a public repository, upload `index.html` and the `assets` folder, then go to Settings > Pages and deploy from the `main` branch.

**Check it on your computer first:** in this folder run `python3 -m http.server` and open http://localhost:8000. Opening the file by double-clicking also works in most browsers.

## Before you submit

- **Contact email** is set to muhammedkhan@college.harvard.edu, in the team section near the bottom of `index.html`.
- **"Who's building it"** has both full names and short bios; edit them near the bottom of `index.html` if you like.
- **Keep the honesty:** the results are from simulation and the prices are estimates. The page says so; judges will trust it more for that.

## What's on the page

1. **Hero:** a live 3D double-hung window at night. "Turn on Duo" calms the vibrating glass and drops the meter; "Take it apart" explodes the device so every part can be clicked; "Play the rumble" is a short audio demo (use headphones). The tabs switch between Duo, Screen, Slim Hood and Screen Pro.
2. Why glass doesn't stop rumble (mass-law chart).
3. An optional full-width video section (see Higgsfield below).
4. How Duo works (three steps).
5. Results, with charts drawn from the simulation data.
6. Other models: Screen, Slim Hood, data-center package.
7. Screen Pro, the future flagship.
8. The research: methods, findings, limits, next steps and references.
9. The business and the team.

## Adding Higgsfield media (optional, about 100 credits)

The page has a full-width section with the line "Sleep with the city outside." It stays hidden until a video exists at `assets/night.mp4`, then appears automatically.

1. **Make a still first.** Stills cost less, and you can pick the best look before spending on video. Use 16:9.
   > Cinematic photo from inside a dark, calm bedroom at night, looking toward a white double-hung window. Amber city lights and light rain outside, soft teal moonlight across the bed, a person asleep in the foreground, shallow depth of field, 35 mm, quiet mood, no text.
2. **Animate it with image-to-video, about 5 seconds.**
   > Slow, steady push-in toward the window. Rain drifts down the glass and the city lights shimmer. The sleeper stays still. No cuts, no camera shake.
3. **Optional product still for your slides** (label it a concept render, since it isn't the real prototype):
   > Close-up product photo of a small white round device, 5 cm across, with a thin glowing teal ring, stuck to a window pane at night, city lights blurred behind, premium studio lighting.
4. **Watch the cost** Higgsfield shows before each generation. A good split is 2 to 4 stills and 1 or 2 videos.
5. **Download the video as MP4 (H.264), 1920 × 1080.** Keep it under about 8 MB. If it's bigger, and you have ffmpeg:
   `ffmpeg -i download.mp4 -vf scale=1920:-2 -c:v libx264 -crf 28 -preset slow -an night.mp4`
   Make the poster image with `ffmpeg -i night.mp4 -frames:v 1 night-poster.jpg`.
6. **Put `night.mp4` and `night-poster.jpg` in the `assets` folder** and upload the folder again.

## How it's built

- three.js r160 from jsDelivr, and Google Fonts (Bricolage Grotesque and Newsreader).
- The 3D models are built in code, so there are no model files to manage.
- The simulation results are embedded as JSON; search `index.html` for `const DATA`.
