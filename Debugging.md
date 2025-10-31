সেদিন বিকেলে হালকা মুডে কাজ করছিলাম ☕
হঠাৎ QA team একটা মেসেজ দিল —
“Login page টা বারবার redirect নিচ্ছে, কিন্তু কোনো error দেখাচ্ছে না।”

Test server-এ গিয়ে দেখি —
পেজটা আসলেই লুপ নিচ্ছে।
একটা বার login করলে আবার login page-এ চলে আসছে।
কোনো exception না, কোনো warning না — সব HTTP 200! 😶

প্রথমে ভাবলাম, “Session expire হচ্ছে?”
তারপর মনে হল, “Spring Security configuration এ কিছু ভুল আছে?”
৫ মিনিট... ১০ মিনিট... কিছুই বের হচ্ছে না।
লগ-এ কিছুই ধরা পড়ছে না।

তখন মনে পড়ল একটা পুরোনো কথা —
“যখন সব ঠিকঠাক মনে হয়, তখন debug level বাড়িয়ে দেখো।”

সাথে সাথেই application.properties এ লিখলাম 👇
logging. level. org. springframework. security = DEBUG

এবার পুরো লগ খুলে দেখি এক লাইন ঝলমল করছে —
UserDetailsService returned null for username=xyz

Boom 💣
ঠিক এখানেই আসল গল্পটা ধরা দিল!

আমার UserDetailsService implementation-এ একটা ছোট্ট typo ছিল —
একটা ভুল condition এর কারণে return null হয়ে যাচ্ছিল,
যেখানে আসলে exception throw করা উচিত ছিল।

🧩 Fix:
✅ UserDetailsService method টায় null না ফেলে —

throw new UsernameNotFoundException("User not found");
এটা যোগ করলাম।
✅ Application restart করলাম।
✅ Login perfectly কাজ করলো! 🎯

তখন এই কথাটাই মাথাতে আসলো,
Debugging isn’t about panic.
It’s about listening to what your system is trying to say. 🧘‍♂️

⚙️ Quick Tip for Spring Boot Devs
🔹 যদি কিছুই বুঝতে না পারেন, প্রথমে debug log চালু করুন।
🔹 কখনো return null করবেন না যেখানে exception দরকার।
🔹 Log হলো আপনার system-এর language — শুধু পড়তে শিখুন।
