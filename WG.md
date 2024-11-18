# WireGuard Config
#### Server Config
ก่อนอื่นก็เข้า [WireGuard](https://www.wireguardconfig.com)  เข้าไป gen key

![image](https://github.com/user-attachments/assets/122c352a-ff4d-42ec-ade2-e5be65db0edd)

เสร็จละก็เข้า mkt บน IDC ไปหน้า wireguard -> peer

![image](https://github.com/user-attachments/assets/c15a10e5-d3b9-4c47-822b-accec9f2a04e)

sort ตาม allow address ใช้ตัวสุดท้ายถึง .251 ก็ สร้างเพิ่ม .250

![image](https://github.com/user-attachments/assets/19c1fad4-96eb-4884-b2b2-a8491058f363)

เอา public key กับ private key // ip ของฝั่ง client มาใส่

ในรูปนี้เป็น allow address เฉยๆ ใส่ให้เกินที่ใช้จริงได้ เช่นฝั่งนั้นเป็น 10.1.xx.xx หลายๆวง ก็ใส่ 10.0.0.0/8 ไปเลยอันเดียวจบ ส่วนจะต้องส่ง traffic อะไรไปทาง vpn บ้าง เด่วไปทำใน ip route อีกที

![image](https://github.com/user-attachments/assets/65c03459-9454-466a-9392-d0ada6ff1daf)


#### Client Config

![image](https://github.com/user-attachments/assets/0437c3a9-b7be-4e14-9d50-b84908df4d5c)

นำ private จากที่เรา gen 
เสร็จละกด OK ได้เลย ตัว public key มันจะ gen ให้เอง ** keepalive ต้องใส่ด้วย เพื่อให้มันสร้าง connection ทุกๆช่วงเวลา xx:xx:xx

![image](https://github.com/user-attachments/assets/293eb99f-7975-4165-a49e-56eb3d4f4f24)

เสร็จละไปหน้า peer ใส่ ข้อมูลของฝั่ง server ip/port/public key

![image](https://github.com/user-attachments/assets/246578b9-9b81-43d9-9e9e-5c50886e1aa4)

ตรง allow address ก็เหมือนเดิม ใส่เยอะกว่าที่ใช้จริงได้ พี่กิฟท์ใส่ 0.0.0.0/0 ก็คือ allow ทั้งหมด ที่วิ่งผ่าน vpn อันนี้มา
เราสามารถไปทำ policy อื่นๆเพิ่มเติมใน access rule ของ firewall อีกทีได้นะ ผ่าน allow address มาละ มันจะไปเข้า firewall ต่อ
ขั้นสุดท้ายคือทำ ip route ที่ฝั่ง client

![image](https://github.com/user-attachments/assets/197af26e-20ce-4854-8a0b-eeffd7e25277)

192.168.80.254 คือ ip wg ของฝั่ง server
192.168.80.250 คือ ip wg ของฝั่ง client

![image](https://github.com/user-attachments/assets/ab7f25d1-6b8c-49df-96d7-383e12b332a7)

![image](https://github.com/user-attachments/assets/ed553ece-fe30-41d5-8514-a60682bb08ca)

