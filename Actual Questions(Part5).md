**Q151(#VPC)**

You are working with a user to set up an application in a new VPC behind a firewall. The user is concerned about data egress. You want to configure the fewest open egress ports. What should you do?

- A. Set up a low-priority (65534) rule that blocks all egress and a high-priority rule (1000) that allows only the appropriate ports.
- B. Set up a high-priority (1000) rule that pairs both ingress and egress ports.
- C. Set up a high-priority (1000) rule that blocks all egress and a low-priority (65534) rule that allows only the appropriate ports.
- D. Set up a high-priority (1000) rule to allow the appropriate ports.

***My choice is A.***

Reason: Every VPC network has two implied firewall rules. These rules exist, but are not shown in the Cloud Console: Implied allow egress rule, Implied deny ingress rule if a higher priority firewall rule may restrict outbound access, A is the answer.

Firewall rules are executed based on the priority. 

See this:https://cloud.google.com/vpc/docs/firewalls#priority_order_for_firewall_rules. 

-----

Q152.()











