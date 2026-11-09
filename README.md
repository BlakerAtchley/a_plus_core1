# CompTIA A+ Study Notes

Organized reference notes on networking, hardware, virtualization, peripherals, and troubleshooting.



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

TCP ports 20 (active-mode data) and 21 (control)
- Transfers files between systems
- Authenticates with a username and password
- Some systems use a generic or anonymous login
- Supports file operations such as listing, adding, and deleting files

#### SSH (Secure Shell)

Encrypted communication link over TCP port 22
- Provides command-line remote access similar to Telnet, but encrypted

#### Telnet (Teletype Network)

TCP port 23
- Log in to devices remotely
- Often used for console access
- Sends data in clear text and is not recommended for production systems

#### SMTP (Simple Mail Transfer Protocol)

TCP port 25
- Transfers email between servers and can submit mail from a device to a mail server
- Clients use protocols such as IMAP or POP3 to retrieve email

#### DNS (Domain Name System)

UDP and TCP port 53
- Resolves domain names to IP addresses
- Example: `www.professormesser.com` resolves to an IP address
- DNS is a critical service; networks commonly use multiple DNS servers

#### DHCP (Dynamic Host Configuration Protocol)

Automated configuration of IP address, subnet mask, and other options over UDP ports 67 (server) and 68 (client)
- Requires a DHCP server, appliance, or a feature integrated into a SOHO router
- Assigns addresses dynamically from a pool
- Each system receives a lease and must renew it at set intervals
- Reservations associate a MAC address with a specific IP address

#### HTTP and HTTPS

Hypertext Transfer Protocol (HTTP) and its encrypted version, HTTPS
- Used by web browsers and other applications
- HTTP traffic is unencrypted; HTTPS traffic is encrypted
- Supported by nearly all web servers and clients
- HTTP uses TCP port 80; HTTPS uses TCP port 443

#### POP3 and IMAP

Receive email from an email server
- POP3 (Post Office Protocol version 3) uses TCP port 110 for basic email retrieval
- IMAP4 (Internet Message Access Protocol version 4) uses TCP port 143 and supports inbox management across multiple clients

#### SMB (Server Message Block)

- Used by Microsoft Windows for file and printer sharing; also called CIFS (Common Internet File System)
- NetBIOS over TCP/IP uses UDP port 137 for name services and TCP port 139 for session service
- Direct SMB communication uses TCP port 445 without NetBIOS

#### LDAP and LDAPS

LDAP (Lightweight Directory Access Protocol) uses TCP port 389; LDAPS commonly uses TCP port 636
- Stores and retrieves information in a network directory
- Commonly used in Microsoft Active Directory

#### RDP (Remote Desktop Protocol)

Share a desktop from a remote location over TCP port 3389
- Remote Desktop Services is included in many Windows versions
- Can connect to an entire desktop or a single application
- Clients are available for Windows, macOS, Linux, iOS, Android, and other platforms

### Port Reference

| Service | Protocol and port | Purpose |
| --- | --- | --- |
| FTP | TCP 20 (active data), 21 (control) | File transfer |
| SSH | TCP 22 | Encrypted remote access |
| Telnet | TCP 23 | Unencrypted remote access |
| SMTP | TCP 25 | Email transfer and submission |
| DNS | UDP/TCP 53 | Name resolution |
| DHCP | UDP 67 (server), 68 (client) | Automatic IPv4 configuration |
| HTTP | TCP 80 | Web traffic |
| POP3 | TCP 110 | Email retrieval |
| NetBIOS | UDP 137, TCP 139 | Name and session services |
| IMAP | TCP 143 | Email access and inbox management |
| HTTPS | TCP 443 | Encrypted web traffic |
| SMB | TCP 445 | File and printer sharing |
| LDAP | TCP 389 | Directory access |
| LDAPS | TCP 636 | Encrypted directory access |
| RDP | TCP 3389 | Remote desktop |

## Wireless Network Technologies



Wireless technologies
IEEE standards
- Institute of Electrical and Electronics Engineers
- 802.11 committee
- Everyone follows these standards.
Also referenced as a generation
- 802.11ac is WIFI 5
- 802.11ax is WIFI 6 and WIFI 6e (extended)
- 802.11be is WIFI 7
- Future versions will increment accordingly

802.11 technologies
Frequencies
- 2.4 GHz, 5, and 6 GHz
- Sometimes a combination
Channels
- Groups of frequencies, numbered by the IEEE
- Frequencies are managed by giverning entities
- Using non-overlapping channles would be optimal
Bandwidth
- Amount of frequency in use
- 20MHz, 40, 80, 160MHz

Band selection and bandwidth
- 2.4 GHz: three commonly used non-overlapping 20 MHz channels in North America
- 5 GHz: channel widths commonly range from 20 to 160 MHz
- 6 GHz: supports wider channels, with available widths depending on the Wi-Fi generation and region

Bluetooth
Remove the wires
- Headsets
- Speakers
- Keybords/Mice
Uses the 2.4GHz range
- Unlicensed ISM (Industrial, Scientific, and Medical) band
- Same as 802.11
Short-range
- Most consumer devices operate over a range of about 10 meters

RFID (Radio-frequency identification)
- Access badges
- Inventory/Assembly line tracking
- Pet/Animal identification
- Anything that needs to be trakced
Radar technology
- Radio energy transmitted to the tag
- RF powers the tag, ID is transmitted back
- Bidirectional communication
- Some tag formats can be active/powered

NFC (Near-field communication)
Two-way wireless communication
- Builds on RFID, which is mostly one way
Payment systems
- Major credit cards
- Online wallets
Bootstrap for other wireless
- NFC helps with Bluetooth pairing
Access token, Identity "card"
- Short range with encryption support


## DNS Configuration


Domain Name System
Translates human-readbale names into computer-readable IP addresses
- You only need to remember www.professormesser.com
Hierarchial
- Follow the path
Distributed database
Many DNS Servers
- 13 root server clusters (over 1,000 actual servers)
- Hundres of generic top level domains (gTLDs) - .com, .org, .net, .etc
- over 275 country code top-level domains (ccTLDs) - .us, .ca, .uk

DNS lookup
- dig command - query macOS ; Windows nslookup

DNS records
Resource Records (RR)
- The database records of domain name services
Over 30 record types
- IP addresses, certificates, host alias names, etc
> **Important:** DNS records are critical configurations. Back up, verify, and test changes.

Address records (A) (AAAA)
Defines the IP address of a host
- This is the most popular query
A records are IPv4 adddresses
- Modify the A record to change the host name to IP address resolution
AAAA records are for IPv6 addresses
- the same DNS server, different records

Canonical name records (CNAME)
- One physical server, multiple services

Mail exchanger records (MX)
- This isn't an IP address; it's a name
- Send and recieve Email 

Text Records (TXT)
Human readable text information
- Useful public information
- Was originally designed for informal information
Can be used for verification purposes
- If you have access to the NS then you must be the administrator of the domain name
Commonly used for email security
- External email servers validate information from your DNS

Domain Keys Identified Mail (DKIM)
- Validated by mail servers, not usually seen by the end user
- The public key is in the DKIM TXT record

Sender Poicy Framework (SPF)
SPF protocol
- A list of all servers authorized to send emails for his domain
- Prevent mail spoofing
- Mail servers perform a check to see if incoking mail really did come from an authorized host

DMARC
Domain based Message Authentication, Reporting, and Conformance (DMARC)
- Prevent unauthorized email use(spoofing)
- An extension of SPF and DKIM
You decide what exteernal email servers should do with emails that don't validate through SPF or DKIM
- That policy is written into a DMARC TXT record
- Accept all, send to spam, or rejet the email
- Compliance reports can be sent to the email administrator


## DHCP


DHCP
IPv4 address configuration used to be manual 
- Ip address, subnet mask, default gateway, DNS servers, NTP servers
Needed a more automatic method
- Scale to thousands of systems
- Hands off Ip configurations
Dynamic Host Configuration Protocol (DHCP)
- Intially realeased in 1997, updated throgh the years
- Provides automatic address/IP configuration
- used for almost all devices

DORA leases
- A four step process
Discover
- Find a DHCP server
Offer
- Get an Offer
Request
- Lock in the offer
Acknowledge
- DHCP server confirmation

DHCP Scopes
Configured on the SHCP server
IP addres range
- And excluded addresses
Subnet mask
Lease durations
Other scope options
- DNS server
- Defualt gateway
- VoIP servers

DHCP protocols
Group of IP addresses
Each subnet has its own scope
- 192.168.1.0/24
- 192.168.2.0/24
- 192.168.3.0/24
A scope is generally a single contigious pool of IP addresses
- DHCP exclusions can be made inside of the scope

Address reservation
- Administratively configured
Table of MAC addresses
- Each MAC address has a matching IP address
Other name
- Static DHCP Assignement 
- Static DHCP
- IP Reservation


## VLANs and VPNs


Local Area Networks (LANs)
- A group of devices in the same broadcast domain

Virtual Local Area Netwrok (VLANs)
- A group of devices in the same broadcast domians
- Seperated logically intsead of physically

Configuring VLANs
Local Area Network
- A group of devices in the same broadcast domain

VPNs (Virtual Private Network)
- Encrypted (private) data trasversing a public network

Concentrator
- Encryption/decryption access device
- Often integrated into a firewall
Many deployment options
- Specialized cyrpotgraphic hardware
- Software-based options available
Used with client software
- Sometimes built into the OS

Clinet-to-Site VPN
On deman access from a remote device
- Software connects to a VPN concentrator
Some software can be configured as always on

Site-to-Site VPN
Always-on
- Or almost always
Firwalls often act as VPN concentratoers
- Probably already have firewalls in place


## Network Devices


Network Devices
many different devices and components
- All have different roles
Some of these functions are combined together
- Wireless router/switch/firewall
Compare different devices
- Undertsand when they shoudl be used

Routers
Routes traffic between IP subnets
- Makes forwarding decisions based on IP address
- Routers inside of switches sometimes called "Layer 3 switches" (OSI Layer 3)
Often connects diverse network types
- LAN, WAN, copper, fiber

Switches
Bridging done in hardware
- Application specific integrated circuit (ASIC)
- Forwards traffic based on data link address
Many ports and features
- The core of an enterprise network
- May provide Power over Ethernet (PoE)
Multilayer switch
- Includes routing functionality

Unmanaged switches
Very few configuration options
- Plug and play
Fixed configuration
- No VLANs
Very little intergration with other devices
- No management protocols
Low price point
- Simple is less expensive

Managed switches
VLAN Support
- Interconnect with other switched via 802.1Q
Traffic prioritization
- Voice traffic gets a higher prioority
Redundancy support
- Maintain uptime if a switch fails
Port mirroring
- Capture packets
External management
- Simple Network Management Protocol (SNMP)

