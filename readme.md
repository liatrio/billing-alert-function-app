# Billing Alert Function App

This repo is an Azure 3.0 Function app with two functions bundled inside. The two functions are **slack-budget-alert** and **teams-budget-alert**.
With these two functions, a function app can call on these two functions with an HTTP trigger to send budget alerts through Slack and Teams.
    
This repo was created alongside Liatrio's [Cloud Adoption Framework (CAF) for Azure](https://github.com/liatrio/terraform-caf-azure) by [Austin White](https://github.com/austinjw), [Christian Hodges](https://github.com/chodges7), and [Micah Perez](https://github.com/Micahperez2)

### Usage

- Fork repo so that you can create GitHub Action secrets
- Create a shared-access-token through your cli

```bash
sas=`az storage blob generate-sas \ 
	--account-name <account-name> \
	# ex: stillingalertfunc \ 
	--container-name <container-name> \ 
	# ex: stc-billing-alert-func-dev-centralus \
 	--name <blob-name> \ 
	# ex: stb-billing-alert-func-dev-centralus \
 	--permissions rw \
 	--https-only \
 	--expiry <expiry-time> \ 
	# ex: 2022-05-01T00:00:00Z \
 	-o tsv`
echo $sas
```
- Create repo secret named SAS\_TOKEN with the token you just made
- Create repo secrets for BLOB, CONTAINER, and ACCOUNT_NAME that match the ones used in the above command
- Run the workflow dispatch on the **publish-to-azure.yaml** GitHub Action to upload the function code to your blob storage
