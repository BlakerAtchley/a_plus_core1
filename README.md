# CompTIA A+ Study Notes

Organized reference notes on networking, hardware, virtualization, peripherals, and troubleshooting.

---

## Networking Fundamentals

This section introduces IP networking, common network technologies, and the way protocols encapsulate data as it moves between systems.

### Encapsulation and Decapsulation

An Ethernet frame carries an IP packet. The IP packet carries a transport-layer segment, such as TCP, which in turn carries application data.

`Ethernet header | IP header | TCP header | HTTP data | Ethernet trailer`

Decapsulation removes each layer's protocol information as the data reaches its destination.

> **Course note:** Add the missing Professor Messer slide content on the two ways to move data between systems.

### Common Ports

Port numbers identify network services. The client and server must use compatible ports and protocols. Ports are important for firewall rules and port-based security; learn each port number, its transport protocol, and its purpose.

#### FTP (File Transfer Protocol)

FTP uses TCP port 20 for active-mode data and port 21 for control.
- Transfers files between systems
- Authenticates with a username and password
- Some systems use a generic or anonymous login
- Supports file operations such as listing, adding, and deleting files

#### SSH (Secure Shell)

SSH provides an encrypted communication link over TCP port 22.
- Provides command-line remote access similar to Telnet, but encrypted

#### Telnet (Teletype Network)

Telnet uses TCP port 23.
- Log in to devices remotely
- Often used for console access
- Sends data in clear text and is not recommended for production systems

#### SMTP (Simple Mail Transfer Protocol)

SMTP uses TCP port 25.
- Transfers email between servers and can submit mail from a device to a mail server
- Clients use protocols such as IMAP or POP3 to retrieve email

#### DNS (Domain Name System)

DNS uses UDP and TCP port 53.
- Resolves domain names to IP addresses
- Example: `www.professormesser.com` resolves to an IP address
- DNS is a critical service; networks commonly use multiple DNS servers

#### DHCP (Dynamic Host Configuration Protocol)

DHCP automatically configures IP addresses, subnet masks, and other options over UDP ports 67 (server) and 68 (client).
- Requires a DHCP server, appliance, or a feature integrated into a SOHO router
- Assigns addresses dynamically from a pool
- Each system receives a lease and must renew it at set intervals
- Reservations associate a MAC address with a specific IP address

#### HTTP and HTTPS

HTTP is the Hypertext Transfer Protocol; HTTPS is its encrypted version.
Cloud computing is more than hosting a server elsewhere; it extends the management of applications and services.
- Supported by nearly all web servers and clients
Cloud resources can scale substantially, with costs based on the services and capacity used.
#### POP3 and IMAP
You can deploy infrastructure in minutes and create or remove resources as needed.
- POP3 (Post Office Protocol version 3) uses TCP port 110 for basic email retrieval
Cloud providers offer an international presence, allowing deployments in specific regions.
#### SMB (Server Message Block)
Use only the resources you need; costs are based on consumption.
- NetBIOS over TCP/IP uses UDP port 137 for name services and TCP port 139 for session service
### Cloud deployment models

#### Public cloud
Public cloud services are generally available over the internet.
LDAP (Lightweight Directory Access Protocol) uses TCP port 389; LDAPS commonly uses TCP port 636.
#### Private cloud
A private cloud is an organization's own virtualized data center.

#### Hybrid cloud
A hybrid cloud combines public and private cloud resources.
RDP lets users share a desktop remotely over TCP port 3389.
#### Community cloud
Several organizations share the same cloud resources.
- Clients are available for Windows, macOS, Linux, iOS, Android, and other platforms
### Infrastructure as a Service (IaaS)
### Port Reference
IaaS is sometimes called hardware as a service (HaaS) because organizations outsource their equipment.
| ------- | ---------------------------------- | --------------------------------- |
The customer remains responsible for managing and securing its systems.
| SSH     | TCP 22                             | Encrypted remote access           |
Data is hosted remotely but remains under the customer's control.
| SMTP    | TCP 25                             | Email transfer and submission     |
Web server hosting is one example of IaaS.
| DHCP    | UDP 67 (server), 68 (client)       | Automatic IPv4 configuration      |
### Software as a Service (SaaS)
| POP3    | TCP 110                            | Email retrieval                   |
SaaS provides on-demand software without requiring a local installation.
- Examples include email and payroll services.
| SMB     | TCP 445                            | File and printer sharing          |
The provider centrally manages the application and hosts the customer's data.
| RDP     | TCP 3389                           | Remote desktop                    |
SaaS is a complete application offering and requires no application development by the customer.
- Examples include Google Mail (Gmail) and Microsoft 365.
## Wireless Network Technologies
### Platform as a Service (PaaS)
### Wireless technologies
PaaS provides a managed platform, including servers, software, maintenance, and facilities; the customer focuses on development.

The provider manages the platform and may employ security professionals to monitor it.
- Evaluate the provider and its security controls carefully.
Wi-Fi generations are also referenced by their IEEE standard:
Develop applications by combining the services and components available on the platform.
- Salesforce.com is one example of a PaaS provider.
- Future versions will increment accordingly.
### Shared responsibility matrix
#### 802.11 technologies
Cloud environments share resources, but the amount of sharing and customer control varies by model.
**Frequencies**
#### Internal or private cloud
An organization builds its own cloud with dedicated resources.
- Costs are primarily upfront, with fewer ongoing service charges.
- Frequencies are managed by governing entities
#### External or public cloud
An external cloud uses shared resources on infrastructure owned by a third party.
- Costs may be metered or paid upfront.
- Common widths include 20, 40, 80, and 160 MHz
### Metered and non-metered billing
**Band selection and bandwidth**
With metered utilization, you pay for the resources you use.
- Charges may apply to uploads (ingress traffic), storage, and downloads (egress traffic).

With non-metered utilization, you pay for a fixed block of storage and may not pay per upload or download.
#### RFID (radio-frequency identification)
### Cloud computing characteristics
- Uses include access badges, inventory and assembly-line tracking, and pet or animal identification.
**Elasticity:** Scale resources up or down as needed, often with rapid provisioning.

**Availability:** Redundancy helps keep services available.
- Used in payment systems, including major credit cards and online wallets.
**File synchronization:** Information can be duplicated across cloud locations.

**Multitenancy:** Multiple clients use the same cloud infrastructure.
## DNS Configuration

### Domain Name System

The Domain Name System (DNS) translates human-readable names into computer-readable IP addresses. For example, users can remember `www.professormesser.com` instead of an IP address.

DNS is hierarchical and distributed.
- Queries follow the hierarchy.
- The system uses many DNS servers, including 13 root server clusters with more than 1,000 servers.
- Hundreds of generic top-level domains (gTLDs) exist, such as `.com`, `.org`, and `.net`.
- More than 275 country-code top-level domains (ccTLDs) exist, such as `.us`, `.ca`, and `.uk`.

### DNS lookup

- Use the `dig` command on macOS or `nslookup` on Windows.

### DNS records

Resource records (RRs) are entries in the DNS database. More than 30 record types are used for IP addresses, certificates, host aliases, and other information.
> **Important:** DNS records are critical configurations. Back up, verify, and test changes.

#### A and AAAA records

Address records define a host's IP address. A records contain IPv4 addresses; AAAA records contain IPv6 addresses.
- A records are among the most common DNS queries.
- Update an A record to change the IPv4 address associated with a host name.

#### CNAME records

Canonical name (CNAME) records allow multiple service names to point to one host name.

#### MX records

Mail exchanger (MX) records identify the mail server responsible for receiving email for a domain.

#### TXT records

Text (TXT) records store text information and can be used for domain verification and email security.
- Administrators who can change a domain's DNS records can typically verify control of that domain.
- External email servers use DNS information to validate messages.

#### DKIM

DomainKeys Identified Mail (DKIM) is validated by mail servers and is not usually visible to end users.
- The public key is stored in a DKIM TXT record.

#### SPF

Sender Policy Framework (SPF) records list the servers authorized to send email for a domain.
- SPF helps prevent mail spoofing.
- Mail servers check whether incoming messages came from an authorized host.

#### DMARC

Domain-based Message Authentication, Reporting, and Conformance (DMARC) extends SPF and DKIM to help prevent unauthorized email use, such as spoofing.
- A DMARC TXT record tells external email servers how to handle messages that fail SPF or DKIM validation.
- Policies can accept messages, send them to spam, or reject them.
- Compliance reports can be sent to the email administrator.

---

## DHCP

### DHCP overview

IPv4 addresses, subnet masks, default gateways, DNS servers, and NTP servers were once configured manually. DHCP provides an automatic approach that scales to thousands of systems.
- The Dynamic Host Configuration Protocol (DHCP) was initially released in 1997 and has been updated over time.
- DHCP provides automatic IP configuration and is used by most network-connected devices.

### DORA lease process

DORA is a four-step process for obtaining a DHCP lease:
- **Discover:** Find a DHCP server.
- **Offer:** Receive an address offer.
- **Request:** Request the offered address.
- **Acknowledge:** Receive confirmation from the DHCP server.

### DHCP scopes

A DHCP scope is configured on the DHCP server and defines an IP address range.
- Administrators can exclude specific addresses from the range.
- Scope options include the subnet mask, lease duration, DNS server, default gateway, and VoIP servers.
- Each subnet has its own scope, such as `192.168.1.0/24`, `192.168.2.0/24`, or `192.168.3.0/24`.
- A scope is generally a single contiguous pool of IP addresses; exclusions can be configured within it.

### Address reservations

An administrator can reserve an IP address for a specific MAC address.
- This is also called static DHCP or an IP reservation.

---

## VLANs and VPNs

### LANs and VLANs

A local area network (LAN) is a group of devices in the same broadcast domain.
- A virtual LAN (VLAN) separates devices logically rather than physically.
- VLANs are configured on the local area network.

### VPNs

A virtual private network (VPN) carries encrypted, private data across a public network.
- A VPN concentrator encrypts and decrypts traffic and is often integrated into a firewall.
- VPNs can use specialized cryptographic hardware or software, sometimes built into the operating system.

#### Client-to-site VPN

Provides on-demand remote access from a client device to a VPN concentrator. Some software can be configured to connect automatically.

#### Site-to-site VPN

Connects networks through an always-on or nearly always-on VPN tunnel. Firewalls often act as VPN concentrators.

---

## Network Devices

Network devices perform different roles, and some combine several functions in one unit, such as a wireless router, switch, and firewall. Compare devices to determine where each is appropriate.

### Routers

Routers forward traffic between IP subnets.
- They make forwarding decisions based on IP addresses.
- Routers integrated into switches are sometimes called Layer 3 switches (OSI layer 3).
- They often connect diverse network types, including LANs, WANs, copper, and fiber.

### Switches

Switches bridge devices in hardware, often using an application-specific integrated circuit (ASIC), and forward traffic based on data-link addresses.
- Enterprise switches provide many ports and features.
- Some switches provide Power over Ethernet (PoE).
- Multilayer switches also include routing functionality.

#### Unmanaged switches

- Offer few configuration options and are generally plug-and-play.
- Use a fixed configuration and typically do not support VLANs or management protocols.
- Cost less because they provide fewer features.

#### Managed switches

- Support VLANs and inter-switch connections using 802.1Q.
- Prioritize traffic, such as giving voice traffic higher priority.
- Support redundancy to maintain uptime if a switch fails.
- Provide port mirroring to capture packets.
- Can be managed externally using the Simple Network Management Protocol (SNMP).

### Access points

An access point is a bridge, not a router.
- A wireless router combines a router and an access point in one device.
- An access point extends a wired network to wireless devices and forwards traffic based on MAC addresses.

### Cabling infrastructure

A punch-down block connects wires directly. A patch panel combines punch-down blocks with RJ-45 connectors.
- Desk cables are punched down to the patch panel once.
- Connections between the patch panel and switch can be changed without special tools by using existing cables.

### Firewalls

- Filter traffic by port number at OSI layer 4 (TCP/UDP); some can also filter by application.
- Encrypt traffic entering or leaving the network to protect communications between sites.
- Proxy traffic as a common security measure.
- Often operate as layer 3 devices (routers) at the network ingress or egress.