Access Poitn
Not a wireless router
- A wireless router is a router and an access point in a single device
An access point is a bridge
- Extends the wired network onto the wireless network
- Makes forwarding decisions based on MAC address

Cable Infrastructure
Punch down block

Patch Panel
Combination of punch down blocks and RJ-45 connectors
Runs from desk are made once
- Permanently punch down to patch panel
Patch panel to switch can be easily changed
- No special tools 
- Use existing cbales

Firewalls
 Filters traffic by port number
 - OSI layer 4 (TCP/UDP)
 - Some firwalls can filter based on the application in use
 Can encrypt traffic into/out of the network
 - Protect you traffic between sites
 Can proxy traffic
 - A common security technique
 Most firewalls can be layer 3 devices (routers)
 - Usually sits on the ingress/egress of the network

 Power over Ethernet (PoE)
 Power provided on an Ethernet cable
 - One wire for both network and electricity
 - Phones, cameras, wireless access points
 - Useful in difficult to power areas
 Power provided at the switch
 - Built in power - Endspans
 - In line power injector - Midspans
 - Commonly marked on the switch or interface
 - The original PoE specification
 - 15.4 watts DC power, 350 mA max current
 PoE+
 - 25.5 watts DC power, 600mA
 PoE++
 - 51 W(Type 3), 600 mA
 - 71.3 W (Type 4), 960 mA 
 - PoE with 10GBASE-T
 Compare the device with the switch support
 - PoE+ won't power a PoE++ device
 
 Cable modem
 Broadband 
 - Transmission across multiple frequencies
 - Different traffic types
 Data on the "cable" network
 - DOCSIS (Data over Cable Service Interface Specification)
 High speed networking
 - Speeds up to 1 Gig are common
 Multiple services
 - Data, voice, video

 DSL modem (Digital Subscriber Line)
 - uses telephone lines
 Download speed is faster than the upload speed (asymmetric)
 - 200Mbits/s downstream /20Mbits/s upstream are common
 - ~10,000 foot limitation from the central office (CL)
 - Faster speeds may be possible if closer t the CO

 ONT (Optical Network terminal)
 - Fiber to the premises
 Connect the ISP fiber network to the copper network
 - Demaraction point (DEMARC) in the data center
 - Terinal box on the side of the building
 Line of responsibily
 - One side of the box is the ISp
 - Other side of the box is your network

Network Interface Card (NIC)
The fundamental network device
- Every device on the network has a NIC
- Computers, server, printer, routers, switches, phones
Specific to the network type
- Ethernet , WAN , wireless,
Often built in to the moterboard
- Or added as an extension card
Contains the hardware address
- Media Access Control (MAC) address
- A unique hardware designation


## IPv4 and IPv6


IP addressing
- IPv4 is the primary protocol for everything we do
- Included in lamost all configurations

IPv6 is now part of all major operating systems
and the backbone of our internet infrastructure

IPv4 addresses
- OSI Layer 3 address

Public IPv4 addresses
Each IPv4 address on the internet in unique
- 1.1.1.1 can communicate to 2.2.2.2
It is estimated that there are over 20 billion devices connected to the internet (and growing)
- IPv4 supports around 4.29 billion adddresses
- There's an obvious scalability issue
We have found ways to manage the demand
- Network Address translation (NAT)

Private IP Address ranges
Large private Ip address ranges
- Properly design and scale large networks
Private IP addresses are not internet routable
- But can be routed internally
- Use NAT for everything else
Defined in RFC 1918
- Request for Comment

IPv6 Addresses
Internet Protocol v6 - 128 bit address
- 340 undecillion addresses
- 6.8 billion people could have many addresses
- hexadecimal instead of decimal

Your DNS is very important!
First 64 bits is generally the network prefix (/64)
Last 64 bits is then the host network address


## Assiging IP Addresses


Netwroking with IPv4

IP address, ex. 192.168.1.1.65
- Every device needs a unique IP address

Subnet Mask 255.255.255.0
- Used by the local device to determine what subnet it's on
    The subnet mask isn't (usually) transmitted across the network  
    You'll asak for the subnet mask all the time
        What's the subnet mask of your network?

Default gateway 192.168.1.1
- The router that allows you to communicate outside of your local subnet
- The default gateway must be an IP address on the locla subnet

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
169.254.0.0. - 169.254.255.255
- First and last 256 addresses are reversed
- Functional block of 169.254.1.0 - 169.254.254.255
- DHCP is not responding

Randomly assigned in this block
- Uses ARP to confirm the address isn't currently in use

Turning dynamic into static
DHCP assigns an IP address from the available from a large pool of addesses
- Your IP address will occasionaly change

You may not want your IP address to change
- Server, printer, or personal preference

Disable DHCP on the device
- Configure the IP address information manually
- Requires additional administration

Better: Configure an IP reservation on the DHCP server
- Associate a specific MAC address with an IP address



## Internet Connection Types

## Satellite Networking

Communication to a satellite
- Non-terrestrial communication

High cost relative to terrestrial networking
- 100Mbits/s down, 5Mbits/s up are common
- Remote sites, difficult to network sites

Relatively high latecy
- Some systems have 250 ms up, 250ms down 
- Starlink advertises 25 to 60 ms

Not always a perfect option
- Line of sight, rain fade

## Fiber

High speed data communication
- Frequencies of light

Higher installation cost than copper
- Equipment is more costly
- More difficult to repair
- Communication over long distances

Large installation in the WAN core
- Supports very high data rates
- SONET, wavelength division multiplexing

Fiber has appeared at the premises
- Business and home use

## Cable

Broadband
- Transmission across multiple frequencies
- Different traffic types

Data on the "cable" network
- DOCSIS (data over cable service interface specification)

High-speed networking
- 50Mbits/s through 1,00+Mbits/s are common

## DSL

ADSL (asymmetric digital subscriber line)
- Uses telephone lines

Download speed is faster than the upload speed (asymmetric)
- 200 Mbit/s downstream / 20 Mbit/s upstream are common
- ~10,000 foot limitation from the central office (CO)
- Faster speeds may be possible if closer to the CO

## Cellular Networks

Mobile devices 
- "Cell" phones

Seperate land into "cells"
- Antenna covers a cell with certain frequencies

Tethering
- Turn your phone into a wireless router

Mobile Hotspot
- Standalone devices
- Uses your phone for other things

## WISP

Wireless Internet Service Provider
- terrestrial internet access using wireless

Connect rural or remote locations
- Internet access for everyone

Many different deployment technologies
- Meshed 802.11
- 5G home internet
- Proprietary wireless

Need an outdooe antenna
- Speeds ~10Mbits/s to 1,00 megabits per second




## Network Types


LAN

Local Area Network
- Local is relative

A building or group of buildings
- High speed connectivity

Ethernet and 802.11 wireless
- Any slower and it isn't local

WAN

Wide area network
- Spanning the globe

Generally connect LANs across a distance
- And generally much slower than the LAN

Many different WAN technologies
- Point to point serial, Multiprotocol Label Switching (MPLS), 
- Terrestrial and non terrestrial

PAN

Personal Area Network
- Your own private network
- Bluetooth, IR, NFC

Automobile
- Auto output
- Integrate with phone

Mobile phone
- Wireless headset

Health
- Workout telemetry, daily reports

MAN

Metropolotian Area Network
- A network in your city
- Larger than a LAN, often smaller than a WAN

Historically MAN specific topologies
- Metro Ethernet

Common to see government ownership
- They "own" the right of way

SAN

Storage Area Network
- Looks and feels like a local storage device
- Block-level access
- Very efficient reading and writing

Require a lot of bandwidth
- may use an isolated network and high speed network technologies

WLAN

Wireless LAN
- 802.11 Technologies

Mobility
- Within a building
- In alimited geographical area

Expand the coverage wth additonal access points
- Downtown area
- Large campus




## Network Tools


Cable Crimpers

"Pinch" the connector onto the wire
- Coaxial, twisted pair, fiber

Connect the modular connector to the Ethernet cable
- The final step of the process 

Metal pronsg are pushed through the insulation
- The plug is also permanently pressed onto the cable sheath

Crimping best practices

Get a good crimper
- And a good pair of electrician's scissors / Cable snips
- And a good wire stripper

Make sure you use the correct modular connectors
- Differences between wire types

Practice, practice, practice
- It won't take long to become proficient

WiFi Analyzer

Hardware base WiFi analyzer
- Avoids operating systems limitations
- View all of the 802.11 information in the air

View WiFi information
- Frequencies/ channels, signal strength, access points, interference, wireless devices

Get frequency information from a spectrum analyzer
- Useful when many different devices are part of the bigger picture

Tone Generator

Tone probe
- Where does that wire go?
- Follow the tone

Tone generator
- Puts an anolog sound on the wire

Inductive probe
- Doesn;t need to touch the copper
- Hear through a small speaker

Easy wire tracing
- Even in complex enviroments

Connect the tone generator to the wire
- Modular jack
- Coax
- Punch down connectors

Use the probe to locate the sound
- The two-tone sound is easy to find

Punch down tool

"Punch" a wire into a wiring block
- 66 block, 110 block, and Krones, others

Can be tedious
- Every wire must be individually punched

Trims the wires during the punch
- Very effiecient process

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

Can Identify missing pins
- Or crossed wires

Not usually used for frequency testing
- Crosstalk, signal loss, etc

Loopback plugs

Useful for testing physical ports
- or fooling your applications

Serial / RS-232 (9 pin or 25 pin)

Network connections
- Ethernet, T1, Fiber

These are not cross-over cables

Taps and port mirrors

Intercept network traffic
- Send a copy to a packet capture device

Physical taps
- Disconnect the ink, put a tap in the middle
- Can be an active or assive tap

Port mirror
- Port redirection, SPAN (Switched Port ANalyzer)
- Software based tap
- Limited dunctionality, but can work well in a pinch




## Display Types


LCD

Liquid crystal display
- Lught shines through liquid crystals

Advantages
- Lightweight
- Relatively low power
- Relatively inexpensive

Disadvantages
- Black levels are a challenge
- Requires serperate backlight
    - Florescent, LED (Light emmiting Diode)
    - Lights can be difficult to replace

LCD Technologies

TN (Twisted Nematic) LCD
- The original CD technology
- Fast response times (gaming!)
- Poor viewing angles - color shifts

IPS (In Plane Swithcing) LCD
- Excellent color representation
- Can be more expensive to produce than TN

VA (Vertical Alignment) LCD
- A good compromise between TN and IPS
- Good color representation
- Often slower response times than TN

OLED 

OLED (Organic Light Emitting Diode)
- Organic compound emits light when recieving an electric current

