🗄️ Database Generalization 🗄️

ডাটাবেস ডিজাইনে কখনও কখনও আমরা দেখি একাধিক entity-এর মধ্যে common attribute আছে।
এই repetitive অংশগুলো সরিয়ে উপরের লেভেলে একটি general entity বানানোকেই বলে Generalization।

🔹 Generalization কীভাবে কাজ করে?
ধরুন, আমাদের কাছে তিনটি entity আছে:

Car

Bike

Bus

তাদের সবারই কিছু common attribute আছে, যেমন:

VehicleID

Brand

Model

EngineCapacity

👉 আলাদা আলাদা টেবিলে রাখলে এই attribute-গুলো বারবার রিপিট হবে।

🟢 তাই আমরা একটা general entity বানাই Vehicle নামে, যেখানে এই common attribute-গুলো থাকবে।
এরপর Car, Bike, Bus শুধু তাদের special attribute গুলো রাখবে।

📌 Example ER Diagram:

 Vehicle
 /  |  \
 Car  Bike  Bus

Vehicle টেবিলে থাকবে → VehicleID, Brand, Model, EngineCapacity

Car টেবিলে → NumberOfDoors

Bike টেবিলে → HasCarrier

Bus টেবিলে → SeatCapacity

✅ Generalization-এর সুবিধা:

Data redundancy কমে যায়

Database structure হয় পরিষ্কার ও maintainable

Query করা সহজ হয় common attributes-এর উপর

💡 Bottom Line:
👉 Generalization হলো bottom-up approach, যেখানে common জিনিসগুলোকে এক জায়গায় তোলা হয়।
এটা database design কে করে আরও efficient, scalable এবং easy-to-maintain।
