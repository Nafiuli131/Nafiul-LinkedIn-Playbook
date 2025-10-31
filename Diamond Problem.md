💎 Java Diamond Problem 💎

আপনি কি জানেন, Java multiple inheritance of classes support করে না? 🤔
কারণ যদি একটি ক্লাস একাধিক ক্লাস থেকে একই নামের method বা property inherit করত, তখন ambiguity দেখা যেত – এটাই আসলে Diamond Problem।

🔹 Diamond Problem কি?
ধরা যাক, Class A-এর একটি method আছে। Class B এবং Class C, দুটোই Class A থেকে inherit করছে।
তারপর Class D, Class B এবং Class C থেকে inherit করলে Class D জানে না কোন Class-এর method কল করবে।

 A
 / \
 B  C
 \ /
 D


এই ambiguity-টাকেই Diamond Problem বলে।

🔹 Java-তে সমাধান:

Java class inheritance-এ multiple inheritance allow করে না, তাই Class D-এর ক্ষেত্রে এই সমস্যা হয় না। ✅

কিন্তু interface-এর default method-এ একই সমস্যা আসতে পারে।

সমাধান: Implementing class-এ explicitly override করতে হয় কোন interface-এর method ব্যবহার হবে।

interface A {
 default void show() { System.out.println("A"); }
}

interface B extends A {
 default void show() { System.out.println("B"); }
}

class C implements A, B {
 @Override
 public void show() {
 B.super.show(); 
 }
}

public class Main {
 public static void main(String[] args) {
 C obj = new C();
 obj.show(); // Output: B
 }
}


✅ মুখ্য শিক্ষা:

Diamond Problem হলো ambiguity যখন multiple inheritance করা হয়।

Java class-এর ক্ষেত্রে এই সমস্যা নেই, কিন্তু interface default method-এ সতর্ক থাকতে হবে।

Explicit override করলে কোড safe এবং clean থাকে।