No backlight-The organic compund provides the light

Thinner and lighter
- Flexible and mobile - no glass needed

Tablets, phones, smart watches
- Very accurate color representation 
- Tends to be a bit higher cost than LCD

Mini LED

Same bcklight technology as a conventional LED-backlight LCD
- But muuch smaller Light Emitting Diodes(LEDs)

Each LCD can be enabled or disabled
- And color and intensity can be different

Much better control over dark screen areas
- Deeper blacks, better color representation

Touchscreen

Merge laptop and tablet input
- Digitizer responds to touch
- No keyboard required
- But often still available

Many options for input
- Use the best one for the job

Digitizers

Use a pen-like device as input
- Stylus input
- Useful for graphical input

Used commonly on laptops/tablets
- Or hybrid devices

Backlight and inverter

LCD displays needs a backlight 
- Florescent lamp or LED lights

Some laptops have inverters
- Turn DC into AC

Verify backlight
- Look closely
- Use a flashlight

May need to replace the LCD inverter or display
- Choose carefully




## Display Attributes


Display Attributes

Not all displays are created equal
- Various specifications, options, and settings

Requirements can vary
- Web browsing
- Video and photo editing
- Information displays
- Phones

Evaluate all of the technical details
- Choose the best displays for the requirement

Pixel density

Measure how many pixels in an inch
- Or pixels per centimeter
- Apply a physicla measurement to a display

A higher pixel densisty looks better
- Higher clarity and sharpness

Consider how the image will be viewd
- Displays
- Printers (dots per inch)

Pixel density comparison

Number of pixels / Number of inches
- Pixels per inch (divided) inch

27 in (diagonal) 4k display
- 3,840 horizontal pixels / 24 inches wide (not diagonal)
- 160 pixels

65 in (diagonal) 4k display
- 3,840 horizontal pixels / 57 inches wide
- 67 pixels per inch

Refresh rates

We are viewing many images shown constecutively
- A still "frame' or image

Usually measured in hertz (Hz)
- Number of cycles per second
- Frames per second (FPS)

Frame rates may vary
- Movies 24 fps
- TV 30 fps
- Video games 60 fps +

Refresh rates

Higher refresh rates are useful for rapidly moving content 
- Video games, sports events, video production

Maximum refresh rate is determined by the video adapter / processor and the display device
- The connection between the two is also important
- HDMI 21. supports 4k at 144hz
- Display port 2.1 supports dual 4k at 144hz

Screen resolution 

The number of pixels 
- Width x height

More pixels means more detailed display output
- Percieved sharpnedd
- A clearer view

Many standards
- Resolutions can vary widely
- 16:9 aspect ratio is common

Color gamut

Color gamut
- The range of colors available on a display or output device
- This is less than the capabilities of the human eye

An important consideration in a display
- Color representation
- Range of colors

Many standards
- sRGB - Standard RED GREEN BLUE
- Adobe RGB
- International Telecommunication Union (ITU) standards for HDTV

Color coverage

A display may be compared with an existing color gamut standard
- Part of the display specifications

Gamut compatiability can vary widely
- Higher percentages tend to be more expensive

OLED displays provide a wide color gamut
- Best in class color gamut support




## Network Cables


The importantance of cables

Fundamental to network communication 
- Incredibly important foundation

Usually only get one good opportunity at building your cable infrastructure
- Make it good !

The vast majority of wireless communication uses cables 
- It has to plug in somewhere

Twisted pair copper cabling

Baanced pair operation
- Two wires with equal and opposite signals
- Trnasmit +, Transmit - / Recieve +, Recieve -

The twist is the secret
- Keeps a single wire constantly moving away from the interface
- The opposite signals are compare on the other end

Pairs in the same cable have different twist rates

Cable categories
- The copper just sits there

Electrical signals are sent over copper cable
- The signal encoding determines the data transfer rate

A cable must be manufactureed to specific standards
- IEEE 802.3 Ethernet standards determine the cable type

Cable standards are described as a "category" of cable 
- Category 5e, Category 6a
- Check the IEEE standard to determine the minimum cable category
- The minimum cable category for 1000BASE - T is category 5

### Copper Cable Categories

| Ethernet standard | Minimum cable category | Maximum supported distance |
| --- | --- | --- |
| 1000BASE-T | Category 5e | 100 m |
| 10GBASE-T | Category 6 | 55 m |
| 10GBASE-T | Category 6A | 100 m |

Coaxial cables

Two or more forms share a common axis
- The inner conductor and the outer shield

RG-6 used in TV/digital cable
- And high-speed internet over cbale

Unshielded and shielded cable

UTP (Unshielded Twisted Pair)
- No additional shielding 
- The most common twisted pair cabling

STP (Shielded Twisted Pair)
- Additonal shielding protects against interference
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

Shieled twisted pair
- Provides frounding
- Adds strength
- Protects against signal interference

Plenum

Plenum space
- Building air circulation
- Heating and AC system

Concerns in the case of a fire
- Smoke and toxic fumes
- Need a cable type for a plenum

Plenum-rated cable

traditional cable jacket
- Polyvinyl chloride (PVC)

Fire rated cable jacket
- Fluorinated ethylene polymer (FEP) or low smoke ppolyvinyl chloride (PVC)

Plenum rated cable may not be as flexible
- May not have the same bend radius

Worst case planning
- Important concerns for any structure




## 568A and 568B Colors


Structured cabling standards

International ISO/IEC 11801 cabling standards
- Defines classes of networking standards

Telecommunications Industrial Association (TIA) 
- Standards, market analysis, trade shows, government affairs, etc.
- ANSI/TIA-568: Commercial Building
Telecommunications Cabling Standard
- http://www.tiaonline.org

Commonly referenced for pin and pair assigments of eight conductor 100 ohm balanced twisted pair cabling 
- T568A and T568B

T568A and T568B termination

Pin assignments from T568B standard
- Eight conductor 100ohm balanced twisted pair cabling

T568A and T568B are different pin assignments for 8P8C connector
- The colors are slighly different between the two

Many organizations traditionally use 568B
- Difficult to change in mid stream

You shouldn't terminate one side of the cable with T568A and the other with T568B
- this has never been the definition of a Gigabit Ethernet crossover cable




## Optical Fiber


Fiber communication

Transmition by light
- The visible spectrum

No RF signal
- Very difficult to monitor or tap

Signal slow to degrade
- Transmission over long distance

Immune to radio interference
- There is no RF

Multimode fiber

Short range communication
- Up to 2km

Relatively inexpensive light source
- LED

Single mode fiber

Long range commmunication
- Up to 100km without processing

Expensive light source
- Commonly uses lasers




## Peripheral Cables


USB (Universal Serial Bus)

Simplify connections
- Printers, storage devices, keyboards, mouse

USB 1.1
- Low speed: 1.5 megabits per second, 3 meters
- Full speed: 12 megabits per second, 5 meters

USB 2.0
- 480 megabits per second, 5 meters

USB 3.0
- Superspeed
- 5 gigabits per second ~3meters
- Standard does not specify a cable length

USB 3.1 
- Max of 10 gigabits per second

USB 3.2
- Max of 20 gigabits per second

USB - C 

USB has a lot of different connectors
- And they have changed over time

Can be annoying to connect USB - A
- Third time's the charm

USB-C replaces all of these
- One connector to rule them all

USB-C describes the physical connector
- It doesn't describe the signal

Serial cables

D-subminiature or D-sub
- The letter refers to the connector size

Commonly used for RS-232
- Recommended standard 232
- An industry standard since 1969

Serial Communications Standard
- Built for modem communication
- Used for modems, printers, mice, networking 

Directly connect to the device
- Traditionally a serial connection
- DB-9 connector, RJ45 serial, USB connection

When all else fails
- The console will be available

A text based serial interface

Requires a serial or USB connection
- May need a USB to DB9 serial adapter

Thunderbolt

High speed serial connector
- Data and power on the same cable
- Based on Mini DispayPort (MDP) standard

Thunderbolt 1
- Two channels
- 10 Gbits/ per channle
- 20 Gigabits/ total throughput
- Mini DisplayPort connector

Thunderbolt 2
- 20 Gigbits/ aggregated channels
- Mini DispayPort connector

Thunderbolt 3
- 40 Gigabits/ aggregated throughput
- USB - C connector

Max 3 m (copper)
- 60 meters (optical)
- Daisy chain up to 6 devices

Thunderbolt 4
- 40 Gigabits/ aggregated throughput
- Support for dual 4k displays
- Increased PCIe bandwidth



## Video Cables


HDMI (High Definition Multimeedia Interface)

Video and audio stream
- All digital, no analog
- ~20 m distance before losing too much signal

19-pin (TYPE A) connector
- One of the most common video connector types

Display Port

Digital information sent in packetized form
- Like ethernet and PCI Express
- Carries both audio and video

Compatible with HDMI and DVI
- Passive adapter(needed)
- Display Port -> HDMI
- Display Port-> DVI

Full size interface may include a locking mechanism
- Don't pull without unlocking

DVI (Digital Visual Interface)

Single and dual link video
- Single link; 3.7 Gbps (1920 x 1200 at 60 Hz)
- Dual link; 7.4 Gbps (2560 x 1600 at 85 Hz)
- No audio support

DVI-A
- Analog signals
- Backward compatibility with VGA

DVI-D
- Digital signals

DVI-I
- Integrated - Digitial and analog in the same connector

VGA (Video Graphics Array)

DB-15 connector
- More accurately called DE-15

Blue Color
- PC System Design Guide

Video only
- No audio signal

Analog signal
- No digital
- Image degrades after 5-10m

USB-C 

A connector 
- Not a protocol

Many uses for USB-C
- Power
- USB data
- Thunderbolt data
- Displayport video
- HDMI video (not common)
- Mobile high definition link (MHL)






## Storage Cables


SATA (Serial AT Attachment)

SATA Revision 1.0
- 1.5 Gbits

SATA Revision 2.0 
- 3.0 Gbits

SATA Revision 3.0 
- 6.0 Gbits

SATA Revision 3.2 
- 16 Gbits

eSATA (external SATA)
- Matches the SATA version
- 2 meters

Power (15pins) Data(7pins)
One power cable and data cable per device
- One-to-one

eSATA Cable

External device connections
- Uses the SATA connector

SATA is usually on the outside of the computer and the eSATA is usually on the inside of the computer






## Adapters and Converters


Adapters and converters

The best laid plans
- Need an adapter

Convert between different connectors
- Electrically compatible

Convert from one format to another
- You need Ethernet but you only have USB

A good temporary fix
- Or a good permanent one

DVI to HDMI

DVI-D and HDMI aare electrically compatible
- HDMI is backward compatible with DVI-D
- No signal conversion required
- No loss of video quality

