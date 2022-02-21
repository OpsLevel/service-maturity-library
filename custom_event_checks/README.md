# Custom Event Check Library

## Overview
With [Custom Event Checks](https://www.opslevel.com/docs/checks/custom-event/), OpsLevel accepts arbitrary JSON payloads from any source such as homegrown internal systems, open-source tooling, or 3rd party vendors that we don’t yet have a first-class integrate with. 

JSON payloads are:
* parsed and mapped to the corresponding services in your OpsLevel account
* evaluated against the specified logic for determining whether a service has passed or failed the check

## Setup
Import any custom event check from this library into your OpsLevel Service Maturity rubric with the steps below:

1. From the [new integraiton menu in OpsLevel](https://app.opslevel.com/integrations/new), create a new Custom Event integration, which creates a new, unique endpoint
1. Import the custom event check using the CLI: `opslevel create check -f ./custom_event_check/$filename.yaml` and you will be prompted to fill out any missing fields from the yaml

## Sending payloads to OpsLevel

TBD
