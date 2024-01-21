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