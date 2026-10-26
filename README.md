# Hood Niggaz

A party game for up to four players. This folder runs it as a website on Render, with online rooms anyone can join.

- `server.js` serves the game at `/` and relays online rooms at `/ws`. It has no dependencies.
- `public/index.html` is the whole game.
- `public/music/` holds the soundtrack. HexFall plays in the menus; the others rotate through matches.
- `render.yaml` tells Render how to run it on the free plan.

## Put it online (one time, about 10 minutes)

1. **Make a GitHub repository.** On github.com choose **New repository**, name it `hexfall`, leave it Public or Private, and create it.
2. **Upload these files.** On the new repo's page choose **uploading an existing file**, drag in everything from this folder (keep the `public` folder), and **Commit changes**.
3. **Create the service on Render.** In the Render dashboard choose **New → Blueprint**, connect your GitHub account if asked, pick the `hexfall` repo, and choose **Apply**. Render reads `render.yaml` and creates a free web service called `hexfall`.
   - If you'd rather not use a Blueprint: **New → Web Service**, pick the repo, set **Runtime** to Node, **Build Command** to `echo no build`, **Start Command** to `node server.js`, **Instance Type** to Free, then **Create Web Service**.
4. **Open your link.** When the deploy finishes, Render shows a link like `https://hexfall-xxxx.onrender.com`. That's the game. Send it to friends.

## Playing online

1. Open the link, pick **Online**, and choose **Create a room**. You'll get a four-letter code.
2. Friends open the same link, pick **Online**, type the code and press **Join**.
3. The host presses **Start**.

Nobody needs a Claude or Render account to play.

## Good to know

- **First load can take about a minute.** On the free plan Render puts the server to sleep after 15 minutes with nobody connected. The first visit wakes it up; after that it's instant.
- **Updating the game.** Replace `public/index.html` in the GitHub repo with a new version and commit. Render redeploys automatically in a minute or two. Anyone in a match at that moment gets disconnected.
- **Limits.** Up to 8 connections per room (4 players plus spectators). Render's free plan includes 750 hours a month, enough to keep this one service running all month.
