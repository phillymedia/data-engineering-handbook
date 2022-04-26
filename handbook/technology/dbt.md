# dbt

[dbt](https://docs.getdbt.com/docs/introduction) (data build tool) is our data modeling and transformation solution. 

dbt development largely consists of writing [Jinja-templated SQL](https://docs.getdbt.com/docs/building-a-dbt-project/jinja-macros/) and YAML configuration files.

## Development

### dbt Core 

#### Workstation Setup

[dbt Core](https://github.com/dbt-labs/dbt-core) ships with a command-line interface (CLI) for running your dbt project. The dbt CLI is free to use and available as an open source project. Use dbt Core when developing on your local machine.

See the following [instructions for developing locally using the dbt CLI](https://docs.getdbt.com/docs/introduction#developing-locally-with-the-command-line-interface-cli).

In Step 2 ("[Set up a profile](https://docs.getdbt.com/dbt-cli/configure-your-profile) to connect to your data warehouse"), refer to the following templates when creating your [`~/.dbt/profiles.yml`](https://docs.getdbt.com/reference/profiles.yml) file, making the appropriate substitutions. There are several methods for conencting to BigQuery, outlined by dbt [BigQuery Profile](https://docs.getdbt.com/reference/warehouse-profiles/bigquery-profile) docs.

##### Service Account Method Template
This method will work for developers with access to the GCS service account key. For others, see the OAuth method below.

```yaml
inquirer-dbt:
  outputs:
    dev:
      dataset: dbt_<Your Inquirer Username>
      keyfile: <path to the service account keyfile>
      location: US
      method: service-account
      priority: interactive
      project: inq-warehouse
      threads: 4
      timeout_seconds: 300
      type: bigquery
  target: dev
```

##### OAuth Method Template

This method will work for anyone with gcloud credentials. See following instructions for [Local OAuth gcloud setup](https://docs.getdbt.com/reference/warehouse-profiles/bigquery-profile#local-oauth-gcloud-setup)

```yaml
inquirer-dbt:
  outputs:
    dev:
      type: bigquery
      method: oauth
      dataset: dbt_<Your Inquirer Username>
      location: US
      priority: interactive
      project: inq-warehouse
      threads: 4
      timeout_seconds: 300
      type: bigquery
  target: dev
```



