# Hearts & Crosses online rooms

The GitHub Pages game is connected to the Firebase project
`hearts-and-crosses`. Realtime Database stores room state; Firebase Anonymous
Authentication assigns each player a guest identity so rooms can be restricted
to their two participants. Players do not need accounts.

## Current setup

- Realtime Database: Singapore (`asia-southeast1`), on the Spark no-cost plan.
- Anonymous sign-in: enabled.
- The database starts locked and only permits signed-in users to read waiting
  rooms and participants to access their own rooms. The room host and guest
  identities cannot be replaced after creation.
- The GitHub Pages domain `joyasiwach99-sys.github.io` is authorized.
- Google Analytics and Gemini in Firebase were left disabled.

## Share a room

Open [Hearts & Crosses](https://joyasiwach99-sys.github.io/hearts-and-crosses/),
choose **Create a room**, then share the room code or copy the invite link from
the room badge. Your friend opens the same site, enters the code, and joins.
The host plays Hearts; the guest plays Crosses. Either player can start a new
round.

## Updating the site

The public source is in the
[GitHub repository](https://github.com/joyasiwach99-sys/hearts-and-crosses).
Changes committed to `main` are published automatically by GitHub Pages. Keep
the Firebase web-app config in `index.html` aligned with the Firebase project;
these web-app settings are public client configuration, not private server
credentials.

The database rules are also checked in as `database.rules.json`. If they need
updating, publish them in Firebase Console under **Realtime Database → Rules**.
Do not switch the database to test mode or open public read/write access.

Rooms are not automatically deleted. Old room records can be removed from
Realtime Database in the Firebase console.
