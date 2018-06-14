# dpdk-snap
dpdk-snap

This is the snapcraft.yaml to build a DPDK Snap.
It is currently still under development.

To build, you need to have snapcraft installed on your system (Ubuntu 18.04):

```
sudo snap install snapcraft --classic 
git clone https://github.com/wililupy/dpdk-snap
cd dpdk-snap
snapcraft
```
Once the snap is installed, you will need to connect four plugs:

```
sudo snap connect dpdk-wililupy:network-observe core:network-observe
sudo snap connect dpdk-wililupy:hardware-observe core:hardware-observe
sudo snap connect dpdk-wililupy:process-control core:process-control
sudo snap connect dpdk-wililupy:system-observe core:system-observe
```
Then you can test by doing the following:

```
sudo -s
mkdir -p /mnt/huge
mount -t hugetlbfs nodev /mnt/huge
echo 1024 > /sys/devices/system/node/node0/hugepages/hugepages-2048kB/nr_hugepages
dpdk-wililupy.testpmd -- -i
```
You can also install this from the snap store in the edge and beta channels:

`sudo snap install dpdk-wililupy --beta --devmode`

This will install the LTS version while `edge` will install the latest DPDK version (18.05-rc0)
You can upgrade using snap as well:

`sudo snap refresh dpdk-wililupy --edge --devmode`

### This is only for Ubuntu Bionic Beaver (18.04) with the stock kernel (4.15.0-22-generic). It has not been tested with any other OS