DVI to VGA

DVI-A includes analog signals
- Backwards compatible with VGA
- Only 640 x 480 is offically supported

May only need an adapter
- Analog to analog

VGA to DVI digital will need a converter
- Check you interface specifications

USB to Ethernet

Some laptops don't have a wired ethernet interface
- Converts USB to Ethernet

USB-C to USB-A

Merge the newwith the old
- Use your old peripherals

USB hub

Connect many devices
- High speed USB connectivity





## Copper Connectors


RJ11 connector

6P2C (6 positions and 2 conductors)
- Some cables will wire additional conductors

Telephone or DSL connections

RJ45 connector 

Registers Jack type 45

8P8C (8 position 8 conductors)
- Modular connector
- Ethernet

F-connector

Coax cable
- Threaded connector

Cable TV
- Cable modem
- DOCSIS (Data Over Cable Service Interface Specification)

Punchdown block

Wire-to-wire patch panel
- No intermediate interface required

Wires are "punched" into the block
- Connecting block is on top

Additional wires punched into connecting block
- Patch the top to the bottom

USB - C

24 pin double sided USB connector
- Used for both hosts and devices

Used for USB, Thubderbolt
- Interface is the same, signal can vary

Molex connector

4 pin peripheral power connector
- Originally created by Molex Connector Company
- AMP Mate n lok
- Provides +12 V and +5 V

power for many devices in the computer case
- Fans
- Storage drives

Lighting

Apple proprietary
- 8 pin didgital signal
- Iphone, Ipad, Ipod devices

Some advantages over Micro USB
- Higher power output for phones and tablets
- Can be inserted either way

DB-9

D0subminiature or D-sub
- The letter refers to the connector size

Commonly used for RS232
- Recommended Standard 232
- An industry standard since 1969

Serial communications standards
- Built for modem communication
- Used for modems, printers, mice, networking

Now used as a configuration port
- Management or console port





## Fiber Connectors


ST - Straight Tip

Bayonet connector 
- Stick and twist

Push on and turn
- Locks in lace
- Turn to unlock

SC - Subcriber Connector

Not actually an abbreviation
- We have created our own names
- Square connector
- Standard connector

Pushed on to lock
- Pull connector to unlock

A popular fiber connector
- Common in many data centers

LC- Lucent Connector

Another popular fiber type
- Smaller and more compact connector

Locks in place with a clip
- Press to release

Other names
- Local Connector
- Litte Connector






## An Overview of Memory


What is memory?

Random Access Memory (RAM) is the most common
- But it is not the only kind of memory

RAM is not referring to hard drive or SSD storage
- Do not mix the two terms
- Data is stored permaently on the drive

Data and programs can only be used when moved to RAM

RAM slots

Memory types have changed throughout the years
- Driven by standarization and technology

One of the most important components of your computer
- Speed,speed,speed

Every motherboard is different
- Check your documentation

DIMM

DIMM 
- Dual inline memory module
- Electrical contacts are different on each side

64 bit data width

SO-DIMM

Small Outline Dual Inline Memory Module
- About half the width as a DIMM

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

SDR v DDR 
- Single Data Rate - one clock cycle = one data transferred
- Dual Data Rate - one clock cyle = two data transfers

Double Data Rate 3 (DDR3) SDRAM

Twice the date rate of DDR2
- Larger chip capactities

No backwards compatibiliy
- Speed brings sacrifice

DDR4 SDRAM

Speed increases over DDR3 
- Faster frequencies

Again, no backward compatibility

DDR5 SDRAM

Faster data transfers between the memory module and motherboard
- Higher speeds than DDR4

The key has moved 
- No backwards compatibilty 





## Memory Technologies



Memory that checks itself

Used on critcal computer systems
- VM servers, databases servers, any server

Parity memory
- Adds an additional parity bit
- Won't always detect an error
- Can'y always correct an error

Error Correction Code(ECC)
- Detects errors and corrects on the fly
- Not all systens use ECC
- It looks the same as non-ECC memory

Parity

Even parity
- The parity bit makes an even number

Valid or error?
- Even parity byte

CPU to RAM throughput

There's a maximum throughput between RAM and CPU
- The memory bandwidth

Measured in MT/s
- Megatransfers/s
- Million transfers per second
- e.g 32 GB DDR5, 1x32GB, 560MT/s

Faster is better
- Physics becomes the challenge

Multi-channel memory

Difficult to increase the speed
- Push as much as possible across a single memory bus

Twoo independent memory buses
- Doubles the throughput
- Two memory modules are faster than one

Dual channel, triple channel, or quad channel memory

Memory combinations should match
- Exact matches are best

Memory module slots are often colored differently






## Storage Devices



Storage Devices

need some way to store information when the computer is off
- RAM requires power to maintain the data

Many different ways to store data
- Hard drives
- Solid state drives
- Flash drive
- Memory cards
- Ooptical drives

Hard Disk Drives (HDD)

Non-volitile magnetic storage
- Radily rotating platters

Random access
- Retrieve data from any part of the drive at any time

Moving parts
- Spinning platters, moving actuator arm
- Mechanical components limit the access speed
- Mechanical components can also break
- Platter, actuator, Arm, head

Spindle Speeds
- RPM            15,000     10,000      7,200       5,400
- Avg Latency    2ms        3ms         4.16ms      5.55ms

Drive Size comparison
- 3.5 in, 2.5in, 22mm (Width)

Solid State Drive (SSD)

Non-volatile memory
- No moving parts

Very fast performance
- No spinning drive delays

2.5in SATA interface

PCIe storage interfaces

High speed for SSD communication
- Used before M.2

Connect directly to the motherboard
- Provides power
- High throughput

PCI Express
- Modern PCIe standards can transfer data at 65 gigbits per second per lane

NVMe

SATA was designed for hard drives
- Uses AHCI (Advanced Host Controller Interface) to move drive data to RAM
- SATA revision 3 throughput up to 6 gbps
- SSDs need a faster communication method

NVMe (Non-Volatile memory express)
- Designed for SSD speeds
- Lower latency, supports higher throughputs
- Uses the PCIe bus
- NVMe using M.2 has a theoretical transfer speed of 20 Gbps

Serial attached SCSI

The latest generation of SCSI technology
- Increased storage throughput
- Serial communication
- SCSI protocol 
- SAS - Serial Attached SCSI

The control abnd management of SCSI
- Useful in large storage arrays

An upgrade to SATA throughput
- SATA can communicate at 6Gbps
- High end SAS can reach 22.5 GBPS

2.5in SAS drive

mSATA (Mini-SATA)

Shrink the SATA drive into smaller devices
- Same data, different for factor
- Great for laptops and mobile devices

Smaller than 2.5in SATA drives
- No spinning drive
- Allows for different form factors

Was used briefly
- Quickly replace by the m.2 standard

M.2 interface

Smaller form factor
- No SATA data or power cables

Can use a PCI Express bus connection
- 4 GB/s throughput or faster when using NVMe PCIe x4

Different connector types
- Needs to be compatible with the slot key/spacere
- B key, Mkey, or B and M key
- Some M.2 drives will support both

B-key and M- Key

M.2 doesn't guarantee NVMe
- Your M.2 interface may be using AHCI
- Check your documentation

Your motherboard may only support one type o fM.2 key
- Check the documentation agaim

Flash drives

Flash memory
- EEPROM (Electrically erasable programmable read only memory)
- Non volatile memory
- No power required to retain data

Limited number of writes
- Can still read the data

Not designed for archival storage
- Easy to lose or damage
- Always have a backup

Optical drives

Samll bumps read with a laser beam
- Microscopic binary storage

Relatively slow
- Archival media

Many different formats
- CD ROM, DVD ROM, Bluray






## RAID



Data redundancy

Hard drives store huge amount of data
- Important data

Hard drives are moving components
- They will eventually break

What happens to the data when the drive fails?
- You can prepare for that
- Use an array of drives

RAID is not backup

RAID

Redundant Array of Independent Disks
- They're also inexpensive disks

Different RAID levels
- Some redundant, some not

RAID 0- Striping

File blocks are split between two or more physical drives
Disk 0 - Block 1A Block 3A block 5A Block 7A
Disk 1 - Block 2A Block 4A Block 6A Block 8A

High performance 
- Data written quickly

No redundancy 
- A drive failure breaks the array
- RAID 0 is zero redundancy

RAID 1- Mirroring

File blocks are duplicated between two or more phyical drives
Disk 0- Block 1 Block 2 block 3 Block 4
Disk 1- Block 1 Block 2 block 3 Block 4

High disk utilization
- Every file is duplicated
- Required disk space is doubled

High redundancy 
- Drive failure does not affect data availability

RAID 5- Stripin with on parity drive

File blocks are striped
- Along with a parity block
- Requires at least three drives
Disk 0- Block 1A Block 1B Block 1C ParityD
Disk 1- Block 2A Block 2B Parity C Block 1D
Disk 2- Block 3A Parity B Block 2C Block 2D
Disk 3-Parity A Block 3B Block 3C Block 3D

Effiecient use of disk space
- Files aren't duplicated, but space is still used for parity

High redundancy 
- Data is available after drive failure
- Parity calculation may affect performance

RAID 6- Striping with two parity drives

Add another parity block
- Requires at least four drives

Could lose two drives
- DATA would continue to be avaiable 

Requires another drive
- Adds more parity
- Does not add more capacity

RAID 10 (RAID 1+0)

the speed of striping the redundancy of mirroring
- A stripe of mirrors - the best of both worlds

Need at least 4 drives






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

Comptia exam objectives:
- "3.5 - Given a scenerio, install and configure motherboards, central processing untis (CPUs), and add-on cards"

Focus on which motherboard would be the best choice for a scenerio
- Memorizing the dimensions of the motherboard probably isn't the most important thing
- ATX, microATC, or ITX

ATX form factor

Advanced Technology Extended

Standarized by Intel in 1995
- Seen many updates over the years

Power
- 20pin connector
- 24 pin connector, additonal 4/8 pin connector

MicroATX(uATX, M-ATX)

Smaller than ATX motherboard
- Limited expansion slots

Backward compatibility
- Similar mounting points
- Similiar power

Very popular form factor
- Actively manufactored as of 2019

ITX form factor

A series of low power motherboards
- Developed by VIA technologies in 2001
- Small for factor

Mini-ITX is screw compatible with ATX 
- Fits almost any enclosure

Small form factor uses
- Single-purpose computing, streaming media






## Motherboard Expansion Slots



A computer bus

Communication path 
- A city of technology

Internal PC growth
- Indepedent pathways

System expansion
- Additional capabilities

PCI

Peripheral Component Interconnect
- Nobody ever calls it that
- Created in 1994

