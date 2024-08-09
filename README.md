<h1 align="center">
  upload_github_release_assets_action
</h1>
<p align="center">
   A GitHub Action for creating GitHub Releases on Linux, Windows, and macOS virtual environments
</p>

Fork By [action gh-release](https://github.com/softprops/action-gh-release.git)
Fork By [upload-artifact](https://github.com/actions/upload-artifact)
```
npm install 
node-version 20.2.0
```
## Usage

### ⬆️ Uploading release assets

You can configure a number of options for your
GitHub release and all are optional.

A common case for GitHub releases is to upload your binary after its been validated and packaged.
Use the `with.files` input to declare a newline-delimited list of glob expressions matching the files
you wish to upload to GitHub releases. If you'd like you can just list the files by name directly.

Below is an example of uploading a single asset named `*.zip`

```yaml
name: Main

on: push

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v3
      - name: Build
        run: |
          echo ${{ github.sha }} > Release.txt
          echo atest > atest.txt

      - name: Test-Upload
        run: cat Release.txt
      - name: Release build 
        uses: george012/upload_github_release_assets_action@latest
        with:
          path: ./build/release/*.txt
```