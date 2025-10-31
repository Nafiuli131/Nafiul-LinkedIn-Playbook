🔹 Normalization Techniques – একটা গল্প, একটা শেখা🔹

কিছুদিন আগে আমার টিমের এক জুনিয়র এসে বলল,ভাই, আমাদের ডাটাবেজ টেবিলে একই ডেটা বারবার রিপিট হচ্ছে। আপডেট করতে গেলেই mismatch হয়, কনফিউশন আলাদা।
আমি বললাম – এই সমস্যার নামই হলো data redundancy। আর একেই সমাধান করার জন্য আছে Normalization।
সে তখন বলল – ভাই, 1NF, 2NF, 3NF এগুলা বইতে পড়ছি, কিন্তু মাথায় ঢোকে নাই।

তখন আমি টেবিল এঁকে বুঝালাম 👇

📌 Without Normalization (Unnormalized Table)

| StudentID | Name  | Courses      | Department | DeptHead |
| --------- | ------ | ------------------ | ---------- | --------- |
| 1     | Rafi  | Math, Physics   | Science  | Dr. Karim |
| 2     | Nabila | Chemistry, Biology | Science  | Dr. Karim |
| 3     | Rafi  | Math, Physics   | Science  | Dr. Karim |


👉 এখানে দেখুন –
এক কলামে একাধিক ভ্যালু (Courses)।
একই ছাত্রের ডেটা বারবার রিপিট হচ্ছে।
Department Head বারবার ডুপ্লিকেট হচ্ছে।

✅ 1NF (First Normal Form)
👉 এক কলামে শুধু একটাই ভ্যালু থাকবে।

| StudentID | Name  | Course  | Department | DeptHead |
| --------- | ------ | --------- | ---------- | --------- |
| 1     | Rafi  | Math   | Science  | Dr. Karim |
| 1     | Rafi  | Physics  | Science  | Dr. Karim |
| 2     | Nabila | Chemistry | Science  | Dr. Karim |
| 2     | Nabila | Biology  | Science  | Dr. Karim |


✅ 2NF (Second Normal Form)
👉 Partial dependency বাদ দিই। Department এর তথ্য আলাদা টেবিলে নেই।

Table: Students
| StudentID | Name  |
| --------- | ------ |
| 1     | Rafi  |
| 2     | Nabila |

Table: Courses
| StudentID | Course  |
| --------- | --------- |
| 1     | Math   |
| 1     | Physics  |
| 2     | Chemistry |
| 2     | Biology  |


Table: Departments
| Department | DeptHead |
| ---------- | --------- |
| Science  | Dr. Karim |


✅ 3NF (Third Normal Form)
👉 Transitive dependency বাদ দিই।
যদি DeptHead আলাদা table এ রাখি –

Table: Departments
| DepartmentID | Department |
| ------------ | ---------- |
| 101     | Science  |


Table: DeptHead
| HeadID | DepartmentID | HeadName |
| ------ | ------------ | --------- |
| 501  | 101     | Dr. Karim |


জুনিয়র তখন বলল –আচ্ছা ভাই, এখন বুঝতেছি। ডেটা যত normalize করি, ততই clean আর maintainable হয়।

আমি বললাম –ঠিকই ধরছো। তবে সবকিছু normalize করলে query জটিল হয়ে যায়। তাই balance বজায় রাখা হলো আসল skill।

💡 Takeaway:
Normalization মানে শুধু একাডেমিক টপিক না, বরং বাস্তব project এ data consistency, redundancy আর update anomaly কমানোর সউপায়।
