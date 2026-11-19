# Personal Dictionary

A Flutter app for building a personal vocabulary collection and reviewing it with flashcards. It tracks words and phrases as they move through a review box, and it can import saved translations from a spreadsheet.

## How it works

- Sign in through Firebase Authentication. Cloud Firestore stores the vocabulary and review state per account.
- Import an Excel workbook with a worksheet named **Saved translations**. [The import routine](lib/home_page.dart) defines the column and worksheet expectations.
- Review words and phrases in [the card view](lib/cards_list.dart). [The vocabulary model](lib/models/words.dart) tracks new items, the review box, and completed words.

For an independent deployment, connect the target platform to your own Firebase project, enable the sign-in method used by the app, and configure Firestore rules to isolate each user's data. Review [app initialization](lib/main.dart) to configure error reporting for your own environment.

## Run locally

Check the SDK and dependency constraints in [`pubspec.yaml`](pubspec.yaml) before choosing a Flutter SDK. This project was originally written for Dart 2.

```sh
flutter pub get
flutter run
```

## Dependency updates

Use `flutter pub get` to install the versions recorded in `pubspec.lock`.
The `archive` constraint keeps the resolver on releases with the fixes
for CVE-2023-39139 and CVE-2023-39137. Keep the version floor when updating
the packages that use it and review the lockfile before committing changes.