### Power over Ethernet (PoE)

PoE supplies power over an Ethernet cable, so one cable carries both network data and power.
- Commonly powers phones, cameras, and wireless access points.
- Useful in areas where it is difficult to provide power.
- Power can come from a switch (an endspan) or an in-line injector (a midspan).
- PoE capability is commonly marked on the switch or interface.
- The original PoE specification provides 15.4 W of DC power, with a maximum current of 350 mA.

#### PoE+

- Provides up to 25.5 W of DC power at 600 mA.

#### PoE++

- Provides 51 W (Type 3) at 600 mA or 71.3 W (Type 4) at 960 mA.
- Supports PoE with 10GBASE-T.
- Check the device's requirements against the switch's capabilities; PoE+ will not power a PoE++ device.

### Cable modems

Cable modems provide broadband service over multiple frequencies and traffic types using DOCSIS (Data Over Cable Service Interface Specification).
- Speeds up to 1 Gbit/s are common.
- Cable connections can carry data, voice, and video.

### DSL modems

Digital Subscriber Line (DSL) modems use telephone lines. Asymmetric services provide faster download than upload speeds.
- 200 Mbit/s downstream and 20 Mbit/s upstream are common.
- Service is limited to approximately 10,000 feet from the central office (CO); higher speeds may be possible closer to the CO.

### Optical network terminals (ONTs)

An ONT connects an ISP's fiber network to a customer's copper network.
- The demarcation point (DEMARC) may be in a data center or at a terminal box on the building.
- The ISP is responsible for one side of the demarcation point; the customer network is on the other side.

### Network interface cards (NICs)

A NIC is the fundamental network interface in a device.
- Computers, servers, printers, routers, switches, and phones use NICs.
- NICs are specific to a network type, such as Ethernet, WAN, or wireless.
- A NIC is often built into the motherboard or added as an expansion card.
- It contains a hardware address called the Media Access Control (MAC) address, a unique hardware identifier.

---

## IPv4 and IPv6

IP addressing
- IPv4 is the primary protocol for everything we do
- Included in lamost all configurations

IPv6 is now part of all major operating systems
and the backbone of our internet infrastructure

IPv4 addresses
- OSI Layer 3 address

Public IPv4 addresses
Each IPv4 address on the internet is unique.
- 1.1.1.1 can communicate to 2.2.2.2
It is estimated that there are over 20 billion devices connected to the internet (and growing)
- IPv4 supports around 4.29 billion addresses.
- There's an obvious scalability issue
We have found ways to manage the demand
- Network Address Translation (NAT)

Private IP Address ranges
Large private IP address ranges
- Properly design and scale large networks
Private IP addresses are not internet routable
- But can be routed internally
- Use NAT for everything else
Defined in RFC 1918
- Request for Comment

IPv6 Addresses
Internet Protocol version 6 (IPv6) uses 128-bit addresses.
- 340 undecillion addresses
- 6.8 billion people could have many addresses
- hexadecimal instead of decimal

Your DNS is very important!
First 64 bits is generally the network prefix (/64)
Last 64 bits is then the host network address

---

## Assigning IP Addresses

Networking with IPv4

Example IP address: 192.168.1.65
- Every device needs a unique IP address

Subnet mask: 255.255.255.0
- Used by the local device to determine what subnet it's on
The subnet mask usually isn't transmitted across the network. You'll often need to ask for it: "What's the subnet mask of your network?"

Default gateway: 192.168.1.1
- The router that allows you to communicate outside of your local subnet
- The default gateway must be an IP address on the local subnet.

Static IP addressing

An IP address that doesn't change
- Without some type of configuration change

Manually configure the IP address
- Type it from the keyboard on each device

Can be difficult to manage
- If the address changes, you must visit the device
- This obviously does not scale

Try to avoid using manual IP addressing
- There are better ways to assign static addresses
- DHCP reservations

**Automatic Private IP Addressing (APIPA)**

An IPv4 link-local address
- No forwarding by routers

APIPA
169.254.0.0 to 169.254.255.255
- The first and last 256 addresses are reserved.
- Functional block of 169.254.1.0 - 169.254.254.255
- DHCP is not responding

Randomly assigned in this block
- Uses ARP to confirm the address isn't currently in use

Turning dynamic into static
DHCP assigns an IP address from a large pool of available addresses.
- Your IP address may change occasionally.

You may not want your IP address to change
- Server, printer, or personal preference

Disable DHCP on the device
- Configure the IP address information manually
- Requires additional administration

Better: Configure an IP reservation on the DHCP server
- Associate a specific MAC address with an IP address

---

## Internet Connection Types

---

## Satellite Networking

Satellite networking provides non-terrestrial communication.

It is expensive relative to terrestrial networking.
- 100 Mbit/s down and 5 Mbit/s up are common.
- It can serve remote or difficult-to-network sites.

Satellite connections have relatively high latency.
- Some systems have 250 ms up and 250 ms down.
- Starlink advertises 25 to 60 ms

Satellite service is not always ideal because it requires line of sight and can be affected by rain fade.

---

## Fiber

Fiber carries high-speed data using light.

Higher installation cost than copper
- Equipment is more costly
- More difficult to repair
- Communication over long distances

Fiber is widely installed in WAN cores.
- Supports very high data rates, including SONET and wavelength-division multiplexing.

Fiber is also available at business and residential premises.

---

## Cable

Cable provides broadband service by transmitting data across multiple frequencies and traffic types.

Cable networks use DOCSIS (Data Over Cable Service Interface Specification).

Speeds from 50 Mbit/s to more than 1,000 Mbit/s are common.

---

## DSL

Asymmetric Digital Subscriber Line (ADSL) uses telephone lines.

Download speeds are faster than upload speeds.
- 200 Mbit/s downstream and 20 Mbit/s upstream are common.
- ~10,000 foot limitation from the central office (CO)
- Faster speeds may be possible if closer to the CO

---

## Cellular Networks

Mobile devices, including cell phones, connect through cellular networks.

Networks divide geographic areas into cells, each served by an antenna using assigned frequencies.

Tethering turns a phone into a wireless router.

Mobile hotspots can be standalone devices or phones that provide network access to other devices.

---

## WISP

Wireless Internet Service Providers (WISPs) provide terrestrial internet access wirelessly.

They can connect rural or remote locations.

Many different deployment technologies
- Meshed 802.11
- 5G home internet
- Proprietary wireless

An outdoor antenna is required.
- Speeds range from about 10 Mbit/s to 1,000 Mbit/s.

---

## Network Types

### LAN (local area network)

A LAN connects devices within a limited area, such as a building or group of buildings.
- Common technologies include Ethernet and 802.11 wireless networking.

### WAN (wide area network)

A WAN connects LANs across large distances, potentially across the globe, and is generally slower than a LAN.
- Technologies include point-to-point serial links, Multiprotocol Label Switching (MPLS), and terrestrial or non-terrestrial links.

### PAN (personal area network)

A PAN connects a person's nearby devices using technologies such as Bluetooth, infrared (IR), or NFC.
- Examples include a car's audio system connecting to a phone, a phone connecting to a wireless headset, and health devices reporting workout data.

### MAN (metropolitan area network)

A MAN covers a city and is larger than a LAN but often smaller than a WAN.
- Metro Ethernet is a common MAN technology.
- Governments often own the right-of-way used by MAN infrastructure.

### SAN (storage area network)

A SAN provides efficient block-level access to storage and can appear to a system like local storage.
- SANs require substantial bandwidth and may use an isolated, high-speed network.

### WLAN (wireless local area network)

A WLAN provides 802.11 wireless connectivity within a building or other limited area.
- Add access points to expand coverage across a downtown area or large campus.

---

## Network Tools

Cable Crimpers

"Pinch" the connector onto the wire
- Coaxial, twisted pair, fiber

Connect the modular connector to the Ethernet cable
- The final step of the process

Metal prongs are pushed through the insulation.
- The plug is also permanently pressed onto the cable sheath

Crimping best practices

Get a good crimper
- A good pair of electrician's scissors or cable snips
- And a good wire stripper

Make sure you use the correct modular connectors
- Differences between wire types

Practice, practice, practice
- It won't take long to become proficient

Wi-Fi analyzer

Hardware-based Wi-Fi analyzer
- Avoids operating systems limitations
- View all of the 802.11 information in the air

View Wi-Fi information
- Frequencies and channels, signal strength, access points, interference, and wireless devices

Get frequency information from a spectrum analyzer
- Useful when many different devices are part of the bigger picture

Tone Generator

Tone probe
- Where does that wire go?
- Follow the tone

Tone generator
- Puts an analog sound on the wire

Inductive probe
- Doesn't need to touch the copper
- Hear the tone through a small speaker

Easy wire tracing, even in complex environments

Connect the tone generator to the wire
- Modular jack
- Coax
- Punch down connectors

Use the probe to locate the sound
- The two-tone sound is easy to find

Punch down tool

"Punch" a wire into a wiring block
- 66 block, 110 block, Krone block, and others

Can be tedious
- Every wire must be individually punched

Trims the wires during the punch
- Very efficient process

Organization is key
- Lots of wires
- Cable management

Maintain your twists
- Your category 6A cable will thank you later

Document everything
- Written documentation
- Tags
- Graffiti

Cable Testers

Relatively simple
- Continuity test
- A simple wire map

Can identify missing pins
- Or crossed wires

Not usually used for frequency testing
- Crosstalk, signal loss, etc

Loopback plugs

Useful for testing physical ports
- Or fooling your applications

Serial / RS-232 (9-pin or 25-pin)

Network connections
- Ethernet, T1, Fiber

These are not cross-over cables

Taps and port mirrors

Intercept network traffic
- Send a copy to a packet capture device

Physical taps
- Disconnect the link and insert a tap in the middle.
- Can be active or passive.

Port mirror
- Port redirection, SPAN (Switched Port Analyzer)
- Software-based tap
- Limited functionality, but can work well in a pinch

---

## Display Types

### LCD (liquid crystal display)

An LCD produces an image by controlling how light passes through liquid crystals.

#### Advantages
- Lightweight
- Relatively low power
- Relatively inexpensive

#### Disadvantages
- Black levels are a challenge
- Requires a separate backlight.
  - Fluorescent or LED (light-emitting diode)
  - Lights can be difficult to replace.

### LCD technologies

#### TN (twisted nematic) LCD
- The original LCD technology
- Fast response times (gaming!)
- Poor viewing angles can cause color shifts.

#### IPS (in-plane switching) LCD
- Excellent color representation
- Can be more expensive to produce than TN

#### VA (vertical alignment) LCD
- A good compromise between TN and IPS
- Good color representation
- Often slower response times than TN

### OLED displays

OLED (organic light-emitting diode)
- An organic compound emits light when it receives an electric current.

No backlight is needed; the organic compound provides the light.

Thinner and lighter
- Flexible and mobile; no glass is needed.

Commonly used in tablets, phones, and smartwatches.
- Provides accurate color representation.
- Usually costs more than LCD.

### Mini-LED displays

Uses the same backlight technology as a conventional LED-backlit LCD, but with much smaller light-emitting diodes (LEDs).

LED backlight zones can be enabled or disabled independently, with different color and intensity levels.

This provides better control over dark areas, deeper blacks, and improved color representation.

### Touchscreens

Touchscreens combine laptop and tablet input.
- A digitizer responds to touch.
- A keyboard is not required, but is often still available.

Choose the input method that best suits the task.

### Digitizers

Digitizers accept input from a pen-like device, or stylus, and are useful for drawing and other graphical tasks.

They are commonly used on laptops, tablets, and hybrid devices.

### Backlights and inverters

LCDs need a backlight, typically a fluorescent lamp or LED.

Some laptops use an inverter to convert DC to AC power for the backlight.

To check the backlight, look closely at the display or shine a flashlight on it.

You may need to replace the LCD inverter or display; check the device documentation before choosing a replacement.

---

## Display Attributes

Displays differ in their specifications, options, and settings.

Requirements vary by use case, including web browsing, video and photo editing, information displays, and phones.

Evaluate the technical details to choose a display that meets the requirements.

