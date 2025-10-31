
গতবার বলেছিলাম, Saga design pattern কিভাবে microservices এ distributed transaction consistency আনে।
আজকে সেই বিষয়টাকেই একটু ডিটেলসে নিয়ে আসি – Saga Orchestration 🎯

🔹 What is Orchestration?
এখানে একটা central orchestrator (controller service) থাকে, যেটা পুরো flow coordinate করে।
মানে, orchestrator জানে কোন step আগে হবে, কোনটা পরে হবে, আর fail হলে rollback কিভাবে হবে।

💡 Example: Flight Booking Orchestration
1️⃣ Orchestrator instruct করে Flight Service → "Ticket book করো"
2️⃣ Success হলে instruct করে Hotel Service → "Room reserve করো"
3️⃣ সব শেষে instruct করে Payment Service → "Payment complete করো"

🚨 Suppose Payment fail হয়ে গেল → তখন orchestrator নিজে compensation trigger করবে

Hotel booking cancel
Flight booking cancel

👉 ফলে system আবার clean & consistent হয়ে যাবে।

✨ Advantages of Orchestration:

Flow control এক জায়গা থেকে হওয়ায় easy to monitor & debug
Complex business process handle করা যায়
Clear visibility কে কোন service call করল

⚠️ Disadvantages:

Orchestrator হয়ে যায় single point of failure
Services orchestrator এর উপর dependency তৈরি করে → coupling বেড়ে যায়

🔑 এক কথায় – Orchestration হলো central brain 🧠 of Saga Pattern,
যেটা পুরো transaction এর director এর মতো কাজ করে 🎬

👉 Next post এ শেয়ার করব Choreography approach – যেখানে orchestrator লাগে না, services নিজেরাই event-driven communication করে।
