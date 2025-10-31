Java শিখতে গিয়ে অনেকের মাথায় প্রথমেই একটা প্রশ্ন আসে: JDK, JRE, আর JVM আসলে কোনটা কী? আর এদের মধ্যে পার্থক্য কী?

চলুন সহজভাবে দেখি—

🔹 JVM (Java Virtual Machine)
 • একে আপনি ভাবতে পারেন জাভার ইঞ্জিন।
 • JVM এর কাজ হলো আপনার লেখা .class ফাইল (bytecode) কে machine language এ translate করা।
 • JVM না থাকলে আপনার কোড run-ই হবে না।

🔹 JRE (Java Runtime Environment)
 • এটাকে ভাবুন runtime package হিসেবে।
 • এর মধ্যে আছে JVM + কিছু core libraries & files, যা জাভা প্রোগ্রাম চালানোর জন্য দরকার।
 • কিন্তু JRE দিয়ে কেবল run করা যায়, নতুন করে কোড লেখা বা compile করা যায় না।

🔹 JDK (Java Development Kit)
 • নামেই বোঝা যাচ্ছে—এটা হলো development kit।
 • এর মধ্যে আছে JRE + compiler (javac) + debugging tools + development libraries।
 • অর্থাৎ আপনি যদি জাভা প্রোগ্রাম develop করতে চান, তবে JDK লাগবেই।

📝 সহজ করে মনে রাখুন:
 • JVM 👉 শুধু রান করার ইঞ্জিন
 • JRE 👉 রান করার জন্য পুরো পরিবেশ
 • JDK 👉 রান + ডেভেলপ দুটোই করার কিট

💡 তাই, আপনি যদি শুধুমাত্র জাভা অ্যাপ চালাতে চান → JRE যথেষ্ট।
কিন্তু যদি কোড লিখে কম্পাইল করতে চান → JDK লাগবেই।

আপনি যখন প্রথমবার জাভা install করবেন, মনে রাখবেন—JDK install করলে JRE ও চলে আসে।
