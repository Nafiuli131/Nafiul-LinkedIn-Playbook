🧠 Cache Invalidation Strategies — The Hardest Part of Caching 🧩

অনেকে বলে —
“There are only two hard things in Computer Science:
cache invalidation and naming things.” 😄

পূর্বের পোস্টে আমরা শিখেছি Common Caching Patterns যেখানে data caching এর কৌশলগুলো নিয়ে আলোচনা করেছিলাম। আজ চলুন দেখি — caching-এর সবচেয়ে কঠিন দিকটা 👉 cache invalidation

❓ কেন এত কঠিন?
কারণ cache একবার stale (পুরনো) হয়ে গেলে অ্যাপ্লিকেশন ভুল ডাটা দেখাতে পারে। আর সেই ভুল ডাটাই হতে পারে বড় বিপর্যয়ের কারণ! 🚨তাই প্রয়োজন — cache কখন এবং কীভাবে invalidate করা হবে, তা ঠিকভাবে পরিকল্পনা করা।

🧩 Common Cache Invalidation Strategies

🔹Time-To-Live (TTL) / Expiry Based:
👉 নির্দিষ্ট সময় পরে cache স্বয়ংক্রিয়ভাবে মেয়াদোত্তীর্ণ হয়ে যায়।
📌 Example:
ইউজার ড্যাশবোর্ডের ডাটা প্রতি ৫ মিনিট পর রিফ্রেশ হয়।
✅ Pros: সহজ, lightweight
⚠️ Cons: TTL শেষ না হওয়া পর্যন্ত পুরনো ডাটা থাকতে পারে

🔹Write Invalidate / Update Invalidate:
👉 যখনই ডাটাবেসে আপডেট হয়, তখন cache থেকেও সেটি মুছে দেওয়া হয় বা আপডেট করা হয়।
📌 Example:
ইউজার প্রোফাইল আপডেট দিলে cache সঙ্গে সঙ্গে invalidate হয়ে যায়।
✅ Pros: সর্বদা fresh data
⚠️ Cons: write-heavy সিস্টেমে overhead বাড়ে

🔹 Explicit Invalidation:
👉 ডেভেলপার বা সিস্টেম নিজে থেকে নির্দিষ্ট cache key invalidate করে দেয়।
📌 Example:
Admin প্যানেল থেকে কোনো product price পরিবর্তন হলে cache clear করা হয়।
✅ Pros: নিয়ন্ত্রিত invalidation
⚠️ Cons: manual mistake-এর ঝুঁকি

🔹 Event-Driven Invalidation:
👉 ডাটাবেস বা মেসেজ কিউ-এর event শুনে cache invalidate করা হয়।
📌 Example:
Kafka event “product_updated” ট্রিগার হলে cache refresh হয়।
✅ Pros: Real-time consistency
⚠️ Cons: Complex implementation

⚖️ কবে কোনটা ব্যবহার করবেন?

| Scenario         | Best Strategy           |
| ------------------------ | --------------------------------- |
| Frequently changing data | Write / Event-driven invalidation |
| Rarely changing data   | TTL-based invalidation      |
| Dashboard / Analytics  | Time-based or manual       |
| E-commerce / Profile   | Write or Event-driven       |

💬 Final Thought
Cache invalidate করা মানে শুধু পুরনো ডাটা মুছে ফেলা নয় — বরং Consistency আর Performance-এর মধ্যে ভারসাম্য রক্ষা করা। ⚖️

💡 একটা সিস্টেমের speed নির্ভর করে cache-এর উপর,
আর সেই cache-এর reliability নির্ভর করে আপনার invalidation strategy-এর উপর।
