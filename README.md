# AQtive Guard AI-SPM Inventory Scan by SandboxAQ

A [GitHub Action](https://github.com/features/actions) for using [AQtive Guard](https://www.aqtiveguard.com/) AI-SPM functionality by [SandboxAQ](https://www.sandboxaq.com/). This action performs static analysis on your code to detect AI assets (such as models, agents, and MCP servers), creating an inventory. This inventory is then  sent to your AQtive Guard instance, where it's enriched with additional information and analyzed for issues. You can view the results in the AQtive Guard web interface. Refer to the [AQtive Guard AI-SPM user guide](https://docs.aqtiveguard.com/aqg-aispm/) for details. 



## Configuration
You can configure the Action as shown in the following example::


```yaml
name: Example workflow for Python using AQtive Guard AI-SPM Inventory Scan by SandboxAQ
on: push
jobs:
  security:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@master
      - name: Run AI-SPM Inventory detection
        uses: sandbox-quantum/aispm-inventory-action@main
        with:
          aqg_instance: https://some_url
          aqg_client_id: ${{ secrets.AQG_CLIENT_ID }}
          aqg_client_secret: ${{ secrets.AQG_CLIENT_SECRET }}
```

## Properties
Properties are passed to GitHub Action via explicit `with` input variables. For security, we strongly recommend using [GitHub secrets](https://docs.github.com/en/enterprise-cloud@latest/actions/how-tos/write-workflows/choose-what-workflows-do/use-secrets) for the sensitive input variables, `aqg_client_id` and `aqg_client_secret`.


| Property          | Required | Description                                                                           |
| ----------------- | -------- | ------------------------------------------------------------------------------------- |
| `aqg_instance`      | yes      | URL of your AQtive Guard instance                                                     |
| `aqg_client_id`     | yes      | Client ID for authentication                                                          |
| `aqg_client_secret` | yes      | Client secret for authentication                                       |

## About
Scans the repository contents for AI usage and reports findings back to AQtive Guard by SandboxAQ.

[Learn more](https://www.aqtiveguard.com/solutions/ai-spm).
