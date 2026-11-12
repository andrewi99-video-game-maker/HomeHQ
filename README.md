# HomeHQ — install guide

**Try it now (no setup):** open `index.html`. Without Firebase it runs in demo mode, saving data on that one device (you can create a household, add helpers, and sign out / switch accounts to preview both sides).

## Put it online so everyone can use it (about 15 minutes, free)
1. **Firebase** (console.firebase.google.com): create a project → Build → **Authentication** → Get started → enable **Email/Password**.
2. Build → **Firestore Database** → Create database (production mode) → **Rules** tab → paste the contents of `firestore.rules` → Publish.
3. Project settings → Your apps → **Web (</>)** → register → copy the `firebaseConfig` values (apiKey, authDomain, projectId, appId) into `const CFG` near the top of `index.html`.
4. **GitHub Pages**: create a repo, upload all files in this folder (index.html, manifest.webmanifest, sw.js, icon-180.png, icon-192.png, icon-512.png, logo.png), then Settings → Pages → Deploy from branch → `main` / root.
5. Firebase → Authentication → Settings → **Authorized domains** → add `YOURNAME.github.io`.
6. Open your Pages link on a phone. **Install:** iPhone: Share → Add to Home Screen. Android/Chrome: ⋮ → Install app (or the Install button in the account menu).

## Using it
- The homeowner taps **Create household**, then **Helpers → Add helper account** (name, username, password) and gives those details to each helper.
- Helpers sign in with the username and password. Account menu (top-right circle) → **Sign out / switch account**.
- To reset a helper’s password, remove the helper and add them again.

## Notes
- Rules let helpers read only the tasks and messages sent to them (or to Everyone); the app shows only what each person should see.
- Photos are compressed and stored in the database (no paid storage needed).
- Notifications appear inside the app while it is open; phone push notifications would need extra setup.

- **Menu and list photos:** the homeowner can photograph the weekly menu (Meals tab) or a written shopping list (Shopping tab). Photos show for everyone. **Read text** uses Tesseract.js (loaded from a CDN, needs internet) to pull the words out so you can fix them and add them as meals or shopping items. Printed text reads well; handwriting usually needs corrections.
- **Add many** creates a whole shopping list from lines you type or paste.
- **Weekly to-do photos:** on the Tasks tab the homeowner can photograph the weekly chore list. **Read text** turns lines like “Mon, Wed: wash the dishes” into tasks (every week on those days, or just this week), sent to one helper or everyone. Helpers see the photo on their Week tab.
- **Logo and icon:** `logo.png` (in-app logo) and `icon-180/192/512.png` (home-screen icon) are made from your emblem. Replace those files to change them.
