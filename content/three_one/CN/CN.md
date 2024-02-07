# Unit-1
## Physical Layer
### Transmission medium
It's defined as anything that carries information from source to destination
Types:
1. Guided (Wired)
	1. Twisted Pair Cable
	2. Coaxial Cable
	3. Fibre Optic Cable
2. Unguided (Wireless)
	1. Radio Waves
	2. Micro Waves
	3. Infrared
## Network Hardware
**Repeater**: Used to regenerate signal over long distances for good signal strength\
**HUB**: A central device that connects multiple computers on the same network\
**Bridge**: Used to connect two different LANs (Local Area Network)\
**Switch**: Connects devices in a network to each other\
**Router**: Routes the packet from source address to destination address through IP address
## OSI (Open System Interconnection)
It's an abstract model, it consists of 7 layers:
1. Application
2. Presentation
3. Session
4. Transport
5. Network
6. Data Link
7. Physical

### Physical Layer
Responsible for physical connection between two devices, information is in the form of bits\
**Functions**:
1. Bit Synchronization
2. Bit Rate Control
3. Physical topology: bus, star, mesh, ring
4. Transmission Media: simple, half-duplex, full-duplex
### Data Link Layer
Responsible to transmit error free data and also reliable and efficient communication. Here data is represented as frames.\
**Functions**:
1. Framing
2. Error Control
3. Flow Control
4. Access Control
### Network Layer
Responsible for routing the packets from source to destination. Here data is represented as packets.\
**Functions**:
1. Logical Addressing
2. Fragmentation
### Transport Layer
Provides logical communication between the application of different hosts. Gives acknowledgement for successful data transmission. Here data is represented as segments\
**Functions**:
1. End-to-End delivery
2. Reliable delivery
### Session Layer
Responsible for session establishment, maintenance and transmission\
**Functions**:
1. Synchronization
### Presentation Layer
Specifies how to present the data from source to destination\
**Functions**:
1. Translation
2. Encryption / Decryption
3. Compression
### Application Layer
It contains applications itself, which produce data that will be transmitted over the network\
**Services**:
1. Email Services
2. File transfer

## TCP / IP Model
It's an implementation model, It has 4 layer:
1. Application
2. Transport
3. Network
4. Data Link

![[osi_tcp.png]]
## Difference b/w TCP / IP and OSI
| OSI | TCP / IP |
| ---- | ---- |
| It's a reference Model | It's an implementation Model |
| It consists 7 layers | It consists 4 layers |
| Session and Presentation layer are separated explained | Combines both session and presentation layer |
| Model is designed before the protocol | Protocol is implemented before the model |
| Protocol independent standard | Protocol depended standard |
# Unit-2
## Data Link Layer
**Functions**:
1. Framing
2. Flow control
3. Access Control
4. Error Control
5. Physical addressing
## Framing
Link layer moves bits in the form of frames from source to destination. Each frame is distinguishable from one another. Framing adds both the sender and receiver address.\
There are two types of framing:
1. Fixed size framing
2. Variable size framing
### Fixed Size Framing
There is no need to define boundaries of the frames, the size the frame itself acts as an delimiter. All the frames will be of the same fixed size.
### Variable Size Framing
Here we need to define end of frame and beginning of the next frame.\
There are two approaches:
1. Character Oriented
2. Bit Oriented
### Character Oriented Protocol
A frame contains header, trailer which contains source, destination addresses and error correction. A new 8-bit or 1 byte flag is added to the frame at the beginning and end of the frame.\
Character oriented protocol was popular when only text was exchanged through data link layer. Any patter used for the flag could also be part of the text message. If this happens the receiving computer assumes the message is a flag, to avoid this byte stuffing is used.
#### Byte stuffing
It's a process of adding an extra byte when ever there is a flag or escape character in the message, which tells to skip that flag or esc character.
![[byte_stuffing.png]]
### Bit Oriented Protocol
We have a delimiter at the beginning and end of the frame. Most protocols use a 8-bit pattern as a flag. Then again that flag could be the actual data so we use bit stuffing to avoid this confusion.
#### Bit Stuffing
An extra bit "0" is added when the data contains when five consecutive "1"s followed by a "0".
![[bit_stuffing.png]]
## Error Detection and Correction
Types of errors:
1. Single bit error
2. Burst error
### Error Detection
Two ways:
1. Parity check
2. Cyclic Redundancy Check
#### Parity Check
A parity bit is added to the data to check for any error. If it's a even parity the number of ones in the data should be even, if there are even 1s in data then "0" is added and if there are odd 1s in the data "1" is added. The receiving computer checks the at the number of 1s and decides if there is error or not.\
When more than 1 bit is corrupted parity check is useless.
![[single_bit_error.png]]
#### Cyclic Redundancy Check
Here the data is divided by a polynomial and the remainder is added to the data and sent to the receiving computer. The receiving computer then divides that data with the same polynomial, the remainder should be zero if not the data corrupted and there is an error.
![[crc.png]]
### Error Correction
Two ways:
1. **Backward Error Correction**: When an error is detected the receiving computer asks to resend the data
2. **Forward Error Correction**: When an error is detected the receiving computer auto corrects the error using error-correcting code.\
Backward Error Correction is useful when retransmission is inexpensive like fibre optics.
## Elementary Data Link Protocols
Protocols of data link layer enables it to perform it's basic function: framing, error control, flow control.\
Types:
1. For Noise-less Channels
	1. Simplex
	2. Stop-and-wait
