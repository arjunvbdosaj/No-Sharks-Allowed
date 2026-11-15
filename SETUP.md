# Shared saving with Firebase

This lets you and Kanon see each other's entries. It takes about 10 minutes and is free.

1. Go to https://console.firebase.google.com and sign in with a Google account. Choose **Create a project**, give it a name such as `no-sharks-allowed`, and finish (you can turn Google Analytics off).
2. In the left menu choose **Build, then Firestore Database, then Create database**. Pick a location near you (for example `europe-west2` for London) and start in **production mode**.
3. Open the **Rules** tab, replace everything with the text below, and click **Publish**:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /tracker/{doc} {
      allow read, write: if true;
    }
  }
}
```

4. Click the gear next to "Project Overview", then **Project settings**. Under **Your apps** click the web icon `</>`, give the app any name, and register it. Firebase shows a block of settings called `firebaseConfig`.
5. Open `config.js` in this folder and copy the `apiKey`, `authDomain`, `projectId` and `appId` values from Firebase over the ones that say PASTE. Keep the quote marks.
6. Upload the changed `config.js` to your GitHub repository (open the file on GitHub, click the pencil, paste, and commit).
7. Open the site on both phones. The line under the title should read **Shared and saved**.

## About privacy
These rules let anyone who has the site address and finds the project ID read and change the tracker data. For a gym log that is usually fine. If you want only the two of you to get in, ask for a version with a sign-in, which uses Firebase Authentication.

## If it says "Saved on this device only"
The settings in `config.js` are missing or wrong, the rules were not published, or Firestore was not created. Check each step above.
