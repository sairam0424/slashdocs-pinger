# slashdocs-pinger

Keeps the Render Free web service `slashdocs-sairam0424` awake by requesting its `/livez` endpoint every
10 minutes between 02:00 and 18:59 UTC (07:30 to 00:29 IST). Outside that window the service is allowed to
spin down so the workspace's shared 750 free instance hours also cover two other Free services.

Nothing here is secret: `/livez` is a public health endpoint and the workflow holds a single `curl`. The host
comes from the repository variable `SLASHDOCS_APP_HOST`. The workflow file is a copy of
`deploy/render/pinger.yml` in the private `slashdocs-tools` repository, which documents the arithmetic.

Public on purpose: private-repository Actions minutes are billed per job rounded up to one minute, which
would exhaust the Free plan's 2,000 minutes mid-month; public repositories have unlimited standard-runner
minutes. To pause, disable the workflow under Actions.
