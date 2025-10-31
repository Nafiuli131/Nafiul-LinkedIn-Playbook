🧩 CAP Theorem — Consistency vs Availability Explained

গত পোস্টে আমরা দেখেছিলাম কিভাবে Failover আর Read Load Balancing সিস্টেমকে স্থিতিশীল রাখে।
 আজ কথা বলি এমন একটা ধারণা নিয়ে যা distributed system design-এর মূল স্তম্ভ —
 👉 CAP Theorem
⚙️ What is CAP Theorem?
 ১৯৯০ সালে Eric Brewer একটা ধারণা দেন —
 একটা distributed system একসাথে তিনটি জিনিস পুরোপুরি দিতে পারে না।
 এই তিনটি হলো 👇
1️⃣ Consistency (C):
 সকল নোডে একই সময়ে একই ডাটা থাকা।
 👉 মানে যেই ডাটাবেসে পড়ো না কেন, ফলাফল সব জায়গায় একই হবে।
2️⃣ Availability (A):
 সিস্টেম সবসময় রেসপন্স দিবে — এমনকি কোনো নোড ডাউন থাকলেও।
 👉 মানে ইউজার অপেক্ষায় থাকবে না, কিছু না কিছু রেসপন্স পাবে।
3️⃣ Partition Tolerance (P):
 নেটওয়ার্ক ভাগ হয়ে গেলেও (এক অংশ অন্য অংশে পৌঁছাতে না পারলেও) সিস্টেম চালু থাকবে।

⚖️ The Core Idea:
 একটি distributed system তিনটার মধ্যে সর্বোচ্চ দুইটা গুণই একসাথে দিতে পারে।
 এটাই CAP Theorem 💡

CP (Consistency + Partition Tolerance) -- Consistent data, but কিছু সময় unavailable হতে পারে
AP (Availability + Partition Tolerance) -- সবসময় রেসপন্স দিবে, কিন্তু কিছু সময় inconsistent data হতে পারে 
CA (Consistency + Availability) -- Theoretical only — Partition Tolerance ছাড়া possible নয় in real-world distributed systems

🧠 Real-Life Analogy:
 ধরা যাক আপনি আর আপনার টিমমেট একসাথে একটি Google Sheet এ এডিট করছেন। ইন্টারনেট স্লো হলে কেউ কিছু সময় পুরনো ডাটা দেখতে পারে (AP)
আবার কেউ এডিট করতে না পারলে consistent থাকবে, কিন্তু available থাকবে না (CP)

📢 Takeaway:
 CAP Theorem আমাদের শেখায় —
 👉 “You can’t have everything.”
 Distributed systems ডিজাইন করার সময় ঠিক করতে হয় কোন দিকটা বেশি গুরুত্বপূর্ণ — Consistency নাকি Availability।
