Open Tech Fund 2015

# Project Title

peermaps

# What is your idea?

Centralized mapping services track users, causing unauthorized surveillance; bend to state power, leading to censored information; and depend heavily upon the Internet to operate, working poorly when connectivity is intermittent. If developers could instead use a BitTorrent-like swarm for map data, the resulting applications could reintroduce censored content and be stored offline, becoming robust against internet outages, state censorship, and corporate control.

Peermaps is a suite of peer-to-peer mapping tools that aims to fill this gap. For the last X months in my spare time, I have been developing Peermaps -- a suite of peer to peer mapping tools with distributed infrastructure
for hosting, sharing, and displaying map data.  [KRM: do you want to include 'editing' here? It might be smart to focus the grant on hosting and displaying data]

The maps will come standalone or embeddable in a web page like centralized
offerings such as Google Maps provide, but instead of phoning home to Google in
order to display every map, the map data is delivered by peers over WebRTC
connections. Any data received is saved locally to use offline and shared with
other peers. 

This architecture is robust against internet outages and state censorship
because map data is saved locally and map data can still be delivered from
whichever limited number of geographically distributed peers are still
reachable.

Sensitive map overlays built in the editor such as the location of a protest
route are encrypted and can be shared securely with trusted peers. [KRM: can you say more here? seems like this could be a paragraph for examples. Maybe starting with, "example applications could include..."]

# What are hoped for goals or longer term effects of the project?

[KRM: this is your chance to really make your resume' shine. you have a host of very successful projects, namely browserify et al, and should talk about how you've been successful before and what the future of peermaps could look like in light of that]

This project is part of a larger effort to build distributed, peer to peer
tools to replace centralized hosted services. [KRM: say more about this. what larger effort? ] 

Centralized services require
reliable access to the internet, are a juicy target for censorship and
surveillance. We want to empower users to break their dependence on these
centralized services in favor of services that nobody can own. [KRM: could be moved up to 1st paragraph]

With peermaps, people will have a solid mapping tool that will still work even
when the internet goes down, and they will be able to share maps with each other
privately, securely, and directly.

# How will you do it?
[KRM: again, i'd focus this a bit more. you might find BEP44 too slow, or get a hiccup in indexed version of OSM. what if you took out the last two bullets?]
This project will implement:

* a geospatial index that works in node and the browser (1 month)
* build indexed versions of Open Street Map, landsat imagery (1 month)
* distribute indexed versions over [webtorrent](https://webtorrent.io) and
[hyperdrive](https://github.com/mafintosh/hyperdrive) (1 week)
* offline-first web viewer for webtorrent-hosted map layers (2 months)
* peer to peer map editor for layer overlays (2 months)
* distribute encrypted map edit feed using [BEP44](https://github.com/feross/bittorrent-dht/pull/61) or hyperdrive (1 month)
* package and test these offline webapps as native applications using phonegap/cordova (2 weeks)

The expected span of this project is 8 months for these deliverables.

A rough implementation of the spatial index is done using KDB trees:
[peermaps/kdb-tree-store](https://github.com/peermaps/kdb-tree-store),
but a BKD index is in the works for faster construction time for very large
datasets.

A bittorrent client can prioritize particular chunks of a file, instead of
downloading a file from start to finish or in random chunks, This technique can
be used to seek into the middle of a video, or even to live boot a docker image
directly from peers on the network without downloading the entire image first.
This trick can also be used to perform efficient geospatial lookups from peers
for planet-scale geographic data and imagery, with an appropriate indexing
strategy. [KRM: they want a bulletted list here. maybe you could 'wow' them with your expertise by putting this in the first section. they will need something to catch their eye. a couple of them currently work at google]

# Who is the project for?

This project is aimed at activists, journalists, and communities in areas with
unreliable internet, either from lack of infrastructure or from state
interference, who need censorship-resistant mapping tools over an unreliable
network. 

# What community currently exists around this project?

Peermaps has [a website](http://peermaps.org),
[a github organization](https://github.com/peermaps),
an IRC channel on freenode, and I've been posting updates on patchwork,
a decentralized social network. Peermaps spans many other projects, so I've been
active in the webtorrent/bittorrent ecosystems and [dat ecosystem](http://dat-data.com/),
actively contributing to projects such as
[bittorrent-dht](https://github.com/feross/bittorrent-dht/pull/61),
and [hyperlog](https://github.com/mafintosh/hyperlog/pulls?utf8=%E2%9C%93&q=is%3Apr+author%3Asubstack).

I've been working with the [Digital Democracy](http://www.digital-democracy.org/)
project to build peer to peer mapping primitives for remote communities, which
has a nice overlap with the goals of the peermaps project and real users in
Guyana, Peru, and Brazil.

[KRM: might be good to mention the community around *you* as a developer here, too. how do you plan on growing the community?  also take a second to say that you really look foward to working with the OTF network, first responders, crisis management researchers, etc. if you have even ever mentioned this to anyone before in any org about how peermaps would make their lives easier you should just cite them in a long list, e.g.  localwiki would count.]

# Why is this project needed?

Peermaps will reduce the effectiveness of tactics to repress freedom of assembly
such as the [Egyptian government's internet shutdown](https://en.wikipedia.org/wiki/Internet_in_Egypt#2011_Internet_shutdown)
in January 2011 or the District Attorney
[subpeona for twitter records](http://cityroom.blogs.nytimes.com/2012/02/06/protesters-lawyer-challenges-twitter-subpoena/)
relating to an October 2011 protest across the Brooklyn Bridge.
Access to accurate maps are even more critical during periods of conflict,
natural disaster, and times of civil unrest. 

Peermaps will also empower people in areas with poor, overly expensive, or
nonexistent internet access to map, edit, and share their surroundings with each
other and the outside world. 
