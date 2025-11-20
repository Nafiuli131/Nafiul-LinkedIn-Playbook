⚡ Short-Circuiting in Java Streams — কম কাজ, বেশি পারফরম্যান্স!

Java Stream API-এর সবচেয়ে underrated power হচ্ছে —
👉 Short-Circuiting Operations

মানে, Stream পুরো data process না করেই
কাজ থামিয়ে দিতে পারে, যতক্ষণ না result পাওয়া যায়।

এটা performance boost-এর জন্য অসাধারণ 💥

🟢 Short-Circuiting কী বোঝায়?

ধরুন আপনি ১,০০,০০০ elements এর মধ্যে
“প্রথম যে number > 50000” — সেটা চান।

Java Stream যদি সব element scan করত —
পারফরম্যান্স যেত 😅👇

কিন্তু Short-Circuiting থাকায়,
যেই match পায় → সাথে সাথে থেমে যায়।

🧠 Which Stream Operations Short-Circuit?
✔ Terminal Operations

findFirst()

findAny()

anyMatch()

allMatch()

noneMatch()

✔ Intermediate (lazy)

limit(n)

skip(n)

এগুলো Stream-কে বলে —
👉 “এখানে থাম — আর প্রক্রিয়া লাগবে না!”

🟦 Example (Very Real)
List<Integer> numbers = List.of(10, 20, 30, 50000, 60000, 70000);

int result = numbers.stream()
        .filter(n -> {
            System.out.println("Checking: " + n);
            return n > 30000;
        })
        .findFirst()
        .orElse(-1);

System.out.println("Result = " + result);

Output হবে:
Checking: 10
Checking: 20
Checking: 30
Checking: 50000
Result = 50000


➡️ Stream 60000 বা 70000 পর্যন্ত গেইলই না!
Because findFirst() short-circuit করেছে ⚡

🍀 কেন এটি গুরুত্বপূর্ণ?

Short-Circuiting → less execution → faster app
বিশেষ করে:
✔ বড় list/map
✔ API/DB call inside stream
✔ Complex computation

High-performance code-এর key weapon এটা।

🔥 Final Thought

Stream শুধু functional cute syntax না —
It's a powerful optimization tool.

Smart developer → streamline করে, short-circuit করে।
যেখানে unnecessary processing avoid করা যায় —
সেখানেই performance জিতে যায় 💪


