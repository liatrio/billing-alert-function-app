# Billing Alert Function App

This repo is an Azure 3.0 Function app with two functions bundled inside. The two functions are **slack-budget-alert** and **teams-budget-alert**.
With these two functions, a function app can call on these two functions with an HTTP trigger to send budget alerts through Slack and Teams.
    
This repo was created alongside Liatrio's [Cloud Adoption Framework (CAF) for Azure](https://github.com/liatrio/terraform-caf-azure) by [Austin White](https://github.com/austinjw), [Christian Hodges](https://github.com/chodges7), and [Micah Perez](https://github.com/Micahperez2)

### Usage

1. Fork repo so that you can create GitHub Action secrets
2. Find the storage account with our function app inside.
    - In the Liatrio CAF, the name is defaulted to `billingalertfunc`
3. Click containers
4. Find and click the container with your blob 
    - In the Liatrio CAF, the name is `billing-alert-function-releases`
5. Create a shared access token
6. Create repo secret named SAS\_TOKEN with the token you just made
7. Run a workflow dispatch on the **publish-to-azure.yaml** GitHub Action
