Not in active development. Outstanding issues tagged as wontfix and closed.

Superseded by [host2dot](https://github.com/deanturpin/hosts2dot).

----

# Hosts file to network topology
By default `hosts2topology` takes a plaintext hosts file on stdin and creates a
file `topology.svg` in the current directory. The
[CIDR](https://en.wikipedia.org/wiki/CIDR) information is extracted from the comments
in the hosts file. If IPs are listed that don't match a netmask they are
connected to the "unknown" network.

The image is rendered using [Graphviz](http://graphviz.org).

```bash
./hosts2topology < hosts
```

![](render/circo.png)

Connections between subnets are indicated by adding a second IP in the comment
at the end of a line.

```bash
# CIDR network description
# 192.168.0.0/27

# Hosts - only the IP is used
192.168.0.1 neque
192.168.0.5 maxime
192.168.0.6 ea # 10.10.10.1

10.10.10.1 one
10.10.10.2 two
```

Output file name and type can be overridden by supplying a file name.

```bash
./hosts2topology one.jpg < hosts
./hosts2topology two.gif < hosts
```

##Alternative rendering engines
Graphviz supports various rendering engines which can be specified on the
command line.

```bash
./hosts2topology three.png sfdp < hosts
./hosts2topology four.gif neato < hosts
```

Running `./generate_all` will create them all in the current directory.

###circo (the default)
![](render/circo.png)

###dot
![](render/dot.png)

###neato
![](render/neato.png)

###fdp
![](render/fdp.png)

###sfdp
![](render/sfdp.png)

###twopi
![](render/twopi.png)

###patchwork
![](render/patchwork.png)
