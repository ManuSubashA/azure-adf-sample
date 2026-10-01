# azure-adf-sample

Minimal ADF repo for practising Git integration, branching, PRs and publish.

Flow: public CSV on GitHub (HTTP) -> ADF Copy -> ADLS Gen2 `bronze` container,
into `<folderPath>/yyyy/MM/dd/<fileName>`.

## Layout (root folder in ADF = /adf)
    adf/
      linkedService/  ls_http_github, ls_adls_bronze
      dataset/        ds_http_csv, ds_adls_bronze_csv   (both parameterised)
      pipeline/       pl_copy_http_to_bronze            (3 parameters)
      trigger/        tr_daily_copy                     (Stopped by default)

## Before you run it
1. Edit adf/linkedService/ls_adls_bronze.json: replace <YOUR_STORAGE_ACCOUNT>.
2. Create a container named `bronze` in that storage account.
3. Give the factory managed identity the role "Storage Blob Data Contributor"
   on the storage account (Access control IAM).
4. Debug the pipeline in ADF Studio.

## Connect to ADF
Manage -> Git configuration -> Configure -> GitHub -> your repo,
collaboration branch main, root folder /adf,
UNTICK "Import existing resources to repository".

## Practice workflow
feature branch -> edit -> Save all -> pull request -> merge to main -> Publish.