### Pixel density

Pixel density measures how many pixels fit in an inch or centimeter.

A higher pixel density generally produces a clearer, sharper image.

Consider how the image will be viewed. Printers, for example, use dots per inch (DPI).

### Pixel density examples

Pixel density is calculated by dividing the number of pixels by the number of inches to get pixels per inch (PPI).

For a 27-inch (diagonal) 4K display that is 24 inches wide, 3,840 horizontal pixels provide 160 pixels per inch.

For a 65-inch (diagonal) 4K display that is 57 inches wide, 3,840 horizontal pixels provide about 67 pixels per inch.

### Refresh rates and frame rates

Displays show a sequence of still images, or frames.

Refresh rate is measured in hertz (Hz), or cycles per second. Frame rate is measured in frames per second (FPS).

Frame rates vary by media type: movies commonly use 24 fps, television uses 30 fps, and video games often use 60 fps or higher.

### Choosing a refresh rate

Higher refresh rates are useful for rapidly moving content, such as video games, sports, and video production.

The video adapter or processor, display, and connection determine the maximum refresh rate.
- HDMI 2.1 supports 4K at 144 Hz.
- DisplayPort 2.1 supports dual 4K at 144 Hz.

### Screen resolution

Resolution is the number of pixels in the image, expressed as width x height.

More pixels can produce more detailed output, increasing perceived sharpness and clarity.

Resolutions vary widely; a 16:9 aspect ratio is common.

### Color gamut

A color gamut is the range of colors available on a display or output device. It is smaller than the range visible to the human eye.

Color gamut is an important display consideration because it affects color representation.

Common standards include sRGB (standard red, green, and blue), Adobe RGB, and International Telecommunication Union (ITU) standards for HDTV.

### Color coverage

A display's color coverage can be compared with an established gamut standard and may be included in its specifications.

Gamut coverage varies widely, and displays with higher coverage percentages tend to cost more.

OLED displays provide a wide color gamut and are often among the best for gamut support.

---

## Network Cables

The importance of cables

Fundamental to network communication
- Incredibly important foundation

Usually only get one good opportunity at building your cable infrastructure
- Make it good!

The vast majority of wireless communication uses cables
- It has to plug in somewhere

Twisted pair copper cabling

Balanced-pair operation
- Two wires with equal and opposite signals
- Transmit +, transmit - / receive +, receive -

The twist is the secret
- Keeps a single wire constantly moving away from the interface
- The opposite signals are compared at the other end.

Pairs in the same cable have different twist rates

Cable categories
- The copper just sits there

Electrical signals are sent over copper cable
- The signal encoding determines the data transfer rate

A cable must be manufactured to specific standards.
- IEEE 802.3 Ethernet standards determine the cable type

Cable standards are described as a "category" of cable.
- Category 5e, Category 6a
- Check the IEEE standard to determine the minimum cable category
- The minimum cable category for 1000BASE-T is Category 5e.

### Copper Cable Categories

| Ethernet standard | Minimum cable category | Maximum supported distance |
| ----------------- | ---------------------- | -------------------------- |
| 1000BASE-T        | Category 5e            | 100 m                      |
| 10GBASE-T         | Category 6             | 55 m                       |
| 10GBASE-T         | Category 6A            | 100 m                      |

Coaxial cables

Two or more forms share a common axis
- The inner conductor and the outer shield

RG-6 used in TV/digital cable
- Also used for high-speed internet over cable

Unshielded and shielded cable

UTP (Unshielded Twisted Pair)
- No additional shielding
- The most common twisted pair cabling

STP (Shielded Twisted Pair)
- Additional shielding protects against interference
- Shield each pair and/or the overall cable
- Requires the cable to be grounded

Abbreviations
- U = unshielded
- S = braided shielding
- F = Foil shielding

(Overall cable)/(individual pairs)TP
- Braided shielding around the entire cable and foil around the pairs is S/FTP
- Foil around the cable and no shielding around the pairs is F/UTP

Direct burial STP

Overhead cable isn't always a good option
- Put the cable in the ground

Provides protection from the elements
- Designed to be waterproof
- Often filled with gel to repel water
- Conduit may not be needed

Shielded twisted pair
- Provides grounding
- Adds strength
- Protects against signal interference

Plenum

Plenum space
- Building air circulation
- Heating and AC system

Smoke and toxic fumes are a concern during a fire, so plenum spaces require appropriately rated cable.

### Plenum-rated cable

A traditional cable jacket is made of polyvinyl chloride (PVC).

A fire-rated jacket may use fluorinated ethylene polymer (FEP) or low-smoke polyvinyl chloride (PVC).

Plenum-rated cable may be less flexible and may have a different bend radius.

Plan for worst-case conditions when selecting cable for a structure.

---

## 568A and 568B Colors

### Structured cabling standards

The international ISO/IEC 11801 standard defines classes of cabling.

The Telecommunications Industry Association (TIA) develops standards and supports the industry through market analysis, trade shows, and government affairs.
- ANSI/TIA-568 is the Commercial Building Telecommunications Cabling Standard.
- TIA website: <http://www.tiaonline.org>

T568A and T568B specify pin and pair assignments for eight-conductor, 100-ohm balanced twisted-pair cabling.

### T568A and T568B termination

The T568B standard defines pin assignments for eight-conductor, 100-ohm balanced twisted-pair cabling.

T568A and T568B use different pin assignments for an 8P8C connector, so their color sequences differ slightly.

Many organizations traditionally use T568B, which can make it difficult to change standards midstream.

Do not terminate one end of a cable with T568A and the other with T568B; that is not the definition of a Gigabit Ethernet crossover cable.

---

## Optical Fiber

### Fiber communication

Fiber transmits data using light, typically in the visible or infrared spectrum.

Fiber does not carry an RF signal, making it difficult to monitor or tap.

The signal degrades slowly, allowing transmission over long distances.

Fiber is immune to radio-frequency interference because it does not use RF signals.

### Multimode fiber

Multimode fiber is used for short-range communication, typically up to 2 km.

It uses a relatively inexpensive light source, such as an LED.

### Single-mode fiber

Single-mode fiber is used for long-range communication, up to 100 km without processing.

It uses a more expensive light source, commonly a laser.

---

## Peripheral Cables

### USB (Universal Serial Bus)

USB simplifies connections for printers, storage devices, keyboards, mice, and other peripherals.

#### USB 1.1
- Low speed: 1.5 Mbit/s, up to 3 m
- Full speed: 12 Mbit/s, up to 5 m

#### USB 2.0
- Up to 480 Mbit/s, with a maximum cable length of 5 m

#### USB 3.0
- SuperSpeed, up to 5 Gbit/s
- The standard does not specify a cable length.

#### USB 3.1
- Up to 10 Gbit/s

#### USB 3.2
- Up to 20 Gbit/s

#### USB-C

USB has had many different connectors over time.

USB-A can be awkward to connect; it may take more than one attempt.

USB-C is a newer connector intended to replace several older connector types.

USB-C describes the physical connector, not the signal or protocol it carries.

### Serial cables

D-subminiature (D-sub) connectors are commonly used for serial connections. The letter refers to the connector size.

RS-232 (Recommended Standard 232) is an industry standard dating to 1969.

Serial communication was developed for modems and is also used with printers, mice, and network devices.

Connect directly to a device using a serial connection, such as a DB-9 connector, RJ-45 serial port, or USB connection.

When other connection methods fail, a device may still provide a text-based serial console.

This requires a serial or USB connection; a USB-to-DB-9 serial adapter may be needed.

### Thunderbolt

Thunderbolt is a high-speed serial interface that carries data and power over the same cable. Early versions used the Mini DisplayPort (MDP) connector.

#### Thunderbolt 1
- Two channels
- 10 Gbit/s per channel
- 20 Gbit/s total throughput
- Mini DisplayPort connector

#### Thunderbolt 2
- 20 Gbit/s across the aggregated channels
- Mini DisplayPort connector

#### Thunderbolt 3
- 40 Gbit/s aggregated throughput
- USB-C connector

Maximum cable lengths are 3 m for copper and 60 m for optical.
- Daisy-chain up to six devices.

#### Thunderbolt 4
- 40 Gbit/s aggregated throughput
- Supports dual 4K displays
- Increased PCIe bandwidth

---

## Video Cables

### HDMI (High-Definition Multimedia Interface)

HDMI carries digital video and audio. Signal quality may degrade over distances of approximately 20 m.

The 19-pin Type A connector is one of the most common video connectors.

### DisplayPort

DisplayPort sends digital information in packets, like Ethernet and PCI Express, and carries both audio and video.

DisplayPort is compatible with HDMI and DVI when used with the appropriate adapter.
- Passive adapters can connect DisplayPort to HDMI or DVI when the interfaces are compatible.

Full-size DisplayPort connectors may have a locking mechanism. Unlock it before disconnecting the cable.

### DVI (Digital Visual Interface)

Single-link and dual-link DVI support different resolutions and refresh rates.
- Single link: 3.7 Gbps (1920 x 1200 at 60 Hz)
- Dual link: 7.4 Gbps (2560 x 1600 at 85 Hz)
- DVI does not carry audio.

#### DVI-A
- Analog signals
- Backward compatibility with VGA

#### DVI-D
- Digital signals

#### DVI-I
- Integrated digital and analog signals in the same connector

### VGA (Video Graphics Array)

DB-15 connector
- More accurately called DE-15

The connector is usually blue, as specified by the PC System Design Guide.

VGA carries video only and does not transmit audio.

VGA uses an analog signal, not a digital one. Image quality can degrade over 5 to 10 m of cable.

### USB-C video

USB-C is a connector, not a protocol.

USB-C can carry power and several types of data or video signals:
- USB data, Thunderbolt data, and DisplayPort video
- HDMI video (less common) and Mobile High-Definition Link (MHL)

---

## Storage Cables

### SATA (Serial AT Attachment)

#### SATA revision 1.0
- 1.5 Gbit/s

#### SATA revision 2.0
- 3.0 Gbit/s

#### SATA revision 3.0
- 6.0 Gbit/s

#### SATA revision 3.2
- 16 Gbit/s

### eSATA (external SATA)
- Matches the SATA version
- 2 meters

### SATA power and data connectors

Each device uses one 15-pin power cable and one 7-pin data cable.
- One-to-one

### eSATA cables

eSATA connects external devices using a SATA-based connector.

SATA is usually inside the computer; eSATA is designed for external connections.

---

## Adapters and Converters

Adapters and converters connect devices with different interfaces or convert between formats.

An adapter may be needed when the available connections do not match.

Adapters can connect different, electrically compatible connectors.

Converters change one format into another, such as USB to Ethernet.

An adapter or converter can be a temporary or permanent solution.

### DVI to HDMI

DVI-D and HDMI are electrically compatible.
- HDMI is backward compatible with DVI-D
- No signal conversion required
- No loss of video quality

### DVI to VGA

DVI-A includes analog signals
- Backward-compatible with VGA.
- Only 640 x 480 is officially supported.

An adapter may be sufficient for analog-to-analog conversion.

VGA to DVI-D requires a converter.
- Check your interface specifications.

USB to Ethernet

Some laptops don't have a wired Ethernet interface.
- A USB-to-Ethernet adapter provides one.

### USB-C to USB-A

An adapter lets newer USB-C devices use older USB-A peripherals.

### USB hubs

USB hubs connect multiple devices and provide high-speed USB connectivity.

---

## Copper Connectors

### RJ11 connector

RJ11 is a 6P2C connector (six positions and two conductors), although some cables include additional conductors.

It is commonly used for telephone and DSL connections.

### RJ45 connector

RJ45 stands for Registered Jack type 45.

It is an 8P8C modular connector (eight positions and eight conductors) commonly used for Ethernet.

### F connector

The F connector is a threaded connector used with coaxial cable.

It is commonly used for cable television and cable modems that use DOCSIS (Data Over Cable Service Interface Specification).

### Punch-down blocks

A punch-down block acts as a wire-to-wire patch panel without an intermediate interface.

Wires are punched into the block, where a connecting block sits on top.

Additional wires can be punched into the connecting block to join the top and bottom wiring.

