# Pour: setup checklist

Everything below is one-time. Once done, the app just works and syncs to your Google account.

## 1. Create the Firebase project
1. Go to https://console.firebase.google.com and click **Add project**. Name it (e.g. `pour-drink-log`). Analytics is optional; you can skip it.

## 2. Register a web app
1. In the project, click the **web icon** (`</>`) to add a web app. Give it a nickname. You do NOT need Firebase Hosting.
2. Firebase shows you a `firebaseConfig = { ... }` object. Copy those values.
3. Open `index.html`, find the block marked **PASTE YOUR FIREBASE CONFIG HERE**, and replace each `PASTE_...` value with yours.

## 3. Turn on Google sign-in
1. Left menu → **Build → Authentication → Get started**.
2. **Sign-in method** tab → enable **Google** → set a support email → Save.

## 4. Turn on Firestore
1. Left menu → **Build → Firestore Database → Create database**.
2. Choose a location (e.g. `northamerica-northeast1` for Canada). Start in production mode.
3. Go to the **Rules** tab, paste the contents of `firestore.rules`, and **Publish**.

## 5. Authorize your domains
1. **Authentication → Settings → Authorized domains → Add domain.**
2. Add your GitHub Pages domain, e.g. `yourusername.github.io`.
   (`localhost` is already there if you want to test locally.)

## 6. Deploy to GitHub Pages
1. Put `index.html` in a repo (a new one, or a folder in an existing repo).
2. Repo **Settings → Pages** → Source: your branch (e.g. `main`), root folder → Save.
3. Wait a minute, then open the published `https://yourusername.github.io/...` URL.

## 7. Add to your phone home screen
- **iPhone (Safari):** Share → Add to Home Screen.
- **Android (Chrome):** ⋮ menu → Add to Home screen / Install app.
- Launches full-screen; data syncs from Firestore, and offline changes sync when you reconnect.

## Notes
- The config values are safe to expose in client code; your data is protected by the Firestore rules in step 4, which allow each signed-in user to access only their own documents.
- To use the same app on another device, just open the URL and sign in with the same Google account.
