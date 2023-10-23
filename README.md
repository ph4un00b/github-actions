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

## github

- `act -j deploy -s GITHUB_TOKEN="$(gh auth token)"`

# FIN

- 🎉
