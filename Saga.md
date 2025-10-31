✈️ আপনি Online এ Flight Book করছেন

ভাবুন, আপনি Dhaka → Dubai একটা flight বুক করলেন। সাথে hotel ও payment করতে হবে।

✅ Flow:

Flight ticket reserve
Hotel room book
Payment complete

সব ঠিকঠাক গেলে তো সমস্যা নাই।

কিন্তু হঠাৎ করে 🤯 payment fail হয়ে গেল!

তাহলে কী হবে❓

Flight booking already হয়ে গেছে
Hotel already reserve হয়ে গেছে
Payment হয়নি

👉 এখানে পুরো system inconsistent হয়ে গেল।

🛡️ এখানেই আসে Saga Design Pattern

Saga বলে – বড় transaction টাকে ছোট ছোট local transaction এ ভাঙো।
আর যদি কোনো একটা fail হয় → তাহলে compensating transaction চালাও।

মানে, Payment fail হলে → Hotel booking cancel হবে
Flight booking cancel হবে
সবকিছু আবার clean হয়ে যাবে

🔥 Why it’s powerful in Microservices:

Data consistency বজায় থাকে
Distributed lock দরকার হয় না
Scalable architecture পাওয়া যায়

👉 এক কথায় – Saga হলো microservices এর transaction hero।
Monolithic এ transaction simple হলেও, distributed system এ Saga ছাড়া consistency রক্ষা করা খুবই কঠিন।
