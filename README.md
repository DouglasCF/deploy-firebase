# Deploy to Firebase

A GitHub Action to deploy to Firebase.

- Make sure that you checkout the repository using the [actions/checkout](https://github.com/actions/checkout) action.
- Make sure that you have the `firebase.json` file in the repository.
- To obtain the Firebase token, run `firebase login:ci` on your local computer and [store the token](https://docs.github.com/en/actions/reference/encrypted-secrets#creating-encrypted-secrets-for-a-repository) as the `FIREBASE_TOKEN` secret.
- Specify the Firebase project name in the `FIREBASE_PROJECT` env var.

## Workflow examples

Deploy the `main` branch when a commit is pushed to it:

```
name: Deploy the main branch
on:
  push:
    branches:
      - main
jobs:
  main:
    name: Deploy to Firebase
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    - uses: douglascf/deploy-firebase@v0.2
      env:
        FIREBASE_TOKEN: ${{ secrets.FIREBASE_TOKEN }}
        FIREBASE_PROJECT: name-of-the-project
```
