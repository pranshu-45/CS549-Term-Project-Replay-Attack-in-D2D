CS549 Term Project - Replay Attacks in D2D communication networks

Here we are trying to simulate replay attacks in d2d networks
We are using psc ns3 as a simulator as it has required d2d modules to simulate d2d networks

What we do: Between the legitimate d2d communication of A and B nodes, A being the sender and B being the receiver, we introduce a new malicious node C. C captures the broadcasted packet, stores it, and then replays it again at a future specified time.
Our aim is to replay packet from C succesfully to B, so that B thinks that it as a legitimate packet sent by A.

Changes done in code

1. packet-sink.h
We have added <bits/stdc++.h> library to use c++ stl data strutures
A vector of packet pointers is created as a public variable in PacketSink class.(To store captured packets)

2. packet-sink.cc
Modified "void PacketSink::HandleRead (Ptr<Socket> socket)" to push the received packet in the above created data structure.

3. lte-sl-out-of-covrg-comm.cc
Added a replay function 
	Built a socket for broadcasting the packet
	Sent the packet
In main function
	Added a malicious node
	Set the associated components: Phy,Mac,IP layer components
	Changed the time of original sender's application for which it remains on to send only one packet
	Scheduled the replay function at t=4
