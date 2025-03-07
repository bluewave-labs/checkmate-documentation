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

If you are not redirected to /register and cannot see the sign-up page automatically, this means that the client cannot reach the server. Make sure the Checkmate Docker server is running.

### Q: I get "Uncaught (in promise) Error" and monitors added but keep pending

If you get an error similar to "Uncaught (in promise) Error: A listener indicated an asynchronous response by returning true, but the message channel closed before a response was received at v (VM7845 vendor.js:142:18472)", remove your "AdBlocker Ultimate". This adblocker is known to not work with Checkmate. &#x20;

### Q: I enabled local Docker volume and set up two Docker container monitors. The state remains at "pending".

You can use a [Docker socket proxy](https://github.com/Tecnativa/docker-socket-proxy) to expose the socket to Checkmate.

### Q: I can't access Checkmate outside the host machine

Problem: I'm running Checkmate on a machine (like with IP `192.168.1.2`). I can access it via [http://localhost/](http://localhost/) and it works well. But if I want to access it outside this machine, it doesn't work. I open [http://192.168.1.2/](http://192.168.1.2/), and it loads some part of the UI, but fails after.

Solution: You need to specify the IP address of your host machine (`192.168.1.2` in our case) in `docker-compose.yml`, do the client part know, where the server is. You can do it by updating the address in this variable:

```
UPTIME_APP_API_BASE_URL: "http://192.168.1.2:5000/api/v1"
```

### Is it possible to increase the login token expiry?

Yes, this is configurable via the env file. TOKEN\_TTL is the parameter you would want to set.&#x20;

### Q: Checkmate server fails to interact with docker.sock. How do I fix it?&#x20;

If the Checkmate server fails to interact with docker.sock when mounting the volume, follow those troubleshooting steps:

#### 1. Verify Docker group membership:

* Check the Docker group: Determine the Group ID (GID) of the Docker group.

```bash
getent group docker # This will usually return something like docker:281)
```

#### 2. Configure Checkmate server user

Method 1 (Direct docker.sock mount): Ensure the user field in your Checkmate server configuration includes the GID of the Docker group.

* Compose YAML:
  * user: nobody:281

or

* Compose YAML:
  * user: nobody:\<Docker Group Name>

Important: The User ID (UID) is typically not critical for this scenario.

* For docker CLI you would add new container variables:
  * PUID: UID
  * PGID: Docker GID

Another method is that, if using a Docker socket proxy, ensure the DOCKER\_HOST environment variable is correctly set:

* Compose YAML
  * environment:
  * \- DOCKER\_HOST=tcp://docker-socket-proxy:2375

3. **Check Docker socket permissions**

Verify read-only access: If mounting \`docker.sock\` directly, ensure the read\_only: true option is set in your Checkmate server configuration. This prevents accidental modifications to the Docker daemon.&#x20;

Restart Checkmate server: After making any configuration changes, restart the Checkmate server to apply the updates.

#### 4. Test Docker interaction:

Once the server is restarted, set up a new docker container monitoring with your container ID within your Checkmate server. Monitor the server logs for any error messages related to Docker communication.\




<details>

<summary></summary>



</details>

\


