<p align="center">
    <a href="https://github.com/OpsLevel/service-maturity-library/blob/main/LICENSE" alt="License">
        <img src="https://img.shields.io/github/license/OpsLevel/service-maturity-library.svg" /></a>
    <a href="https://GitHub.com/OpsLevel/service-maturity-library/issues/" alt="Issues">
        <img src="https://img.shields.io/github/issues/OpsLevel/service-maturity-library.svg" /></a>  
    <a href="https://github.com/OpsLevel/service-maturity-library/graphs/contributors" alt="Contributors">
        <img src="https://img.shields.io/github/contributors/OpsLevel/service-maturity-library" /></a>
    <a href="https://github.com/OpsLevel/service-maturity-library/pulse" alt="Activity">
        <img src="https://img.shields.io/github/commit-activity/m/OpsLevel/service-maturity-library" /></a>
</p>

<p align="center">

A collection of check definitions which can be imported to your [OpsLevel](https://www.opslevel.com/) rubric.

### Prerequisite

- [OpsLevel CLI](https://github.com/OpsLevel/cli/)
- [OpsLevel API Token](https://app.opslevel.com/api_tokens)

# Quickstart

The folder structure is setup to group similar check types together.  Each `yaml` file is a check which can be imported into your rubric.  We will walk you through importing a "Custom Event Check" that can parse payloads from Pagerduty and check if there have been no incidents in the last 7 days.

Once you have the opslevel CLI installed and an API token setup clone this repository.  From their navigate in a terminal to the root of the repository.  Inspect our example file:

```sh
cat ./custom_event_checks/demo.yaml
```

All of the fields in this file correspond to fields that can be set in the UI so it should feel familiar.  There are a handful of fields that might need custom values unique to your OpsLevel account.  For the example in this "Custom Event Check" you will need to setup an [integration](https://www.opslevel.com/docs/checks/custom-event/) in your account first and then dig out the alias with the CLI.

- Head over to your [OpsLevel integrations page](https://app.opslevel.com/integrations) and create a new integration.
- Select "Custom Event" and give it a unique name, then click "Create".
- Run `opslevel list integrations` to print out the integrations in a table, find your newly created integration and copy the "ALIAS" value.
- Paste the value you copied into the field `integration` in `./custom_event_check/demo.yaml` and save the file.
- Run `opslevel create check -f ./custom_event_check/demo.yaml` to create the check.
- ... Profit!

Most fields in these check definitions use aliases to reference other resources - always remember you can use the CLI `list` command to get a table which shows you the alias for a given resource.  For example:

```sh
opslevel list categories
```

or

```sh
opslevel list filters
```

Then copy the "ALIAS" field's value into the cooresponding check definition property.

# Contributing

This repository is open to the public for contribution.  While OpsLevel does curate and maintain the files we welcome any and all contributions to collectively build up a library of useful checks that may help others in the future on their service maturity jounery.

## Exporting a Check

The OpsLevel CLI also has the capability to export a check from your account so that you can share them with others.  Please make note of the folder structure when submitting new files to be included.

To perform an export:

- Run `opslevel list checks` to print out the table of your existing checks and copy the "ID" of the check you want to export
- Then `opslevel get check -o yaml XXX_CHECK_ID_XXX > ./custom_event_check/my_example.yaml` to export the check to an importable definition
- Read through the exported file and make sure there is no company specific details
  - You also likely want to comment out the `filter` and `owner` fields as those are usually company specific
- Once you are happy with the definition please submit a PR and an OpsLevel engineer will review it.

Thank you for your contribution!