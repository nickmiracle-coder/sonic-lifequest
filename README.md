# Sonic LifeQuest

An interactive version of the supplied Life Quest book, with a separate Blogger connection for completed-quest posts.

## What is included from the book

- 208 numbered chapter invitations across all 16 chapters, with their book descriptions and chapter notes.
- 108 Country Atlas entries and their three reflection questions.
- 20 Travel Experiences with a matching Travel Field Notes archive shelf.
- All 550 film titles from the Cinema Cabinet, plus its ten cinema-memory prompts.
- The First Times pages, six People Archive pages, 26 Future Sonic prompts, 15 Photo Atlas prompts, eight Unlisted pages, five Make Your Own doors, and the three Next Chapter prompts.

Choose any Book of Doors item to add it to My Life Quest. Finishing a personal quest records its completion date and creates an Adventure Blog post. The book treats these as invitations: skip a prompt, repeat it, or make a door of your own.

## Connect Blogger

The Blogger API is enabled in a free Google Cloud project. A web OAuth client is configured for `http://localhost:8000`, and the signed-in Google account is the only test user. The site is prefilled for `https://sonictheoptimist.blogspot.com` and includes that client ID.

To connect the local preview, serve the contents of this folder at `http://localhost:8000`, open the site, choose **Adventure Blog → Connect to Blogger**, and approve Google’s access screen yourself. Keep **Publish each completed quest automatically** on. When you complete a personal quest while connected, LifeQuest will post its title, category and completion date. If you are disconnected, the post stays as a local draft; reconnect and choose **Publish to Blogger** on that post.

The OAuth app is in Google’s **Testing** mode, so only the configured test account can use it. The browser receives an OAuth access token for the current session; LifeQuest does not store the token or client secret in your files or backup.

When you publish the site to an HTTPS host, add that public website origin to the OAuth client’s **Authorized JavaScript origins** in Google Cloud before connecting from the hosted site. The current OAuth client only allows `http://localhost:8000`. Google may take a few minutes to apply origin changes.

For safety, the Google access token is held only for the current page session. Reconnect after reopening the site. The app does not store the token in your quest data or backup. Turning automatic publishing off keeps future completions as local drafts.

## Data and recovery

Quests, book selections, film ratings and reviews, memory notes, blog drafts, and optional journal photos autosave in this browser. Use **Download full backup** regularly and keep the JSON file somewhere safe. **Restore from backup** restores that complete collection. A backup created on one device can be imported on another.

The public site URL opens the app but does not contain your local collection. **Share snapshot** creates a separate read-only link with completed quest titles, themes and dates only. It excludes journal entries, photos, film reviews, unfinished quests, and Blogger drafts.

Clearing this browser’s site data can remove the local collection; restoring the JSON backup recovers it. The Google access token is not part of backups, so connect Blogger again after restoring.

## Publish the site

Upload all three site files (`index.html`, `app.js`, and `lifequest-book.js`) to a static host such as GitHub Pages, Netlify, or Cloudflare Pages. No build command or database is required. Use the HTTPS site URL for the public profile and register that same origin in the Google OAuth client. Browser-only progress stays in the browser where it was entered; it does not sync across devices. Use **Download full backup** to protect progress and **Share snapshot** for a read-only public view of finished quests.

