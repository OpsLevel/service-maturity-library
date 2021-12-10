# Custom Event Check Library

## Overview
With [Custom Event Checks](https://www.opslevel.com/docs/checks/custom-event/), OpsLevel accepts arbitrary JSON payloads from any source–homegrown internal systems, open-source tooling, or 3rd party vendors we don’t yet have a first-class integrate with. 

JSON payloads are:
* parsed and mapped to the corresponding services in your OpsLevel account
* evaluated against the specified logic for determining whether a service has passed or failed the check

## Setup
Import any custom event check from this library into your OpsLevel Service Maturity rubric with the steps below:

1. Open the .yaml file of the check you want to import
2. From the [new integraiton menu in OpsLevel](https://app.opslevel.com/integrations/new), create a new Custom Event integration, which creates a new, unique endpoint
3. Using the OpsLevel CLI run `opslevel list integrations` to find the integration alias for this new endpoint. Paste this value into the `integration` field of the .yaml file
4. Determine which cell on your rubric (which Category and Level, e.g. _Security_ and _Bronze_) you want to import the check to
5. Using the OpsLevel CLI run  `opslevel list categories` and `opslevel list levels` and paste the appropriate aliases into the corresponding fields of the .yaml file
6. Save the .yaml file
7. Import the custom event check using the CLI: `opslevel create check -f ./custom_event_check/$filename.yaml`

### Notes
These fields are required to successfully import a custom event check: 

* name
* category
* level
* integration
* serviceSelector
* successCriteria

Other fields are optional (and can thus be added later in the UI), but highly recommended.


## Sending payloads to OpsLevel
