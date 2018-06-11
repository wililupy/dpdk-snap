# dpdk-snap
dpdk-snap

This is the snapcraft.yaml to build a DPDK Snap.
It is currently still under development.

To build, you need to have snapcraft installed on your system (Ubuntu 18.04):

<pre><code>sudo snap install snapcraft --classic 
git clone https://github.com/wililupy/dpdk-snap
cd dpdk-snap
snapcraft</code></pre>

Once the snap is installed, you will need to connect two plugs:

<pre><code>sudo snap connect dpdk:network-observe core:network-observe
sudo snap connect dpdk:hardware-observe core:hardware-observe</code></pre>

Then you can test by doing the following:

<pre><code>sudo -s
mkdir -p /mnt/huge
mount -t hugetlbfs nodev /mnt/huge
echo 1024 > /sys/devices/system/node/node0/hugepages/hugepages-2048kB/nr_hugepages
dpdk-wililupy.testpmd -- -i</code></pre>

You can also install this from the snap store in the edge and beta channels:

<code>sudo snap install dpdk-wililupy --beta --devmode</code>

This will install the LTS version while <code>edge</code> will install the latest DPDK version (18.05-rc0)
You can upgrade using snap as well:

<code>sudo snap refresh dpdk-wililupy --edge --devmode</code>

<h3>This is only for Ubuntu Bionic Beaver (18.04) with the stock kernel (4.15.0-22-generic). 
It has not been tested with any other OS
