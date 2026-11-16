# Firebase synchronization setup

Firebase project: `household-chore-tracker-a42b4`.
GitHub Pages app: https://f25h6trccf-boop.github.io/household-chore-tracker/

## Current status
- Firestore production database created; Email/Password Authentication enabled.
- Firebase web configuration is recorded in `firebase-config.js`.
- **Synchronization is NOT enabled yet.** Existing app uses per-device localStorage.
- `firestore.rules` is a safe deny-all starter policy, not an operational rule set.

## Before enabling shared writes
1. Add `f25h6trccf-boop.github.io` to Firebase Authentication > Settings > Authorized domains, if absent.
2. Create unique Firebase Authentication accounts for each participating family member; never put their passwords or a shared parent PIN in GitHub.
3. Bind each Firebase Auth UID to a household member and a server-authorized role. Use Firestore rules to restrict access to this household and validate role-sensitive writes.
4. Adults (Logan, Myk, Natalie) alone may approve bonus point awards. The client must not be able to self-assign adult roles or forge award authorship.
5. Define a single shared household document structure for weekly checkmarks and an immutable bonus award ledger; add realtime listeners and error/offline states.
6. Back up existing localStorage on each device and perform a controlled one-time migration. Avoid merging multiple devices without reviewing conflicting checkmarks and awards.
7. Test with two separate devices/accounts before turning on synchronization.

Do not deploy permissive rules such as `allow read, write: if true`, or grant access to all authenticated users.
