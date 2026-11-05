# dex2rs workspace

This repository is the build workspace for the **Dex2rs** Android app. The app
created it from `rodroidmods/dex2rs-workspace-template` when you signed in.

## What it is used for

When you convert an APK in the app, the app:

1. uploads your APK and method filter here as a release asset named
   `input-<job_id>.zip`,
2. starts the `convert` workflow with that id,
3. watches the run, then downloads `output-<job_id>.apk`,
4. deletes both assets.

Nothing else is stored here. The workflow deletes the input as soon as the run
finishes, and the app deletes the output after downloading it.

## What it costs

GitHub Actions minutes on **your** account, and nothing else. A conversion is
usually a few minutes; the repo is private, so it draws on your monthly
included minutes.

## What not to change

`.github/workflows/convert.yml` is a thin caller. The pipeline itself lives in
`rodroidmods/dex2rs`, so fixes reach every workspace at once. Editing the caller
will not break the app, but the app may rewrite it during a repair.

## Deleting it

Deleting this repository is safe and revokes nothing else. The app recreates it
the next time you convert something, if you still want the cloud build.

## If a build fails

Open the **Actions** tab and read the failed step. The app shows the same log
tail, but the web view has the full output.
