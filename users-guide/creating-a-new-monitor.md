---
icon: chart-simple
---

# Uptime monitor

Follow these steps to create a new monitor.

## Checks to perform

Select the type of checks you want to configure:

* **Website monitoring**
  * Uses HTTP(s) protocols to monitor your website or API endpoint.
  * Options: HTTPS or HTTP.
* **Ping monitoring**
  * Confirms the server's availability using ping responses.
* **Docker monitoring:**\
  Monitors whether a Docker container is running.
  * Ensure your Docker daemon is exposed.
  * Docker IDs must be the full 64 char Docker ID.  You can run `docker inpsect <short_id>` to get the full container ID.
* **Port monitoring**
  * Checks whether your port is open or not.

***

## General settings

* **URL to Monitor:**\
  Provide the complete URL of the website or service you want to monitor.
* **Display Name (Optional):**\
  Assign a custom name for easier identification in your dashboard.

***

## Incident notifications

Stay informed when incidents occur:

* **Email Notifications:** Receive alerts via email.
* **Notification integration:** If you want to get notified on Discord, Slack, Telegram or via Webhooks, you can use this section. Click on the button and you'll see a list of notification channels.

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

***

## Ignore TLS/SSL error

If there is a TLS/SSL error when connecting to a service, you can tell Checkmate to continue checking the service's uptime.

## Advanced settings

* **Check frequency:**\
  Set the frequency of checks. The default is 1 minute, but you can adjust this based on your requirements.

After completing all configurations, click the **Create monitor** button at the bottom-right to activate your monitor.

***
