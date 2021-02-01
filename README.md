# LoRaWAN-Study

### LoRa vs LoRaWAN – What is the difference?

People may mean LoRaWAN when they talk about LoRa. But in reality, they are different.   
- LoRa contains only the link layer protocol which is perfect to be used in P2P communications between nodes.   
  - They exist in the PHY (Physical) layer only which enables long-range communication link.   
  - The PHY layer defines how the electronic signal is modulated which is connected to a data link layer. The data link layer detects changes in the PHY layer and establishes a protocol to send data to adjacent nodes.   
- On the other hand, LoRaWAN is a media access control (MAC) layer protocol that is built on top of LoRa. It includes the network layer too which allows it to be possible to send information to any base station that is already connected to a cloud platform.   
  - LoRaWAN is the MAC sub-layer which is designed for large-scale public networks with a single operator.   
  - LoRaWAN can work in different frequencies by just connecting the right antenna to its socket    

**In simpler terms, LoRa is the PHY layer while LoRaWAN is the data link layer. They come together to comprise the LPWA networking technology stack.**   


### LoRa/LoRaWAN Gateway
- Single Channel Gateway   
A single-channel gateway is a LoRa device that acts as a gateway by forwarding LoRa packets to the network. As it's usually built using a SX1272/SX1276 instead of SX1301/SX1257, it's a lot cheaper than a full gateway, making it a favorite choice for people to start with LoRaWAN. However, single-channel gateways are extremely limited compared to a real gateway. Single-channel gateways often lead to undesired design choices for solutions that you might build and can hurt the LoRaWAN server.

- Multichannel Gateway   
Multichannel LoRaWAN gateway is the real LoRa Alliance compliance gateway which is powered by SX1301 or others. Single-channel gateways can only receive on one channel and one spreading factor at the same time, whereas a full gateway can receive on eight channels (some even ten) and six spreading factors at the same time.
8-Channel example : http://vctec.co.kr/product/8%EC%B1%84%EB%84%90-lora-%EA%B2%8C%EC%9D%B4%ED%8A%B8%EC%9B%A8%EC%9D%B4-hat-%ED%82%A4%ED%8A%B8-sx1301-8-channel-lora-gateway-hat-with-lora-and-/15569/    

### What is Spreading Factor(SF)?
The spreading factor (SF) impacts the communication performance of LoRa, which uses an SF between 7 and 12. A larger SF increases the time on air, which increases energy consumption, reduces the data rate, and improves communication range. For successful communication, as determined by the SF, the modulation method must correspond between a transmitter and a receiver for a given packet.

### LoRaWAN Device Classes
https://www.thethingsnetwork.org/docs/lorawan/classes.html

### Frame Structure   
http://www.techplayon.com/lora-long-range-network-architecture-protocol-architecture-and-frame-formats/   

### MAC Layer   
https://m.blog.naver.com/PostView.nhn?blogId=tnseo444&logNo=221140719936&proxyReferer=https:%2F%2Fwww.google.co.kr%2F   

### OTAA & ABP communication   
http://www.techplayon.com/lora-device-activation-call-flow-join-procedure-using-otaa-and-abp/   

### LoRaWAN Specification - LoRa Alliance
https://lora-alliance.org/wp-content/uploads/2020/11/LoRaWAN-1.0.4-Specification-Package_0.zip

### LoRaWAN Regional Parameters
https://lora-alliance.org/wp-content/uploads/2020/11/RP_2-1.0.2.pdf

