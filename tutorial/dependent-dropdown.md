การสร้าง Dropdown เพื่อสร้างตัวเลือก จังหวัด, อำเภอ, ตำบล
---------------------------
ในตัวอย่างนี้จะเป็นใช้ widget [Dependent Dropdown Widget](http://demos.krajee.com/widgets#depdrop) ของ krajee เพราะสามารถใช้งานได้ง่ายๆ แค่สร้าง action ตามที่ widget กำหนดโดยที่ไม่ต้องไปยุ่งกับ javascript มากมายเพราะ widget ทำไว้ให้หมดแล้ว เรามีหน้าที่ `config` ให้มันรู้ว่า action ใหนที่จะไปดึงข้อมูลอำเภอ action ใหนจะไปดึงข้อมูลตำบล

![dependent](/images/depdrop.png)

## หลักการทำงาน
![deropdown](/images/dropdown-flow.png)


- ขั้นตอนแรก จังหวัดเราจะทำการใช้ dropdownList แบบธรรมดาและคิวรีข้อมูลขึ้นมาเพื่อกำหนดค่าให้กับ dropdownList จังหวัดเพื่อแสดงผล
![deropdown](/images/province.png)

- เมื่อมีการคลิกเลือกจังหวัด ก็จะทำการส่งข้อมูลรหัสจังหวัด ที่เลือกไปที่ `actionGetAmphur()` เพื่อทำการค้นหาอำเภอ
 และจะส่งข้อมูลกลับมาในรูปแบบ `json` ไปให้ widget และนำไปแสดงผลที่ DropdownList อำเภอ
 ![deropdown](/images/amphur.png)
- เมื่อทำการเลือกอำเภอ ก็จะทำการส่งข้อมูลรหัสอำเภอที่เลือกไปที่ `actionGetDistrict()` เพื่อทำการค้นหาข้อมูลตำบล และส่งข้อมูลกลับให้ widget ในรูปแบบของ `json`เพื่อนำไปแสดงผลต่อที่ dropdownList ตำบล
![deropdown](/images/district.png)





 ให้หลังจากนั้นเมื่อมีการคลิกที่ จังหวัดและทำการเลือกจังหวัด จะมีการเรียกไปที่ actionGetAmphur() และส่งค่า รหัสจังหวัดไปด้วยเพื่อทำการค้นหาข้อมูลอำเภอของจังหวัดนี้ จากนั้น action จะส่งข้อมูล json อำเภอกลับมาและ widget จะทำการใส่ข้อมูลเข้าไปที่ dropdownList อำเภอให้


ตัวเลือกจังหวัดเราจะใช้ dropdownList ธรรมดาโดยคิวรีข้อมูลจังหวัดมาไว้ก่อนและใส่ค่าให้กับ dropdownList ปกติ และทำการกำหนดค่า id ให้กับมันด้วย