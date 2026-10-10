# Nyth Atom cloud build bundle

This bundle adds a GitHub Actions workflow to attempt a cloud build of the supplied patch project.
It does not contain a prebuilt APK. The workflow has not been executed in this environment, so success is not guaranteed.

## One-time setup from a phone
1. Create a **Private** GitHub repository.
2. Upload `NythAtom_patch_project.zip` to the repository root.
3. Add the workflow file at `.github/workflows/build-apk.yml` using **Add file → Create new file**; copy the contents of the bundled `.github/workflows/build-apk.yml` into it and commit.
4. Open the repository's **Actions** tab, select **Build Nyth Atom APK**, tap **Run workflow**, then wait for the run to finish.
5. If successful, open the completed run and download the `NythAtom-APK` artifact. Extract the downloaded artifact ZIP to get the `.apk` file.

The workflow installs Java 17, Android Build Tools 35.0.0, and Apktool 2.10.0, then runs the project's `build.sh`. It creates a fresh signing key for each run. Keep the repository private because the project ZIP contains the original APK.

## Important
- This is a build automation attempt, not proof that the APK works. The workflow must actually pass before an APK artifact is available.
- The output is signed with a new key and will not update the original app in place. Do not uninstall the original app until you have decided to install and test the rebuilt one.
- Login, gateway access, and gameplay still need real-device testing. Do not assume they work just because signature verification passes.
- If the workflow fails, open the failed job and share the first meaningful error lines to debug it.
