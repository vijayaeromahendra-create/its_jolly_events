It's_Jolly_Events PWA (Firebase version) - setup guide
=======================================================

Files: index.html, firebase-config.js, firestore.rules, service-worker.js,
manifest.webmanifest, _headers, icons/   (Its_Jolly_Events.html is a duplicate of index.html)

A. CREATE THE FIREBASE PROJECT (free Spark plan is enough)
1. Go to https://console.firebase.google.com and click Add project.
2. Build > Authentication > Get started > Sign-in method > enable "Email/Password".
3. Build > Firestore Database > Create database > pick a location (Mumbai/asia-south1 is close to India)
   > Production mode.
4. Firestore > Rules tab: replace everything with the contents of firestore.rules and click Publish.
5. Project settings (gear icon) > Your apps > Web (</>) > register app > copy the firebaseConfig values.

B. CONFIGURE THE APP
6. Open firebase-config.js in Notepad and paste your values in place of every PASTE_YOUR... text. Save.

C. DEPLOY TO NETLIFY
7. Netlify > your site > Deploys > drag and drop the CONTENTS of this folder (not the zip file).

D. FIRST USE
8. Open the site on the device that already has your real data. Choose Admin login (default admin / admin123),
   then in the cloud screen click "Create Account" with your email + a password. Your data uploads to the cloud.
9. On your phone and tablet: open the site, sign in with the SAME email and password. The data appears.
   If an old version of the app is installed, remove it and re-add to home screen once.
10. Optional but recommended: in firebase-config.js set window.JOLLY_ALLOW_SIGNUP = false and redeploy,
    so nobody else can create accounts.

HOW SYNC WORKS
- Every change is saved to the cloud within about a second, and other signed-in devices update live.
- Works offline: changes are saved on the device and upload when the internet returns.
- All devices (and workers) share ONE cloud account's data. Worker devices must sign in to the same cloud account
  once; each worker then uses their own worker User ID in the app.

LIMITS / TIPS
- All app data is stored in a single Firestore document, which has a 1 MB limit (thousands of records).
  The app warns if you get close; export backups regularly.
- If two people edit at the exact same moment, the last save wins.
- Change the default admin password in the app before entering real business data.
