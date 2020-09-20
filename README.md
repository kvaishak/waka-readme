# Dev Metrics in Readme

[Wakatime](https://wakatime.com) Weekly Metrics on your Profile Readme

## Update your Readme

Add a comment to your README like the follows

```md
<!--START_SECTION:waka-->
```text
Go           4 hrs 35 mins   ████████████▓░░░░░░░░░░░░   50.93 % 
JavaScript   2 hrs 58 mins   ████████▒░░░░░░░░░░░░░░░░   32.96 % 
Markdown     56 mins         ██▓░░░░░░░░░░░░░░░░░░░░░░   10.46 % 
HTML         11 mins         ▓░░░░░░░░░░░░░░░░░░░░░░░░   02.13 % 
JSON         8 mins          ▒░░░░░░░░░░░░░░░░░░░░░░░░   01.61 % 
```
<!--END_SECTION:waka-->
```

The lines will be our entrypoints for our metrics.

## Using it

- Get a GitHub Access Token with a `repo` scope and save it in the Repo Secrets `GH_TOKEN = <Your GitHub Access Token>`
- Get your Wakatime API Key and save it as `WAKATIME_API_KEY = <your wakatime API Key>` in your Repository Secrets

That's it. The Action runs everyday at 00.00 UTC

----
Here is Sample Worflow File

```yml
name: Waka Readme

on:
  push:
    branches: [ master ]
  schedule:
    # Runs at 12am UTC
    - cron: '0 0 * * *'

jobs:
  build:
    runs-on: ubuntu-latest
    
    steps:
      - name: Checkout
        uses: actions/checkout@v2
      
      - name: Update Readme
        uses: athul/waka-readme@master
        with:
          WAKATIME_API_KEY: ${{ secrets.WAKATIME_API_KEY }}
          GH_TOKEN: ${{ secrets.GH_TOKEN}}
          USERNAME: <username> # optional, it will automaticially use the username that executing the workflow
```
