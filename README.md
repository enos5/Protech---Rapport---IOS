# Protech Rapport iOS export

This repository contains the Unity-generated Xcode project in `ios-export/`.
Codemagic builds that project and publishes it to TestFlight.

## Update the Unity export

1. In Unity, build for iOS and select this repository's `ios-export/` directory
   as the output directory. Use **Replace** when you need a fresh export.
   Always select `ios-export/`, because Replace clears the selected directory.
2. Review and commit the changes from the repository root:

   ```bash
   git status
   git add -A ios-export/
   git diff --cached --stat
   git commit -m "Update Unity iOS export"
   git push origin main
   ```

`git add -A ios-export/` includes new, modified, and deleted generated files.
Install Git LFS before working with this repository (`git lfs install`);
native libraries in `ios-export/Libraries/` use LFS.

## Maintain custom files

Keep `codemagic.yaml`, `.gitattributes`, documentation, support/privacy pages,
and other manually maintained files outside `ios-export/` so exports preserve
them. Stage changes to these files separately when committing them.

If Xcode needs custom files or settings in the generated project, keep their
source in the Unity project and apply them with a Unity post-build script.
Manual changes inside `ios-export/` can be removed by the next export.