2. For Noisy Channels
	1. Stop-and-wait ARQ
	2. Go-back-N ARQ
	3. Selective Repeat ARQ
### Simplex
It's a hypothetical protocol designed for unidirectional data transmission over an ideal channel through which data transmission will can never go wrong. The sender sends all the available data and receiver process all the data at once. Since it's hypothetical there is no flow control and error control.
### Stop-and-Wait
It's for noise-less channels. It provides unidirectional data transmission without any error-control facilities. However it provides flow-control facilities so that the fast sender does not clog the slow receiver. Sender can only send a frame when it receives the acknowledgement that receiver is available for further data.
### Stop-and-Wait ARQ
Stop-and-Wait ARQ (Automatic Repeat Request) is a variation of above protocol but with error control facility appropriate for noisy channels. The sender keeps the copy of the frames and waits for the acknowledgement from the receiver for a certain time, if it doesn't receive any ack or neg-ack then it retransmits the frame, if positive ack is received it sends the next frame
### Go-back-N ARQ
It provides for sending multiple frames before receiving any acknowledgement of first frame. It uses a concept of sliding window so it's a sliding window protocol. The frames are sequentially numbered and finite number of frames are sent. If ack is not received all the frames are sent again.
### Selective Repeat ARQ
Same as Go-back-N ARQ but when if it doesn't receive ack for frames it only sends those frames for which the ack is not received.
# Unit-3
## Design Issues
1. Store and forward packet switching
2. Services provided to Transport layer
3. Implementation of connectionless service
4. Implementation of connection oriented service
## Routing Algorithms
types:
1. Non-adaptive
	1. Shortest Path
	2. Flooding
2. Adaptive
	1. Distance Vectoring
	2. Hierarchical Routing
	3. Link State Routing
## Congestion Control
Congestion occurs when there is an overload in the network. When more number of packets are being sent then the network capacity. Congestion Control either prevents this from happening or solves the congestion.\
**Categories**:
1. Open Loop Congestion Control
	1. Retransmission Policy
	2. Window Policy
	3. Acknowledgement Policy
	4. Discarding Policy
	5. Admission Policy
2. Closed Loop Congestion Control
	1. Back Pressure
	2. Choke Packet
	3. Implicit Signaling
	4. Explicit Signaling

**Congestion Control Algorithms:**
1. Leaky Bucket
2. Token Bucket
## Quality of Service
Its a internetworking issue which can be defined as a flow which is required for communication.\
**Flow Characteristics:**
1. Reliability
2. Delay
3. Jitter
4. Bandwidth

# Unit-4
## TCP (Transmission Control Protocol)
Responsible for delivery of a message from one process to another. A process is an application program running on a host\
Three protocols:
1. TCP
2. UDP
3. SCTP (Stream Control Transmission Protocol)
![[tcp_header.png]]

**Six flags:**
1. URG - Urgent Pointer is valid
2. FIN - Terminate the connection
3. ACK - Acknowledgement is valid
4. SYN - Synchronize
5. RST - Reset the Connection
6. PSH - Request for PUSH
## UDP (User Datagram Protocol)
![[udp_header.png]]
## TCP and UDP differences
![[tcp_udp.png]]
# Unit-5
## E-mail Architecture
Four Scenarios:
1. **First Scenario**:
![[email_one.png]]
2. **Second Scenario**:
![[email_two.png]]
3. **Third Scenario**:
![[email_three.png]]
4. **Fourth Scenario**:
![[email_four.png]]
## DNS (Domain Naming System)
DNS is a directory service that provides a mapping between the name of a host on the network and its numerical address. DNS is a service that translates the domain name into IP addresses. This allows the users of networks to utilize user-friendly names when looking for other hosts instead of remembering the IP addresses.\
Three types of Domains:
1. Generic
2. Country
3. Inverse

**Generic**: .org, .com, .dev and so on\
**Country**: .in, .us, .ca, .uk\
**Inverse**: When the sever wants to know the host of an address to know it's authorization it request it's name. This is called inverse domain when we have and address and want to know the name