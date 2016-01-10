# ravello-breakingpoint-demo
Demo files showing Ixia BreakingPoint Virtual with OpenWRT Reouter as Device Under Test

Overview
                    
BreakingPoint Virtual Edition is a software-based test platform that enables you to run a BreakingPoint vController and traffic generation blades on a virtual chassis.
                    
BreakingPoint Virtual Edition offers the following benefits:
Low Hardware Cost - You can use low-cost servers or dedicated virtualization servers to generate the traffic.
More Efficient use of Hardware - The same servers used to generate Ixia traffic can also be used for other non- Ixia applications; or the virtual Ixia ports can be hosted on a virtualization server used to host other applications.
Ease of Use – The BreakingPoint Virtual Edition GUI is nearly identical to the standard hardware versions, reducing the learning time.
Reduced System Administration - The BreakingPoint Virtual Edition chassis does not need be maintained or monitored in a lab because it is virtual in nature.
Rapid and Easy Deployment - Virtual Ixia ports can be instantiated as necessary, used to generate traffic, and then destroyed when no longer needed.
BreakingPoint Virtual Edition is delivered as a pre-configured .ova template.    
Basic Elements
The basic elements involved in the BreakingPoint Virtual Edition are:
A simple installer based on a single OVA image or installation script.
Deployment and discovery tools for easy provisioning of Virtual Blades (vBlades). l A license server that also runs on the BreakingPoint vController.
Components of BreakingPoint Virtual Edition    
The components of BPS-VE are:
vBlades for virtualization of load modules: n A single management interface
From two to eight virtual test ports                
See the Hardware Requirements for minimum vBlade specifications.
vController for virtualization of the System Controller:
Controls up to 12 vBlades and up to 96 vPorts
Controls vBlades spanning across different physical servers
                    
The following image depicts the components of BreakingPoint Virtual Edition.

https://raw.githubusercontent.com/ibenrodriguez/ravello-breakingpoint-demo/master/ravello-ixia-bpve-demo.png

Setup Notes: 
http://wiki.openwrt.org/doc/uci/network