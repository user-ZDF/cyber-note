# The OSI and TCP/IP

Study notes on network basics.

## 1. What is the OSI model?

The OSI (Open Systems Interconnection) model is a way to think about how data moves between two devices on a network. It splits the process into seven parts. Each part has a task. This helps people understand, build and fix networks. It also helps companies make equipment and software work together.

The OSI model is mostly used for teaching and fixing problems. The Internet is built using the TCP/IP model instead.

## 2. The seven layers

The layers go from the bottom to the top. The bottom is Layer 1. The top is Layer 7.

 Layer  Role  Examples Data unit 


7 Application  Gives network services to programs  HTTP, DNS, SMTP , Data 

 6 Presentation Changes data into formats: like encoding, compression, encryption | UTF-8, JPEG, TLS (see note) | Data |

 5  Session  Starts, controls. Ends connections between programs  RPC NetBIOS Data 

 4  Transport  Sends data between programs using ports  TCP UDP  Segment (TCP) / Datagram (UDP)

3 Network Uses addresses and routes data between networks  IP ICMP routers  Packet 

2 Data Link  Sends data between devices on the network (MAC addresses)  Ethernet, Wi-Fi switches Frame 

 1  Physical  Sends bits over a network medium  Cables, fiber, radio  Bits 

**Note:** TLS does not fit perfectly into the OSI model. It is often connected with Layers 5 and 6.

**Memory aid (Layer 1 to 7):** Please Do Not Throw Sausage Pizza Away (Physical, Data Link, Network, Transport, Session, Presentation, Application).

## 3. Decapsulation

When a device sends data each layer puts its information on top of the data from the layer above. This is called encapsulation. The information includes things like port numbers, IP addresses or MAC addresses.

On the receiving side the data is step by step. This is called decapsulation. Each layer looks at its information removes it and passes the data to the layer.

 Layer  Data unit  What the layer adds 

 4. Transport  Segment  TCP header (source and destination ports, sequence numbers)

 3. Network  Packet  IP header (source and destination IP addresses)

 2. Data Link Frame  Ethernet header (MAC addresses) and trailer (error check)

 1. Physical  Bits  Nothing added: the frame is turned into signals 

## 4. OSI vs TCP/IP

TCP/IP is the model used for the Internet. It has four layers. These cover the seven OSI layers like this:

 TCP/IP layer  OSI layers covered

Application 7 Application, 6 Presentation, 5 Session 

Transport ( 4 Transport )

Internet ( 3 Network )

 Network Access (Link)  2 Data Link, 1 Physical 

- OSI has seven layers. It is a way to think about how networks work.

- TCP/IP has four layers. It is the system used on the Internet.

## 5. Switch vs router

Device OSI layer  Forwards traffic based on  Role

Switch  2. Data Link MAC addresses  Connects devices in the network 

 Router  3. Network  IP addresses  Connects networks. Sends packets between them

Some switches work with more layers but a regular switch works on Layer 2.

## 6. Example: opening a website


1. Application (7): the browser finds the IP address of the website using DNS. Then it gets ready to send an HTTP request.

2. Presentation / Session (6 and 5): TLS makes the connection secure (HTTPS). It is often connected with these layers.

3. Transport (4): TCP starts a connection with a three-step process (SYN, SYN-ACK, ACK). It sends the data to port 443.

4. Network (3): IP adds the source and destination IP addresses. Routers send the packet toward the server.

5. Data Link (2): Ethernet or Wi-Fi puts the packet into a frame that is sent to the device ( the router).

6. Physical (1): the frame is sent as light or radio signals.

In order: DNS TCP handshake TLS handshake then the HTTP request. On the server side each layer takes off its header until the web server gets the request.

## 7. Key points

- Layers go from the bottom. Physical is Layer 1 and Application is Layer 7.

- Transport is above Network.

- The OSI Network layer is the same as the TCP/IP Internet layer. It is not the same, as the TCP/IP Network Access layer.

- Each layer adds a header when sending (encapsulation) and removes it when receiving (decapsulation).

- A switch works on Layer 2 (MAC addresses). A router works on Layer 3 (IP addresses)
