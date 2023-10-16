# Jarkom-Modul-Hands-On

#### Muhammad Rafi Insan Fillah (5025211169)

## TCP

### 1. What is the IP address and TCP port number used by the client computer (source) that is transferring the alice.txt file to gaia.cs.umass.edu? 

![image](https://github.com/Mengz04/Jarkom-Modul-Hands-On/assets/78022264/f5b43999-11de-4e45-ab48-c4e8382d219b)

The client IP address is 192.168.86.68 and the source port is 55639

### 2. What is the IP address of gaia.cs.umass.edu? On what port number is it sending and receiving TCP segments for this connection?

![image](https://github.com/Mengz04/Jarkom-Modul-Hands-On/assets/78022264/30ce5a5a-e371-4395-8a5d-54a39653acc9)

The gaia IP address is 128.119.245.12 and the source port is 80

### 3. What is the sequence number of the TCP SYN segment that is used to initiate the TCP connection between the client computer and gaia.cs.umass.edu?. What is it in this TCP segment that identifies the segment as a SYN segment? Will the TCP receiver in this session be able to use Selective Acknowledgments (allowing TCP to function a bit more like a “selective repeat” receiver, see section 3.4.5 in the text)?

![image](https://github.com/Mengz04/Jarkom-Modul-Hands-On/assets/78022264/170ad776-3669-453c-b7ec-f97e083ec063)


The sequence number (raw) is 4236649187. The identifying segment is the flags that is 0x002 (SYN). From the follow TCP stream there are no SACK options, so the following packet cannot use Selective Acknowledgments.

### 4. What is the sequence number of the SYNACK segment sent by gaia.cs.umass.edu to the client computer in reply to the SYN? What is it in the segment that identifies the segment as a SYNACK segment? What is the value of the Acknowledgement field in the SYNACK segment? How did gaia.cs.umass.edu determine that value? 

![image](https://github.com/Mengz04/Jarkom-Modul-Hands-On/assets/78022264/336bbf88-3486-424d-86ba-cb6d42651d42)


The sequence number (raw) is 1068969752. The identifying segment is the flags that is 0x012 (SYN, ACK). The value is 0x012. The SYN-ACK flag value (0x12) is a result of setting both the SYN and ACK flags in the TCP header to 1 (indicating they are active), This is a standard part of the TCP protocol and is used to establish a connection in a reliable and synchronized manner.

### 5. What is the sequence number of the TCP segment containing the header of the HTTP POST command? How many bytes of data are contained in the payload (data) field of this TCP segment? Did all of the data in the transferred file alice.txt fit into this single
segment?

![image](https://github.com/Mengz04/Jarkom-Modul-Hands-On/assets/78022264/0c9e4d65-ee30-446c-8445-4c51e8391b20)

The sequence number (raw) is 4236801228 with 1385 bytes payload

### 6. Consider the TCP segment containing the HTTP “POST” as the first segment in the data transfer part of the TCP connection.
 - At what time was the first segment (the one containing the HTTP POST) in the data-transfer part of the TCP connection sent?
 - At what time was the ACK for this first data-containing segment received?
 - What is the RTT for this first data-containing segment?

![image](https://github.com/Mengz04/Jarkom-Modul-Hands-On/assets/78022264/eb831df5-9359-4970-b9d6-5d49bbf4f503)

![image](https://github.com/Mengz04/Jarkom-Modul-Hands-On/assets/78022264/14a304d8-0b7c-4d69-b68a-11246b840e11)


first segment arrival is at Feb  3, 2021 09:43:26.840557000 SE Asia Standard Time, the response segment is at Feb  3, 2021 09:43:26.885500000 SE Asia Standard Time, so the EstimatedRTT is more or less 0.449 second.

### 7. What is the length (header plus payload) of each of the first four data-carrying TCP segments?

![image](https://github.com/Mengz04/Jarkom-Modul-Hands-On/assets/78022264/5a15ac2e-8e87-4782-94f5-7397d081c85b)

![image](https://github.com/Mengz04/Jarkom-Modul-Hands-On/assets/78022264/3647bd22-9e5f-44a3-9b13-6e4d2b058794)

The first segment has length of 1437 bytes, the response is 829 bytes

## UDP

### 1. Select the first UDP segment in your trace. What is the packet number4 of this segment in the trace file? What type of application-layer payload or protocol message is being carried in this UDP segment? Look at the details of this packet in Wireshark. How many fields there are in the UDP header? What are the names of these fields? 

![image](https://github.com/Mengz04/Jarkom-Modul-Hands-On/assets/78022264/0db2b019-9280-403b-a44f-06483af111bb)

Packet number 5, application-layer SSDP carries NOTIFY messages in its application-layer payload. There are 5 primary fields that is source port, destination port, length, checksum, and checksum status.

### 2. By consulting the displayed information in Wireshark’s packet content field for this packet (or by consulting the textbook), what is the length (in bytes) of each of the UDP header fields?

![image](https://github.com/Mengz04/Jarkom-Modul-Hands-On/assets/78022264/f9cff2ce-1255-4bda-b2b3-c18d5f6b5995)

The first packet payload length is 275 bytes

### 3. The value in the Length field is the length of what?. Verify your claim with your captured UDP packet. 

The total number of bytes in the packet

### 4. What is the maximum number of bytes that can be included in a UDP payload?

![image](https://github.com/Mengz04/Jarkom-Modul-Hands-On/assets/78022264/a0ae3434-51d4-4d73-a836-0355f2c0badd)

with a common MTU of 1500 bytes, the UDP SSDP payload can be up to 1472 bytes (1500 bytes MTU - 20 bytes for IP header - 8 bytes for UDP header). 

### 5. What is the largest possible source port number?

Source port numbers are 16-bit values, so they can range from 0 to maximum 65535

### 6. What is the protocol number for UDP?

![image](https://github.com/Mengz04/Jarkom-Modul-Hands-On/assets/78022264/f45b79a5-eb3e-410d-b6b8-f126a4f663d4)

The protocol number for UDP is 17

### 7. Examine the pair of UDP packets in which your host sends the first UDP packet and the second UDP packet is a reply to this first UDP packet. What is the packet number5 of the first of these two UDP segments in the trace file? What is the packet number6 of the second of these two UDP segments in the trace file? Describe the relationship between the port numbers in the two packets. 

![image](https://github.com/Mengz04/Jarkom-Modul-Hands-On/assets/78022264/dd978a9e-a050-4f76-9b9a-6bda7fe854d8)

The UDP packet that has response to it is packet number 15 and the response is 17. The source port for the first packet is 53 and the destination port is 58350, the response packet has it in reverse (source port 58350 & destination port 53).
