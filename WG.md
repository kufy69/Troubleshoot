# อ่าน SIP Message
## ตัวอย่าง SIP Message 
```
INVITE sip:bob@10.1.1.2:5060 SIP/2.0
Via: SIP/2.0/UDP 10.1.1.1:5060;branch=z9hG4bK7765432
From: Alice <sip:alice@10.1.1.1>;tag=123456
To: Bob <sip:bob@10.1.1.2>
Call-ID: abc123@10.1.1.1
CSeq: 1 INVITE
Contact: <sip:alice@10.1.1.1:5060>
Content-Type: application/sdp
Content-Length: 158

v=0
o=alice 123456 789012 IN IP4 10.1.1.1
s=Call with Bob
c=IN IP4 10.1.1.1
t=0 0
m=audio 49172 RTP/AVP 0
a=rtpmap:0 PCMU/8000
```

### 1. Request Line:
```
INVITE sip:bob@10.1.1.2:5060 SIP/2.0
```
 - INVITE คือ ประเภทของ request (method) ใช้เริ่มต้นการโทร
 - bob@10.1.1.2:5060 คือ ปลายทางที่ต้องการติดต่อ (IP และ port)
 - SIP/2.0 คือ เวอร์ชันของโปรโตคอล SIP

### 2. Via Header:
```
Via: SIP/2.0/UDP 10.1.1.1:5060;branch=z9hG4bK7765432
```
  - บอกเส้นทางที่ message นี้ผ่านมา
  - UDP คือ โปรโตคอลที่ใช้ส่ง
  - branch คือ ID ที่ใช้ระบุ transaction นี้

### 3. From Header:
```
From: Alice <sip:alice@10.1.1.1>;tag=123456
```
  - แสดงผู้ส่ง message
  - tag ใช้ระบุ dialog นี้

### 4. To Header:
```
To: Bob <sip:bob@10.1.1.2>
```
  - แสดงผู้รับ message

### 5. Call-ID:
```
Call-ID: abc123@10.1.1.1
```
  - เป็น ID เฉพาะสำหรับการโทรนี้
  - ใช้จับคู่ request และ response ของการสนทนาเดียวกัน

### 6. CSeq (Command Sequence):
```
CSeq: 1 INVITE
```
  - เลขลำดับของ request
  - ใช้จับคู่ request กับ response
