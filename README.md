# Vulnerabilities not found elsewhere

From time to time I find vulnerabilities. If this has not been published anywhere else, I publish it here.

## Paradox IP150S Denial of Service Vulnerability

Special setup of the router rsp. firewall connecting the Paradox IP150S to the internet leads to a denial of service because of firmware restart.

The vulnerability has a score of 5.3 (Medium) according to CVSS v3.1 and the vector string is: [CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:N/I:N/A:L](https://www.first.org/cvss/calculator/3.1#CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:N/I:N/A:L).

### Details

The vulnerability affects the Paradox IP150S with firmware V5.02.058. To provoke the denial of service the following steps must be taken:

  * In the router's firewall, block access to port 53/UDP (DNS) for the target IP addresses 8.8.8.8 and 1.1.1.1 with REJECT.
  * At the same time, in the router's firewall, also block access to port 3478/TCP (Paradox InField) with REJECT for all destinations.
  * Now try to access Paradox IP150S port 10000/TCP with Paradox BabyWare. Establishing a connection is practically impossible.
  * When trying to access with a webbroser on port 80/TCP, access is possible only after several attempts.
  * If the connection with the web browser could be established, then several firmware restarts can be found in the event log of the Paradox IP150S at the times of the connection attempts. These firmware restarts are obviously responsible for the failure to establish a connection with Paradox BabyWare or with the web browser.

### Remedy

If the firewall rules in the router are changed from REJECT to DROP, then the vulnerability is not detectable.

### History

2023-06-08: Created ticket [#170067](https://support.paradox.com/portal/en/ticket/580177000054202075) at Paradox support portal.

2023-06-17: Found ticket [#170067](https://support.paradox.com/portal/en/ticket/580177000054202075) has been closed from Paradox support with no feedback.

2023-06-17: Published Paradox IP150S Denial of Service Vulnerability.
