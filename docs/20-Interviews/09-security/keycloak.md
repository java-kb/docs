---
title: Keycloak Interview
parent: Security Interview
grand_parent: Interviews
has_children: true
nav_order: 1
---

# Keycloak Interview

1. **Can you run Keycloak on Docker and Kubernetes?**{: .label-red }

   Yes. Keycloak distributes container images for Docker, which runs on Kubernetes. There is also a Kubernetes Operator for Keycloak that makes it easier to install and manage Keycloak on Kubernetes.
2. **What is the Keycloak admin console?**{: .label-red }
   
   The Keycloak admin console provides an extensive console to allow you to configure and manage Keycloak, including managing applications and users.

3. **What is the Keycloak account console?**{: .label-red }

   The Keycloak account console provides a self-service console for end users of your applications to manage their own accounts, including updating their profile and changing their password.

4. **How does an application authenticate with Keycloak?**{: .label-red }

   The application redirects the user to the login pages provided by Keycloak. Following authentication, the user is redirected back to the application and the application obtains an ID token from Keycloak that it can use to discover information about the authenticated user.
5. **What do you need to configure in the Keycloak admin console in order to allow an application to authenticate with Keycloak?**{: .label-red }

   For an application to be permitted to authenticate users with Keycloak, it must first be registered as a client with Keycloak.
