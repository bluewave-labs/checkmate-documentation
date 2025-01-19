---
icon: plus
---

# Uptime monitor

Creating a new monitor involves a few steps, as mentioned below.

### General settings

* **URL to monitor:** Enter the full URL of the website or service you want to monitor.
* **Display name:** Optionally, provide a custom name for your monitor. This helps identify it easily in your dashboard.

### Checks to perform

* **Website monitoring:** This option uses HTTP(s) to monitor your website or API endpoint. You can choose between HTTPS and HTTP protocols.
* **Ping monitoring:** Checks whether your server is available.&#x20;
* **Docker monitoring:** Checks whether a Docker container is running. To do this, you need to expose your Docker daemon.

### Incident notifications

When there's a new incident, you can choose how to be notified. Currently it supports notification by email, and soon there will be more ways to notify the admin.

### Advanced settings

* **Check frequency:** Set how often the system should check your monitor. The current setting is 1 minute, but you can change this duration to reflect your requirements.

After configuring all settings, click the "Create monitor" button at the bottom right to set up your new monitor.
