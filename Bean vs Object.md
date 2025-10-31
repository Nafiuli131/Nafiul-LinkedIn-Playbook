******Spring Boot: Bean vs Object******

Spring Boot এ development করার সময় অনেকেই confuse হয়ে যায় bean আর object নিয়ে।
আমি নিজেও শুরুতে এটা বুঝতে struggle করেছি।

🔹 Object:
*সাধারণ Java তে আমরা new keyword দিয়ে তৈরি করি।
*Container বা framework এর কোন role নেই।
*প্রতিবার new করলে আলাদা instance তৈরি হয়।

Example:
MyService service = new MyService(); // সাধারণ object

🔹 Bean:
*Spring container দ্বারা manage করা object।
*@Component, @Service, @Repository, @Controller ইত্যাদি annotation দিয়ে Spring এটাকে register করে।
*Container inject করে dependency automatically।
*Singleton by default, অর্থাৎ container এ শুধু একটাই instance থাকে।

Example:
@Service
public class MyService {
 // Spring এই instance টাকে Bean হিসেবে manage করবে
}

🔹Difference in practice:
যদি আপনি new MyService() করেন, Spring কোনো control রাখবে না।
কিন্তু যদি Spring bean ব্যবহার করেন, তখন container handle করবে lifecycle, dependency injection, proxy, transaction management সব কিছু।

সুতরাং Spring Boot এ development মানেই শুধু object বানানো নয়, bean তৈরি করে Spring কে manage করতে দেওয়াই smart development।