Many expansion options
- 32 bit and 64 bit bus width
- Parallel communciation

A common expanison interface on previous computer generations
- PCI Express is th newer technology

PCI Express

Also know as PCIe
- Replaces the older PCI standard

Communicates serially
- Unidirectional serial "lanes"
- Slower devices don't slow down everyone

One, two, four, eight, sixteen, or thirty two full duplex lanes
- x1, x2, x4, x16, x32
- "x" is pronounced "by" ("by 4," "by 16")






## Motherboard Connections



24 pin Motherboard power

Main motherboard power
- Provides +3.3 V, +/- 5V, and +/- 12 V

20 pin connector was the riginal ATX standard
- 24 pin was added for PCI Express power

You can connect a 24 pin connector to a 20 pin motherboard
- Some cables are 20 pin +4 pin

PCIe 6pin and 8 pin power

Additional power for PCI Express adapters
- 6 pin (75watts), 8 pin (150watts)
- Provides +12V

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
- Power, peripheral connections, Lights, buttons






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
- These switch paces often

Server motherboards

Multisocket
- Supports multiple physical CPU packages
- Split the load

Memory slots
- Supports 4+ modules

Expansion slots
- Many slots and different sizes

Overall size
- Designed for a rack mounted system
- Larger ATX sized system





## Hardware (25%)

    Component installation: setting up RAM, CPUs, and storage device
    Cables and connectors: working with HDMI, Ethernet, and USB cables.
    Peripheral devices: installing and maintaining printers, scanner, and other peripherals.
    Motherboards and power: configuring motherbards, power supplies, and cooling solutions.


## The BIOS


### BIOS (Basic Input/Output System)

The software used to start your computer
* Firmware
* Also called System BIOS or ROM BIOS
* Stored in ROM or flash memory

### Startup sequence

Initializes the CPU and memory
* Builds the workspace

POST
- Power on self test

Look for a boot loader
- Start the operating system

Legacy BIOS

The original/ traditional BIOS
- It's been around for more than 25 years

Older operating system talked to hardware through BIOS
- Instead of accessing hardware directly

Limited hardware support
- No drivers for modern newtork, video, and storage devices

UEFI BIOS

Unified Extensible Firmware interface
- Based on Intel's EFI (Extensible Firmware Interface)

A defined standard
- Implemented by manufactures

Designed to replace the leagcy BIOS
- Need a modern BIOS for modern computers
- Graphical and text based






## BIOS Settings



The secret button(s)

Launching the system setup
- Del, F1, F2, Ctrl-S, CTRL-ALT-S

Hyper -V (Windowns 10/11)
- Turn Windows features on and off

VMWare workstation
- http://professormesser.link/vmware

But not Virtual BOX
- http://www.virtualbox.org

Many simulators online
- Serach for UEIF BIOS Simulator

Fast Startup

Windows 10/11 and (previous versions)
- Doesn't actually shut down all the way
- Starts up so uickly, you cna't open the BIOS configuration

From the Windows Desktop
- Hold down shift when clicking Restart
- Settings/ipdates&Security/Recovery/Advanced startup/Restart now
- System COnfiguration(msconfig)

Interrupt normal boot three times
- Presents the boot option screen

Important Tips

make a backup of your BIOS configuration
- Write detailed notes
- Take a picture

Don't make a change unless you're certain of the setting 
- It's difficult to leave it alone

Did I mention the backup?
- It can save a lot of time!

Boot options

What happens when you power on?
- The BIOS knows

Disable hardware
- Unavailable to the operating system

Modify the boot order
- Which boot first?
- Move to the next in order
- USB drive,SSD,hard drive

USB permissions

A security challenge
- Very small storage devices
- Very large capactities

USB connections
- Convienent
- High speed

US Department of Defense banned USB flash media for 15 months in 2008 
- SillyFDC worm

Fans 

Computing power creates heat
- A lot of heat

Many different cooling fans
- CPU fans
- Chassis fans

Motherboards often include an integrated fan controller
- And temperature sensors
- The motherboard increases and decreases the fan speeds

Secure Boot

Malicious software can "own" your system
- Malicious drivers or OS software

Secure boot
- Part of the UEFI specification

Digitally sign known good software
- Cryptographically secure
- Software won't run without the proper signature

Support in many different operating system
- Windows and Linux support

UEFI BIOS Secure Boot

UEFI BIOS protections 
- BIOS include the manufractures's public key
- Digital sisganture is checked during a BIOS update
- BIOS prevents unauthorized writes to the flash

Secure Boot verifies the bootloader
- Checks the OS bootloader's digital signature
- Bootloader must be signed with a trusted certificate
- Or manually  approved digital signature

Boot password management

Boot password/User password
- System won't start
- Need the password to boot the operating system

Supervisor/BIIOS password
- Restrict BIOS changed
- Must use BIOS password to change any configuration settings

Remember you password!
- Must reset the BIOS to recover

Clearing a boot password

Store the BIOS configuration
- Your settings

Complementary metal-oxide semiconductor (CMOS)
- A type of memory
- may be backed up with a battery

Usually flash memory these days
- Easily stored and accessed

Reset with a jumper
- Short (connect) two pins on the mother board

Temperature monitoring

Part of the BIOS
- Built in diagnotics

Run from the BIOS menu
- No additonal media or software required

Focused on hardware checks
- Doesn't touch the operating system

Virtualization Support

Run other operating systems within a single hardware platform
- Multiple operating systems share physical hardware components

Virtualization in software was limited
- Performance and hardware management challenges

Virtualization added to the processor
- Hardware is faster and easier to manage
- Intel Virtualiztion Technology (VT)
- AMD Virtualization (AMD-V)






## HSM and TPM



Keeping Secrets

IT security is based around secrets
- And trusting other devices ana dapplications

We use a lot of encryption
- Web servers, file storage, phone data

The secret part is the key
- Unlocks all of this encryption

We need to storre this key somewhere
- How do you securely store these secrets?
- Where do you store these secrets?

Trusted Platform Module (TPM)

A pecification for crypograhic functions
- Hardware to help with single device encryption fucntions

Cryptohraphic processor
- Random number generator, kety generator

Persistent memory
- Includes unique keys burned in during production

Versatile memory
- Storage keys, hardware configuration information

password protected
- No dictionary attacks

Contains a unique secret key
- Not available outside od this device

Links this key to this computer
- Can't move an encrypted drive to another computer
- The key is on this computer

Also used as a physical pouint of reference
- A root of trust
- has this computer been modified or tampered with?

Can't use this key on another computer
- Crypotgraphy for a single device

Hardware Security Module (HSM)

Often used in large enviroments
- Servers clusters, many diverse devices

Key backup
- Secures storage for servers
- Lightweight HSMs for personal use (Smart card, USB, flash drive)

Often high end cryptographic hardware
- Plug-in card or serperate harware device

Crypographic accelerators
- Performs crypographic functions for other devices
- Only HSM knows the key

TPMs and HSMs

TPM
- Used on a single system
- Secure data on a local device
- Often built into a motherboard or available as an add-on module
- Mobile phone booting, screen locking, and encrypted storage

HSM
- Used by many systems
- Secure data across multiple devices
- Often deployed as a high-end server or appliance in a data center
- Protect the Certificate Authority key on a central secure device






## CPU Features



Operating system technologies

32-bit v 64-bit
- Processor specific 

32-bit processor cans store
- 2 to the 32 power = 4.294,967,296 values

64-bit processors can store
- 2 to the 64 power = 18.446,744,073,709,551,616 values
- 4 GB vs. 17 billion GB
- The OS has a maximum supported value

Hardware drivers are specific to the OS version (32-bit/ 64- bit)
- 32-bit(x86) 64-bit (x64)

32-bit OS cannot run 64-bit apps
- But 64-bit OS can run 32-bit apps

Apps in a 64 OS can run 32-bit apps
- 32-bit apps:\\Program Files(x86)
- 64-bit apps:\\Program files

Advanced RISC Machine (ARM)

CPU architecture developed by Arm Ltd.
- They design the chip , other license and build

Simplfied intruction set
- Efficient and fast processing 
- Less power
- Less heat

Traditionally used for mobile and IoT devices
- Adoption by Apple and other manufactures for desktop and laptops
- The lines are constantly blurring 

Proccessor Cores

Dual-core/Quad-core/Octa-core/multi-core
- And more all the time

Multiple cores
- Each core has its own cache
- The entire chip may have a shared cache






## Expansion Cards



Extend the functionality of you rcomuter
- You may need more than the motherboards providers

Relatively simple process
- Designed for end user installation

Install hardware
- Add a card

Install a driver
- Software for the operating system

Sound card

Output
- High-end audio
- Advanced headphone amp
- Home theater, Dolby decoding

Multiple inputs
- Music capture
- Podcasting
- Microphone

Video Card

Many CPUs include an integrated GPU
- Video functionality is built into the CPU package

Discrete graphics
- The CPU in not part of the CPU

Seperate interface card
- High performance

Capture Card

Video as an input
- Video capture
- Live streaming
- External cameras

High performance
- Video bandwidths can be quite high
- PCI Express connection

Ntework Interface Card (NIC)

Ethernet connection
- Motherboard may not include a NIC
- Onboard NIC may not be working

Additonal Connections
- Servers
- Routers
- Sercurity Devices

Documentation

Check the motherboard documentation
- Number and type of slots

Check the adapter card documentation
- Minimum requirements - Hardware, sorftware
- Knowledge base - Any 'gotchas"
- Support forums - What are other people saying?

You may need to perform a driver installation before installing hardware

Driver installation

You checked the documentation first, right?

Check the web for the latest version

Uninstall previous drivers through Windows Device Manager

Manufacturer provided setup program

Manual installation through Windows Device Manager

Check the Device Manager for the status
- Does it work?






## Cooling



Case fans

Cool air is pulled througha personal computer
- Always check for good airflow

Motherboard layout become important

Component location is key 
- Devices, wiring, power

Many different sizes and styles
- And volume levels

On-board fans

Designed to cool an entire adapter card

Can be bulky 
- May take additonal adapter card space

Usually seen on high-end graphics cards

Fan specifications

Standard sizes
- 80 mm, 120mm, 200mm

Different speeds
- Variable speeds

Different noise levels
- Not all fans sound the same

Fanless / passive cooling

No fans, no noise
- Silent operation

Specialized funtions 
- Video servers, tv top box, satellite reciever, media server

Functions are very controlled
- Carefully measurede thermal tests

Low power components
- Heat sink

Heat Sink

Dissipate heat through thermal conduction
- Copper or aluminmum alloy

Fins/grid increase surface area
- Heat is then transferred to the cooler air

They get HOT - don't touch them!

Thermal paste creates a good contact between the chip and the heat sick

