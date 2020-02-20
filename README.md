# p2p links

This is a set of links for projects that I keep track of on the peer-to-peer space.

The goal is not to list every single project, but to keep track of the level of interest I have on each project.

Suggestions are appreciated, but not garanteed to be included in the list. Worst case scenario, it will be documented as part of the discussion on the PR and searchable :)

## Using all the time

### [Zerotier](https://zerotier.com/)

Overlay network **[comercial|free managed tier available|Open Source]**

This is one of the greatest tools that I use daily. This creates a virtual network on top of any other network the device is connected. Each device can then talk directly to each other over IPv6 or NAT-punch-holed connection.

This provides each device with their own static IP, regardless of being on 4G, wired, home network or the office (unless firewalled, it happens). You can then connect to the device anywhere, using any other tool you want.

It simulates a LAN network, so MDNS and broadcast works. It can run on MIPS OpenWRT routers, and then you can bridge every device to the virtual network without installing anything beyound the router.

It provides also a [6PLANE](https://zerotier.atlassian.net/wiki/spaces/SD/pages/7274520/Using+NDP+Emulated+6PLANE+Addressing+With+Docker) address, so each docker container running on a computer will have it's own IPv6 address accessible on the virtual network. It allows cross-node cross-container communication, over the internet or locally.

I keep a [multi-architecture Docker](https://hub.docker.com/r/bltavares/zerotier) up-to-date to have it runnig on all my [homelab](https://github.com/bltavares/homelab) devices. This allows me to add a new device on my virtual network only having to install Docker. The Docker image runs on ARMv6, ARMv7, ARM64, and Amd64, so any raspberry pi anywhere can talk to each other.

Available apps for Raspberry, Linux, Android, iOS, Windows and Mac.

#### To keep an eye related to Zerotier

- [Zerotier 2.0](https://zerotier.com/zerotier-2-0-status/) and the promise of an easier way to run a virtual network without internet.

- [Tailscale](https://tailscale.com/) new company built on top of Wireguard promising a similar experience to ZeroTier. Given that Wireguard requires key-exchanges and some setup both on each peer, the experience seems to require some extra tooling/central server. Let's see. There are also many [1](https://github.com/gawen/wirehub) [2](https://github.com/squat/kilo) [3](https://github.com/manuels/wireguard-p2p) early-phase projects to make wireguard managament create p2p networks.

- [Yggdrasil](https://yggdrasil-network.github.io/) open-source project also interested in providing a p2p overlay network. Similar to [cjdns](https://github.com/cjdelisle/cjdns) (main network is [hyperboria](https://hyperboria.net/)), with a different route propagation strattegy. Both require a peer with a static public ip to get on board of the network. Zerotier is one less service to maintain with their central server, and the option to run your own if needed. Yggdrasil nor cjdns are available on mobile.

- [Tinc](https://tinc-vpn.org/) is an older alternative I've used 5-6 years ago. It also requires both peer to be configured to talk to each other. Also available for ARM, MIPS and AMD devices. Some iOS options available over Cydia, and non-official Android apps. I had lot's of issues in the past to keep a stable connection, but it could have changed.

## Installed, check from time to time

### [Scuttlebutt](https://scuttlebutt.nz/) (SBB)

decentralised social network **[Open source|Protocol|Applications]**

[Get started](https://scuttlebutt.nz/get-started/) by selecting one of the apps that usins SSB protocol and start social networking. The protocol let's you store content locally, and download content from other devices on the network when they are connected. Your friends will carry your data, and they can share your data to other friends when they are connected. This is a gossip-based protocol.

SSB is a social network, and a protocol. The protocol lets you build many social apps, such as a distributed p2p github [git-ssb](https://git.scuttlebot.io/%25n92DiQh7ietE%2BR%2BX%2FI403LQoyf2DtR3WQfCkDKlheQU%3D.sha256). [There are many apps](https://handbook.scuttlebutt.nz/applications), such as [ssb-npm](https://handbook.scuttlebutt.nz/applications#ssb-npm), a [blog platform](https://github.com/ticktackim/ticktack-workplan), [chess](https://github.com/Happy0/ssb-chess) and so on.

I have installed [Patchwork](https://github.com/ssbc/patchwork) on my Desktop, and it is connected to many pubs. From time to time (2-3 times per month) I open the app, download messages from people I've followed and read how things are being developed. I mostly follow developers of the protocol and the apps there, to keep an eye on the evolution of the project. I barely post tho.

I have installed [Manyverse](https://www.manyver.se/) on Android. I've been using it since the early beta, and I've deleted my secret key many many many times. I would like to use it more. Let me know and I can send you an invite to get you on board on Manyverse.

#### To keep an eye related to SSB

All apps ship copies of Node.js (Electron and Node-Mobile), as the protocol relies on how Node.js.
This is being worked on by many people to allow porting the protocol to other languages, such as [Sunrisechoir](https://github.com/sunrise-choir) for Rust (specially this one) and [the Go version](https://github.com/cryptoscope/ssb)
This should make apps leaner and easier to embbedd SSB into other apps.

## Community run networks

[Altermundi](https://altermundi.net/), [Freifunk](https://freifunk.net/), [Guifi.net](https://guifi.net/en), [NYC Mesh](https://www.nycmesh.net/) are p2p community networks, where physical devices are put together to talk to each other. They use funny-named (eg: [B.A.T.M.A.N.](https://www.open-mesh.org/projects/open-mesh/wiki)) tools to broadcast route table to connected wifi routers running OpenWRT.

 If your device is connected to one router, it can multi-hop to another internally routed device in the LAN, or find a new route to the internet. With a few connected nodes, internet can be distributed to all participants at a lower cost.

 Each community run project often have a lot of documentation about network tools and setups of p2p routers. They use VPNs (wireguard,openvpn), overlay networks (cjdns/hyperboria) and physical connections to join all routers. Eg: [NYC Mesh docs](https://docs.nycmesh.net/)

Every year, the underling route propagation projects get together to battle wich project handles more members on [BattleMesh](https://battlemesh.org/).

This networks setup can use [Libremesh](https://libremesh.org/), [qmp](https://qmp.cat/) or [gluon](https://gluon.readthedocs.io) as a base distribution to get started, or generate a custom firmware with everything pre-configured like [Freifunk Image Builder](https://meshkit.freifunk.net/) does.

These community local networks allow people to create new networks easily, such as in natural disaters, and allow people to keep connected using internal services or dweb apps.
As an example [Altermundi support for Germany Klimmacamp](https://altermundi.net/article/mesh-networks-for-activists/) and [Meshnet for DWeb Camp 2019](https://dweb-camp-2019.github.io/meshnet/). Goes well with [DWeb apps]

I would love to have one in SP, but it requires hardward and effort to start and mantain on a log term.
