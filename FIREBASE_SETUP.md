# Hearts & Crosses: online room setup

The game uses Firebase Realtime Database for live moves and Firebase anonymous
authentication so players can join without creating accounts.

## 1. Create and configure a Firebase project

1. Create a project at [Firebase Console](https://console.firebase.google.com/).
2. In **Build → Realtime Database**, create a database and copy its database URL.
3. In **Build → Authentication → Sign-in method**, enable **Anonymous**.
4. In **Project settings → General**, register a Web app and copy its Firebase
   configuration.
5. In `index.html`, replace the placeholder values in `firebaseConfig` with the
   Web app's `apiKey`, `authDomain`, `projectId`, and `appId`, plus the exact
   Realtime Database URL shown in the console.

The web app config is intended to be public. The database rules below limit room
access to authenticated players; do not put private credentials in `index.html`.

## 2. Publish the database rules and website

Install the Firebase command-line tools, sign in, and select your project:

```sh
npm install -g firebase-tools
firebase login
firebase use --add
```

Choose the Firebase project you created, then deploy the rules and site from
this folder:

```sh
firebase deploy --only database,hosting
```

Firebase Hosting will print a public `https://…web.app` URL. Open it, choose
**Create a room**, and share the six-character room code or the invite link.
Your friend can open the link or enter the code with **Join**. The room code is
also a button in the game header; tap it to copy the invite link.

## Notes

- The first person in a room plays Hearts; the second plays Crosses.
- Either player can start a new round. The score stays with the room.
- Rooms are not automatically deleted. Old room records can be removed from
  Realtime Database in the Firebase console.
- These rules keep reads and writes scoped to authenticated room participants;
  they are intended for a casual game, not for storing sensitive data.
