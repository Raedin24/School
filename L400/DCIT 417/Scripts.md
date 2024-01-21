# Simple Point-To-Point Network
Steps:
1. Command Line
2. Create nodes
3. Create point-to-point channel  and set attributes
4. Install point-to-point on netdevice container
5. Install internet protocols on nodes
6. Set base IP address
7. Assign IP address to node devices
8. Create UDP server, port 9
9. Install server on application container. Start and stop
10. Create UDP client and set ping attributes
12. Install client on application container
13. Start and end simulation
```cpp
#include "ns3/core-module.h"
#include "ns3/point-to-point-module.h"
#include "ns3/network-module.h"
#inlucde "ns3/internet-module.h"
#include "ns3/application-module.h"

using namespace ns3;

NS_LOG_COMPONENT_DEFINE(firstExample);

int main(int argc, char* argv[])
{
	CommandLine cmd(__FILE__);
	cmd.Parse(argc, argv);

	Time::SetResolution(Time::NS);
	LogComponentEnable("UdpEchoClientApplication", LOG_LEVEL_INFO)
	LogComponentEnable("UdpEchoServerApplication", LOG_LEVEL_INFO);

	NodeContainer nodes;
	nodes.Create(2);

	PointToPointHelper pointToPoint;
	pointToPoint.SetAttribute("DataRate", StringValue("5mbps"));
	pointToPoint.SetAttribute("Delay", StringValue("2ms))

	NetDeviceContainer devices;
	devices = pointToPoint.Install(devices);

	InternetStackHelper stack;
	stack.Install(devices)

	Ipv4AddressHelper address;
	address.SetBase("10.1.1.10", "255.255.255.0")

	Ipv4InterfaceContainer interfaces = address.Assign(devices);

	UdpEchoServerHelper echoServer(9);

	ApplicationContainer serverApps = echoServer.Install(nodes.Get(1));
	echoServer.Start(Seconds(1.0));
	echoServer.Stop(Seconds(10.0));

	UdpEchoClientHelper echoClient(interfaces.GetAddress(1), 9);
	echoClient.SetAttribute("MaxPackets", UintegerValue(4));
	echoClient.SetAttribute("Interval", TimeValue(Seconds(1.0)));
	echoClient.SetAttribute("PacketSize", UintegerValue(1024));

	ApplicationContainer clientApps = echoClient.Install(nodes.Get(0));
	echoClient.Start(Seconds(2.0));
	echoClient.Stop(Seconds(10.0));

	Simulator::Run();
	Simulator::Destroy();
	return 0;
}
```


