🚦 Load Balancing – The Secret Behind Smooth Applications

কিছুদিন আগে আমার Spring Boot অ্যাপ্লিকেশন production এ গিয়েছিল। প্রথমে সবকিছু ঠিকঠাক চলছিল, কিন্তু হঠাৎ user load বেড়ে গেলে API response time আকাশ ছুঁতে লাগলো, কিছু request তো fail-ই করলো। তখনই বুঝলাম — একটা সার্ভারের উপর ভরসা করা মানেই ঝুঁকি।

এখানেই আসে Load Balancer।

👉 এটি incoming requests কে multiple server এ distribute করে।
👉 কোনো server down হলে অন্যটা সাথে সাথে দায়িত্ব নেয়।
👉 ফলে application থাকে fast, reliable & highly available।

একটা analogy দিই:
ভাবুন একটা রেস্টুরেন্টে সবাইকে এক টেবিলে বসানো হলো—অবশ্যই chaos হবে। কিন্তু waiter যদি সবাইকে আলাদা টেবিলে smartly বসায়, তাহলে service smooth হবে। Load balancer ও আসলে ঠিক এটাই করে।

⚡ Algorithms matter too:
Round Robin → পালা করে সার্ভারে request পাঠানো
Least Connections → যেখানে কম load, সেখানে পাঠানো
IP Hash → একই user সবসময় একই সার্ভারে যাবে

প্র্যাক্টিক্যালি, আমি Nginx দিয়ে একই অ্যাপ্লিকেশনের multiple instance (8081, 8082, 8083) run করালাম। তারপর load balancer request গুলো evenly ভাগ করে দিলো। Result → traffic spike এও system stable, আর end-users কিছুই বুঝলো না।
