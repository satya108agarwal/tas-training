You can use Apps Metrics to see application logs and metrics. Unlike `cf logs` command, logs are persistent and you can search past logs.

Click "View in App Metrics" in Apps Manager.

The following metrics are displayed.

> Note: The three metrics displayed on the first line are called RED metrics and are generally the most important metrics to measure.
> * **Rate** … App Metrics defaults to HTTP Request Count (per minute)
> * **Error** … App Metrics defaults to 5XX error messages per minute (HTTP Request Errors) for the app.
> * **Duration** … App Metrics defaults to the average latency of the app (HTTP Request Latency in milliseconds). Percentile such as "95 percentile" is generally better.

Click "Logs" to display the application log.


By default, only the application log is displayed. Click "App (Application)", select "ALL" or "RTR (Router)", and click "APPLY" button.

The access log is also displayed. It is good to check the access log also.
