---
title: Security Interview
parent: Interviews
has_children: true
nav_order: 9
---

# Security Interview
1. **How does an application securely invoke a protected backend service?**{: .label-red }

   The application includes an access token in the request, which the backend service can verify to decide whether access should be granted.

1. **How does OAuth 2.0 allow an application to access resources provided by a different application without asking for the user’s username and password?**

   {: .label-red }OAuth 2.0 enables an application to obtain an access token that grants access to a set of resources provided by a different application on behalf of the user.

1. **What does OpenID Connect add to OAuth 2.0?**{: .label-red }

   OpenID Connect adds an authentication layer on top of OAuth 2.0.


1. **What does JWT add to OAuth 2.0?**{: .label-red }

   OAuth 2.0 does not define a standard format for tokens. By leveraging JWT as the token format, applications are able to directly verify and understand the contents of the token.