### USB-C

USB-C is a 24-pin, double-sided connector used by both hosts and devices.

It can carry USB or Thunderbolt signals; the connector is the same, but the signal can differ.

### Molex connector

The 4-pin Molex connector is a peripheral power connector originally created by Molex Connector Company. AMP Mate-N-Lok is another name associated with this connector.
- Provides +12 V and +5 V.

It powers devices inside a computer case, including fans and storage drives.

### Lightning connector

Lightning is Apple's proprietary 8-pin digital connector, used by some iPhone, iPad, and iPod devices.

Compared with Micro USB, Lightning can provide higher power output for phones and tablets and can be inserted in either orientation.

### DB-9 connector

DB-9 is a D-subminiature (D-sub) connector. The letter refers to the connector size.

It is commonly used for RS-232 (Recommended Standard 232), an industry standard since 1969.

Serial communication was developed for modems and is also used with printers, mice, and networking equipment.

DB-9 connectors are now often used as management or console ports.

---

## Fiber Connectors

### ST (Straight Tip)

ST is a bayonet-style connector that attaches with a push and twist.

Push it on and turn it to lock; turn it in the opposite direction to unlock.

### SC (Subscriber Connector)

The name is not actually an abbreviation, although it is sometimes expanded as "square connector" or "standard connector."

The connector locks when pushed in and unlocks when pulled out.

SC is a popular fiber connector used in many data centers.

### LC (Lucent Connector)

LC is another popular fiber connector; it is smaller and more compact than some alternatives.

It locks in place with a clip; press the clip to release it.

Other informal expansions include "local connector" and "little connector."

---

## An Overview of Memory

What is memory?

Random Access Memory (RAM) is the most common
- But it is not the only kind of memory

RAM is not referring to hard drive or SSD storage
- Do not mix the two terms
- Data is stored permanently on the drive.

Data and programs can only be used when moved to RAM

RAM slots

Memory types have changed throughout the years
- Driven by standardization and technology

One of the most important components of your computer
- Speed, speed, speed

Every motherboard is different
- Check your documentation

DIMM

DIMM
- Dual inline memory module
- Electrical contacts are different on each side

64 bit data width

SO-DIMM

Small Outline Dual Inline Memory Module
- About half the width of a DIMM

Dynamic Random Access Memory

The memory on the DIMM

Dynamic
- Needs constant refreshing
- Without refreshing, the data in memory disappears

Random access
- Any storage location can be accessed directly
- Unlike magnetic tape

SDRAM

Synchronous DRAM (SDRAM)

SDRAM is synchronous with the common system clock
- Queue up one process while waiting for another
- Classic DRAM did not wait for a clock signal

SDR vs. DDR
- Single Data Rate: one data transfer per clock cycle
- Double Data Rate: two data transfers per clock cycle

Double Data Rate 3 (DDR3) SDRAM

Twice the data rate of DDR2
- Larger chip capacities

No backward compatibility
- Speed brings sacrifice

DDR4 SDRAM

Speed increases over DDR3
- Faster frequencies

Again, no backward compatibility

DDR5 SDRAM

Faster data transfers between the memory module and motherboard
- Higher speeds than DDR4

The key has moved.
- No backward compatibility

---

## Memory Technologies

### Error detection and correction

Some memory can detect or correct errors and is used in critical systems such as virtual machine and database servers.

**Parity memory** adds a parity bit.
- Parity can detect some errors, but it cannot always detect or correct them.

**Error-correcting code (ECC) memory** detects and corrects some errors automatically.
- Not all systems support ECC memory.
- ECC memory looks similar to non-ECC memory.

With even parity, the parity bit makes the total number of 1 bits even. Check whether a given byte has valid or invalid even parity.

### CPU-to-RAM throughput

The maximum data transfer rate between RAM and the CPU is the memory bandwidth.
- It is measured in MT/s (megatransfers per second).
- For example, a 32 GB DDR5 module may be rated at 560 MT/s.
- Higher throughput is useful, but is limited by hardware capabilities.

### Multichannel memory

Increasing the speed of a single memory bus is difficult, so systems can use multiple independent memory channels to increase throughput.
- Dual-, triple-, and quad-channel configurations are common.
- Matching memory modules are recommended for best results.
- Motherboard memory slots are often color-coded to indicate channel groupings.

---

## Storage Devices

Computers need a way to store information when they are powered off.
- RAM requires power to maintain the data

Common storage devices include hard drives, solid-state drives, flash drives, memory cards, and optical drives.

### Hard disk drives (HDDs)

HDDs use nonvolatile magnetic storage on rapidly rotating platters.

HDDs provide random access, allowing data to be retrieved from any part of the drive.

HDDs contain moving parts, including spinning platters, an actuator arm, and read/write heads.
- Mechanical components limit access speed and can fail.

Spindle speeds and average latency
- RPM: 15,000; 10,000; 7,200; 5,400
- Average latency: 2 ms; 3 ms; 4.16 ms; 5.55 ms

Common drive widths include 3.5 in, 2.5 in, and 22 mm.

### Solid-state drives (SSDs)

SSDs use nonvolatile memory and have no moving parts.

They provide fast performance without the delays associated with spinning disks.

Some SSDs use a 2.5-in SATA interface.

### PCIe storage interfaces

PCIe provides high-speed communication with SSDs and was used before the M.2 form factor became common.

PCIe storage devices connect directly to the motherboard for power and high throughput.

Modern PCIe standards can transfer data at 65 gigabits per second per lane.

### NVMe

SATA was designed for hard drives and uses AHCI (Advanced Host Controller Interface) to move drive data to RAM.
- SATA revision 3 has throughput up to 6 Gbit/s.
- SSDs need a faster communication method.

Non-Volatile Memory Express (NVMe) was designed for SSD speeds.
- It provides lower latency and higher throughput.
- It uses the PCIe bus.
- An NVMe drive using M.2 has a theoretical transfer speed of 20 Gbps.

### Serial Attached SCSI (SAS)

SAS is a serial SCSI technology that increases storage throughput.

It is useful for controlling and managing large storage arrays.

SAS can provide higher throughput than SATA.
- SATA can communicate at 6 Gbit/s.
- High-end SAS can reach 22.5 Gbit/s.

SAS drives are also available in a 2.5-in form factor.

### mSATA (Mini-SATA)

mSATA adapted SATA technology to a smaller form factor for laptops and mobile devices.

These drives are smaller than 2.5-in SATA drives, have no spinning parts, and support different form factors.

mSATA was used briefly before being largely replaced by the M.2 standard.

### M.2 interface

M.2 is a smaller form factor that does not require separate SATA data or power cables.

M.2 devices can use a PCI Express bus connection.
- NVMe over PCIe x4 can provide 4 GB/s throughput or more.

M.2 connectors use different key types, including B, M, and B+M.
- A drive's key must match the slot; some drives support both B and M keys.

An M.2 connector does not guarantee NVMe support; the interface may use AHCI.
- Check the device documentation.

Your motherboard may support only one type of M.2 key, so check its documentation.

### Flash drives

Flash drives use EEPROM (electrically erasable programmable read-only memory), a type of nonvolatile memory that retains data without power.

Flash memory has a limited number of write cycles, but data can still be read.

Flash drives are not designed for archival storage; they can be lost or damaged, so keep a backup.

### Optical drives

Optical drives use a laser to read microscopic marks that store data in binary form.

Optical media is relatively slow but can be used for archival storage.

Common formats include CD-ROM, DVD-ROM, and Blu-ray.

---

## RAID

RAID (Redundant Array of Independent Disks) combines multiple drives to improve performance, provide redundancy, or both. It is not a substitute for backups.
- RAID was also historically called "Redundant Array of Inexpensive Disks."
- Different RAID levels provide different combinations of performance, capacity, and redundancy.

RAID 0: Striping

RAID 0 splits file blocks across two or more physical drives.
```text
Disk 0: Block 1A | Block 3A | Block 5A | Block 7A
Disk 1: Block 2A | Block 4A | Block 6A | Block 8A
```

Striping can improve performance because data is written across multiple drives.

RAID 0 provides no redundancy. If one drive fails, the array fails and data may be lost.

RAID 1: Mirroring

RAID 1 duplicates file blocks across two or more physical drives.
```text
Disk 0: Block 1 | Block 2 | Block 3 | Block 4
Disk 1: Block 1 | Block 2 | Block 3 | Block 4
```

Mirroring duplicates every file, so the required disk space is doubled.

RAID 1 provides redundancy; a single drive failure does not affect data availability.

RAID 5: Striping with one parity drive

RAID 5 stripes file blocks and distributes parity blocks across the drives. It requires at least three drives.
```text
Disk 0: Block 1A | Block 1B | Block 1C | Parity D
Disk 1: Block 2A | Block 2B | Parity C | Block 1D
Disk 2: Block 3A | Parity B | Block 2C | Block 2D
Disk 3: Parity A | Block 3B | Block 3C | Block 3D
```

RAID 5 uses disk space efficiently because files are not duplicated, although some capacity is used for parity.

RAID 5 can recover from a single drive failure, though parity calculations may affect performance.

RAID 6: Striping with two parity drives

RAID 6 adds a second parity block and requires at least four drives.

It can tolerate the failure of up to two drives while keeping data available.

The additional parity requires another drive's worth of capacity but does not increase usable capacity.

RAID 10 (RAID 1+0)

Combines the speed of striping with the redundancy of mirroring.
- RAID 10 combines striping and mirroring and requires at least four drives.

---

## Motherboards

Motherboard form factors

Physical size
- Case sizing

Basic Layout
- Room for smaller changes

Power
- Standard connectors

Airflow
- Increasingly important

Wikipedia: There are 40 different motherboard types

What you need to know

CompTIA exam objective:
- "3.5: Given a scenario, install and configure motherboards, central processing units (CPUs), and add-on cards."

Focus on choosing the best motherboard for a scenario.
- Memorizing motherboard dimensions is probably not the most important thing.
- Know ATX, microATX, and ITX form factors.

ATX form factor

Advanced Technology Extended

Standardized by Intel in 1995
- Seen many updates over the years

Power
- 20-pin connector
- 24-pin connector, with an additional 4- or 8-pin connector

MicroATX (uATX, M-ATX)

Smaller than ATX motherboard
- Limited expansion slots

Backward compatibility
- Similar mounting points
- Similar power

Very popular form factor
- Actively manufactured as of 2019

ITX form factor

A series of low-power motherboards
- Developed by VIA technologies in 2001
- Small form factor

Mini-ITX is screw compatible with ATX
- Fits almost any enclosure

Small form factor uses
- Single-purpose computing, streaming media

---

## Motherboard Expansion Slots

A computer bus

Communication path
- A path for data between components

Internal PC growth
- Independent pathways

System expansion
- Additional capabilities

PCI

Peripheral Component Interconnect
- Nobody ever calls it that
- Created in 1994

Many expansion options
- 32 bit and 64 bit bus width
- Parallel communication

A common expansion interface on previous computer generations
- PCI Express is the newer technology.

PCI Express

Also known as PCIe
- Replaces the older PCI standard

Communicates serially
- Unidirectional serial "lanes"
- Slower devices don't slow down everyone

One, two, four, eight, sixteen, or thirty two full duplex lanes
- x1, x2, x4, x16, x32
- "x" is pronounced "by" ("by 4," "by 16")

---

## Motherboard Connections

24-pin motherboard power

Main motherboard power
- Provides +3.3 V, +/- 5V, and +/- 12 V

The 20-pin connector was the original ATX standard.
- The 24-pin connector was added for PCI Express power.

You can connect a 24 pin connector to a 20 pin motherboard
- Some cables are 20 pin +4 pin

PCIe 6-pin and 8-pin power

Additional power for PCI Express adapters
- 6-pin (75 W) and 8-pin (150 W) connectors
- Provide +12 V

Commonly seen on high power components
- Video adapters

Some cables have two pieces
- 6 pin and 2 pin = 8 pin
- Use on both 6 pin and 8 pin connectors

Storage drive interfaces - SATA

eSATA

Headers

A pin header
- A simple electrical interface
- The connector is attached to the header

