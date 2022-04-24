# Apollo-HPC
 Mini raspberry pi cluster with slurm workload manager

# Cluster Infomation
 Base compute node with Raspberry Pi 4
 ```
2 x Raspberry Pi 4 8GB(RAM)
4 x Raspberry Pi 4 4GB(RAM)
1 x Nvidia Jetson nano 4GB(RAM) (Optional)
1 x SSD 120 GB
1 x Gigabit Ethernet Switch
1 x Router
```
# Install
## Hardware

                                   |--(CAT6)->[Control-Service] RPI4 - 8GB(RAM)
             ________________      |    |-(USB)->[NFS-SSD] - 120GB
            | Gigabit Switch |---> |--(CAT6)->[Compute-Node1] RPI4 - 8GB(RAM)
             ------^---------      |--(CAT6)->[Compute-Node2] RPI4 - 4GB(RAM)
             ______|____           |--(CAT6)->[Compute-Node3] RPI4 - 4GB(RAM)
            | Router MT |          |--(CAT6)->[Compute-Node4] RPI4 - 4GB(RAM)
Internet -->| DHCP & GW |          |--(CAT6)->[Compute-Node5] RPI4 - 4GB(RAM)
             -----------           |--(CAT6)->(Option)[GPU-Node1] NVD nano -  4GB(RAM)

## Network 
## Software
MUNGE
SLURM
Lmod
Easybuild
MPI(MPICH, OpenMPI)
ATLAS
OpenBLAS
HPL

### Install Development Tools
```bash
sudo apt install build-essential libssl-dev ntp
```
### MUNGE
 1. The munge is installed on every node in the cluster. (both service and compute)
 2. Download MUNGE form source
 ```bash
 wget https://github.com/dun/munge/releases/download/munge-0.5.14/munge-0.5.14.tar.xz
 ```
 3. Install MUNGE
 ```bash
 tar -xvJf munge-0.5.14.tar.xz \
  && cd munge-0.5.14          \
  && ./configure              \
     --prefix=/usr            \
     --sysconfdir=/etc        \
     --localstatedir=/var     \
     --runstatedir=/run       \
  && make                     \
  && sudo make install
 ```
 4. Create `mungue` user and group
 ```bash
 sudo adduser munge --uid 1001  --system --no-create-home --group
 ```