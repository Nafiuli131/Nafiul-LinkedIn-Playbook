🔄 Eventual Consistency Explained

গত পোস্টে আমরা দেখেছি CAP Theorem — যেখানে বোঝা গেছে distributed system একসাথে Consistency, Availability, আর Partition Tolerance — তিনটাকেই ১০০% দেওয়া সম্ভব নয়।
 তবে প্রশ্ন আসে —
 👉 যদি সিস্টেম সবসময় consistent না থাকে, তাহলে ইউজার কি ভুল ডাটা দেখতে পারে? 😕
এখানেই আসে Eventual Consistency ধারণা।

⚙️ What is Eventual Consistency?
 Eventual Consistency মানে হলো —
 “এখনই না হলেও, কিছু সময় পর সব Replica একই জায়গায় মিলবে।”
অর্থাৎ সিস্টেম কিছু সময়ের জন্য inconsistent থাকতে পারে,
 কিন্তু সময়ের সঙ্গে সঙ্গে সব নোড বা ডাটাবেস একই ডাটায় পৌঁছে যাবে।

🧠 Simple Example:
 ধরা যাক আপনি Amazon-এ একটা প্রোডাক্টের রিভিউ দিলেন।
 আপনি সঙ্গে সঙ্গে সেটা দেখতে পাচ্ছেন না — কিন্তু কয়েক সেকেন্ড পর অন্যরাও আপনার রিভিউ দেখতে পাবে।
 👉 সেই কয়েক সেকেন্ডের গ্যাপটাই হলো eventual consistency delay।

🚀 Why Eventual Consistency Is Powerful:
 ✅ High Availability — সিস্টেম কখনও বন্ধ হয় না
 ✅ Fast Response — ডাটাবেস অপেক্ষা করে না
 ✅ Scalable Architecture — অনেক সার্ভার একসাথে কাজ করতে পারে

📌 তবে, downside হলো:
 কিছু সময় ইউজার পুরনো ডাটা দেখতে পারে — তাই সিস্টেম ডিজাইন করার সময় সাবধানে থাকতে হয় কোন অপারেশন consistent থাকা দরকার, আর কোনটা না থাকলেও চলবে।

🧭 Analogy:
 ভাবুন, আপনার এক বন্ধু ঢাকা থেকে আপনার কাছে টাকা পাঠালেন,
 কিন্তু ব্যাংকের সব শাখায় সেই তথ্য পৌঁছাতে ২ মিনিট সময় লাগল।
 এই ২ মিনিটে সিস্টেম technically inconsistent —
 কিন্তু শেষে সবাই একই ডাটা দেখবে — that’s eventual consistency! 💰