Many different uses
- Power, peripheral connections, lights, and buttons

---

## Motherboard Compatibility

Intel and AMD

Two solid CPU manufacturers
- The differences are subtle

Cost
- AMD tends to be a bit less expensive

Different sockets
- The motherboard is designed for a particular CPU

Choosing a side
- Historically, AMD is value and Intel is performance
- These performance differences shift over time.

Server motherboards

Multisocket
- Supports multiple physical CPU packages
- Split the load

Memory slots
- Supports 4+ modules

Expansion slots
- Many slots and different sizes

Overall size
- Designed for a rack-mounted system
- Larger than a typical ATX system

---

## Hardware (25%)

- Component installation: Set up RAM, CPUs, and storage devices.
- Cables and connectors: Work with HDMI, Ethernet, and USB cables.
- Peripheral devices: Install and maintain printers, scanners, and other peripherals.
- Motherboards and power: Configure motherboards, power supplies, and cooling solutions.

---

## The BIOS

### BIOS (Basic Input/Output System)

The BIOS is firmware that initializes the computer and starts the operating system.
- It is also called System BIOS or ROM BIOS.
- It is stored in ROM or flash memory.

### Startup sequence

The BIOS initializes the CPU and memory, then builds the workspace.

POST (power-on self-test) checks the system during startup.

The BIOS looks for a boot loader, which starts the operating system.

### Legacy BIOS

The legacy BIOS is the original BIOS design and has been used for decades.

Older operating systems communicated with hardware through the BIOS rather than accessing it directly.

Legacy BIOS has limited hardware support and does not provide drivers for modern network, video, and storage devices.

### UEFI BIOS

UEFI (Unified Extensible Firmware Interface) is based on Intel's EFI (Extensible Firmware Interface).

UEFI is a defined standard implemented by manufacturers.

UEFI is designed to replace legacy BIOS in modern computers and supports graphical and text-based interfaces.

---

## BIOS Settings

### Opening BIOS setup

Use the system setup key during startup. Common keys include Del, F1, F2, Ctrl+S, and Ctrl+Alt+S.

Hyper-V is available through Turn Windows features on or off in Windows 10 and Windows 11.

VMware Workstation: <http://professormesser.link/vmware>

VirtualBox: <http://www.virtualbox.org>

Online simulators are also available; search for a UEFI BIOS simulator.

### Fast Startup

Fast Startup in Windows 10/11 and earlier versions does not fully shut down the computer.
- The computer starts too quickly to open BIOS setup during startup.

To open advanced startup options from the Windows desktop:
- Hold Shift while selecting Restart.
- Select Settings > Update & Security > Recovery > Advanced startup > Restart now.
- Alternatively, open System Configuration (`msconfig`).

Interrupting normal startup three times may display the boot options screen.

### BIOS configuration tips

Back up your BIOS configuration by writing detailed notes or taking a picture.

Do not change a setting unless you understand it; unnecessary changes can be difficult to troubleshoot.

Keep a backup of the configuration to save time during recovery.

### Boot options

The BIOS determines what happens when you power on the computer.

Disabled hardware is unavailable to the operating system.

You can modify the boot order to choose which device starts first, such as a USB drive, SSD, or hard drive.

### USB security

USB storage presents a security challenge because devices are small but can hold large amounts of data.

USB connections are convenient and provide high-speed data transfer.

The U.S. Department of Defense banned USB flash media for 15 months in 2008.
- SillyFDC worm

### Fan control

Computer components generate heat.

Computers use CPU and chassis fans for cooling.

Motherboards often include a fan controller and temperature sensors that adjust fan speed.

### Secure Boot

Malicious drivers or operating-system software can compromise a system.

Secure Boot is part of the UEFI specification.

It uses digital signatures to verify trusted software.
- Software will not run during the boot process without an approved signature.

Secure Boot is supported by operating systems such as Windows and Linux.

### UEFI firmware protection

UEFI firmware can include the manufacturer's public key and check the digital signature during a BIOS update.
- The BIOS can prevent unauthorized writes to flash memory.

Secure Boot verifies the operating system's bootloader signature.
- The bootloader must be signed with a trusted certificate or an explicitly approved signature.

### Boot password management

A boot or user password prevents the system from starting until the password is entered.

A supervisor or BIOS password restricts changes to BIOS settings.

Remember the password; you may need to reset the BIOS if it is lost.

### Clearing a boot password

Before clearing a boot password, store the BIOS configuration settings.

Complementary metal-oxide semiconductor (CMOS) memory may be backed up by a battery.

Modern systems usually store BIOS settings in flash memory, where they can be stored and accessed easily.

Some systems can be reset with a jumper that shorts (connects) two motherboard pins.

### Temperature monitoring

The BIOS may include built-in temperature monitoring and diagnostics.

Run these checks from the BIOS menu; no additional media or software is required.

These checks focus on hardware and do not involve the operating system.

### Virtualization support

Virtualization lets multiple operating systems run on one hardware platform and share its physical components.

Software-based virtualization was limited by performance and hardware-management challenges.

Processor support for virtualization improves performance and hardware management.
- Intel Virtualization Technology (VT)
- AMD Virtualization (AMD-V)

---

## HSM and TPM

### Secrets and keys

IT security relies on secrets and trust between devices and applications.

Encryption protects web servers, stored files, and phone data.

The encryption key is the secret that unlocks protected data.

Keys must be stored securely. Trusted Platform Modules (TPMs) and Hardware Security Modules (HSMs) provide ways to protect them.

### Trusted Platform Module (TPM)

A TPM is a specification for hardware that supports cryptographic functions on a single device.

It includes a cryptographic processor with random-number and key-generation functions.

Persistent memory can include unique keys installed during production.

TPM memory can store keys and hardware configuration information.

Password protection can help resist dictionary attacks.

A TPM contains a unique secret key that is not available outside the device.

The TPM links this key to the computer, so an encrypted drive may not work when moved to another computer.

The TPM can also serve as a root of trust, helping determine whether the computer has been modified or tampered with.

This cryptographic protection is specific to one device; the key cannot be used on another computer.

### Hardware Security Module (HSM)

HSMs are often used in large environments with server clusters and many different devices.

HSMs provide secure key storage and backup for servers. Lightweight HSMs for personal use may be available as smart cards or USB devices.

An HSM is often high-end cryptographic hardware in a plug-in card or separate device.

HSMs can accelerate cryptographic functions for other devices while keeping the key protected inside the module.

### TPM and HSM comparison

**TPM:** Used on a single system to protect local data. It is often built into the motherboard or available as an add-on module.
- Uses include mobile-device booting, screen locking, and encrypted storage.

**HSM:** Used by multiple systems to protect data across devices. It is often deployed as a high-end server or data-center appliance.
- An HSM can protect a Certificate Authority key on a central secure device.

---

## CPU Features

### Operating-system support

Processors and operating systems may support 32-bit or 64-bit architectures.

A 32-bit processor can represent $2^{32}$ values (4,294,967,296).

A 64-bit processor can represent $2^{64}$ values (18,446,744,073,709,551,616).
- This allows a much larger address space than 32-bit systems, though the operating system still has a maximum supported value.

Hardware drivers must match the operating system architecture: 32-bit (x86) or 64-bit (x64).

A 32-bit operating system cannot run 64-bit applications, but a 64-bit operating system can run 32-bit applications.

On 64-bit Windows, 32-bit applications are typically installed in `Program Files (x86)`, while 64-bit applications are installed in `Program Files`.

Advanced RISC Machine (ARM)

ARM is a CPU architecture developed by Arm Ltd.
- Arm designs the chip architecture; other companies license and build the chips.

Its simplified instruction set supports efficient processing with lower power use and heat output.

ARM has traditionally been used in mobile and IoT devices, but Apple and other manufacturers have also adopted it for desktops and laptops.

### Processor cores

Processors are available with two, four, eight, or more cores.

Each core has its own cache, and the processor may also have a shared cache.

---

## Expansion Cards

Expansion cards extend a computer's functionality when the motherboard does not provide the required features.

Installation is usually straightforward because cards are designed for end-user installation.

Install the card, then install its driver so the operating system can use it.

### Sound cards

Sound cards can provide high-end audio, an advanced headphone amplifier, and home-theater or Dolby decoding.

They may also include inputs for music capture, podcasting, and microphones.

### Video cards

Many CPUs include an integrated GPU, which provides video functionality within the CPU package.

Discrete graphics use a separate graphics card for higher performance.

### Capture cards

Capture cards accept video input for recording, live streaming, or connecting external cameras.

They can require high video bandwidth and commonly use a PCI Express connection.

### Network interface cards (NICs)

A NIC adds an Ethernet connection when the motherboard does not include one or its onboard NIC is not working.

NICs can also add connections to servers, routers, and security devices.

### Documentation and installation

Check the motherboard documentation for the number and type of available slots.

Check the adapter card documentation for minimum hardware and software requirements, known issues, and support information.
- Support forums can provide useful information from other users.

Some devices require driver installation before the hardware is installed.

### Driver installation

Check the documentation before installation.

Download the latest driver from the manufacturer's website.

Uninstall previous drivers through Windows Device Manager.

Use the manufacturer's setup program or install the driver manually through Windows Device Manager.

After installation, check Device Manager to confirm that the card is working.

---

## Cooling

Case fans

Cool air is pulled through a personal computer.
- Always check for good airflow

Motherboard layout becomes important.

Component location is key
- Devices, wiring, power

Many different sizes and styles
- And volume levels

On-board fans

Designed to cool an entire adapter card

Can be bulky
- May take additional adapter card space

Usually seen on high-end graphics cards

Fan specifications

Standard sizes
- 80 mm, 120 mm, and 200 mm

Different speeds
- Variable speeds

Different noise levels
- Not all fans sound the same

Fanless / passive cooling

No fans, no noise
- Silent operation

Specialized functions
- Video servers, TV set-top boxes, satellite receivers, and media servers

Functions are very controlled
- Carefully measured thermal tests

Low power components
- Heat sink

Heat Sink

Dissipate heat through thermal conduction
- Copper or aluminum alloy

Fins/grid increase surface area
- Heat is then transferred to the cooler air

They get HOT - don't touch them!

Thermal paste creates good contact between the chip and the heat sink.

Thermal paste

Thermal grease, conductive grease
- Thermally conductive adhesive

Place between the heat sink and the component
- Improves thermal conductivity
- Moves the heat away from the component

A little bit goes a long way
- Pea-sized application

Thermal pad

Conduct heat without the mess
- Cut to size and install

Easy to use
- Won't leak and damage components

Almost as effective as thermal paste
- But still very good

Not reusable
- Remove and replace

Liquid cooling

Coolant is circulated through a computer
- Not a new concept
  - Used in automobiles and mainframe computers

High-end systems

Gaming, graphics

Overclocking

---

## Computer Power

### Electrical safety

**Warning:** Always disconnect a device from its power source before working on it.
- Some devices store a charge in capacitors. Know how to discharge them safely before touching internal components.
- Never connect your body to any part of an electrical system or to its ground wire.
- Respect electricity; it can cause serious injury.

### Computer power supplies

Computers use direct current (DC), while most power sources provide alternating current (AC).
- A power supply converts 120 V AC or 240 V AC to 3.3 V DC, 5 V DC, and 12 V DC.
- A faulty power supply can prevent the computer from working.

### Amperes, voltage, and power

An ampere (amp, A) measures the rate of electron flow past a point in one second. It is analogous to the diameter of a hose.

Voltage (volt, V) is the electrical "pressure" that pushes electrons, analogous to how far a faucet is open.

A watt (W) measures real power use.
- Volts x amps = watts.
- 120 V x 0.5 A = 60 W.

### AC and DC current

Alternating current (AC) constantly reverses direction and distributes electricity efficiently over long distances.
- AC frequency is important: the United States and Canada use 110 to 120 V AC at 60 Hz; Europe uses 220 to 240 V AC at 50 Hz.

Direct current (DC) flows in one direction at a constant voltage.

Voltage varies by country. If a power supply requires manual switching between 120 V and 230 V, check the setting with a meter or use an auto-switching power supply.
- Never connect a 120 V power supply to a 230 V source unless it supports that voltage.