Themal paste

Thermal grease, conductive grease
- Thermmaly conductive adhesive

Place between the heat sink and the component
- Improves thermal conductivity
- Moves the heat away from the component

A little bit goes a long way
- Pea sized application

Themal pad

Conduct heat without the mess
- Cut to size amd install

Easy to use
- Won't leak and damage components

Almsot as effective as thermal paste
- But still very good

Not reusable 
- Remove and replace

Liquid cooling

Coolant is circulated through a computer
- Not a new concept
    Automobiles, mainfram computers

High end systems

Gaming, graphics

Overclocking






## Computer Power



WARNING

ALWAYS DICONNECT FROM THE POWER SOURCE WHEN WORKING ON A DEVICE
- Always.Seriously

Some devices store a charge in capacitors
- Know how to discharge before touching

NEVER CONNECT YOUR BODY TO ANY PART OF AN EECTRICAL SYSTEM
- DO NOT CONNECT YOURSELF TO THE GROUND WIRE OF AN ELECTRICAL SYSTEM

RESPECT ELECTRICITY
- It does not respect you

Computer power supply

Computer uses DC voltage
- Most power sources provide AC voltage

Convert 120 v AC or 240 V AC
- to 3.3 C DC, 5V DC, and 12 V DC

You'll know when this isn't working 
- An important component

AMP and VOLT

Ampere (Amp, A) - The rate of electron flow past a point in one second
- The diameter of the hose

Voltage (volt, V) Electrical "pressure" pushing the electrons
- How open the faucet is

Power

Watt(W) - Measurement of real power use
- volt * amps = watts
- 120 V * 0.5A = 60 W

Current

Alternating Current (AC)
- Direction of current constantly reverses
- Distributes electricity effiecently over long distances
- Frequency of this cycle is important
    US/Canada - 110 to 120 V of AC (VAC) , 60 (Hz)
    Europe - 220 to 240 VAC, 50 Hz

Direct Current (DC)
- Current moves in one direction with a constant voltage

Voltage varies by country

Manually swith between q20 V and 230V
- Get your meter!
- Or use an auto voltage switching power supply

Don't plug a 120 V power supply into a 230 V power source!

Power Supply output

Different voltages
- For different components

Positive and negative voltage
- Voltage is a difference in potential
- The electrical ground is a common reference point
- Depends on where you measure from

At the door of your house
- The second floor is +10 ft
- The basement is -10 ft

+12V 
- PCIe adapters, hard drive motors, cooling fans, most modern componenets

+5 V
- Some motherboard components
- Many components are now using +3.3V

+3.3V
- M.2 slots, RAM slots, motherboard logic circuits

+5 VSB
- Standby Voltage

- 12V
- Integrated LAN
- Olde serial ports
- Some PCI cards

- 5V
- Available for ISA adapter cards
- Most cards didn't use it
- Today's motherboards don't have ISA slots

24-pin motherboard power

Main motherboard power
- Provides +3.3V, +/- 5V, and +/-12V

20-pin connector was the original ATX standard
- 24 pin was added for PCI Express power

You can connect a 24-pin connector to a 20 pin motherboard
- Some cables are 20-pin +4 pin

Redudant power supplies

Two (or more) power supplies
- Internal to the server

Each power supply casn handle 100% of the load
- Would normally run at 50% of the load

How-swappable
- Replace a faulty power supply without powering down

Power supplu connectors

Fixed connectors
- Connected tot he power supply
- Many have too many connectors
- May not have enough

Modular
- Adds cables as needed
- Fewer leftover wires, better airflow
- A bit more expensive

Sizing a power supply

Power supplies are rated by watts
- Overall and by individual volatges

Bigger isn't necessarily better
- More expensive Doesn't speed up your computer

Physical size is relatively standard
- Older cases and systems may have proprietary sizes

Calculate the watts required for all components
- CPU,s torage devices, video adapter
- Many online calaculators

Video adapters are usually the largest power draw
- Many video card specifications list a recommended power supply wattage

50% capacity is a good rule of thumb
- Power supply runs efficiently and there's room to grow

Energy efficiency

Converting AC to DC isn't perfect
- Some power is often lost
- Heat is generated

Check the efficiency range 
- Power supplies often range between 80%-96%
- Can depend on voltage and redundant power

More efficiency means more DC power
- And less heat: save money!

There's an established certification program
- Pick the right efficiency for you requirements


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


## Laser Printer Maintenance



Combine a laser, high voltage, charged ions, powdered ink, heat, and paper

Very high quality

Fast printing speeds

Very complex 
- Many moving parts
- Requires on-printer memory and processing
- Messy on the inside

Corona wire or charge roller negatively charges the drum

The laser neutralizes the neagtive charge

Negatievly-charged toner sticks to the areas marked by the laser

Toner on the drum is transferred to the paper

The fuser uses heat and pressure to melt toner to the page

The drum is cleaned for another pass

Replacing the toner catridge

Look for the messages 
- Low doesn't mean empty

The toner can also contain the OPC drum
- Orgainc photoconductor drum
- Sensitive to light; keep it in the bag

Power down the printer
- Safety first 

Remove pakcing strips from the new drum
- Replace it with the old

Laser printer maintenance kit

Laser printers wear out
- All those moving parts
- Heat and pressure

Standard maintenance kits
- Replacement feed rollers, new fuser unit, etc

When to perform maintenance?
- Check th printer's page counter

Power down and replace the components
- Fuser units are HOT

Reset the page counter when you're done!

Laser printer calibration

Different toner cartidges print with different densities
- Some dark, some light

Laser printer calibration can adjust the density
- makes it looks perfectM
Can be automated or a manual process
- Every printer is different 
- Check the printer manual

Laser printer cleaning

laser printers are dirty
- All that toner and paper dust
- Toner should be handled properly

Check manufacturer's recommendations
- Water, isopropyl alcohol (IPA)
- Don't use harsh chemicals

Ouside- damp cloth

Inside - wipe dust away
- Don't use a normal vacuum cleaner or compressed air
- Wash toner from skin with cold water
- Clean rollers with IPA






## Inkject Printers


Ink-dispersion printer

Relatively inexpensive technology

Quiet

High resolution

Expensive ink
- Proprietary

Eventually fades

Clogs easily

Ink cartidge

Place drops of ink onto a page
- Pulled from a set of cartidges

CMYK
- Cyan, Magenta, Yellow, Key(Black)

Print head

Some consumer printers integrate the print head into the ink cartridge
- Change the cartridge, get a new print head

Others seperate the ink cartridge from the print head

Feed rollers

Pick up and feed paper through the printer
- Must be clean and not worn

Duplexing
- Print on both sides of the paper
- Included with some printers






## Inkjet Printer Maintenance



Cleaning print heads

Small droplets of ink
- And small holes in a print head

Clogged heads is a big issue
- Many printers automatically clean every day
- Output has streaks or sections of missing color

Cleaning process can be started manually
- Only takes a few minutes

Some print heads/cartridges can be removed
- Manually cleaning may help

Replacing inkjet cartridges

Usually seperate colors
- Cyan, Magenta, Yellow, and Key (CMYK)
- Some cartridges will combine these

Takes seconds to replace
- Takes a few minutes to calibrate and prepare the cartridge

Recycle the empty cartridge
- All plastic

Align nozzles to the paper
- Lines should be crisp
- Colors should align

Printers includes a calibration option
- May need to make minor adjustments

Clearing Jams

Lots of turns and twists
- A jam is inevitable

Remove tray paper
- Any loose paper

Remove paper from the path
- Firm pressure, don't rip

Check for any scraps of paper
- Remove all loose paper






## Thermal Printers



White paper
- Turns black when heated
- No ink!
- Common as a reciept or label printer

Very quiet
- Almost silent

Paper is sensitive to light and heat
- Any clear tap

Feed assembly

Pull paper through the printer
- Releatively small paper path

Heating Element

Full length heating element
- No moving print head

Thermal Paper

paper covered with a chemical
- Thermochromic paper/thermal paper
- Changes color when heated

Cash registers, credit card terminals
- Quiet areas

Looks like normal paper
- Feels a bit different






## Thermal Printers Maintenance



Thermal paper replacement

Relatively inexpensive
- But impossible to substitute

Different sizes
- Not like laser printer paper
- Keep a list

Actual replacement process is easy
- Simple paper feed
- Small device

Cleaning the heating element

Liquid cleaner
- IPA
- Get a cleaning pen
- Check manufacturer's recommendations

Swab gently
- Usually small areas

Use a clenaing card
- Clean the head
- And paper pathways

Removing debris

Relatively small amount
- Paper bits and dust
- No toner!

Blow out the printer
- Take it outside

Wipe it out
- Damp cloth

Avoid using a vacuum
- Unless it's designed for computers
    Resist static buildup/discharge

Pper sensitivity to heat

Heat is used to creat the output on the thermal paper
- More heat will darkey the entire page

Avoid hot areas
- Car dashboard
- Radiator
- Hair dryers

Reciept will aslo fade over time 
- Don't use as archival media






## Impact Printers



Dot-matrix (impact) printers

Print hear with a small matrix of pins
- Presses against a ribbion to make a mark on paper

Good for carbon/multiple copies

Low cost per page

Noisy

Poor graphics

Relatively niche use cases

Dot-matrix printer head

Moves back and forth
- Pins hit ribbon and paper

One matrix
- Must move across the page to print

Printer ribbon

Fabric
- One long ribbon
- Never ending circle

Easy to replace
- One single unit

Proprietary size
- Specific to printer model

Tractor Feed

Continuous paper feed
- Perofrations between pages

Paper pulled through with holes on the side of the paper
- Instead of using friction

Multipart paper

Carbonless copying
- Mulitple copies of a single form in a single pass

Impact with the top sheet is duplicated on pages underneath
- Micro-encapsulated ink on the back of the first sheet
- Clay surface reaction on the top of the second sheet

Impact activates these inks, dyes, and clay
- Can be a mild irritation with certain chemical combinations

Easier and less expensive to just print another copy
- May be difficult to find multipart paper in use
- Or dot matrix printers






## Impact Printers Maintenance



Printer Ribbon Replacement

Single ribbon
- Self contained
- One long circle

Replace when ink becomes too light
- Ink is eventually consumed

Designed to be modular
- Replace in less than a minute

Print head replacement

Takes a lot of abuse
- Directly hits the ribbon and paper

Gets hot
- Watch your fingers

Another modular part
- Look for a release lever or bar

Replace with the ribbon for the best effect
- The output should look perfect

Replacing paper

Not as easy as a laser printer
- Paper must be feed perfectly into holes
    Tractor feed

Forms must be positioned correctly
- Text needs to fit a predefined apce

Paper must feed without constraint
- make sure nothing is in the way



