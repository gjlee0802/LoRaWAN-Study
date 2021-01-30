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


### Frame Structure   
http://www.techplayon.com/lora-long-range-network-architecture-protocol-architecture-and-frame-formats/   

### MAC Layer   
https://m.blog.naver.com/PostView.nhn?blogId=tnseo444&logNo=221140719936&proxyReferer=https:%2F%2Fwww.google.co.kr%2F   

### OTAA & ABP communication   
http://www.techplayon.com/lora-device-activation-call-flow-join-procedure-using-otaa-and-abp/   

### LoRaWAN Specification - LoRa Alliance
https://lora-alliance.org/wp-content/uploads/2020/11/LoRaWAN-1.0.4-Specification-Package_0.zip

### LoRaWAN Classes
https://www.thethingsnetwork.org/docs/lorawan/classes.html
