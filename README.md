# spotify-tracks-archiver-action V1.0.2

[![pre-commit.ci status](https://results.pre-commit.ci/badge/github/keller00/spotify-tracks-archiver-action/main.svg)](https://results.pre-commit.ci/latest/github/keller00/spotify-tracks-archiver)

A GitHub action to run [spotify-tracks-archiver](https://github.com/keller00/spotify-tracks-archiver)

## Use this action

```yaml
name: Backup Spotify "Saved Songs" library

on:
  schedule:
        - cron: 0 4 * * 6
  workflow_dispatch:

jobs:
  pre-commit:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    - uses: actions/setup-python@v3
    - uses: keller00/spotify-tracks-archiver-action@v1.0.2
      with:
        output-file: library.json
      env:
        CLIENT_ID: ${{ secrets.CLIENT_ID }}
        CLIENT_SECRET: ${{ secrets.CLIENT_SECRET }}
        REFRESH_TOKEN: ${{ secrets.REFRESH_TOKEN }}
```

This does the following:
1. Checks out your repository to commit the JSON file to.
2. It sets up the newest availabe Python 3 (`spotify_tracks_archiver` requires Python 3.9, or newer).
3. Executes `spotify_tracks_archiver`.

This example sets up this job to run once a week.