# Multi Point-To-Point Network
```cpp
#include "ns3/applications-module.h"
#include "ns3/core-module.h"
#include "ns3/network-module.h"
#include "ns3/internet-module.h"
#include "ns3/point-to-point-module.h"

using namespace ns3;

NS_LOG_COMPONENT_DEFINE("multipoint");

int main(int argc, char* argv[])
{
	// Command line
	CommandLine cmd(__FILE__);
	cmd.Parse(argc, argv);
	
	Time::SetResolution(Time::NS);
	LogComponentEnable("UdpEchoClientApplication", LOG_LEVEL_INFO);
	LogComponentEnable("UdpEchoServerApplication", LOG_LEVEL_INFO);
	
	// Create nodes
	NodeContainer nodes;
	nodes.Create(6);
	NodeContainer n0n4 = NodeContainer(nodes.Get(0), nodes.Get(4);
	NodeContainer n1n4 = NodeContainer(nodes.Get(1), nodes.Get(4);
	NodeContainer n2n5 = NodeContainer(nodes.Get(2), nodes.Get(5);	
	NodeContainer n3n5 = NodeContainer(nodes.Get(3), nodes.Get(5);	
	NodeContainer n4n5 = NodeContainer(nodes.Get(4), nodes.Get(5);	
	
	// Point-to-Point
	PointToPointHelper p2p;
	p2p.SetAttributes("DataRate", StringValue("5mbps");
	p2p.SetAttributes("Delay", StringValue("2ms");
	
	// NetDevice
	NetDeviceContainer d0d4 = p2p.Install(n0n4);
	NetDeviceContainer d1d4 = p2p.Install(n1n4);	
	NetDeviceContainer d2d5 = p2p.Install(n2n5);
	NetDeviceContainer d3d5 = p2p.Install(n3n5);
	NetDeviceContainer d4d5 = p2p.Install(n4n5);
	
	Ipv4AddressHelper address;
	
	address.SetBase("10.1.1.0", "255.255.255.0");
	Ipv4InterfaceContainer i0i4 = address.Assign(d0d4);
	
	address.SetBase("10.1.2.0", "255.255.255.0");
	Ipv4InterfaceContainer i1i4 = address.Assign(d1d4);

	address.SetBase("10.1.3.0", "255.255.255.0");
	Ipv4InterfaceContainer i2i5 = address.Assign(d2d5);
	
	address.SetBase("10.1.4.0", "255.255.255.0");
	Ipv4InterfaceContainer i3i5 = address.Assign(d3d5);	
	
	address.SetBase("10.1.5.0", "255.255.255.0");
	Ipv4InterfaceContainer i4i5 = address.Assign(d4d5);	
	
	UdpEchoServerHelper echoServer1(9);
	UdpEchoServerHelper echoServer2(10);
	
	ApplicationContainer serverApp1 = echoServer1.Install(nodes.Get(4);
	serverApp1.Start(Seconds(1.0));
	serverApp1.Start(Seconds(10.0));
	
	Application Container serverApp2 = echoServer2.Install(nodes.Get(5);
	serverApp2.Start(Seconds(1.0));
	serverApp2.Stop(Seconds(10.0));
	
	UdpEchoClientHelper echoClient1(i4i5.GetAddress(0), 9);
	echoClient1.SetAttribute("MaxPackets", UintegerValue(4));
	echoClient1.SetAttribute("Interval", TimeValue(Seconds(1.0));
	echoClient1.SetAttribute("PacketSize", UintegerValue(1024));
	
	UdpEchoClientHelper echoClient2(i4i5.GetAddress(1), 10);
	echoClient2.SetAttribute("MaxPackets", UintegerValue(4));
	echoClient2.SetAttribute("Interval", TimeValue(Seconds(1.0));
	echoClient2.SetAttribute("PacketSize", UintegerValue(1024));
	
	ApplicationContainer clientApp1 = echoClient1.Install(nodes.Get(0));
	clientApp1.Start(Seconds(2.0);
	clientApp1.Stop(Seconds(10.0);
	
	ApplicationContainer clientApp2 = echoClient2.Install(nodes.Get(2));
	clientApp2.Start(Seconds(2.0);
	clientApp2.Stop(Seconds(10.0);	

	// Additional Code for running NetAnim
	AnimationInterface anim("anim.xml");
	anim.SetConstantPosition(nodes.Get(0), 1.0, 1.0);
	anim.SetConstantPosition(nodes.Get(1), 3.0, 1.0);
	anim.SetConstantPosition(nodes.Get(4), 2.0, 2.0);
	anim.SetConstantPosition(nodes.Get(2), 1.0, 4.0);
	anim.SetConstantPosition(nodes.Get(3), 3.0, 4.0);
	anim.SetConstantPosition(nodes.Get(5), 2.0, 3.0);	
	
	Simulator::Run();
	Simulator::Destroy();
	return 0;
}
```


# CSMA Network
```cpp
#include "ns3/applications-module.h"
#include "ns3/core-module.h"
#include "ns3/network-module.h"
#include "ns3/internet-module.h"
#include "ns3/csma-module.h"

using namespace ns3;

NS_LOG_COMPONENT_DEFINE("csma");

int main(argc, char* argv[])
{
	CommandLine cmd(__FILE__);
	cmd.Parse(argc, argv);

	NodeContainer csmaNodes;
	csmaNodes.Create(4)

	CsmaHelper csma;
	csma.SetAttribute("DataRate", StringValue("1000mbps"))
	csma.SetAttribute("Delay", TimeValue(Nanoseconds(6560)));

	NetDeviceHelper csmaDevices = csma.Install(csmaNodes);

	InternetStackHelper stack;
	stack.Install()

}
```