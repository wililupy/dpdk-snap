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

<pre><code> sudo snap connect dpdk:network-observe core:network-observe
sudo snap connect dpdk-hardware-observe core:hardware-observe</code></pre>

Then you can test by doing the following:

<pre><code>sudo -s
mkdir -p /mnt/huge
mount -t hugetlbfs nodev /mnt/huge
echo 1024 > /sys/devices/system/node/node0/hugepages/hugepages-2048kB/nr_hugepages
dpdk.testpmd -- -i</code></pre>


