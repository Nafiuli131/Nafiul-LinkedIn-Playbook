🔁 Database Replication Techniques Explained

গত পোস্টে আমরা দেখেছি Master–Replica (Primary–Replica) আর্কিটেকচারে কিভাবে রিড–রাইট আলাদা করে পারফরম্যান্স ও রিলায়েবিলিটি বাড়ানো যায়।
 আজ একটু গভীরে যাই — রেপ্লিকেশন আসলে কীভাবে হয়?

🧩 Asynchronous Replication:
 এখানে Master DB নিজের কাজ শেষ করে ফেলে, Replica পরে ডাটা আপডেট করে।
 👉 মানে Master অপেক্ষা করে না — ফলে সিস্টেম ফাস্ট থাকে, কিন্তু হঠাৎ Master ক্র্যাশ করলে Replica হয়তো একদম সাম্প্রতিক ডাটা পায় না।
📌 Use Case: বড় স্কেলের সিস্টেম যেখানে লাইটনিং পারফরম্যান্স দরকার, যেমন সোশ্যাল অ্যাপস বা রিড-হেভি সার্ভিস।

⚙️ Synchronous Replication:
 এখানে Master তখনই “write complete” বলে যখন Replica সফলভাবে সেই ডাটা রিসিভ করে ফেলে।
 👉 মানে ডাটা সেফ থাকে, কিন্তু রাইট ল্যাটেন্সি (delay) কিছুটা বেড়ে যায়।
📌 Use Case: ব্যাংকিং, পেমেন্ট, বা যেখানে ডাটা লস একদম সহ্য করা যায় না।

🕓 Semi-synchronous Replication:
 একটা ব্যালান্সড অ্যাপ্রোচ।
 Master Replica-কে ডাটা পাঠায় এবং অন্তত একটি Replica থেকে acknowledgment পাওয়ার পরেই পরবর্তী অপারেশনে যায়।
 👉 এতে কিছুটা নিরাপত্তা, কিছুটা স্পিড — দুটোই মিলে যায়।

💬 Summary:
| Technique    | Speed ⚡ | Data Safety 🛡️ | Common Use Case  |
| ---------------- | -------- | --------------- | ----------------- |
| Asynchronous   | Fastest | Moderate    | Large-scale apps |
| Synchronous   | Slower  | Highest     | Banking, Finance |
| Semi-synchronous | Balanced | Good      | Mid-level systems |

🌱 Takeaway:
 Replication শুধু ডাটা কপি করা না — বরং এটা এক ধরনের স্ট্র্যাটেজি, যেখানে “পারফরম্যান্স বনাম কনসিস্টেন্সি”-র মধ্যে সঠিক ভারসাম্যটা খুঁজে বের করতে হয়।
