গতবার বলেছিলাম, Orchestrator থেকে central ভাবে flow manage করা যায়। কিন্তু সবকিছু কি সবসময় centrally control করা যায়? 🤔

👉 এর বিকল্প হলো Saga Choreography 🎶

🔹 What is Choreography?
এখানে কোনো central orchestrator থাকে না। Services নিজেরা event publish করে, আর অন্য services সেই event শুনে action নেয়। Exactly like একটি dance choreography – সবাই নিজের step জানে, director লাগে না।

💡 Example: Flight Booking Choreography
 1️⃣ Flight Service → Ticket book করে → event publish কর“FlightBooked”
 2️⃣ Hotel Service → সেই event শুনে → room reserve করে → event publish করে “HotelBooked”
 3️⃣ Payment Service → সেই event শুনে → payment complete করে

🚨 যদি Payment fail হয় → Payment Service একটা “PaymentFailed” event publish করবে →Hotel Service সেটা শুনে reservation cancel করবে → Flight Service booking cancel করবে।

✨ Advantages of Choreography:
No single point of failure (distributed control)
Event-driven, loosely coupled system
Easy to scale and extend

⚠️ Disadvantages:

Flow visualization কঠিন ( কে কাকে trigger করল track করা tough )
Complex business logic হলে debugging খুব hard হয়ে যায়।

👉 With this, both Orchestration এবং Choreography cover করলাম।
 আপনার মতে কোনটা বেশি effective — Centralized control (Orchestration) নাকি Event-driven autonomy (Choreography)❓