### Power-supply output

Power supplies provide different voltages for different components. Voltage is a difference in electrical potential measured relative to a common reference point, usually ground.
- An analogy: the second floor of a house may be +10 ft and the basement -10 ft relative to the front door.
- **+12 V:** PCIe adapters, hard-drive motors, cooling fans, and many modern components.
- **+5 V:** Some motherboard components; many components now use +3.3 V.
- **+3.3 V:** M.2 slots, RAM slots, and motherboard logic circuits.
- **+5 VSB:** Standby voltage.
- **-12 V:** Integrated LAN, older serial ports, and some PCI cards.
- **-5 V:** Available for ISA adapter cards, although most cards did not use it. Modern motherboards do not have ISA slots.

### Motherboard power connectors

The 24-pin connector provides the main motherboard power, including +3.3 V, +/- 5 V, and +/- 12 V.
- The 20-pin connector was the original ATX standard; the 24-pin version was added for PCI Express power.
- A 24-pin connector can connect to a 20-pin motherboard. Some cables split into 20-pin and 4-pin sections.

### Redundant power supplies

Servers may contain two or more power supplies.
- Each supply can handle 100% of the load; normally, each runs at about 50%.
- Hot-swappable supplies can be replaced without powering down the server.

### Power-supply connectors

Fixed cables are attached to the power supply, so a supply may have too many or too few connectors for a system.
- Modular power supplies let users add cables as needed, reducing unused wires and improving airflow, but they may cost more.

### Sizing and efficiency

Power supplies are rated in watts, both overall and for individual voltage rails. A larger supply is not necessarily better and will not make a computer faster.
- Older cases and systems may use proprietary power-supply sizes.
- Calculate the wattage required by all components, including the CPU, storage devices, and video adapter. Online calculators can help.
- Video adapters often draw the most power; check the manufacturer's recommended supply wattage.
- A supply operating at about 50% capacity can provide efficiency and room to grow.

Converting AC to DC is not perfectly efficient; some power is lost as heat.
- Power supplies commonly range from 80% to 96% efficiency, depending on voltage and redundancy.
- Higher efficiency means more DC power and less heat, which can reduce costs.
- Choose a suitable rating from an established certification program.

---

## Multifunction Devices

### Multifunction devices

Multifunction devices (MFDs) combine printing, scanning, faxing, network access, and sometimes phone-line connections or web printing.
* Many things can go wrong, so installation and troubleshooting are part of the job.
* During unboxing, plan for the device's size and keep it out of walkways.
* Check the area for power, network access, and accessibility.

### Printer drivers

* Use drivers specific to the printer model.
* Select drivers for the correct operating system, such as Windows 10 or Windows 11.
* Select the correct operating system version; 32-bit drivers differ from 64-bit drivers.
* Drivers cannot be mixed and matched.

### PCL and PostScript

* PCL (Printer Command Language) was created by Hewlett-Packard and is commonly used across the industry.
* PostScript was created by Adobe Systems and is popular with high-end printers.
* Match the drivers to the printer: PCL printers need PCL drivers, and PostScript printers need PostScript drivers.

### Firmware

The firmware is the multifunction device's internal operating system.
* Starts the system and connects it to the network.
* Interprets incoming data and runs the printing process.
* Update firmware to avoid incompatibilities and fix bugs.
* Download firmware from the device manufacturer's website and install it with a stable platform and power source.

### Wired device sharing

* **USB:** A common connector. Printers may use USB Type B while computers use USB Type A, or both may use USB-C.
* **Ethernet:** Uses an RJ45 connector.
* A printer may support more than one connection option.

### Wireless device sharing

* **Bluetooth:** Limited range.
* **802.11 infrastructure mode:** Multiple devices connect through an access point.
* **802.11 ad hoc mode:** Devices connect directly without an access point.

### Printer sharing

* **Printer share:** The printer connects to a computer, which shares it with other users. The computer must be running.
* **Print server:** Sends jobs directly to the printer. Jobs are queued and managed on the printer, often through a web interface or client utility.

### Configuration settings

* **Duplex:** Saves paper by printing on both sides; not all printers support it.
* **Orientation:** Choose portrait or landscape. The paper does not rotate; the printer adjusts the output.
* **Tray settings:** Printers may have multiple trays for plain paper or letterhead. Choose the correct tray in the print dialog.
* **Quality:** Configure resolution, color or grayscale, and color-saving options.

### Printer security

* **User authentication:** Set rights and permissions for printing and printer management, or allow everyone to print.
* **Badging:** Require users to authenticate at the printer with an employee badge before their jobs print.
* **Audit logs:** Support cost management and security monitoring. Logs may be available in Event Viewer, system events, the printer, or the print server.
* **Secure printing:** The printer must support it. Set a passcode and enter it at the printer to release the job.

### Flatbed scanners

* Available as part of an all-in-one multifunction device or as a standalone flatbed.
* May include an ADF (Automatic Document Feeder) for multiple pages.

### Network scan services

* **Scan to email:** Sends scans to your inbox; large scans can fill your mailbox.
* **Scan to folder:** Uses SMB (Server Message Block) to send files to a Microsoft share.
* **Scan to cloud:** Stores scans in a cloud account such as Google Drive or Dropbox.

---

## Laser Printer Maintenance

Laser printers combine a laser, high voltage, charged ions, powdered ink, heat, and paper.

They produce very high-quality output.

They print quickly.

They are very complex.
- Many moving parts
- Requires on-printer memory and processing
- Messy on the inside

Corona wire or charge roller negatively charges the drum

The laser neutralizes the negative charge.

Negatively charged toner sticks to the areas marked by the laser.

Toner on the drum is transferred to the paper

The fuser uses heat and pressure to bond toner to the page.

The drum is cleaned for another pass

Replacing the toner cartridge

Check the printer messages.
- Low doesn't mean empty

The toner can also contain the OPC drum
- Organic photoconductor drum
- Sensitive to light; keep it in the bag

Power down the printer
- Safety first

Remove the packing strips from the new drum.
- Replace the old drum.

Laser printer maintenance kit

Laser printers wear out
- All those moving parts
- Heat and pressure

Standard maintenance kits
- Replacement feed rollers, new fuser unit, etc

When to perform maintenance?
- Check the printer's page counter.

Power down and replace the components
- Fuser units are HOT

Reset the page counter when you're done!

Laser printer calibration

Different toner cartridges print with different densities.
- Some dark, some light

Laser printer calibration can adjust the density
- Adjust the density until the output looks correct.
Can be automated or a manual process
- Every printer is different
- Check the printer manual

Laser printer cleaning

Laser printers are dirty.
- All that toner and paper dust
- Toner should be handled properly

Check manufacturer's recommendations
- Water, isopropyl alcohol (IPA)
- Don't use harsh chemicals

Outside: use a damp cloth.

Inside: wipe away dust.
- Don't use a normal vacuum cleaner or compressed air
- Wash toner from skin with cold water
- Clean rollers with IPA

---

## Inkjet Printers

Inkjet printers disperse ink onto paper. They are relatively inexpensive, quiet, and capable of high-resolution output, but their proprietary ink can be costly. Prints may fade, and the print heads can clog.

### Ink cartridges and print heads

Cartridges supply ink to the print head, which places drops of ink on the page.
- CMYK stands for cyan, magenta, yellow, and key (black).
- Some consumer printers integrate the print head into the cartridge, so replacing the cartridge also replaces the print head.
- Other printers use separate ink cartridges and print heads.

### Feed rollers and duplexing

Feed rollers pull paper through the printer and must be kept clean and in good condition.
- Duplexing prints on both sides of the paper and is included with some printers.

---

## Inkjet Printer Maintenance

### Cleaning print heads

Print heads use small ink droplets and nozzles, which can clog.
- Many printers clean the heads automatically each day.
- Streaks or missing colors can indicate a clog.
- A cleaning cycle can also be started manually and usually takes a few minutes.
- If the print head or cartridge is removable, manual cleaning may help; follow the printer's instructions.

### Replacing and aligning inkjet cartridges

Cartridges usually contain separate colors: cyan, magenta, yellow, and key (black), although some combine colors.
- Replacing a cartridge takes seconds; calibration and preparation may take a few minutes.
- Recycle empty cartridges where possible.
- Align the nozzles so printed lines are crisp and colors line up. Use the printer's calibration option and make small adjustments if needed.

### Clearing paper jams

Paper jams are common because paper travels through many turns and rollers.
- Remove the tray and any loose paper.
- Pull jammed paper firmly along the paper path without tearing it.
- Check for and remove all scraps of paper.

---

## Thermal Printers

Thermal printers use heat-sensitive paper that darkens when heated, so they require no ink. They are very quiet and are commonly used for receipts and labels.

### Thermal paper and print mechanism

Thermal paper is coated with a thermochromic chemical that changes color when heated.
- The paper is sensitive to light and heat; keep it away from hot areas and clear tape.
- Thermal printers use a feed assembly and a full-length heating element rather than a moving print head.
- The paper looks similar to ordinary paper but may feel different.
- Common uses include cash registers and credit-card terminals.

---

## Thermal Printer Maintenance

### Thermal printer maintenance

Thermal paper is inexpensive but cannot be substituted with ordinary printer paper. Keep track of the required roll size; replacement is usually a simple feed process.

Clean the heating element with a recommended liquid cleaner, such as isopropyl alcohol (IPA), or a cleaning pen.
- Check the manufacturer's recommendations and swab small areas gently.
- A cleaning card can clean the print head and paper path.

Remove paper bits and dust by taking the printer outside and blowing it out, then wiping it with a damp cloth.
- Avoid using a vacuum unless it is designed for computers and protects against static discharge.

Excessive heat can darken the entire page. Keep thermal paper away from car dashboards, radiators, and hair dryers.
- Receipts fade over time, so thermal paper is not suitable for archival storage.

---

## Impact Printers

Dot-matrix printers are impact printers that use a print head with a matrix of pins to strike an inked ribbon against the paper.
- They are useful for carbon or multipart copies and have a low cost per page.
- They are noisy, produce limited graphics, and are now used in niche situations.

### Dot-matrix print head and ribbon

The print head moves back and forth across the page while its pins strike the ribbon and paper.
- The fabric ribbon is a continuous loop, often supplied as a single modular unit.
- Ribbon sizes may be specific to the printer model.

### Tractor feed and multipart paper

Tractor-feed printers pull continuous paper through perforations along the paper edges rather than relying on friction.

Multipart paper produces multiple copies of a form in one pass without carbon paper.
- Impact on the top sheet activates micro-encapsulated ink on its back and a clay coating on the sheet below.
- These inks, dyes, and coatings can cause mild irritation in some chemical combinations.
- Multipart paper and dot-matrix printers can be difficult to find, so printing another copy may be easier and less expensive.

---

## Impact Printers Maintenance

### Replacing the ribbon

Replace the ribbon when the print becomes too light because its ink is eventually consumed.
- Most ribbons are modular and can be replaced in less than a minute.

### Replacing the print head

The print head takes considerable wear because it repeatedly strikes the ribbon and paper. It also becomes hot, so use care when handling it.
- Look for a release lever or bar to remove the modular print head.
- Use a compatible ribbon and print head to maintain output quality.

### Replacing paper

Loading paper is more exacting than with a laser printer.
- Align tractor-feed paper with the feed holes.
- Position forms so the text fits the predefined space.
- Ensure the paper can feed freely and that nothing blocks the path.

---

## Virtualization and cloud computing (11%)

Virtualization concepts include virtual machines, hypervisors, and desktop virtualization. Cloud models include IaaS, SaaS, and PaaS.

---

## Virtualization Concepts

One computer can run multiple operating systems, such as macOS, Windows 11, and Ubuntu Linux, at the same time.
* Each operating system has its own CPU, memory, and network resources, even though they share one physical computer.
* **Host-based virtualization:** Runs virtual machines alongside your normal desktop environment.
* **Standalone virtualization:** An enterprise server hosts virtual machines.
* Virtualization has been used since IBM mainframe systems in 1967.

### Sandboxing

