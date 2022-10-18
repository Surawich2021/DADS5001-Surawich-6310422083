![Most-Amazing-Places-To-Visit-In-Thailand](https://user-images.githubusercontent.com/77851559/196423055-445e5c90-a831-4ecf-9e68-230f46482996.jpg)






# Topic:
การท่องเที่ยวหลังวิกฤติการณ์โควิด19ฟื้นจริงหรือไม่ ? 
อุทยานแห่งชาติแห่งไหนมีศักยภาพดีที่สุด ?

# Dataset:
1.เงินรายได้อุทยานแห่งชาติ 155แห่ง 7ปีย้อนหลัง

2.จำนวนนักท่องเที่ยวอุทยานแห่งชาติ 155แห่ง 7ปีย้อนหลัง 

3.พื้นที่อุทยานแห่งชาติ 155 แห่ง 15ปีย้อนหลัง

# Question:
1.จริงหรือไม่ที่จำนวนนักท่องเที่ยวไทยและนักท่องเที่ยวต่างชาติในอุทยานแห่งชาติมีแนวโน้มเพิ่มขึ้นเรื่อย ๆในทุกๆปี (ปี 2016-2022) ?

2.จริงหรือไม่ที่อุทยานที่มีพื้นที่ใหญ่กว่าสามารถสร้างรายได้จากนักท่องเที่ยวได้มากกว่าอุทยานที่มีพื้นที่เล็กกว่า (ปี 2016-2022) ?

3.ถ้าจะจัดสรรงบประมาณเพื่อส่งเสริมการท่องเที่ยวอุทยานแห่งชาติ 10 อันดับแรกที่รัฐบาลควรส่งเสริมคือที่ไหนบ้าง (ตั้งแต่ปี 2023 เป็นต้นไป)?

# Challenge:
1.ใช้เวลาในการทำความสะอาดข้อมูลนานมากถึง80-90%ของเวลาของ project ทั้งหมด เช่น 

- Missing data (N/A)

- Duplicated data

- Space error ของ text

- ชื่ออุทยานในไฟล์ข้อมูลรายได้อุทยานและชื่ออุทยานข้อมูลนักท่องเที่ยวในแต่ล่ะปี inconsistency ทำให้ต้องใช้ข้อมูลเพิ่มเติมทาง internet มาแก้ปัญหา เพราะไม่มี business user มาช่วยตอบ โดยมีทั้งเปลี่ยนชื่ออุทยานแห่งชาติระหว่างปี ชื่อใกล้เคียงกัน ชื่อมีวงเล็บ เป็นต้น 

2.ใช้ matplotlib แสดงผลภาษาไทยใน graph ไม่ได้

3.เนื่องจากไม่มีข้อมูลงบประมาณของอุทยานแต่ล่ะแห่งในแต่ล่ะปี ผู้เขียนจึงต้องตั้งสมมติฐานว่าอุทยานที่มีพื้นที่ขนาดใหญ่กว่าอุทยานที่มีพื้นที่ขนาดเล็กย่อมจะใช้งบประมาณในการดูแลรักษามากกว่า 

และเพื่อให้สามารถเปรียบเทียบศักยภาพของอุทยานแห่งชาติแต่ล่ะอุทยานได้ จึงเปลี่ยนไปคำนวนผลตอบแทนรายได้ของอุทยานแห่งชาติต่อจำนวนนักท่องเที่ยวแทน

# Github link:

https://github.com/Surawich2021/DADS5001-Surawich-6310422083


จากสถานการณ์โควิดในรอบ3ปีที่ผ่านมา ส่งผลกระทบหนักต่อรายได้จากการท่องเที่ยวในประเทศไทยซึ่งเป็นรายได้หลักของประเทศ วันนี้เราจะมาวิเคราะห์ข้อมูลการท่องเที่ยวอุทยานแห่งชาติกันว่ามีแนวโน้มฟื้นตัวหรือไม่หลังวิกฤติโควิด19 และพื้นที่อุทยานแห่งชาติแห่งไหนที่มีศักยภาพทำรายได้ต่อหัวนักท่องเที่ยวมากที่สุด เพื่อที่จะเป็นเครื่องมือแนะนำให้กับรัฐบาลใช้เป็นแหล่งท่องเที่ยวหลักในการหารายได้จากอุทยานแห่งชาติเพื่อฟื้นฟูประเทศ
	เริ่มต้นจาก import library ที่จำเป็นในการวิเคราะห์ข้อมูลได้แก่ pandas, numpy, matplotlib, seaborn และ sklearn และเช็ค version ดังรูปที่ 1
 ![01](https://user-images.githubusercontent.com/77851559/196460560-ace4bc2c-1bf4-4d5c-aee2-41d6e2416d7a.JPG)

*รูปที่ 1*

หลังจากนั้นให้นำข้อมูลนักท่องเที่ยวอุทยานแห่งชาติมา import และวิเคราะห์เพื่อตอบคำถามแรก ว่าปัญหาโควิด19 ว่ามีผลกระทบกับจำนวนนักท่องเที่ยวอุทยานแห่งชาติมากน้อยแค่ไหน และสถานการณ์ปัจจุบันหลังยุคโควิดที่ได้มีการเปิดประเทศแล้วจำนวนนักท่องเที่ยวอุทยานแห่งชาติกลับมาเป็นปกติเหมือนก่อนยุคโควิดแล้วหรือไม่ โดยเทียบเป็นช่วงเวลาก่อนโควิด, ช่วงเวลาระหว่างโควิด และช่วงเวลาหลังโควิด และมีขั้นตอนดังต่อไปนี้ (รายละเอียดดูใน Jupyter Notebook)
	
- load traveler data.

- Check null value, Drop column no. and Change type of name to category.

- Calculate total traveler per year.

- Calculate average traveler per year and adjust format before creating bar chart.

- Plot bar chart with trend.

- Plot bar chart without trend

จะได้รูปของปริมาณเฉลี่ยของนักท่องเที่ยวต่อจำนวนอุทยานพร้อมกับเส้นแนวโน้ม ดังรูปที่ 2
![02](https://user-images.githubusercontent.com/77851559/196460971-398911b6-a6e9-4193-9078-e5a7b5e17462.JPG)

*รูปที่ 2*

เพื่อนำเสนอให้ผู้บริหารเข้าใจง่าย เราอาจปรับแต่งสีของชาร์ต และเอากราฟเส้นออกเพื่อให้เห็นความหมายของข้อมูลชัดเจนยิ่งขึ้น โดยสีเขียวหมายถึงจำนวนนักท่องเที่ยวเฉลี่ยที่เพิ่มขึ้นเมื่อเทียบกับปีก่อน และสีแดงหมายถึงจำนวนนักท่องเที่ยวเฉลี่ยที่ลดลงเมื่อเทียบกับปีก่อน ดังรูปที่ 3
![03](https://user-images.githubusercontent.com/77851559/196461186-4f51806a-a2c6-41fc-b84a-bd93a31be5aa.JPG)

*รูปที่ 3*

# Answer 1:

จะได้ข้อสรุปของคำถามแรกว่า ช่วงก่อนโควิด ปี2016-2019 จำนวนนักท่องเที่ยวจะเพิ่มขึ้นเรื่อย ๆในทุกๆปี แต่ช่วงวิกฤติโควิด19 ปี2020-2021 จำนวนนักท่องเที่ยวลดลงเป็นอย่างมาก และเพิ่งมาฟื้นตัวได้ในปี 2022 เท่านั้น

ที่นี้ลองเอาข้อมูลจำนวนในอุทยานแห่งชาติในทุกๆเดือน ตั้งแต่ปี2016-2022 มาพล๊อทดู Trend ของจำนวนนักท่องเที่ยวในแต่ล่ะเดือนว่าเป็น Seasonal หรือไม่ โดยมีขั้นตอนดังต่อไปนี้ (รายละเอียดดูใน Jupyter Notebook)

- Drop total traveler column.

- Combine all traveler data into total traveler file.

- Check null value.

- Replace null value to zero because no traveler visited in the natural park.

- Recheck total traveler data.

- Create array for counting the column.

- Create array for collecting the first row of data. (Kao-yai Natural Park)

- Plot bar chart with trend.

![04](https://user-images.githubusercontent.com/77851559/196461301-9fb25c53-e2ed-4524-ae8e-d761c7b48636.JPG)

*รูปที่ 4*

จากรูปที่ 4 ตัวอย่างจำนวนนักท่องเที่ยวของอุทยานแห่งชาติเขาใหญ่ จะพบว่า ไม่ว่าจะเป็นช่วงก่อนโควิด ปี2016-2019 ช่วงวิกฤติโควิด19 ปี2020-2021 หรือช่วงหลังวิกฤติโควิด19 จำนวนนักท่องเที่ยวจะสูงที่สุดในเดือนธันวาคมของทุกๆปี และมีความเป็น Seasonal อย่างชัดเจนตามรูปในกราฟเส้น Time Series

เพื่อตอบคำถามที่สองว่า จริงหรือไม่ที่อุทยานที่มีพื้นที่ใหญ่กว่าสามารถสร้างรายได้จากนักท่องเที่ยวได้มากกว่าอุทยานที่มีพื้นที่เล็กกว่า (ปี 2016-2022)?  เพื่อใช้ในการบริหารจัดการพื้นที่เขตอุทยานแห่งชาติ จากสมมติฐานที่ว่าเมื่อขยายพื้นที่เขตอุทยานแห่งชาติย่อมต้องเพิ่มงบประมาณในการบริหารพื้นที่เขตอุทยานตามไปด้วย ดังนั้นถ้ารายได้ของอุทยานไม่เพิ่มตามพื้นที่เขตอุทยานที่เพิ่มขึ้นย่อมจะทำให้สิ้นเปลืองงบประมาณของรัฐบาลโดยใช่เหตุ จึงไม่สมควรขยายพื้นที่อุทยานแห่งชาติในอนาคตและเอาประโยชน์จากที่ดินเหล่านั้นไปทำอย่างอื่นที่มีมูลค่ามากกว่า
ให้นำข้อมูลพื้นที่อุทยานแห่งชาติ และรายได้อุทยานแห่งชาติมา import และวิเคราะห์ตามขั้นตอนดังต่อไปนี้ (รายละเอียดดูใน Jupyter Notebook)

Area analysis data

- Load the area data.

- Drop column ปี, จังหวัด, พื้นที่(ไร่) and Check null value.

- Rename column หน่วยงาน,พื้นที่(ตร. กม.) and Change type of name to category.

- Check null value.

- Check duplicate data.

- Sort data by name and area and Remove duplicate data.

- Descending sort data by area.

- Select top10 maximum area.

- Plot top10 maximum area the natural park in bar chart format.

Revenue analysis data

- Load the revenue data.

- Check null value, Change type of column Name and Choose only column Name and Total.

- Join revenue data from every year.

- Check null value and Replace it by zero because no revenue in the natural park.

- Calculate total revenue from every year and select column only Name and Total.

- Descending sort the natural park by total revenue.

- Select top10 maximum total revenue the natural park.

- Plot top10 maximum total revenue the natural park in bar chart format.

Revenue & Area analysis data

- Join revenue data and area data

- Delete null value row.

- Subplot all necessary graph for correlation analysis between total revenue and area.

- Plot the jointplot of total revenue and area.

- Plot kdeplot of total revenue and area.

- Calculate correlation between total revenue and area.

- Plot the heatmap of total revenue and area.

- Plot the pairplot of total revenue and area.

- Plot the lmplot of total revenue and area.

![05](https://user-images.githubusercontent.com/77851559/196461489-bde0fc9f-d2aa-4c3c-8369-aa1fd4213c06.JPG)

*รูปที่ 5*

จากรูปที่ 5 จะพบว่า TOP10 อุทยานแห่งชาติที่มีพื้นที่สูงสุดได้แก่
1.	แก่งกระจาน
2.	ทับลาน
3.	เขาใหญ่
4.	ดอยภูคา
5.	เขื่อนศรีนครินทร์
6.	เขาแหลม
7.	ตะรุเตา
8.	ศรีลานนา
9.	ทุ่งแสลงหลวง
10.	ห้วยน้ำดัง

![06](https://user-images.githubusercontent.com/77851559/196461626-32c515e0-58ea-488b-bb43-ce9930083dc1.JPG)

*รูปที่ 6*

จากรูปที่ 6 จะพบว่า TOP10 อุทยานแห่งชาติที่ทำรายได้สะสมสูงสุดตั้งแต่ปี 2016-2022 ได้แก่
1.	หมู่เกาะพีพี
2.	อ่าวพังงา
3.	หมู่เกาะสิมิลัน
4.	หมู่เกาะเสม็ด
5.	เขาใหญ่
6.	เอราวัณ
7.	ดอยอินทนนท์
8.	เขาสก
9.	หมู่เกาะลันตา
10.	หมู่เกาะช้าง

ลองใช้ seaborn พล๊อตกราฟหลายๆแบบ เพื่อหาความสัมพันธ์ระหว่างรายได้กับพื้นที่ ดังรูปที่7 พบว่าไม่มีความสัมพันธ์ไปในแนวทางเดียวกันเลย

![07 1](https://user-images.githubusercontent.com/77851559/196462011-89b28d53-abbf-4830-b908-d52d93999535.JPG)
![07 2](https://user-images.githubusercontent.com/77851559/196462157-f51f8efb-af9d-4114-a8ae-8b88662cc5ed.JPG)
![07 3](https://user-images.githubusercontent.com/77851559/196462272-4a7f4862-71c3-4bcc-a9e3-6a36b4c28a22.JPG)
![07 4](https://user-images.githubusercontent.com/77851559/196462402-d418ef5f-2b4a-4333-bd14-4e91d3ccc878.JPG)
![07 5](https://user-images.githubusercontent.com/77851559/196462553-b8af7425-03fa-414f-864f-8e32ac387cfb.JPG)
![07 6](https://user-images.githubusercontent.com/77851559/196462670-3acab858-554f-4745-99c8-3b6b77b4c385.JPG)
![07 7](https://user-images.githubusercontent.com/77851559/196462946-b14c18fb-4b4d-494a-92cc-e06e260706b5.JPG)
![07 8](https://user-images.githubusercontent.com/77851559/196463052-eed2fb22-7c57-416b-8f11-187f48828f59.JPG)
![07 9](https://user-images.githubusercontent.com/77851559/196463162-fc7ca3ee-1be9-4d5b-bf54-c7608346c868.JPG)
![07 10](https://user-images.githubusercontent.com/77851559/196463305-d39c80ff-db5a-4fd8-8bd9-eb67d3b6d6c9.JPG)

*รูปที่ 7*

# Answer 2:

จะได้ข้อสรุปของคำถามที่สองว่า รายได้รวมของอุทยานแห่งชาติกับพื้นที่ของอุทยานแห่งชาติ ไม่มีความสัมพันธ์ไปในแนวทางกันเลย นั่นหมายความว่าพื้นที่อุทยานที่มากขึ้นไม่ได้มีส่วนทำให้รายได้รวมของอุทยานเพิ่มขึ้นแต่อย่างใด ซึ่งต่อให้ผลลัพธ์มีความสัมพันธ์ไปในแนวทางเดียวกันเราก็ยังสรุปไม่ได้อยู่ดีว่าเป็นเหตุเป็นผลซึ่งกันและกัน

ที่นี้มาถึงคำถามสำคัญ คำถามสุดท้ายที่ว่า ถ้าจะจัดสรรงบประมาณเพื่อส่งเสริมการท่องเที่ยวอุทยานแห่งชาติ 10 อันดับแรกที่รัฐบาลควรส่งเสริมคือที่ไหนบ้าง (ตั้งแต่ปี 2023 เป็นต้นไป)? ให้นำข้อมูลรายได้อุทยานแห่งชาติ จำนวนนักท่องเที่ยวอุทยานแห่งชาติ และพื้นที่อุทยานแห่งชาติมารวมกัน และวิเคราะห์ตามขั้นตอนดังต่อไปนี้ (รายละเอียดดูใน Jupyter Notebook)

Preliminary check the correlation between total traveler, total revenue and area.

- Calculate total traveler data.

- Select column name and total traveler.

- Join traveler data and revenue with area data.

- Delete null value row.

- Calculate correlation between total revenue and area.

- Plot the heatmap of total revenue and area.

- Calculate revenue per traveler (THB / person)

- Calculate revenue per traveler score.

- Calculate traveler score.

- Calculate area score.

- Calculate correlation between total revenue and area.

- Plot the heatmap of total revenue and area.

- Plot the pairplot of total traveler and total revenue and area.

- Recheck total traveler and total revenue and area data.

Define the criteria for classifying the type of natural park.

- Define the type of natural park with following criteria.

Group "Star": R-score>=1 and T-score>=1

Group "Cash Cow": R-score>=1 and T-score<1

Group "Question": R-score=<1 and T-score>=1

Group "Dog": R-score<1 and T-score<1

- Combine all group of the natural park

- Recheck data after combination.

- Recheck column after combination.

- Plot the pairplot of data.

Apply K-Mean clustering algorithm.

- Apply K-Mean clustering algorithm k =4 to classify the type of natural park.

- Import sklearn library.

- Define X data for K-Mean model.

- Run model.

- Check centroid data.

- Plot data with centroid.

- Recheck the group name.

- Validate the model accuracy by using train data.

- Input the test data for checking the predicted result.

Apply Elbow method to find out the best k-value.

- Try to visualize data with different k-value and Check the inertia value.

- Print the result of inertia.

- Plot data to check elbow and Select the best k-value.

Plot the star group of natural park in bar chart format.

- Select the star group.

- Plot the star group of natural park in bar chart format.

ทำการหาค่าสัมพันธ์ correlation ของข้อมูลจำนวนนักท่องเที่ยวสะสม รายได้สะสมของอุทยานแห่งชาติ และพื้นที่อุทยานแห่งชาติ พร้อมทั้งพล๊อตกราฟ Heat Map ดังรูปที่8 จะพบว่ามีเฉพาะจำนวนนักท่องเที่ยวสะสมและ รายได้สะสมของอุทยานแห่งชาติเท่านั้นที่เป็นไปในแนวทางเดียวกัน

![08](https://user-images.githubusercontent.com/77851559/196463485-710d7da6-f9ea-4078-957b-ec642b07ed74.JPG)

*รูปที่8*

เพื่อให้ข้อมูลที่ได้จากแต่ล่ะอุทยานมีลักษณะเป็น scale เดียวกันเมื่อเทียบกับข้อมูลอุทยานแห่งชาติอื่น ๆ เราจึงใช้สูตรคำนวนให้เป็นเปอร์เซนต์ ดังต่อไปนี้

รายได้ต่อนักท่องเที่ยว (บาท/คน)

Revenue per Traveler (RPT) = total revenue / total traveler 

คะแนนรายได้ต่อนักท่องเที่ยวมาตรฐาน

R-score = (RPT / total RPT) * 100 %

คะแนนจำนวนนักท่องเที่ยวมาตรฐาน

T-score = (traveler / total traveler) * 100 %

คะแนนพื้นที่อุทยานมาตรฐาน

A-score = (area / total area) * 100 %

เมื่อนำข้อมูล R-score, T-score และ A-score มาพล๊อตกราฟ Heat Map และ Pair Plot ดังรูปที่9 จะพบว่าทั้ง 3ค่ามีความสัมพันธ์กันน้อยมาก ดังรูปที่9

![09 1](https://user-images.githubusercontent.com/77851559/196463711-dbc145cc-51af-455a-986e-7335d110a9c2.JPG)
![09 2](https://user-images.githubusercontent.com/77851559/196463802-39f4c721-8e2c-468d-a735-38ea3396a890.JPG)

*รูปที่9*

ทำการแบ่งกลุ่มประเภทของอุทยานโดยใช้เงื่อนไขดังต่อไปนี้

- กลุ่ม Star คือ อุทยานที่มีค่า R-score>=1 และ T-score>=1

- กลุ่ม Cash Cow คือ อุทยานที่มีค่า R-score>=1 และ T-score<1

- กลุ่ม Question คือ อุทยานที่มีค่า R-score<1 และ T-score>=1

- กลุ่ม Dog คือ อุทยานที่มีค่า R-score<1 และ T-score<1

พร้อมทั้งเพิ่มคอลัมน์ Group และ Cluster ตัวอย่าง ดังรูปที่10

![10 1](https://user-images.githubusercontent.com/77851559/196463903-fe2eed61-17fe-4a68-ba33-504deaf35df4.JPG)
![10 2](https://user-images.githubusercontent.com/77851559/196464042-784e5a0b-100c-4a57-b072-98290f310e5b.JPG)

*รูปที่10*

หลังจากแบ่งกลุ่มแล้วให้เอาข้อมูลมารวมกันอีกครั้ง ดังรูปที่11

![11](https://user-images.githubusercontent.com/77851559/196464172-35dae15c-2109-4314-bb45-4d06fc05a757.JPG)

*รูปที่11*

ทำการพล๊อตกราฟ Pair Plot อีกครั้งเพื่อเช็คความสัมพันธ์ของข้อมูล ดังรูปที่12

![12](https://user-images.githubusercontent.com/77851559/196464273-c797caff-bc02-4943-b8e2-1cd29dbb910c.JPG)

*รูปที่12*

ที่นี้ลองมาใช้อัลกอริทึม KMeans โดยที่ใช้ค่า k=4 เพื่อตรวจสอบดูว่าถ้าแบ่งเป็น 4กลุ่มอุทยานแห่งชาติตามเงื่อนไขข้างต้นแล้วเป็นการแบ่งกลุ่มที่เหมาะสมหรือไม่ ดังรูปที่13

![13](https://user-images.githubusercontent.com/77851559/196464518-8d48752e-4079-4cac-b45b-924dd68d2510.JPG)
*รูปที่13*

จากรูปจะพบว่าจุดศูนย์กลางในการแบ่งกลุ่มแต่ล่ะกลุ่ม (จุด centroid) ไม่น่าจะเป็นจุดที่เหมาะสมสำหรับการแบ่งกลุ่มอุทยานแห่งชาติให้บาลานซ์ซึ่งกันและกัน ซึ่งเมื่อเราทดลองโดยการป้อนข้อมูล train data เข้าไปเพื่อตรวจสอบโมเดลก็จะพบว่าถ้าใช้โมเดลนี้ในการแบ่งกลุ่มก็จะพบว่ามีการทำนายค่าแบ่งกลุ่มไปผิดบ้าง ตัวอย่างเช่น ข้อมูลจริงกลุ่ม Cash Cow ควรจะมี16 อุทยาน แต่ดันทำนายถูกต้องแค่13 อุทยาน ทำนายผิดไป3อุทยาน ดังรูปที่ 14

![14](https://user-images.githubusercontent.com/77851559/196464670-0217e497-406b-4e31-9b69-435ad8e364a6.JPG)

*รูปที่14*


จะเห็นว่าถ้าใช้กลุ่มแค่4กลุ่ม จะแบ่งกลุ่มได้ไม่ชัดเจน เราจึงใช้ Elbow Method มาคำนวนหาค่า centroid ของอัลกอริทึม k-means เพื่อให้ได้ผลลัพธ์ที่ดีกว่าเดิม ดังรูปที่15

![15](https://user-images.githubusercontent.com/77851559/196464759-93011999-db90-42b5-b28c-ad30c1459e76.JPG)

*รูปที่15*

เมื่อนำค่า inertia ซึ่งเป็นค่าที่ใช้ระบุความแม่นยำของจุด centroid ว่าแบ่งกลุ่มได้อย่างเหมาะสมมาพล๊อตกราฟ เพื่อหาจุด Elbow จะพบว่าใช้ค่า k=7 จะเป็นค่าที่เหมาะสมมากที่สุด คือแบ่งกลุ่มอุทยานแห่งชาติให้ได้7กลุ่มจะเป็นการแบ่งที่ดีที่สุด ดังรูปที่16

![16](https://user-images.githubusercontent.com/77851559/196464857-bad3da84-0b73-43a9-9432-d26d0129e9ef.JPG)

*รูปที่16*

อย่างไรก็ดีการแบ่งกลุ่มที่มากเกินไปอาจจะทำให้ business user สับสนได้ ผู้เขียนจึงคิดว่าการใช้เพียงแค่ 4กลุ่มก็น่าจะทำให้ business user มีแนวทางบริหารจัดการการท่องเที่ยวอุทยานแห่งชาติได้เหมาะสมกว่า จึงเลือกค่า k=4 ตามค่าเริ่มต้นก็น่าจะเพียงพอแล้ว

จากการวิเคราะห์ผลลัพธ์ทั้งหมดของการหาอุทยานแห่งชาติที่ทำรายได้ต่อหัวนักท่องเที่ยวมากที่สุดและจำนวนนักท่องเที่ยวมากที่สุดจะพบว่าอยู่ในกลุ่ม "Star" ดังรูปที่17 ได้แก่

1.หมู่เกาะสิมิลัน 

2.หมู่เกาะพีพี 

3.อ่าวพังงา 

4.หมู่เกาะลันตา 

5.เขาสก 

6.เอราวัณ 

7.เกาะเสม็ด 

8.ตะรุเตา 

9.หมู่เกาะช้าง 

10.ดอยอินทนนท์

![17](https://user-images.githubusercontent.com/77851559/196465008-50867d4f-9e82-46a0-9cf1-4658560ad027.JPG)

![19](https://user-images.githubusercontent.com/77851559/196497389-0aec07e4-0f07-4b50-98e9-31b4d4e455ca.JPG)

*รูปที่17*

# Answer 3:

ดังนั้นการตอบคำถามสุดท้ายนี้ ว่าถ้าจะจัดสรรงบประมาณเพื่อส่งเสริมการท่องเที่ยวอุทยานแห่งชาติ ที่รัฐบาลควรส่งเสริมตั้งแต่ปี2023เป็นต้นไป ก็ควรเน้นโฟกัสการโปรโมตการท่องเที่ยว10อุทยานแห่งชาติข้างต้น เนื่องจากเป็นอุทยานที่มีศักยภาพมากเป็นพิเศษทั้งในแง่ของรายได้ต่อหัวนักท่องเที่ยวและจำนวนนักท่องเที่ยว จึงจะเป็นคำตอบที่เหมาะสมที่สุด 

นอกจากนี้การพิจารณามุมมองของศักยภาพของอุทยานแห่งชาติ โดยใช้เพียงเฉพาะข้อมูลรายได้อย่างเดียวและไม่พิจารณาเป็นรายได้ต่อหัวนักท่องเที่ยวอาจจะไม่ถูกต้องนัก ตัวอย่างเช่น

อุทยานหมู่เกาะพีพีซึ่งเป็นอุทยานแห่งชาติอันดับหนึ่งในแง่ของรายได้รวม กลับทำรายได้ต่อหัวนักท่องเที่ยวได้เป็นอันดับสองรองจากอุทยานแห่งชาติหมู่เกาะสิมิลันขาดลอย (464บาท/คน เทียบกับ 310บาท/คน)

![18](https://user-images.githubusercontent.com/77851559/196481588-249fff67-14b3-4e7f-abf6-a77c4a119f0a.jpg)

ขอให้ท่านผู้อ่านที่กำลังวางแผนท่องเที่ยวช่วง High Season หน้าหนาวนี้ เลือกเที่ยวอุทยานแห่งชาติในดวงใจกันให้สนุกน่ะครับ

"Remember that happiness is a way of travel – not a destination." – Roy M. Goodman

จำไว้ว่า ความสุขของการเดินทางเกิดขึ้นระหว่างทางที่ไป ไม่ใช่จุดหมายปลายทางครับ

