# Simple Point-To-Point Network
```cpp
#include "ns3/core-module.h"
#include "ns3/point-to-point-module.h"
#include "ns3/network-module.h"
#inlucde "ns3/internet-module.h"
#include "ns3/application-module.h"

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
	pointToPoint.SetAttribute("Delay", StringValue("2ms));

}
```