A sandbox is an isolated testing environment with no connection to the real world or production system.
* Provides a safe place to try code and recover from mistakes.
* Developers can build applications in a secure environment and test them in separate sandboxes.
* Additional development features can include restoring a previous snapshot and running additional systems.
* A separate test environment brings the pieces together to check that they work.

### Legacy software and operating systems

* Run different versions of an application in separate VMs on the same system.
* If an application requires an older operating system, create a VM with that operating system.

### Cross-platform virtualization

* Windows, macOS, and Linux each have strengths and weaknesses.
* Run different operating systems at the same time and move between them without rebooting.
* Save time and resources by using one physical computer.

---

## Virtualization Services

### The hypervisor

A hypervisor, or virtual machine manager, manages the virtual platform and guest operating systems.
* May require a CPU that supports virtualization, which can improve performance.
* Manages hardware resources such as the CPU, networking, and security.
* Allows multiple operating systems to run on the same hardware.
* Each application instance has its own operating system, adding overhead and complexity. Virtualization can be relatively expensive.

### Hypervisor types

* **Type 1: Bare metal.** The hypervisor is the primary operating system. Examples include VMware ESXi, Microsoft Hyper-V, and Xen Project.
* **Type 2: Hosted.** The hypervisor runs in an existing OS such as Windows, Linux, or macOS, and virtual machines run on top of it. Examples include VMware Player, Oracle VirtualBox, and Parallels Desktop.

### Resource requirements

* **CPU:** Intel Virtualization Technology (VT) or AMD-V support.
* **Memory:** Additional memory beyond the host OS requirements.
* **Disk space:** Each guest OS has its own image and needs space for the OS and data.
* **Network:** Configure networking for each guest OS, often with a virtual switch.

### Network requirements

Most client-side virtual machine managers provide their own internal virtual networks.
* **Shared network address:** The VM shares the physical host's IP address, uses a private IP address internally, and uses NAT to translate traffic to the host IP.
* **Bridged network address:** The VM appears as a device on the physical network.
* **Private address:** The VM cannot communicate outside the virtual network.

### Hypervisor security

* The hypervisor is an attractive target, though the notes report no significant vulnerabilities yet.
* **VM escaping:** Malware detects that it is in a VM, compromises the hypervisor, and may move between guest operating systems.
* Hosted services use virtual environments; malware on one customer's server may attempt to gather information from another.

### Guest operating system security

Each guest is self-contained, like a real computer.
* Use traditional security controls such as a host-based firewall and antivirus or anti-spyware software.
* Watch for rogue VMs that attackers try to install.
* Self-contained VMs provided by third parties can be dangerous because you may not know what is running on them.

### Virtual Desktop Infrastructure (VDI)

* Applications run on a remote server; the local device provides a keyboard, mouse, and screen.
* Desktop as a Service (DaaS) is a related model.
* The client can use a minimal operating system and require less memory and CPU power.
* Network connectivity is critical because everything happens across the network.

### Application containerization

A container is a standardized, portable unit of software that contains an application and its dependencies.
* Runs as an isolated process in a sandbox so apps cannot interact with each other.
* Container images are lightweight, use the host kernel, and provide separation between applications.

---

## Cloud Models

### Cloud computing

More than just a server hosted elsewhere
- Extends the management of applications and services

Effectively unlimited resources
- You just have to pay for it

Deploy infrastructure in minutes.
- Create and tear it down as needed.

International scope
- Deploy in specific parts of the world.

Use only the required resources
- Costs are based on the amount you use.

Cloud deployment models

Public
- Generally available over the internet.

Private
- Your own virtualized local data center.

Hybrid
- A mix of public and private clouds.

Community
- Several organizations share the same resources

Infrastructure as a Service (IaaS)

Sometimes called hardware as a service (HaaS)
- Outsource your equipment

You're still responsible for management and security.

Your data is hosted remotely, but remains more within your control.

Web server providers are one example of infrastructure as a service.

Software as a Service (SaaS)

On-demand software
- No local installation
- Why manage your own email or payroll systems?

Data and applications are managed centrally.
- Your data is hosted by the provider.

A complete application offering
- No development work required
- Google Mail, Microsoft 365

Platform as a Service (PaaS)

No servers, no software, no maintenance team, no HVAC
- Someone else handles the platform, you handle the development

You don't have direct control of the data, personnel, or infrastructure.
- The provider handles the platform; trained security professionals monitor it.
  - Evaluate the provider and its security controls carefully.

Put the building blocks together
- Develop your app using the building blocks available on the platform.
- Salesforce.com

Responsibility matrix

---

## Cloud Characteristics

Shared resources

Internal/private cloud
- Dedicated resources
- Build your own cloud
- Pay for everything up front
- No ongoing costs

External/public cloud
- Shared resources with a public cloud
- Underlying infrastructure owned by a third party
- Costs may be metered or paid up front.

Metered and non-metered

Metered utilization
- You pay for what you use
- Cost to upload (ingress traffic)
- Cost to store
- Cost to download (egress traffic)

Non-metered utilization
- You pay for a block of storage
- No cost to upload
- No cost to download

Cloud computing characteristics

Elasticity
- Seamlessly scale up and scale down as needed
- The cloud enables instant resource provisioning

Availability
- Systems are always available
- Redundancy provides availability.

File synchronization
- Information can be duplicated across cloud locations

Multitenancy
- Many different clients use the same cloud infrastructure.

---

## Troubleshooting Hardware

POST (power-on self-test)

Tests major system components before the operating system boots.
- Main system (CPU, BIOS)
- Video
- Memory

Failures are usually indicated by beeps or codes.
- BIOS versions can differ, so check your documentation.

Don't bother memorizing the beep codes
- They're all different between manufacturers
- Know what to do when you hear them

POST and boot

Blank screen on boot
- Listen for beeps
- Bad video, bad RAM, bad CPU
- BIOS configuration issue

BIOS time and date settings
- Maintained with the motherboard battery
- Replace the battery

### Incorrect boot device

If the system attempts to boot from the wrong device:
- Set the boot order in the BIOS.
- Confirm that the startup device has a valid operating system.
- Check for removable media in the startup device.

### Crash screens

Windows stop errors, including the Blue Screen of Death (BSOD), indicate serious system problems.

Crash screens contain important information and may also be written to the event log.

### Blue screens and shutdowns

BSODs during startup or shutdown may be caused by faulty hardware, drivers, or applications.

Try Last Known Good Configuration, System Restore, or rolling back a driver.
- You can also try Safe Mode.

Reseat or remove the hardware, if possible.

Run hardware diagnostics provided by the manufacturer; the BIOS may also include diagnostic tools.

### Application crash screens

Applications have their own error notifications, and the amount of useful information varies.

Help desk tickets vary in quality, so collect as many details as possible.

A detailed transcript of the error is useful, and screenshots can provide even more information.
- Ask users to include screenshots in ticket instructions.

### Blank screen

First, confirm that the monitor is connected; check both the power and signal cables.

Check the monitor's selected input: HDMI, DisplayPort, DVI, or VGA.

If the image is dim, check the brightness controls.

Try the monitor on another computer to determine whether the monitor is faulty.

If video fails after Windows loads, try VGA mode (F8).

### No power

Check for power at the source and from the power supply. Use a multimeter if needed.

### Fans spin, but other devices have no power

Check where the fans are connected and verify the power-supply output.
- If the system does not POST, the motherboard may be faulty.
- Case fans may have lower voltage requirements than other components.

### Sluggish performance

Use Task Manager to check for high CPU utilization and disk I/O.

Install the latest Windows updates and drivers.

Check available disk space and defragment a hard disk if appropriate.

Power-saving mode on a laptop may throttle the CPU.

Run an antivirus or anti-malware scan.

### Overheating

CPUs, video adapters, and memory generate heat.

Check that fans, airflow, and heat sinks are clean and unobstructed.

Verify temperatures with monitoring software built into the BIOS or with a utility such as HWMonitor: <http://www.cpuid.com/>.

### Smoke or burning smell

Smoke or a burning smell may indicate an electrical problem.

Disconnect power immediately; a computer should not produce a burning odor.

After the system has cooled, locate and replace all damaged components.

### Random shutdowns

An unexpected shutdown may produce a black screen without warning. Check Event Viewer for details.

The cause may be heat, especially during gaming or other CPU- and graphics-intensive tasks.
- Check all fans and heat sinks.
- The BIOS may show fan status and temperatures.

Failing hardware is another possibility. Check for recent changes, review Device Manager, and run diagnostics.

Many issues are possible; eliminate components and causes that are working correctly.

### Application crashes

An application may stop working, display an error, or close without warning.

Check Event Viewer and other logs for diagnostic information.

Check Reliability Monitor for a history of application problems and possible solutions.

Reinstall the application or contact its support team.

### Unusual noises

Computers should hum, not grind or make other unusual noises.

Rattling may indicate loose components.

Scraping may indicate a hard-drive problem.

Clicking may indicate a fan problem.

Popping may indicate a blown capacitor.

### Inaccurate system date and time

* A bad motherboard battery is a common cause; it is often a button-style battery.

A bad battery may require you to reconfigure BIOS settings or the date and time on every boot.

On older systems, reset the BIOS configuration by removing the battery.
* Newer computers use a jumper.

---

## Hardware and network troubleshooting (28%)

- Diagnosing issues: Identify and fix hardware, network, and connectivity problems.
- Troubleshooting tools: Use multimeters, cable testers, and loopback plugs.

---

## Troubleshooting Storage Devices

### Storage failure symptoms

#### Read/write failures

An error such as "Cannot read from the source disk" may indicate a drive problem.

#### Slow performance

Constant drive activity and repeated retries can indicate a failing or overloaded drive.

#### Clicking or grinding noises

Loud clicking, grinding, or scraping can indicate mechanical failure in a hard drive.
- Hard drives contain spinning platters and moving actuator arms, so a small mechanical problem can cause failure.
- Metal-on-metal contact can cause poor performance or make the drive inaccessible.
- Recovery can be difficult; restore from a recent, well-maintained backup.

### Troubleshooting disk failures

If possible, back up important data first. A failing drive may deteriorate quickly.
- Check for loose or damaged cables.
- Check for overheating, especially if problems occur after startup.
- Check the power supply, particularly if new devices were recently added.
- Run diagnostics from the drive or computer manufacturer, preferably on a known-good computer.

### Boot failure symptoms

If the drive is not recognized or the computer reports "Boot device not found," note any indicator lights, beeps, or error messages.
- If the operating system is not found, confirm that the drive is detected.
- Check cables and other physical connections.
- Check the BIOS boot sequence for removable disks, such as USB drives, and disabled storage interfaces.
- For a new installation, verify data and power cables and try a different SATA interface.
- Test the drive in another computer if possible.

### Data loss or corruption

Hard drives are mechanical and will eventually fail. Repairs can be difficult, expensive, and unsuccessful.
- An SSD may stop working; sometimes it can read data but cannot write it.
- Lost or corrupted data may be impossible to recover.
- Always maintain a backup.

### RAID failures

A drive failure in a RAID array may be caused by hardware, power, or communication problems.
- Failures may be indicated by error messages, email notifications, or audible alarms.
- Carefully analyze the array, including its drives and volumes.

### S.M.A.R.T. monitoring

Self-Monitoring, Analysis, and Reporting Technology (S.M.A.R.T.) can help identify warning signs before a drive fails.
- Use a third-party utility or tools built into the drive array.
- Monitor metrics over time for changes or increasing values; monitoring may be provided by a NAS or other software.
- Configure automated email, text, or console notifications.
- Back up data and replace a failing drive before it causes an outage.

### Extended read/write times

Reading and writing data involves memory access, bus communication, drive access, and transfers to or from storage. Delays can occur at any point.
- Input/output operations per second (IOPS) is a broad measure of storage performance.
- It can help compare drives; for example, a hard drive may provide about 200 IOPS, while an SSD may provide 1,000,000 IOPS.

### Missing drives

If the operating system starts normally but other drives are missing, check the BIOS.
- Internal drives may have failed or become disconnected.
- External drives may lack power or have a faulty cable.
- Network shares may be connected at startup, reconnected at sign-in, or mapped by a login script.

