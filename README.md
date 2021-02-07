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

### Receive Windows
- Following each uplink transmission, the end-device SHALL open one or two receive windows (RX1 and RX2);   
if no packet destined for the end-device is received in RX1, it SHALL open RX2.    
The receive windows start times are defined using the end of the transmission as a reference, see follow Figure.   

- 번역: RX1에 최종 장치로 향하는 패킷이 수신되지 않으면 RX2를 열어야 한다.    
수신 윈도우 시작 시간은 전송 끝을 기준으로 정의된다(그림 참조).   
![End-device-receive-slot-timing](https://user-images.githubusercontent.com/49184890/106476311-45bbea00-64ea-11eb-9a91-6caef31ece09.PNG)

### Receiver activity during receive windows
If a preamble is detected during one of the receive windows, the radio receiver SHOULD stay active until the downlink frame is demodulated. If a frame was detected and subsequently demodulated during the first receive window, and the frame was intended for this end-device after address and MIC (message integrity code) checks, the end-device SHALL NOT open the second receive window.   

### First receive-window channel, data rate, and start
첫 번째 수신 창 RX1은 uplink 주파수의 function인 주파수와 uplink data rate의 function인 data rate를 사용한다.   
RX1은 업링크 변조가 종료된 후 'RECEIVE_DELAY1' 초 이내에 개방되어야 한다.   
uplink와 RX1 data rates 간의 관계는 지역별로 다르며 자세한 것은 RP002 문서를 참고한다.   

### Second receive window channel, data rate, and start
두 번째 수신 창 RX2는 열린 경우 **고정으로** 구성 가능한 주파수와 data rate를 사용하며, 업링크 변조가 끝난 후 'RECEIVE_DELAY2' 초 이내에 개방되어야 한다.   
주파수 및 데이터 속도는 MAC 명령으로 수정할 수 있다. 기본 주파수와 datarate는 지역별로 다르며 자세한 것은 RP002 문서를 참고한다.   

### Receive window duration
수신 창의 지속 시간은 적어도 uplink 변조가 끝난 후 RECEIVE_DELAY1 또는 RECEIVE_DELAY2에서 시작하는 **downlink preamble을 감지하기 위해 end-device의 무선 송수신기에 필요한 시간**이어야 한다.

### Frame Structure   
http://www.techplayon.com/lora-long-range-network-architecture-protocol-architecture-and-frame-formats/   

### MAC Layer   
https://m.blog.naver.com/PostView.nhn?blogId=tnseo444&logNo=221140719936&proxyReferer=https:%2F%2Fwww.google.co.kr%2F   

### MAC Commands
If present, **an FPort value of 0** indicates that the **FRMPayload contains only MAC commands**.   
A single data frame MAY contain any sequence of MAC commands, either piggybacked in the FOpts field or,    
when sent as a separate data frame, in the FRMPayload field with the FPort field set to 0.   

참고: 콘텐츠를 암호화해야 하는 MAC 명령은 별도의 데이터 프레임의 FRM 페이로드로 전송되어야 한다.   

- CID   
A MAC command consists of a command identifier (CID) of 1 octet followed by a possibly empty command-specific sequence of octets.   
![CID](https://user-images.githubusercontent.com/49184890/107111186-3d203680-6891-11eb-8001-eca5d22d91bb.PNG)

- Link Check Commands(LinkCheckReq, LinkCheckAns)   
![link_check](https://user-images.githubusercontent.com/49184890/107111052-1dd4d980-6890-11eb-8c11-289f5d49f35d.PNG)

### OTAA & ABP communication   
http://www.techplayon.com/lora-device-activation-call-flow-join-procedure-using-otaa-and-abp/   
- OTAA   
![LoRa-Call4](https://user-images.githubusercontent.com/49184890/107114718-6b127480-68ab-11eb-93df-6c66e71c17cc.png)
- Join Request Frame   
![JR_FRAME](https://user-images.githubusercontent.com/49184890/107114702-52a25a00-68ab-11eb-8fea-a5997b695371.PNG)
- Join Accept Frame   
![JA_FRAME](https://user-images.githubusercontent.com/49184890/107114710-5f26b280-68ab-11eb-95a8-66ec408f943a.PNG)
  - JoinNonce field   
  Please refer to the following documents to know additional behavior for the 'JoinNonce(AppNonce)' value in the Join Server to prevent synchronization issues related to the LoRaWAN Join Procedure.   
  https://lora-alliance.org/wp-content/uploads/2020/11/lorawan-1.0.x-join-synch-issues-remedies-v1.0.0.pdf   

  - NetID field   
  Please refer to the following documents for details.(p50)   
  https://lora-alliance.org/wp-content/uploads/2020/11/TS002-1.1.0_LoRaWAN_Backend_Interfaces.pdf
  ![스크린샷, 2021-02-07 16-45-50](https://user-images.githubusercontent.com/49184890/107140261-3dd5cd00-6964-11eb-9ab5-8a7900bba363.png)

  - DLSettings field    
  ![스크린샷, 2021-02-07 16-04-02](https://user-images.githubusercontent.com/49184890/107139400-36abc080-695e-11eb-9fc3-dc4bbb436672.png)   


### LoRaWAN Specification - LoRa Alliance
https://lora-alliance.org/wp-content/uploads/2020/11/LoRaWAN-1.0.4-Specification-Package_0.zip

### LoRaWAN Regional Parameters
https://lora-alliance.org/wp-content/uploads/2020/11/RP_2-1.0.2.pdf

