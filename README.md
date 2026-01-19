# Pihole

## Current Pihole Setup & Configuration

Pihole is currently deployed via the app catalog in TrueNAS, and is listening on the same IP as TrueNAS.

Inside of Pihole, I created custom DNS records for all of the services currently running on my NAS (see <a href="https://github.com/Nikolas-Guidone/Home-NAS/blob/main/README.md#user-content-current-apps-and-services">Current Apps and Services </a>)
*Note - All IP's and Ports in this document have been modified and do not reflect the production environment*



| Domain            |  IP                |
| --------------    |  ---------------   |
| immich.home       |  192.168.1.50      |
| jarvis.home       |  192.168.1.50      |
| jellyfin.home     |  192.168.1.50      |
| npm.home          |  192.168.1.50      |
| pihole.home       |  192.168.1.50      |
| truenas.home      |  192.168.1.40      |
| vaultwarden.home  |  192.168.1.50      |

Per the DNS chart, truenas.home is being routed to a different IP than the other hostnames. When configuring Pihole originally, I started with a singular route on the DNS table. This route was jellyfin.home > 192.168.1.40. From here, there were multiple different paths I could have taken to then point traffic towards Pihole for DNS records. After careful consideration and planning of each way, I decided to go the route of manual DNS configuration per device as this made the most sense for my current setup and hardware. For testing purposes, I used my iPhone 15 Pro Max that is currently running IOS 26.2. In order to acheive my goal, I went into my iPhone's settings > Wi-Fi > The information icon of my current Wi-Fi network > Configure DNS > Manual. From here, I removed the DNS server that was already in place (192.168.1.5 - Default Gateway) and added in the IP that Pihole is listening to - 192.168.1.40. Now, my iPhone will route all network traffic towards 192.168.1.40 > through Pihole > out towards the correct end destination. Once I saved this configuration on my phone, I was able to see the Total Queries, Queries Blocked, Percentage Blocked and Domains on List all increasing with every passing packet and query. Going into the Query Log, I am able to see data of each indivdual event. As you can see in the image below, the Logs are able to provide crucial information for every query that is processed through Pihole. I can see the time and date, the query status, the type of record being requested, the domain, requesting client, and the query reply time.
