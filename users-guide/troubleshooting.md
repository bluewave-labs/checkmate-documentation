---
icon: syringe
---

# Troubleshooting

### **Q: I installed Checkmate, but I don't see the registration page to sign up for the first time**&#x20;

A: Normally the application will automatically redirect you to the register page if you have not yet created an account.

If the client cannot reach the server then the server client does not know that you do not have an account yet and won't redirect you.

If you are not redirected to /register and you cannot see the sign up page automatically, then client cannot reach the server. Make sure the Checkmate Docker server is running.

