**[Running node as a service](https://github.com/clemahieu/raiblocks/wiki/Running-rai_node-as-a-service)**
    
**To manage node, use [RPC commands](https://github.com/clemahieu/raiblocks/wiki/RPC-protocol) or [CLI](https://github.com/clemahieu/raiblocks/wiki/Command-line-interface)**   

***

# Ubuntu 16.04 LTS Server, Ubuntu 16.10+, Debian 8 Jessie, Debian 9 Stretch

### Dependency Build Instructions 

```bash
sudo apt-get update && sudo apt-get upgrade   
sudo apt-get install git cmake g++ curl wget
```   
### Building static Boost
```bash
wget -O boost_1_66_0.tar.gz http://sourceforge.net/projects/boost/files/boost/1.66.0/boost_1_66_0.tar.gz/download   
tar xzvf boost_1_66_0.tar.gz   
cd boost_1_66_0   
./bootstrap.sh   
./b2 --prefix=../[boost] link=static install   
cd ..
```
### Building rai_node

```bash
git clone --recursive https://github.com/clemahieu/raiblocks.git rai_build   
cd rai_build   
cmake -DBOOST_ROOT=../[boost]/ -G "Unix Makefiles"   
make rai_node   
cp rai_node ../rai_node && cp librai_lib.so .. && cd .. && ./rai_node --diagnostics
```

# CentOS 7

### Dependency Build Instructions 

```bash
sudo yum check-update   
sudo yum install git cmake gcc gcc-c++ libstdc++-static curl wget   
```

### Building static Boost

```bash
wget -O boost_1_66_0.tar.gz http://sourceforge.net/projects/boost/files/boost/1.66.0/boost_1_66_0.tar.gz/download   
tar xzvf boost_1_66_0.tar.gz   
cd boost_1_66_0   
./bootstrap.sh   
./b2 --prefix=../[boost] link=static install   
cd ..
```

### Building rai_node

```bash
git clone --recursive https://github.com/clemahieu/raiblocks.git rai_build   
cd rai_build   
cmake -DBOOST_ROOT=../[boost]/ -G "Unix Makefiles"   
make rai_node   
cp rai_node ../rai_node && cp librai_lib.so .. && cd .. && ./rai_node --diagnostics
```

# Ubuntu 16.04 on Digital Ocean Droplet ($5/Month 512Mb Ram, 1 Core, 20Gb SSD)
Sign up at digitalocean.com

Create Droplet

Add swap space -https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04

```bash
sudo fallocate -l 2G /swapfile  
sudo chmod 600 /swapfile  
sudo mkswap /swapfile  
sudo swapon /swapfile

sudo apt-get update  
sudo apt-get install g++ make cmake -y

wget -O boost_1_66_0.tar.gz https://dl.bintray.com/boostorg/release/1.66.0/source/boost_1_66_0.tar.gz  
tar xzvf boost_1_66_0.tar.gz  
cd boost_1_66_0  
./bootstrap.sh  
./b2 --prefix=../[boost] link=static install  
cd ..

git clone https://github.com/clemahieu/raiblocks.git  
cd raiblocks/

git submodule init  
git submodule update

cmake -DBOOST_ROOT=../[boost]/ -G "Unix Makefiles" 
 
make rai_node

./rai_node --daemon

# check block count  
./rai_node --debug_block_count
```