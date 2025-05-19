---
description: >-
  Distributed uptime monitor will be available for the public starting from
  version 2.1. Please get in touch with us if you would like to see a demo.
hidden: true
icon: globe
---

# Distributed uptime

Checkmate's distributed uptime monitor [powered by Uprock](https://prism.uprock.com) is designed to assess and ensure the continuous availability and performance of websites, applications, or services from multiple locations.

This is done by deploying monitoring nodes across various regions. This way it provides a comprehensive view of a service's global accessibility. This way detecting outages or performance issues that might affect users in specific areas can be detected globally, not from a set of predefined locations.&#x20;

Currently, Checkmate's distributed uptime functionality is powered by hundreds of thousands of devices globally.&#x20;

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption><p>Distributed uptime monitor checking Solana's endpoint</p></figcaption></figure>

### **How it works**

1. **Global monitoring nodes:** The system utilizes a network of monitoring nodes in different locations worldwide. Those nodes cover all countries worldwide.
2. **Regular checks:** These nodes perform scheduled checks on the target service, such as sending HTTP requests to a website or pinging a server, to verify its availability and measure response times.
3. **Data aggregation:** The collected data from all nodes is aggregated to provide a holistic view of the service uptime and performance metrics.
4. **Alerting mechanism:** If a node detects an issue, such as downtime or degraded performance, the system can trigger alerts to notify administrators, enabling swift remediation.

This distributed approach ensures that monitoring is not limited to a single point, offering a more accurate representation of a service's global performance and reliability.

[UpRock Prism](https://prism.uprock.com) powered by Checkmate is a platform that offers detailed insights into your website's performance, including load times, downtime incidents, and speed test metrics. This helps you optimize your online presence.

Distributed uptime monitor functionality works with $UPT tokens. When you buy $UPT, you can use distributed uptime monitoring. For more help please [get in touch with us](mailto://hello@bluewavelabs.ca) on how to deploy this service for you and connect your wallet.&#x20;

## Configuring distributed uptime monitor

When you configure your distributed uptime monitor, you can add an endpoint with the help of the configuration pane under Distributed Uptime > Create.&#x20;

This page allows you to set up a new monitor to track the availability and performance of your website or API endpoint. Follow these steps to configure the settings:

* Enter the full URL of the website or API endpoint you want to monitor.
  * Example: `https://www.example.com` or `https://api.example.com/v1`.
* Enter a name to identify this monitor. This is optional and can be helpful if you're monitoring multiple URLs.
  * Example: "Main Website" or "API Endpoint".
* Select the type of monitoring you'd like to perform:
  1. **Website monitoring**:
     * This mode checks your website or API endpoint using HTTP or HTTPS protocols.
     * Choose either:
       * **HTTPS** (recommended for secure websites).
       * **HTTP** (for non-secure endpoints).
* Decide whether you'd like to be notified of incidents (e.g., downtime, errors):
  1. **Enable email notifications**:
     * Check the box if you want to receive notifications.
     * Notifications will be sent to the email address shown
  2. Leave the box unchecked if you don't require notifications
* Select how often the system should check the URL.&#x20;

Once you've filled in the details, click the **Save** button to start monitoring the URL.

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

Once you are done adding your distributed uptime monitor, you'll see it under its sidebar entry. Here you can also edit, clone, remove or delete an uptime using the gear icon.

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

If you need more information about the distributed uptime monitor, please do not hesitate to [contact u](mailto://helllo@bluewavelabs.ca)s.
