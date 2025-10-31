⚙️ Failover & Read Load Balancing Explained

গত পোস্টে আলোচনা করেছিলাম Replication Techniques নিয়ে — কিভাবে ডাটাবেসের মধ্যে ডাটা সিঙ্ক হয়।
 আজ দেখা যাক সেই রেপ্লিকেশন সিস্টেম কীভাবে সার্ভিস continuity নিশ্চিত করে, আর লোড শেয়ারিং করে।

💥 Failover — যখন Master Down হয়ে যায়:
 ধরা যাক আপনার Primary DB (Master) হঠাৎ ক্র্যাশ করল।
 এই অবস্থায় সিস্টেমকে একটুও থেমে না থেকে চালু রাখাই হলো “Failover”।
👉 সহজভাবে, Failover মানে হলো:
 যখন Master অকেজো হয়, তখন Replica (Slave) — যেটা আপ-টু-ডেট — সেটি স্বয়ংক্রিয়ভাবে নতুন Master হয়ে যায়।
🔁 অনেক সময় এই প্রক্রিয়া automated হয় (যেমন MySQL Group Replication, Aurora RDS ইত্যাদিতে),
 আবার অনেক সিস্টেমে manual promotion করতে হয় (যেমন সাধারণ MySQL সেটআপে)।

📌 Benefit:
Zero (বা very low) downtime
Continuous availability
Disaster recovery readiness

⚖️ Read Load Balancing — যখন রিড বেশি:
 বেশিরভাগ অ্যাপ্লিকেশনে রিড অপারেশন রাইটের তুলনায় অনেক বেশি হয়।
 তাহলে কেন সব রিডও Master-এর ওপর দেওয়া হবে?
👉 এখানেই আসে Read Load Balancing।
 রিড কোয়েরিগুলো বিভিন্ন Replica DB-তে ভাগ করে দেওয়া হয়, যাতে প্রতিটা সার্ভারের ওপর চাপ কমে।
📈 ফলাফল:
Application performance বাড়ে
Master রাইট অপারেশনে ফোকাস করতে পারে
Replica গুলো efficiently ব্যবহৃত হয
🧠 Example:
 ধরা যাক তোমার অ্যাপে ৫টা Replica আছে।
 তাহলে একটায় লগইন ডাটা পড়ছে, একটায় প্রোফাইল ডাটা, অন্যগুলোতে পোস্ট/কমেন্ট ডাটা।
 সব মিলে সিস্টেম স্মুথ ও স্কেলেবল।

🚀 Takeaway:
 Failover আর Read Load Balancing একসাথে ডাটাবেস সিস্টেমকে দেয়
 ✅ High Availability
 ✅ Scalability
 ✅ Reliability
