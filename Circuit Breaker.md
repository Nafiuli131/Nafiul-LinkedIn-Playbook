⚡ Circuit Breaker Pattern – সিস্টেমের সেফটি সুইচ
Distributed system বা microservices এ সবচেয়ে বড় চ্যালেঞ্জ হলো — এক সার্ভিস down হয়ে গেলে যেন পুরো সিস্টেম না ভেঙে পড়ে।
এখানেই আসে Circuit Breaker pattern।

👉 Circuit Breaker মূলত একটা safety switch, যা detect করে কোনো service বারবার fail করছে কিনা।
যদি করে, তখন request ব্লক করে দ্রুত fallback দেয় — যাতে system slow না হয় বা hang না করে।

🔹 Circuit Breaker এর ৩টা State:
1️⃣ Closed – সবকিছু স্বাভাবিক। Requests সরাসরি service এ যাচ্ছে, ঠিকঠাক response আসছে।
2️⃣ Open – Service বারবার fail করলে breaker trip করে open হয়ে যায়। এখন নতুন request service এ যাবে না, সরাসরি fallback দেওয়া হবে। এতে user experience বাঁচে।
3️⃣ Half-Open – কিছুক্ষণ পর breaker test mode এ যায়। কয়েকটা limited request আবার service এ পাঠায়।

Success হলে আবার Closed এ যাবে।
Fail হলে আবার Open এ ফিরে যাবে।

✅ কি কারণে আমরা Circuit Breaker Pattern use করবো? 
System কে cascading failure থেকে বাঁচায়
Response time কমায়
User experience smooth রাখে
Fault tolerance বাড়ায়

Finally আমরা বলতে পারি Circuit Breaker হলো smart ভাবে ব্যর্থতা সামলে system কে resilient করে তোলা।
