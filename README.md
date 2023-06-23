# Vulnerabilities not found elsewhere

From time to time I find vulnerabilities. If this has not been published anywhere else, I publish it here.

## Auth Bypass in Google Familiy Link

This vulnerability is about bypassing restrictions on access rights in Google Familiy Link.

If the daily limit in Google Family Link is reached, then the daily limit can be bypassed by removing the battery without shutting down the cell phone. The cell phone can continue to be used after a restart without respecting the daily limit of Google Family Link.

The vulnerability has a score of 4.1 (Medium) according to CVSS v3.1. The vector string is: [CVSS:3.1/AV:P/AC:L/PR:L/UI:R/S:U/C:N/I:N/A:H](https://www.first.org/cvss/calculator/3.1#CVSS:3.1/AV:P/AC:L/PR:L/UI:R/S:U/C:N/I:N/A:H).

### Details

This vulnerability was abused from my child that was looking endlessly Youtube videos.

Versions of the installed apps:
* Google Family Link: 1.86.0.0.419708555 1)
* Google Family Link Manager: 1.0.0.257492102 2)
* Android: 5.1 Lollipop MR1 (22)

A short video of my child demonstrating the vulnerability.

### Remedy

None.

### Researcher

[Uwe Disch](https://github.com/uwedisch/)

### History

2023-06-20: Created the report [Auth Bypass in Google Familiy Link](https://bughunters.google.com/profile/5f5d3940-408e-4bf5-9ccc-66cb1461adcb/tracker/5088218895613952) at Google Bug Hunters

2023-06-23: After a few status updates on the report, this was closed because ... _the described scenario cannot be scaled up to im­pact a large number of users or the platform as a whole._

2023-06-23: Published the vulnerability [Auth Bypass in Google Familiy Link](https://issuetracker.google.com/issues/288188498).

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

### Researcher

[Uwe Disch](https://github.com/uwedisch/)

### History

2023-06-08: Created ticket [#170067](https://support.paradox.com/portal/en/ticket/580177000054202075) at Paradox support portal.

2023-06-17: Found ticket [#170067](https://support.paradox.com/portal/en/ticket/580177000054202075) has been closed from Paradox support without any response.

2023-06-17: Published Paradox IP150S Denial of Service Vulnerability.
