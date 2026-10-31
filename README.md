# PoC repo: artifact poisoning in a `workflow_run` lint-comment workflow

`main` holds the victim shape: a `Lint` workflow that uploads a `linter-report`
artifact on `pull_request`, and the AdobeDocs `Post Linter Report` workflow that
downloads that artifact from the triggering run and feeds it to
`npm install --no-save github:AdobeDocs/adp-devsite-scripts`.

The `attack` branch simulates a fork PR: it keeps the workflow name `Lint` but
uploads attacker-chosen files (including a `package.json`) inside the artifact
with that exact name.
