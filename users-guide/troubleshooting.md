---
icon: syringe
---

# Troubleshooting

## **General troubleshooting steps**

If you are having trouble running Checkmate, those are the general steps you can take towards finding the issue.&#x20;

**Verify port availability:**&#x20;

* Ensure the port used by the Checkmate server (e.g., 5000) is not already in use by another application or container.&#x20;
* Check environment variables: Verify that all required environment variables are set correctly with valid values.&#x20;
* Check database connections: If using external databases (Redis, MongoDB), verify that the client points to the correct IP address and port for each database.&#x20;
* Check for port interference: Verify that no other containers or applications create port conflicts.

**Check network connectivity:**

* Verify your internet connection.
* Check for firewall/antivirus interference.
* Review proxy server settings.

**Check Docker server status:**

* Access the Docker dashboard to check the server container's status.
* Inspect the server container's logs for error messages.

**Check application configuration:**

* Review client-side configuration for any misconfigurations.
* Enable debug logging: Enable error or warn log levels in the client application for more detailed troubleshooting information.

**Test server endpoint directly**:

* Try accessing the server endpoint directly in your browser (e.g., localhost:5000/api/v1).
  * If you see any message other than "Cannot GET /api/v1" error, it indicates that the server might not be binding to the specified port or is not running correctly, regardless of what the server logs show.

**Restart Checkmate Docker services:**

* Restart the Checkmate server container.
* Restart the Checkmate client container.
* Restart the MongoDB client container.

**Clear browser cache and cookies**

* Clear your browser's cache and cookies.

## General FAQ

### **Q: I installed Checkmate, but I don't see the registration page to sign up for the first time**&#x20;

A: Normally the application will automatically redirect you to the register page if you have not yet created an account.

If the client cannot reach the server then the server client does not know that you do not have an account yet and won't redirect you.

If you are not redirected to /register and you cannot see the sign up page automatically, then client cannot reach the server. Make sure the Checkmate Docker server is running.

