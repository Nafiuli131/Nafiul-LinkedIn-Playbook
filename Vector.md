🌱 Java Vector – এক পুরনো যোদ্ধার গল্প

আমি যখন প্রথম Java শিখছিলাম, তখন সবসময়ArrayList নিয়েই কাজ করতাম। মনে হতো এটাই ultimate solution। কিন্তু পরে ধীরে ধীরে জানতে পারলাম Java Collections এর ভেতরে এক পুরনো যোদ্ধা লুকিয়ে আছে – নাম তার Vector।

প্রথমে ভেবেছিলাম, “এটা আবার কে?” 

কোডে ব্যবহার করতে গিয়েই বুঝলাম, এটার আসল শক্তি হলো 👉 thread-safety।
মানে ধরুন, একসাথে অনেকগুলো থ্রেড আপনার ডেটায় হাত দিচ্ছে। ArrayList গুলিয়ে ফেলতে পারে, কিন্তু Vector গুছিয়ে রাখে – যেন এক disciplined soldier!

🛠️ Example:
Vector<String> skills = new Vector<>();
skills.add("Java");
skills.add("C++");
skills.add("Python");

System.out.println(skills);

🖥️ Output:
[Java, C++, Python]

⚖️ তবে মজার ব্যাপার হলো—
Vector thread-safe হলেও ArrayList এর মতো ফাস্ট নয়।
আজকের দিনে খুব কম জায়গায় এর ব্যবহার আছে।
কিন্তু এর concept বুঝলে Java collections framework অনেক পরিষ্কার হয়ে যায়।

💡 আমার শেখা:
 সব টুলস modern হতে হবে এমন না। অনেক পুরনো জিনিসও আজকের দিনে ভালোভাবে বুঝতে পারলে fundamentals আরও শক্ত হয়।
