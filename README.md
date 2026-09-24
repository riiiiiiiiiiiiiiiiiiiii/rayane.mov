# rayanekabbara site

Single-page portfolio for Rayane Kabbara. Static HTML, no build step.

- `index.html` – the whole site
- `media/` – reels as H.264 mp4 plus poster frames (source .mov files live in `Assets/`, which is git-ignored)

## Publishing on GitHub Pages

1. Create a new repository on GitHub and push this folder to the `main` branch.
2. In the repository settings, open **Pages**, set Source to **Deploy from a branch**, branch `main`, folder `/ (root)`.
3. For the custom domain, enter it under **Custom domain** on the same page (GitHub writes a `CNAME` file), then add the DNS records GitHub shows you at the registrar.

## Re-encoding a reel

```bash
ffmpeg -i "input.mov" -c:v libx264 -preset slow -crf 21 -pix_fmt yuv420p -movflags +faststart -c:a aac -b:a 160k media/output.mp4
ffmpeg -ss 2 -i media/output.mp4 -frames:v 1 -q:v 3 media/output.jpg
```