## Virtualization and cloud computing (11%)

Virtualization concepts include virtual machines, hypervisors, and desktop virtualization. Cloud models include IaaS, SaaS, and PaaS.

    
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




## Cloud Models

### Cloud computing

More than just a server hosted elsewhere
- Extend the management of applications and services

Effectively unlimited resources
- You just have to pay for it

Deploy an infrastructure in minutes
- Create and tear down as you need

International scope
- Deploy in psecific parts of the world

Use only the required resources
- Cost is based on the amount you use

Cloud deployemnt models

Public 
- Available to everyone over the internet

Private 
- Your own virtualized local data center

Hybrid 
- A mix of public and private 

Community
- Serveral organizations share the same resources

Infrastructure as a Service (IaaS)

Sometimes called hardware as a service (HaaS)
- Outsaource your equipment

Your're still responsible for the management
- And for the security

Your data is out there, but more within your control

Web server providers

Software as a Service (SaaS)

On-demand software
- No local installation
- Why manage your own email distribution? or payroll?

Central management of data and applications
- Your data is out there

A complete application offering
- No development work required
- Google Mail, Microsoft 365

Platofrm as a Service (PaaS)

No servers, no software, no maintenance team, no HVAC
- Someone else handles the platform, you handle the development

You don't have direct control of the data, people, or infrastructure
- Trained security professionals are watching your stuff
    Choose carefully

Put the building blocks together
- Develop your app from wha't available on the platform
- Sales.Force.com

Responsibility matrix






## Cloud Charatceristics



Shared resources

Internal/private cloud
- Dedicated resources
- Build your own cloud
- Pay for everythingup front
- No ongoing costs

External/public cloud
- Shared resources witha publlic cloud
- Underlying infrastructure owned by a third party
- Cost may be metered or up front 

Metered and non-metered

Metered utilization
- You pay for what you use
- Cost to upload - ingress traffic
- Cost to store
- Cost to download - egress traffic

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
- Redundancy provides availiability

File synchronization
- Information can be duplicated across cloud locations

Multitenancy
- Many different clients are using the same cloud infrastructure






## Troubleshooting Hardware



POST (Power on Self Test)

test major system components ebfore booting the operating system
- Main system (CPU, BIOS)
- Video
- Memory

Failures are usually noted with beeps and/or codes
- BIOS versions can differ, check your documentation

Don't bother memorizing the beep codes
- They're all different between manufacturers
- Know what to do when you hear them

POST and boot

Blank screen on boot
- Listen for beeps
- Bad video, bad RAM, bad CPU
- BIOS configuration issue

BIOS time and setting
- Maintained with the motherboard battery
- Replace the battery

Attempts to boot to incorrect device
- Set boot order in BIOS configuration
- Confirm that the startup device has a valid operating system
- Check for media in a startup device

Crash screens 

Windows Stop Error

blue Screen of Death
- You don't want this

Contains important information
- Also written to event log

Bluescrrens and shutdowns

Startup and shutdown BSOD
- Bad hardware, bad drivers, bad application

Use last known good, system restore, or rollback driver
- Try Safe Mode

Reseat or remove the hardware
- If possible

Run hardware diagonstics
- Provided by the manufacturer
- BIOS may have hardware diagnostics

Proprietary crash screens

Every application has their own notifications
- Some are very informational
- Some are quite bad

The quality of information contained in a help desk ticket can vary
- Get as many details as possible

A detailed transcript of the error would be valuable
- Screenshots are even better
- Ask for the screenshot in the ticket instructions

Blank screen 

Is the monitor connected?
- We wouldn't ask if it wasn't a common solution
- Check both power and signal cable

Input selection on monitor
- HDMI, DisplayPort, DVI, VGA

Image is dim
- Check brightness controls

Swap the monitor
- Try the monitor on another computer

No video after Windows load
- Use VGA mode (F8)

No power

No Power
- No power at the source
- No power from the power supply
- Get out your multimeter

Fans spin - no power to other devices
- Where is you r fan power connected?
- No POST - bad motherboard?
- Case fans have lower voltage requirements
- Check the power supply output

Sluggish performance

Task Manager
- Check for high CPU utilization and I/O

Windows Update
- Last patches and drivers

Disk Space
- Check for available space and defrag

Laptops may be using power-saving mode
- Throttles the CPU

Anti-virus and anti-malware
- Scan for bad guys

Overheating

Heat Generation
- CPUs, video adapters, memory

Cooling system
- Fans and airflow
- Heat sinks
- Clean and clear

Verify with monitoring software
- Built in BIOS 
- Try HWMonitor
    http://www.cpuid.com/

Smoke and burning smell

Electrical problems
- The smoke makes everything work

Always disconnect power
- There should never be a burned odor

Locate bad components
- Even after the system has colled down
- Replace all damaged components

Random Shutdown

No warning, black screen
- May have some details in your Event Viewer

Heat related issue
- High CPU or grahics, gaming
- Check all fans and heat sinks
- BIOS may show fan status and temperatures

Failing hardware
- Has anything changed?
- Check Device Manager, run diagnostics

Could be anything
- Eliminate what's working

Application crashes

Application stops working
- May provide an error message
- May just disappear

Check Event Viewer or logs
- Often includes useful reconnaissance

Check the realiability monitor
- A history of application problems
- Checks for resolutions

Reinstall the application
- Contact application support

Unusal Noises

Computers should hum
- Not grind

Rattling
- Lose components

Scraping 
- Hard drive issues

Clicking
- Fan problems

Pop 
- Blown capacitor

### Inaccurate system date and time

* A bad motherboard battery is a common cause; it is often a button-style battery.

A bad battery will require a BIOS configuration or date/time configuration on every boot

On older systems, can reset the BIOS configuration by removiing the battery
* Newer computers use a jumper


## Hardware and network troubleshooting (28%)

    Diagnosing issues: identifying and fixing hardware, network and connectivity problems.
    Troubleshooting tools: using multimeters, cable testers, and loopback plugs.




## Troubleshooting Storage Devices



Storage failure symptoms

Read/write failure
- "Cannot read from the source disk"

Slow performance
- Constant LED activity
- Rety.. Retry.. Retry

Loud clicking noise
- The click ofdeath
- May also include grinding and scraping

Grinding noises

hard drives are mechanical devices
- Spinning drives (often 5,400 RPM and higher)
- Moving actuator arms

Very high tolerances
- One small problem can cause the drive to fail

Metal on metal
- Clicking or grinding 
- Poor performance, or no access at all

Difficult to recover from this issue
- Time to get you rwell managed and very recent backup

Troubleshooting disk failures

Get a backup (if possible)
- First thing - a bad drive is bad

Check for loose or damaged cables

Check for overheating
- Especially if problems occur after startup

Check power supplu 
- Especially if new devices were added

Run hard drive diagnostics
- From the drive or computer manufacturer
- Perferably on a known-good computer

Boot failure symptoms

Drive not recognized, Boot device not found
- Lights (or no lights)
- Beeps
- Error message

Operating system not found
- The drive is there
- Windows is not

Check your cables
- Physical problems

Check boot sequence in BIOA
- Check for removable disks (especially USB)
- Check for disabled storage interfaces

For new installation, check hardware configuration
- Data and power cables
- Try different SATA interfaces

Try the drive on a different computer

Data loss/corruption

Hard drives are mechanical devices
- They will eventually fail

Repairs are difficult and expensive
- Dust-free enviroment
- Not always successful

An SSD may simply stop working
- Sometimes canread but not write

Data becomes unavailable or corrupted
- Can be impossible to recover

ALWAYS HAVE A BACKUP

RAID failure

A drive in a RAID array has failed
- Hardware failure
- Power issue
- Communication issue

Almost always very obvious
- Error messages
- Email notifications
- Audible alarms

A careful analysis is required
- Many drives
- Different volumes

S.M.A.R.T

Self-Monitoring, Analysis, and Reporting Technology
- Use third party utilities

Avoid hardware failure
- Look for warning signs

Schedule disk checks
- Built in to most drive arrays

Warning signs
- Replace a drive

Monitoring SMART metric over time
- Watch for changes or incrementing values
- May be part of a NAS or third party software

Automated notifications
- Email
- Text message
- Console notifications

Resolve the issue before it's a problem
- Get a good backup
- Replace the bad drive

Etended read/write times

A lot happens when reading or writing data
- Memory access, communication across the bus, spinning drive access, writing or reading the data to the storage device, et.

Delays can occur anywhere along the way
- Need a way to measure storage device access

Input/Output operations per second (IOPS)
- A broad metric of maximum performance

Useful for comparing storage devices
- Hard drive: 200 IOPS
- SSD: 1,000,000 IOPS

Missing drives in OS

OSboots normally
- Other drives not shown
- Check the BIOS

Internal drives 
- Bad drive or disconnected cable

External drives
- No power to the drive or bad cable connection

Network shares
- Shared drives can be connected during startup
- Options to reconnect at sign in
- Connected with login script

Array missing

Missing or faulty RAID controller






## Troubleshooting Dispaly Issues



Incorrect input source

Is it connected?
- We wouldn't ask if it wasn't a real solution
- Check both power and signal cable

Input selection on monitor
- HDMI, DVI, VGA, DisplayPort

Image is dim
- Check brightness controls

Swap the monitor
- Try the monitor on another computer

No video after Windows loads
- Use VGA mode (F8)

LCD projector bulbs

LCD projectors and heat
- Very bright metal-halide bulbs
- Operate at around 1,000 degrees Celsius

Cooling is always an issue
- Fans constantly cool the bulb
- Shuts down if temperatures are high
- Fan cools bulbs slowly after light is off

Replace a burnt out bulb
- And clean dust from the air filters and external air input/output

Fuzzy image

An LCD display is fixed
- The number of pixels doens't change

A display looks best when the video settings match a display's native resolution
- A mismatch can cause distortion

If changing the dispay resolution, try using a multiple of the native resolution 
- 2560x1600 is the same ratio as 1920x1200

Burn in 

A problem across all monitor types
- Some displays will pixel shift
- you probably won't notice it

LCDs have "image sticking"
- Try to remove by displayin a white screen for an extended period

Dead pixels

Always black 
- A manufracturing defect

This probably isn't a problem on your side
- Not a cable or power issue

Clean the monitor screen
- Damp cloht

You'll have to replace the monitor
- No other options

Flashing screen

Check the video cable connections
- A loose cable will cause loss of signal

Replace the video cable
- Usually a quick fix

The problem could be with the monitor
- Try switching the display

Confirm the display settings in the operating system 
- May not match the monitor

Incorrect color display

Colors may not be properly represented
- Too much red, green blue, yellow etc

Monitor settings
- Tint
- Custom color presets
- Factory Reset

