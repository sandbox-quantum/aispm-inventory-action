# SandboxAQ AQtive Guard AI SPM Inventory Scan

A [GitHub Action](https://github.com/features/actions) for using [SandboxAQ](https://www.sandboxaq.com/) AQtive Guard
AI SPM functionality. This action scans your code using static analysis to detect AI assets (such as models, agents, MCP servers, ...).
Once the inventory is created, it'll be sent to your AQtive Guard instance, where it'll be enriched
with additional information and analyzed for issues. You can inspect the results in your AQtive Guard web interface.

You can use the Action as follows:

```yaml
name: Example workflow for Python using SandboxAQ AQtive Guard AI SPM
on: push
jobs:
  security:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@master
      - name: Run AI-SPM Inventory detection
        uses: sandbox-quantum/aqg-actions/aispm-inventory-action@main
        with:
          aqg_instance: https://some_url
          aqg_client_id: ${{ secrets.AQG_CLIENT_ID }}
          aqg_client_secret: ${{ secrets.AQG_CLIENT_SECRET }}
```

## Properties

This Action has properties which are passed to the underlying image, passed as an explicit input variable (using `with`).
We recommend [using secrets](https://docs.github.com/en/enterprise-cloud@latest/actions/how-tos/write-workflows/choose-what-workflows-do/use-secrets)
for `aqg_client_id` and `aqg_client_secret`.

| Property          | Required | Description                                                                           |
| ----------------- | -------- | ------------------------------------------------------------------------------------- |
| aqg_instance      | yes      | URL of your AQtive Guard instance                                                     |
| aqg_client_id     | yes      | Client ID for authentication                                                          |
| aqg_client_secret | yes      | Authentication token to connect to AQtive Guard                                       |

