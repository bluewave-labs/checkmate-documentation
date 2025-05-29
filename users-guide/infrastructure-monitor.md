---
icon: server
---

# Infrastructure monitor

The infrastructure monitor is the only feature of Checkmate that retrieves data from remote servers using Checkmate's server agent, Capture. In order to check a remote server's CPU, disk, memory and disk, you need to install Checkmate agent first. Please read [this section](server-monitoring-agent.md) to install Capture.

{% hint style="warning" %}
Note that Capture agent is not installed on the Checkmate server by default.
{% endhint %}

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

For an available list of platforms and what kind of data Capture retrieves, [please see this table](https://github.com/bluewave-labs/capture).

This guide walks you through setting up an infrastructure monitor in Checkmate to track and receive alerts about your server's performance and status.

### Step 1: Click on the Infrastructure Monitor link

Navigate to the **Infrastructure** section in Checkmate and click the **Create** button to access the setup form for creating a new infrastructure monitor.

### Step 2: Configure general settings

In this section, you'll define the server to monitor and provide essential credentials.

1. **Server URL**:
   * Enter the URL of the host you want to monitor. Ensure the server is running the **Checkmate Monitoring Agent** to start data collection.
2. **Display name (optional)**:
   * Add a friendly name for the server to make it easier to identify in your monitoring dashboard.
3. **Authorization secret**:
   * Enter the secret key required to authenticate with the monitoring agent on the server.

### Step 3: Enable incident notifications (optional)

To receive notifications when an incident occurs:

1. Check the box labeled **Notify via email**.
2. Enter the email address where notifications should be sent.

### Step 4: Customize alerts (optional)

Set specific thresholds for server performance metrics. When these thresholds are exceeded, you’ll receive notifications.

1. Check the metrics you want to monitor:
   * **CPU**: Specify a percentage threshold (e.g., 80%) for CPU usage.
   * **Memory**: Specify a percentage threshold (e.g., 70%) for memory usage.
   * **Disk**: Specify a percentage threshold (e.g., 90%) for disk usage.
   * **Temperature**: Specify a temperature threshold (e.g., 75°C).
2. Adjust the thresholds to match your monitoring needs.

### Step 5: Configure advanced settings

Define how frequently the infrastructure monitor checks the server for updates:

* Use the **Check Frequency** dropdown menu to select an interval (e.g., every 15 seconds).

### Step 6: Create the monitor

Once all settings are configured, click the **Create Infrastructure Monitor** button at the bottom of the page to finalize the setup.

Your new infrastructure monitor will now appear in the monitoring dashboard, and it will actively track the server based on your selected preferences.

<figure><img src="https://github.com/bluewave-labs/checkmate-documentation/blob/main/.gitbook/assets/steps_infra.png" alt=""><figcaption></figcaption></figure>