### Missing RAID array

A missing array may indicate a missing or faulty RAID controller.

---

## Troubleshooting Display Issues

### Incorrect input source

Confirm that the monitor is connected and that both the power and signal cables are secure.
- Select the correct monitor input: HDMI, DVI, VGA, or DisplayPort.
- If the image is dim, check the brightness controls.
- Test the monitor on another computer to determine whether the monitor is faulty.
- If video fails after Windows loads, try VGA mode (F8).

### LCD projector bulbs

LCD projectors use bright metal-halide bulbs that can operate at around 1,000 degrees Celsius.
- Fans cool the bulb during operation and continue cooling it after the light is turned off.
- The projector may shut down if temperatures become too high.
- When replacing a burned-out bulb, clean dust from the air filters and external air intakes and outlets.

### Fuzzy image

An LCD display has a fixed number of pixels. It looks best when the video settings match its native resolution; a mismatch can cause distortion.
- When changing resolution, try a multiple of the native resolution.
- For example, 2560 x 1600 and 1920 x 1200 have the same aspect ratio.

### Burn-in and image sticking

Burn-in can affect different monitor types. Some displays shift pixels to reduce the effect, often without the user noticing.
- LCDs can experience image sticking; displaying a white screen for an extended period may help remove it.

### Dead pixels

A dead pixel may remain black because of a manufacturing defect; it is usually not caused by a cable or power issue.
- Clean the monitor screen with a damp cloth.
- If the defect persists, the monitor may need to be replaced.

### Flickering screen

Check the video-cable connections; a loose cable can cause signal loss.
- Replace the cable if needed.
- Test another display to determine whether the monitor is faulty.
- Confirm that the operating-system display settings match the monitor.

### Incorrect color

If colors are inaccurate, check the monitor's tint, color presets, and factory-reset options.
- Check the graphics driver configuration.
- If the display looks too blue, check the operating system's Night light settings.

### Audio issues

If the monitor's speakers have no sound or low volume, check the monitor's audio controls, volume, and mute status.
- Confirm that audio is sent over HDMI, DisplayPort, or Thunderbolt by checking the operating system's selected output.
- If the monitor has other audio inputs, check its audio jacks.

### Dim image

Check the monitor's brightness and contrast settings.
- Check operating-system settings for auto-dimming, battery dimming, or driver controls.
- A backlight problem may affect all or only part of the screen.

### Image quality and geometry

Flickering or incorrect color patterns may still allow limited use, but should be investigated.
- Check the cable pins, especially if a color is missing.
- Confirm that the operating-system refresh rate and resolution match the display specifications.
- Check or replace the cable and troubleshoot the video driver; disabling hardware acceleration may help isolate a software issue.

### Sizing and scaling

The display may scale the video output to fit the screen. Check the monitor's scaling options.
- Adjust the operating-system resolution and scaling settings to change the size of the user interface and icons.

### Distorted image

Lines, flashing colors, or blocks may indicate a hardware or software problem.
- LCD panels are fragile; a damaged panel usually needs replacement.
- Check for a faulty cable or adapter.
- Check for a faulty video driver.

---

## Troubleshooting Mobile Devices

### Battery health and reception

Replace an aging battery; batteries can only be recharged a limited number of times.
- Poor reception may cause a device to search constantly for a signal. Check that Airplane mode is off.
- Disable unnecessary features such as Wi-Fi, Bluetooth, or GPS when appropriate.
- Check application battery usage in Settings > Battery on iOS/iPadOS or Android.

### Swollen or faulty batteries

A swollen battery may contain built-up gas and is designed to contain it.
- Do not open the battery pack or container because this creates a significant fire risk.
- Stop using a faulty battery and dispose of it properly; device damage is preferable to a fire.

### Broken screens

Back up the device before replacing a broken screen.
- Broken glass is sharp. A screen protector or clear tape may help protect users until repair.
- Screen replacement usually has no easy workaround.

### Charging problems

Check each part of the charging process, including the cable, connector, and power adapter.
- Remove obstructions from the connector.
- Do not use frayed or damaged cables; try a known-good cable.
- Check the power adapter with a multimeter if needed.

### Connectivity problems

Poor or unavailable cellular or Wi-Fi connectivity can depend on location and signal strength.
- Cellular service may be better outdoors.
- Wi-Fi has limited range; interference can reduce throughput.
- A channel or frequency change may help with Wi-Fi interference.

### Liquid damage

Many phones have a Liquid Contact Indicator (LCI) that changes color after contact with liquid.
- Power the phone down and do not turn it back on.
- If possible, remove the case, cards, back cover, and battery.
- Do not put the phone in rice; this is not an effective drying method.
- Do not turn it on, charge it, connect it to power, press keys, heat it, or move it around.
- Wait at least a day, or until it appears dry, and then wait a few additional hours.

### Overheating

Phones may shut down automatically to prevent overheating damage.
- Battery charging and discharging, CPU use, and display brightness all generate heat.
- Check app usage because some apps use significant CPU resources.
- Avoid direct sunlight, which can quickly overheat a phone.

### Digitizer issues

A digitizer problem may cause a black touchscreen or prevent touches from registering.
- For an iOS reset, use the device's documented power-off and restart button sequence.
- To restart some Android devices, remove and reinstall the battery if possible, or hold the power and volume-down buttons.
- Key combinations vary by phone, and some devices do not support a button-based reset.

### Physically damaged ports

Charging and data-transfer ports can be damaged by rough handling or accidents.
- Inspect the port if the device will not charge.
- If the port is not modular, repair may require replacing the system board.

### Malware

Malware is a concern on mobile devices as well as computers.
- Look for unusual apps, large data transfers, pop-up messages, high CPU use, overheating, or excessive battery drain.
- Use a security app or scanner to identify infections.

### Cursor drift

Random input or cursor movement without touching the device is common on older screens.
- Recalibrating the screen may resolve the drift.

### Application installation problems

Check available storage and delete unnecessary data if there is not enough space.
- Check network connectivity because apps are downloaded from external services.
- Check operating-system and app compatibility; update the OS or app when possible.
- Clear the Google Play Store cache or verify the iCloud credentials, then log out and back in if needed.

### Stylus problems

- Check the stylus battery and recharge it if necessary.
- Check its Bluetooth connection and try pairing it again.
- Inspect the stylus for physical wear and replace the tip if needed.

Restarting the device can reset the operating system and network connections.

### Degraded performance

Outdated operating-system or app software, low storage, hardware issues, and too many background apps can slow a device.
- Update the software and restart the device.
- Low storage can cause slowdowns and crashes.
- Faulty RAM or storage can also cause performance problems.
- Close unused background apps to reduce memory use.

---

## Troubleshooting Networks

### No network connectivity

Check for a link light and confirm that the cable is connected.
- Ping the loopback address (`127.0.0.1`) to test the protocol stack.
- Ping the local IP address to check the local configuration, adapter, and link.
- Ping the default gateway to test connectivity on the local network.
- Ping an address beyond the router, such as `8.8.8.8` or `9.9.9.9`.

### Intermittent wireless connectivity

Interference from another device using the same frequency can disrupt a wireless connection.
- Check signal strength and the transmitting and receiving antennas.
- Check the channel; automatic selection is common, but manual tuning may help.
- Multipath interference can occur when signals reflect off flat surfaces.
- Place access points close to the users who need coverage.

### Slow network speeds

A slow connection may not be caused by the network itself.
- Confirm end-to-end connectivity with a ping or application login, then run a speed test.
- Evaluate utilization, errors, throughput, and filtering or access control lists (ACLs) at each network hop.
- A packet capture may be needed for detailed verification.

### Limited or no connectivity

Windows may display "Limited or no connectivity" or "No Internet Access" in the system tray.
- Check the local IP address; an APIPA address provides only local connectivity.
- If a DHCP address is assigned, ping the local gateway and a remote IP address.

### Jitter

Real-time media, such as voice and live video, is sensitive to delay and requires data to arrive at regular intervals.
- Lost packets may not be retransmitted because the conversation cannot be rewound.
- Jitter is variation in packet arrival times; excessive jitter can cause missed information and choppy voice calls.

### Poor VoIP quality

Real-time applications require high throughput and low latency.
- Run a speed test to identify slow links.
- Verify local networking equipment; an older router can cause problems.
- Review network performance and use a packet capture if needed.

### Port flapping

Port flapping occurs when a network interface repeatedly goes up and down.
- Verify the cable and wiring.
- Move the device to another switch interface to determine whether the problem follows the port or the device.
- Replace faulty hardware or cables; additional purchases may be required.

### High latency

Latency is the delay between a request and its response. Some latency is expected because of the limits of physics.
- Measure response times at each step; multiple tools may be needed.
- Packet captures can provide microsecond-level detail. Capture traffic at both ends when possible.

### External interference

Predictable sources include fluorescent lights, microwave ovens, cordless telephones, and other high-power sources.
- Unpredictable interference can occur in multi-tenant buildings.
- Measure the signal-to-noise ratio (SNR) and monitor performance.

The signal is the desired transmission; noise is unwanted interference from other networks or devices. A larger SNR is better; a 1:1 ratio is poor.

### Authentication issues

Accessing a resource requires the correct credentials, such as a username, password, or other authentication factor.
- Verify that the session is active; it may need to be refreshed by logging out and back in.
- Authentication problems may be difficult to see when they occur in a service or background process.
- Capture packets to verify connectivity and look for errors.

### Intermittent Internet connectivity

Determine the scope of the outage using ongoing pings, traceroute to a known destination, and speed tests.
- For external issues, contact the Internet Service Provider (ISP) and have contract and account information available.
- Check the service-level agreement (SLA).

---

## Troubleshooting Printers

### Testing and diagnostics

Print or scan a test page using the utility built into Windows or the printer; a separate application is not required.
- Use web-based tools built into the printer, vendor-specific utilities, or generic diagnostic utilities.

### Poor print quality

- **Lines down the page:** Clean inkjet print heads or check a laser printer's photosensitive drum for scratches.
- **Faded prints or blank pages:** Check toner or ink levels.
- **Double images or speckling:** Clean the laser printer's optical drum. A ghost image may come from a previous drum rotation.

### Garbled printing

The wrong printer driver or model may cause garbled output.
- Check that the page description language (PCL or PostScript) matches the printer.
- Print a test page to verify printer operation.
- If only one application has the problem, check its output and update the application.

### Paper jams and feed problems

Remove jammed paper carefully to avoid tearing it or damaging internal components.
- If paper does not feed or multiple pages feed at once, check the trays and pickup rollers. Pickup rollers may be included in a laser printer maintenance kit.
- Creased paper may indicate a problem in the paper path; check the paper weight.
- Follow the printer manual when clearing jams. Some inkjet printers require a specific procedure.

### Print queue problems

Corrupted print jobs can cause the print spooler to crash or freeze. Most spooler configurations restart automatically.
- Check Windows Event Viewer and the Windows Print Service logs.
- Monitor the queue to identify whether one job is causing the problem.

### Grinding noises

Grinding indicates that something may not be operating properly.
- Check for a paper jam or stalled carriage.
- Follow the manufacturer's maintenance instructions; the printer may require additional maintenance or replacement.

### Finishing problems

Finishing operations occur after ink or toner is applied and may include collating or binding.
- For staple jams, follow the manufacturer's procedure; larger printers may collate and staple sets of pages.
- If hole-punch locations are incorrect, verify the printer driver and update it if needed.

### Incorrect page orientation

If a portrait document prints in landscape, check the settings in the print driver and on the printer console.
- Update the driver if the orientation settings are correct but the problem persists.

### Unrecognized paper tray

Office printers often have trays for plain letter paper, legal paper, letterhead, or colored paper.
- The page size selected in the print driver must match the paper in the tray; for example, a 14-inch legal page cannot print correctly on 11-inch letter paper.
- Compare the user's configuration with the trays installed in the printer.

### Connectivity problems

Printers are network devices and follow the same networking rules as other devices.
- Confirm whether the connection is wired or wireless.
- Verify the IP address, subnet mask, default gateway, DNS, and other network settings.
- Check the print server, which may be part of the printer.