Driver configuration
- Color tint

OS configuration - Very blue
- Night light settings

Audio issues

Many monitors include speakers
- No sound, low volume

Monitor may have audio controls
- Check volume levels and mute status

Confirm audio input over HDMI, DisplayPort, or Thunderbolt
- Check the HDMI audio output in the OS

The monitor may support other audio input interfaces
- Check for audio jacks

Dim Image

Monior video settings
- Brightness
- Contrast

Check the OS
- Auto dimming
- Dim on battery power
- Driver settings

Backlight feature
- Some or all of the light
- May only be a section of the screen

Image quality problems

Flickering, color patterns incorrect
- you can almost wokr with this

Check the cabl epins
- Especially if missing a color

Distorted image and geometry
- Check the OS refresh rate and resolution settings
- Need to match the display specifications
- Check or replace cable

Disable hardware acceleration
- Troubleshoot with the software drivers

Sizing issues

The video output
- The display may scale to fit the image (or not)
- Check the display for a scaling option

The size of the user interface and icons
- Modify the OS resolution settings
- Change the scaling options

Distorted image

Lines, flashing colors, blocks
- Difficult to see

Hardware failure
- LCD panels are very easy to break
- No easy fix - replace the display

Other hardware
- Bad cable
- Bad cable adapter

Software configuration
- Bad video driver






## Troubleshooting Mobile Devices



Poor battery health

Replace aging batter
- there's only so many recharges

Bad recpetion
- Always searching fro signal
- Airplane mode on the ground

Disable unnecessary features
- 802.11 wireless, Bluetooth, GPS

Check application battery usage
- iOS and IPadOS: Seetings/Battery
- Android: Settings/Battery

Swollen battery

Buildup of gas
- Designed to self-contain
- Do NOT open the battery packet/container
    Significant fire risk
    You'll be sorry

Faulty battery
- Stop using immediately
- Dispose of properly

Device can be damaged
- Better than having a fire

Broken screen

TIme for a backup
- Do this first

Replace the screen
- No easy fixes

The glass is sharp
- Screen protectors can help
- Use clear tape until repaired

Improper charging

Check everything in the charging process
- Cables, interfaces

Check the cable interface
- Remove any obstructions

Check the cable
- Don't use frayed or damaged cables
- Try a known-good cable

Verify the power adapter
- Check with a multimeter

Poor ot no connectivity

Cellular or WIFI
- Location, Location, Location

Cellular
- Signal strength
- Location matters
- Outdoor connectivity may be better

WiFi
- Limited range
- Interference can be limit throughput
- May need a channel/frequency configuration change

Liquid Damage

Many phones have a Liquid Contact Indicator (LCI)
- Turns color when liquid has been present

Power down the phone
- Don't power it back on. Don't do it.

Remove the caae, cards, back, batter
- If possible

Putting the phone in a a bag of rice doesn't actually work well.

Leave it alone
- Don't turn it on
- Do not charge the phone
- Do not connect it to power
- Do not press any keys
- Do not heat the phone
- Do not move it around

Wait at least a day
- Or until the phone appears to be dry
- And then perhaps a few hours after that

Overheating

Phone will automatically shut down
- Avoid overheating damage

Charging/discharging the battery, CPU usage, display light
- All of these create heat

Check app usage
- Some apps can use a lot of CPU

Avoid direct sunlight
- Quickly overheats

Digitizer issues

Touchscreen completly black or not responding to input
- Screen presses do not register

Apple iOS reset
- Press power button, slide to power off, press power button
- Hold down power button and Honme | Volume for 10 seconds

Android device restart
- Remove battery, put back in, power on
- Hold down power and volume down until restart
    Some phones have different key comnbinations
    some phones do not have a key based reset

Physically damaged ports

External interface
- Charging and data transfer

Rough handling and accidents
- Damages the interface

Not charging
- Look closely

Not modular
- Requires a system board replacement

Malware

Always a concern
- Even on mobile devices
- The device type doesn't matter

Look for symptoms
- Unusal apps
- Large data transfers
- Pop up messages
- High CPU usage, device overheating
- Excessive battery use

Try a security app or scanner
- Identify malware infections

Cursor drift

Random input or cursor moves without touching the device
- Common on older screens

The system will adjust to the new calibration parameters
- No more drift

Unable to install new applications

Available space
- Check storage capacity and delete unnecessary data

Network Connectivity
- Apps are downloaded from an external resource

OS or app compatibility
- Upgrade the OS and check for an updated application version

Store cache or user credentials
- Clear the Google Play Store cache or check iCloud username and password
- Logoout and log back in

Stylus doees not work

Power
- Check the stylus battery charge ad recharge if necessary

Bluetooth connectivity
- Check the connection and try re-pairing

Stylus hardware issue
- A stylus can suffer through a lot of physcial wear
- Check the tip and see if a tip replacement would apply

Restart the device
- Resets the OS, the network and everything else

Degraded performance

Outdated OS and app software
- Time to upgrade and restart

Low storage
- Slowdowns and crashes

Hardware issues
- Bad RAM or storage drive

Excessive background apps
- Excessive memory usage - try closing some apps






## Troubleshooting Networks



No network connectivity

Do you have a link light?
- Is it plugged in?

Ping loopback (127.0.0.01)
- Is the protocol stack working?
- Availiablity and intermittent connectivity

Ping local IP address
- Checks local configuration, adapter, and link signal

Ping default gateway
- Connectivity on the local network 

Ping devices on router's other side
- 8.8.8.8 or 9.9.9.9

Intermittent wireless connectivity

Interference 
- Something else is using our frequency

Signal strength 
- transmitting signal, transmitting antenna, recieving antenna

Incorrect channel
- Usually automatic; look for manual tuning

Bounce and latency
- Multipath interference; flat surfaces

Incorrect access point placement
- Locate close to the users 

Slow network speeds

The network is slow!
- It's probably not the network

Confirm end-to-end connectivity
- Ping or application login
- Validate with a speed test

Evaluate connectivity on each network hop
- Utilization, errors, total throughput, filtering/ACLs

may require a packet capture
- The iltimate verification

Limited or no connectivity

Windows alert in the system tray
- "Limited or no connectivity"
- "No Internet Access"

Check the local IP address
- An APIPA address will only have local connectivity

If DHCP address is obtained perform the ping test 
- Local gateway, remote IP address

Jitter

Most real-time media is sensitive to delay
- Data should arrive at regular intervals
- Voice communication, Live Video

If you miss a packet, there's no retransmission
- There's no time to "rewind" you phone call

Jitter is the time between frames
- Excessive jitter can cause you to miss information, "choppy" voice valls

Poor VoIP quality

High speed and low latency 
- Real time applications are demanding

Check the Internet Connection
- A speed test can identify slow links

Verify the local networking equipment
- An old router can cause significant problems

View the network performance
- A packet capture would be useful

Port flapping

Network interface goes up and down
- Over and over again

Verify the cable
- Check the wiring

Move between switch interfaces
- Is the flapping associated with the switch interface or the device?

Replace bad hardware or cables
- May require additonal  purchases

High latency 

A delay between the request and the response 
- Waiting time

Some latency is expected and normal
- Laws of physics apply

Examine the response times at every step along the way
- This may require multiple measurement tools

Packet captures can provide detailed analysis
- Microsecond granularity
- Get captures from both sides

External interference

Predictable
- Flourescent lights
- Microwave ovens
- Cordless telephones
- High-power sources

- Unpredicatable
- Multi-tenant building

Measurements
- Signal to noise ratio (SNR)
- Performance monitor

Siganl to noise ratio (SNR)

Signal 
- What you want

Noise
- What you don't want 
- Interference from other networks and devices

You want a very large ratio
- The same amount of signal to noise (1:1) would be bad

Authentication issues

Access a resource
- Requires the proper credentials
- Username, password, other factors

Verify an active session
- May need to be refreshed
- Logout and back in 

May be difficult to see
- Part of a service or background process

Perform a packet capture
- Verify connectivity and look for errors

Intermittent Internet Connectivity

Determine the scope of the outage
- Ongoing pings
- Tracerout to a know location
- Speed tests

External issues require external support
- Work directly with the Internet Service Provider (ISP)
- Have your contract and account information available

Check your SLA
- Service level agreeement






## Troubleshooting Printers



Testing the printer

Print or scan a test page
- Built into Windows
- Not an application

Use diagnostic tools
- Web-based utilites built into the printer
- Vendor specific
- Generic utilities

Bad output

Lines down the printed page
- Inkject: Clean print heads
- Laser: Check for scratched photsensitive drum

Faded prints, blankk pages
- Low toner or ink

Double/echo images or speckling
- Laser printer optical drum not cleaned properly
- Ghost or "shadow" from previous drum rotation

Garbled print

Bad printer driver/ wrong model
- Incorrect page description lanaguage (PCL or PostScript)

Verify the printer functionality
- Check with a test page

Bad application
- Check the output 
- Upgrade the application

Paper jam

Careful when removing
- Don't rip the paper
- Don't damage internal components

paper not feeding or misfeeds multiple pages
- Check the trays
- Pickup rollers are part of a laser printer maintenance kit

Creased paper
- Probems in the paper path
- Check the paper weight 

Multiple prints pending in queue

Corrupted print jobs
- Print spooler will crash or freeze 
- Most spooler configuration will automatically restart

Problems are logged
- Windows Event Viewer, Windows-Print Service

One job may be causing the issue 
- Monitor the queue for details

Grinding nosies 

Never a good sound from your printer
- The ink is already manufactured

Something is not operting properly
- Paper jam
- Carriage is stalled or jammed

Each printer has a different process
- Check the manuals for removing paper jams
- Some inkjet printers have a particular process

May require additonal maintenance 
- Or replace the printer

Finishing issues

Finishing happens after the ink or toner has been applied
- Collate, binding

Staple jams
- larger printer will ollate and staple groups of papers
- Each printer manufacturer has a different removal process

Incorrect hold punch location
- Verify with the printer driver
- May require a driver update

Incorrect page orientation

Print a portrait page
- Get a landscape print

Check the settings when printing
- Controlled the print driver
- May require a driver update

The printer also has a default setting
- Check the settings on the printer console

Tray not recognized

Office printer often have multiple paper trays
- Plain letter, plain legal, letterhead, paper colors

The size of the printed page needs to match the size of the paper in the tray
- You can't print a 14" legal page to an 11" letter page

The definition of the paper tray is part of the driver configuration
- Compare the user's configuration with the installed printer trays

Connectivity issues

the printer is a network device
- Follows the same rules as any other device

Confirm the connection type
- Wired , wireless

Verify IP address configuration
- IP, subnet masks, default gateway, DNS, etc

Check the print server
- May be part of the printer
