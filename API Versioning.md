🚀 API Versioning — Keeping Your Clients Happy

একটা সময় আপনি একটা সুন্দর API বানালেন।
সবকিছু একদম ঠিকঠাক চলছে — client-রা খুশি, data flow একদম মসৃণ।

তারপর একদিন আপনি ভাবলেন —
“চলুন, নতুন একটা ফিচার যোগ করি!”
ফিচার যোগ করলেন…
আর হঠাৎই client app গুলো crash করতে শুরু করল 😅

💥 সমস্যা কোথায়?
API আপডেট হয়েছে, কিন্তু client app পুরোনো structure আশা করছে।
আগে যেটা "name" পেত, এখন সেটা "fullName" নামে আসছে।

ফলাফল? — পুরোনো client গুলোর চোখে আপনি “breaking change” করলেন।

🧠 এখানেই আসে API Versioning
Versioning মানে হলো —
পুরোনোদের ভাঙবেন না, নতুনদের এগিয়ে নিয়ে যাবেন।
অর্থাৎ backward compatibility রক্ষা করে evolve করা।

⚖️ কল্পনা করুন
বামে 👉 /api/v1/users — পুরোনো version
ডানে 👉 /api/v2/users — নতুন version

পুরোনো app আগের মতোই কাজ করছে,
আর নতুন app নতুন response structure পাচ্ছে।
সবাই খুশি ❤️

💬 ছোট্ট একটা কথা
Versioning মানে কেবল কোড নয়,
এটা হলো respect for your users.
কারণ আপনি জানেন, কারো পুরোনো সিস্টেমও হয়তো এখনো সেই API’র ওপর নির্ভর করছে।
