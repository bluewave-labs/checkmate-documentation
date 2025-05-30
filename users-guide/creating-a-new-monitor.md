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

### **Check frequency**

Set the frequency of checks. The default is 1 minute, but you can adjust this based on your requirements.

After completing all configurations, click the **Create monitor** button at the bottom-right to activate your monitor.

### Response validations

When creating or configuring an uptime monitor in Checkmate, you have access to advanced settings that allow for precise response validation. This guide explains how to use these features effectively.

**Match method**

The Match Method determines how Checkmate compares your expected value with the actual response data.

| Method  | Description                                               | Example                                                     |
| ------- | --------------------------------------------------------- | ----------------------------------------------------------- |
| Equal   | Checks if the response exactly matches the expected value | success matches only if response contains exactly “success” |
| Include | Checks if the response contains the expected value        | Welcome matches if response contains “Welcome” anywhere     |
| Regex   | Uses regular expression pattern matching                  | ^\[A-Z]\[a-z]+$ matches any capitalized word                |

\
The Expected Value field defines what you want to check for in the response body content.

### JSON path

The JSON Path field allows you to extract and validate specific data from JSON responses using JMESPath syntax.

#### When to Use JSON Path

* When testing APIs that return JSON responses
* When you need to validate nested data within a complex response
* When you only care about a specific value in a larger JSON object

#### Example Scenarios

**Scenario 1: Checking Website Availability**

| Field          | Value    | Explanation                  |
| -------------- | -------- | ---------------------------- |
| Match Method   | Include  | Partial match is sufficient  |
| Expected Value | \</html> | Looking for HTML closing tag |
| JSON Path      | empty    | Check the entire response    |

**Scenario 2: Verifying User Data in API Response**

| Field          | Value            | Explanation                                    |
| -------------- | ---------------- | ---------------------------------------------- |
| Match Method   | Equal            | Exact match required                           |
| Expected Value | true             | Checking if user is active                     |
| JSON Path      | data.user.active | Extract the active status from the user object |

**Scenario 3: Checking for Error Messages**

| Field          | Value   | Explanation                    |
| -------------- | ------- | ------------------------------ |
| Match Method   | Include | Partial match is sufficient    |
| Expected Value | error   | Looking for any error message  |
| JSON Path      | message | Extract only the message field |

When monitoring websites, it’s essential to understand how Checkmate evaluates responses:

\
How response checking works:

1. Response Body Only: The Expected Value field checks the response body content only, not HTTP metadata like status codes. Checkmate does not provide a direct way to check the HTTP status code through Expected Value.
2. For Website Monitoring (HTML Responses):
   1. Focus on checking for content that should be present on your website:
      1. Use Expected Value: Google with Match Method: Include for Google.com
      2. Use Expected Value: \<html with Match Method: Include for most websites
3. For JSON API Monitoring:
   1. If the API includes the status code in the response body, use JSON Path to extract it:
      1. JSON Path: status with Expected Value: success
   2. For API health checks, look for specific content or status indicators in the response body

### Reliable website monitoring examples

| Website    | Expected Value | Match Method | JSON Path      | Explanation                                    |
| ---------- | -------------- | ------------ | -------------- | ---------------------------------------------- |
| Google.com | Google         | Include      | empty          | Checks if “Google” appears in the response     |
| GitHub.com | GitHub         | Include      | empty          | Checks if “GitHub” appears in the response     |
| Any site   | \</html>       | Include      | empty          | Checks if the HTML document is properly closed |
| API        | "success"      | Include      | empty          | Checks if response contains success message    |
| JSON API   | true           | Equal        | status.success | Checks if success field is true in JSON        |

Remember that for a reliable monitoring, check for content that’s consistently present in your specific website or API response.

\
