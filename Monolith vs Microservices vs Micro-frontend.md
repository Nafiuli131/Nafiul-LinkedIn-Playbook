Monolith vs Microservices vs Micro-frontend

ধরুন আপনি একটা প্রজেক্টে কাজ করছেন। ব্যাকএন্ড বানালেন Spring Boot দিয়ে, ফ্রন্টএন্ড বানালেন ReactJS দিয়ে। আপনি ভাবলেন - ওহ! এক backend, এক frontend, আলাদা আলাদা অ্যাপ্লিকেশন। এটাকেই তো Microservices বলে!

কিন্তু আসল সত্য হলো, না!

কারণ Microservices মানে হলো—ব্যাকএন্ডকে ছোট ছোট স্বাধীন সার্ভিসে ভাগ করা।
যেমন:
Authentication Service
Order Service
Payment Service
Notification Service

প্রতিটি সার্ভিস আলাদা কোডবেস, আলাদা ডাটাবেস, আলাদা ডিপ্লয়মেন্ট।
একটা ফিচার বদলাতে হলে পুরো সিস্টেম রিলিজ করার দরকার নেই।

অন্যদিকে, একটা বড় Spring Boot backend থাকলে সেটা এখনও মনোলিথ।React শুধু আলাদা লেয়ার হিসেবে কাজ করছে, এটাতে মাইক্রোসার্ভিসের মতো সুবিধা আসছে না।

এখন আসি Micro-frontend এ, এটাকে আপনি ভাবতে পারেন Microservices এর
মতোই, তবে frontend দুনিয়ায়। একটা বড় React অ্যাপকে ছোট ছোট UI অংশে ভাগ করা হয়, যেগুলো আলাদা টিম বানাতে পারে, আলাদা করে ডিপ্লয় করতে পারে।
উদাহরণস্বরূপ:
Login/Signup Module
Product Catalog Module
Cart Module
Profile Module
সবগুলো মিলে ইউজারের কাছে একটাই অ্যাপ মনে হয়, কিন্তু ভেতরে এগুলো আলাদা মাইক্রো-অ্যাপ।

Bottom line:
Backend ভাগ হলে → Microservices
Frontend ভাগ হলে → Micro-frontend
শুধু একটা backend + একটা frontend = Monolith + UI
