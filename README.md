# Automated API Monitor (n8n)

A scheduled workflow that monitors a REST API and sends an email
alert when a check fails. Built as a hands-on QA / test automation exercise.

## What it does
- Calls a target API endpoint on a schedule.
- **Availability check:** verifies the API responds (catches connection
  errors and non-2xx status codes).
- **Content assertion:** verifies the response body is correct (e.g. a
  field has the expected value), so a "200 OK with wrong data" is still caught.
- **Alerting:** sends an email report when any check fails, including the
  response details for debugging.

## QA concepts demonstrated
- Test assertions (status code + response content)
- Positive and negative test paths
- Error handling and failure reporting
- Scheduled, automated execution (basic CI-style monitoring)

## How it works
Schedule Trigger → HTTP Request, which branches:
- On connection / HTTP error → email alert ("API down")
- On success → IF assertion on response content → email alert if content
  is unexpected

## Tools
- n8n (workflow automation)
- SMTP (email alerts)

## Usage
Import `api-monitor.json` into n8n, set your own SMTP credentials and
target URL, then publish.
