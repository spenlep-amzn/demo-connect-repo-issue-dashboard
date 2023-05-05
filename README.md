# blitz-github-dashboard

> Uses a feature from the open source [lowlighter/metrics](https://github.com/lowlighter/metrics/tree/master) project.

Proof-of-concept GitHub OPS Dashboard, for ChatInterface, ChatJS, and UI-Examples repositories

---

<picture>
  <img src="/chat-interface-metrics.repository.svg" alt="Metrics" width="700">
</picture>

<picture>
  <img src="/chatjs-metrics.repository.svg" alt="Metrics" width="700">
</picture>

<picture>
  <img src="/chat-ui-examples-metrics.repository.svg" alt="Metrics" width="700">
</picture>

## Usage

Follow [this documentation](https://github.com/lowlighter/metrics/blob/master/.github/readme/partials/documentation/setup/action.md) to get this set up. This uses a feature from the  open source [lowlighter/metrics](https://github.com/lowlighter/metrics/tree/master) project.

1. Created `todo.yml`

```yml
name: Metrics
on:
  # Schedule daily updates
  schedule: [{cron: "0 0 * * *"}]
  # (optional) Run workflow manually
  workflow_dispatch:
  # (optional) Run workflow when pushing on master/main
  push: {branches: ["master", "main"]}
jobs:
  github-metrics:
    strategy:
      matrix:
        repository: ["chatjs", "chat-interface", "chat-ui-examples"]
    runs-on: ubuntu-latest
    permissions:
      contents: write
      
    steps:
      - uses: lowlighter/metrics@latest
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          template: repository
          filename: ${{ matrix.repository }}-metrics.repository.svg
          user: amazon-connect
          repo: amazon-connect-${{ matrix.repository }}
          plugin_lines: yes
          plugin_followup: yes
```

2. Updated the `README.md`

```
# My Metrics Snapshot

![](./chat-ui-examples-metrics.repository.svg)
```
