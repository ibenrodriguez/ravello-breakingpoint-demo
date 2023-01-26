# ravello-breakingpoint-demo
Demo files showing Ixia BreakingPoint Virtual with OpenWRT Router as Device Under Test DUT

# Overview
BreakingPoint Virtual Edition is a software-based test platform that enables you to run a BreakingPoint vController and traffic generation blades on a virtual chassis.
                    
BreakingPoint Virtual Edition offers the following benefits:
- Low Hardware Cost - You can use low-cost servers or dedicated virtualization servers to generate the traffic.
- More Efficient use of Hardware - The same servers used to generate Ixia traffic can also be used for other non- Ixia applications; or the virtual Ixia ports can be hosted on a virtualization server used to host other applications.
- Ease of Use – The BreakingPoint Virtual Edition GUI is nearly identical to the standard hardware versions, reducing the learning time.
- Reduced System Administration - The BreakingPoint Virtual Edition chassis does not need be maintained or monitored in a lab because it is virtual in nature.
- Rapid and Easy Deployment - Virtual Ixia ports can be instantiated as necessary, used to generate traffic, and then destroyed when no longer needed.
- BreakingPoint Virtual Edition is delivered as a pre-configured .ova template.    

# Basic Elements
The basic elements involved in the BreakingPoint Virtual Edition are:

- A simple installer based on a single OVA image or installation script.
- Deployment and discovery tools for easy provisioning of Virtual Blades (vBlades). l A license server that also runs on the BreakingPoint vController.
- vBlades for virtualization of load modules using a single management interface with from two to eight virtual test ports
- vController for virtualization of the System Controller:
  - Controls up to 12 vBlades and up to 96 vPorts
  - Controls vBlades spanning across different physical servers
                    
The following image depicts the components of BreakingPoint Virtual Edition.

![alt text](https://raw.githubusercontent.com/ibenrodriguez/ravello-breakingpoint-demo/master/ravello-ixia-bpve-demo.png "Ixia Breaking Point Demo on Ravello Drawing")

# Setup Notes: 
- http://wiki.openwrt.org/doc/uci/network
  - run this command after making changes to /etc/config/network

```
  /etc/init.d/network reload
  root@OpenWrt:~# cat /etc/config/network

config interface 'loopback'
	option ifname 'lo'
	option proto 'static'
	option ipaddr '127.0.0.1'
	option netmask '255.0.0.0'

config interface 'lan'
	option ifname 'eth0'
	option proto 'static'
	option ipaddr '10.10.0.10'
	option netmask '255.255.0.0'
        option gateway '10.10.0.1'
 	option dns '8.8.8.8'
config interface 'west'
	option ifname 'eth1'
	option proto 'static'
	option ipaddr '10.20.0.10'
	option netmask '255.255.0.0'

config interface 'east'
	option ifname 'eth2'
	option proto 'static'
	option ipaddr '10.30.0.10'
	option netmask '255.255.0.0'


root@OpenWrt:~# /etc/init.d/network reload
```

- LuCI Essentials - Installing LuCI on uHTTPd
This installs the essentials of the Web User Interface LuCI. See "opkg update && opkg list luci-*" for all available packages to administer OpenWrt through LuCI.
  - opkg update
  - opkg install luci-ssl # enable https for luci
- Ravello's service currently does not support DHCP for ESXi's nested vms.
  - As you can see, for now you can either use a static IP's for the ESXi or create your own DHCP server for this purpose. 
  - https://www.ravellosystems.com/blog/guest-vm-connectivity-setup/
  - And how to create your own DHCP server:
  - https://www.ravellosystems.com/blog/configure-dhcp-esxi/
  - we are using OpenWRT for the local DHCP server and device under test L3 rotuer. You can replace this with your own device.
- Windows 7 VM used to build the environment
  - VMware vSphere C++ Desktop Client installed to manage ESXi host
  - Download the Ixia Breaking Point VE OVA Image
  - Import the OVA to the ESXi host
  - Putty SSH Client installed

