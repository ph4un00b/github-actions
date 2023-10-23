# Overview

Simple Node.js application to demonstrate the use of GitHub Actions

# Look Ma, no Makefile!

All the tasks necessary for testing, building and deploying this code is already
defined in `.github/workflows/` so why would you want to also create a
`Makefile` for local development? Now you can use
[act](https://github.com/nektos/act) to run the actions locally!

Try these:

- `act -j test` - run the tests
- `act` - run the the entire pipeline
- `act -l` - view the execution graph

## required

- gh

## env

- `act -j env` - takes .env file by default❗
- `act -j env --env-file .env.example`

## workflow dispatch

- `act -j dispatch --input A=from --input B=cmd`
- `act -j dispatch -e .\payload.json`
- `-j payloadEv -s GITHUB_TOKEN="$(gh auth token)" -e .\payload.json`

## github

- `act -j deploy -s GITHUB_TOKEN="$(gh auth token)"`

## endpoints

- get:
  `gh api -H "Accept: application/vnd.github+json" -H "X-GitHub-Api-Version: 2022-11-28" /repos/ph4un00b/github-actions`
- post event wget:
  `wget --header="Accept: application/vnd.github+json" \ --header="Authorization: Bearer <YOUR-TOKEN>" \ --header="X-GitHub-Api-Version: 2022-11-28" \ --post-data='{"event_type":"on-demand-test","client_payload":{"unit":false,"integration":true}}' \ --no-check-certificate \ --output-document=output.json \ https://api.github.com/repos/OWNER/REPO/dispatches`
- post event ps:
  `Invoke-RestMethod -Uri "https://api.github.com/repos/ph4un00b/github-actions/dispatches" -Method Post -Headers @{"Accept" = "application/vnd.github+json"; "Authorization" = "Bearer $(gh auth token)"; "X-GitHub-Api-Version" = "2022-11-28"} -Body '{"event_type":"on-demand-test","client_payload":{"unit":false,"integration":true}}' -ContentType "application/json"`

# FIN

- 🎉
