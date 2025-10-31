🚀 Java Virtual Thread 🚀

Java 19 এর পর থেকে আমরা একটা দারুণ জিনিস পেলাম – Virtual Thread।
এখন প্রশ্ন আসতে পারে, Virtual Thread আসলে কী?

🔹 আগে চলুন একটু পিছনে যাই:

OS Level Thread / Kernel Thread 👉 এগুলো সরাসরি অপারেটিং সিস্টেম ম্যানেজ করে। CPU scheduling, context switching—সবকিছুই OS এর দায়িত্ব। কিন্তু এগুলো তৈরি ও মেইনটেইন করতে অনেক খরচ (expensive)।

User Level Thread 👉 এগুলো ইউজার স্পেসে ম্যানেজ হয়, কিন্তু OS এগুলো সম্পর্কে জানে না। ফলে performance কিছুটা ভালো হয়, কিন্তু drawback হলো, একবার কোনো থ্রেড ব্লক হলে, পুরো প্রক্রিয়াই থেমে যেতে পারে।

Platform Thread (Java এর ক্লাসিক থ্রেড) 👉 Java এর traditional thread আসলে OS thread এর উপর wrapper। তাই অনেক বেশি memory নেয় এবং বেশি সংখ্যক concurrent thread handle করতে গেলে সমস্যা হয়।

🔹 এখানেই এলো Virtual Thread

Virtual Thread basically হলো user-mode managed lightweight thread, কিন্তু Java runtime এগুলোকে OS এর উপর efficient ভাবে schedule করে।

হাজার হাজার virtual thread বানালেও JVM ও OS handle করতে পারে।

Block করলে পুরো process আটকে থাকে না।

Developer এর জন্য API একই থাকে – মানে Thread API তে কোনো বড় পরিবর্তন লাগবে না, কিন্তু under the hood huge optimization হচ্ছে।

🔹 কেন Virtual Thread এত important?

ধরুন আপনি একটা server লিখলেন যেখানে প্রতিটি incoming request এর জন্য একটা thread লাগছে। Traditional thread দিয়ে কয়েক হাজার request handle করা কঠিন, কিন্তু Virtual Thread দিয়ে লক্ষ-লক্ষ concurrent request handle করা সম্ভব, তাও minimal resource ব্যবহার করে।

🔹 Platform Thread Example

public class PlatformThreadExample {
 public static void main(String[] args) throws InterruptedException {
 Thread t1 = new Thread(() -> {
 System.out.println("Running in a Platform Thread: " + Thread.currentThread());
 });
 t1.start();
 t1.join();
 }
}

✅ Possible Output:

Running in a Platform Thread: Thread[#21,Thread-0,5,main]
👉 এখানে Thread-0 বা এই রকম কিছু আসবে, যেটা OS level thread এর সাথে directly map করা।

🔹 Virtual Thread Example (Java 19+)

public class VirtualThreadExample {
 public static void main(String[] args) throws InterruptedException {
 Thread t1 = Thread.startVirtualThread(() -> {
 System.out.println("Running in a Virtual Thread: " + Thread.currentThread());
 });
 t1.join();
 }
}

✅ Possible Output:

Running in a Virtual Thread: VirtualThread[#22]/runnable@ForkJoinPool-1-worker-1
👉 এখানে দেখা যাচ্ছে VirtualThread[#22] — মানে এটা একটা lightweight virtual thread যেটা JVM নিজে schedule করেছে।

🏆 Key Difference
Platform Thread → সরাসরি OS thread (heavyweight, সীমিত সংখ্যক)
Virtual Thread → JVM managed, lightweight, হাজার হাজার তৈরি করা যায়
