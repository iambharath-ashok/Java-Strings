# Java-Strings: In and Out of Strings in Java
# String in Java


## 1.	Java String Interview Questions

### Question #1.	What is String in Java? Is String is Data Type?

-	String is a Class in java and defined in java.lang package
-	String is  not a primitive data type like int and long
-	String class represents character Strings
-	String Immutable and Final
-	JVM uses String Pool to store all the objects


### Question #2.	What are different ways to create String Object?

-	We can create String object using new operator like any normal java class 
-	We can use double quotes to create a String object
-	There are several constructors available in String class to get String from 
	
	-	char array
	-	byte array
	-	StringBuffer
	-	StringBuilder
	
	
	String str = new String("abc");
	String str1 = "abc";
	String str = "abc" + "efg";
	String hell = "hell";
	
	String hello = hell + "o";
	
	
-	When we create a String using double quotes
	
	-	JVM looks for String in the String pool to find if any other String is stored with the same value
	-	If found,  it just returns the reference to that String object 
	-	Else it creates a new String object with given value and stores it in the String pool	

-	When we use the new operator
	
	-	JVM creates the String object in Heap Memory but don’t store it into the String Pool
	-	We can use intern() method to store the String object into String pool 
	-	Or return the reference if there is already a String with equal value present in the pool
	
### Question #3.	Write a method to check if input String is Palindrome?

	
	public boolean isPalindrome(String str) {
		
		StringBuilder stringBuilder = new StringBuilder(str);
		
		return stringBuilder.reverse().equals(str);
	}
	
	public static void main(String[] args) {
		
		Scanner scan = new Scanner(System.in);
		String string = scan.next();
		
		if(isPalindrome(string)) {
			System.out.println(string +": is Palindrome");
		} else {
			System.out.println(string +": is not Palindrome");
			
		}
	}
	
	
	public static boolean isPalindrome(String str) {
		if(!Optional.<String>ofNullable(str).isPresent()) {
			return false;
		}
		int strLength = str.length();
		
		for (int i = 0; i< str.length()/2; i++) {
			if(str.charAt(i) == str.charAt(--strLength)) {
				continue;
			} else {
				return false;
			}
		}
		return true;
	}
	
	
### Question #4.	Write a method that will remove given character from the String?
	
	
	
	public String removeCharacter(String str, char characterToBeRemoved) {
		
		
		if(!Optional.ofNullable(str).isPresent()) {
			return null;
		}
		
		return str.replaceAll(Character.toString(characterToBeRemoved), "");
	}
	
### Question #5.	How can we make String upper case or lower case?


	public String toLowerCase(String str) {
		
		if(!Optional.ofNullable().isPresent()) {
			return null;
		}
		return str.toLowerCase();
	}
	
	
	public String toUpperCase(String str) {
		
		if(!Optional.ofNullable().isPresent()) {
			return null;
		}
		return str.toUpperCase();
	}
	
### Question #6.	What is String subSequence method?

-	Java 1.4 has introduced CharSequence interface
-	String implements CharSequence interface and provides implementation for subSequence() method
-	subSequence() method internally invokes String class subString() method 

	#### Code snippet of String subSequence method implementation:

	public CharSequence subSequence(int beginIndex, int endIndex) {
		return this.substring(beginIndex, endIndex);
	}
	
	
-	String subSequence method returns a character sequence that is a subsequence of this sequence
-   str.subSequence(begin, end) behaves same as the invocation of str.substring(begin, end)
-	There is no benefit in using subSequence method
-	Ideally we should always use String substring method	
	
	
	#### Code Snippet of subSequence() method Use Cases:
	
		public class StringSubsequence {

			/**
			 * This class shows usage of String subSequence method
			 * 
			 * @param args
			 */
			public static void main(String[] args) {
				String str = "www.iambharath.guru";
				System.out.println("Last 4 char String: " + str.subSequence(str.length() - 4, str.length()));
				System.out.println("First 4 char String: " + str.subSequence(0, 4));
				System.out.println("website name: " + str.subSequence(4, 14));
				// substring vs subSequence
				System.out.println("substring == subSequence ? " + (str.substring(4, 14) == str.subSequence(4, 14)));
				System.out.println("substring == substring ? " + (str.substring(4, 14) == str.substring(4, 14)));
				System.out.println("subSequence == subSequence ? " + (str.subSequence(4, 14) == str.subSequence(4, 14)));
				System.out.println("substring equals subSequence ? " + (str.substring(4, 14).equals(str.subSequence(4, 14))));
			}

		}


	#### Output:
		
		Last 4 char String: guru
		First 4 char String: www.
		website name: iambharath
		substring == subSequence ? false
		substring == substring ? false
		subSequence == subSequence ? false
		substring equals subSequence ? true

		
		
		
	
	
### Question #7. How to compare two Strings in java program?	

- 	Java String implements java.lang.Comparable interface
####	There are two variants of compareTo() methods 
	
	#### 1.	compareTo(String anotherString)
	
		-	compareTo() method 	String object with passed String Objects Lexicographically
		-	If String object precedes the argument passed, it returns negative integer 
		-	If String object follows the argument String passed, it returns a positive integer
		-	It returns zero when both the String have the same value
		-	In this case equals(String str) method will also return true
		
	#### 2.	compareToIgnoreCase(String anotherString)

		-	This method is similar to the first one, except that it ignores the case
		-	It uses String CASE_INSENSITIVE_ORDER Comparator for case insensitive comparison
		-	If the value is zero then equalsIgnoreCase(String str) will also return true
			

	#### Code Snippet 1:
	
		public class StringCompareToExample {
			/**
			 * This class show String compareTo examples
			 * @param args
			 */
			public static void main(String[] args) {
				String str = "ABC";
				System.out.println(str.compareTo("DEF"));
				System.out.println(str.compareToIgnoreCase("abc"));
			}
		}
		
	#### Output:

		-3
		0
	
	-	Above negative output is because “ABC” is lexicographically less than the “DEF”
	-	Output is -3 because it compares the character values one by one	
	
	#### Code Snippet 2:
	
		public static void main(String[] args) {
			char a = 'A';
			char d = 'D';
			System.out.println(a-d); //prints -3
		}
	
	#### Output: 
	
		-3
	
	-	So when “ABC” is compared to “DEF”, the character at first index is compared
	-	Since they are different and ‘A’ comes before ‘D’ lexicographically
	-	It returns a negative integer with the difference between them, hence output is -3
	-	If we compare “AABC” with “ADBC”, then also we will get the same output as -3



### Question #8. How to convert String to char and vice versa?

-	This is a tricky question because String is a sequence of characters
-	So we can’t convert it to a single character
-	We can use use charAt method to get the character at given index 
-	Or we can use toCharArray() method to convert String to character array


	#### Code Snippet:	
		
		
		public static void main(String[] args) {
			String bharath = "Bharath The Great";
			
			//string to char array
			char [] charArray1 = bharath.toCharArray();
			System.out.println(charArray1.length);
			
			//char at specific index
			char c = bharath.charAt(2);
			System.out.println(c);
			
			//Copy string characters to char array
			char[] getCharsArray = new char[9];
			bharath.getChars(9, bharath.length(), getCharsArray, 0);
			System.out.println(getCharsArray);
			
		}
	
	
	#### Output:	
	
			17
			1
			The Great





### Question #9.	How to convert String to byte array and vice versa?

-	We can use String getBytes() method to convert String to byte array 
-	We can use String constructor new String(byte[] arr) to convert byte array to String


	#### Code Snippet of String to Byte Array:
		
		public static void main(String[] args) {
			String str = "Bharath The Great";
			byte[] byteArr = str.getBytes();
			// print the byte[] elements
			System.out.println("String to byte array: " + Arrays.toString(byteArr));
		}
	#### Output: 
	
			[66, 104, 97, 114, 97, 116, 104, 32, 84, 104, 101, 32, 71, 114, 101, 97, 116]
		
		
		
	#### Code snippet of Byte Array to String
	
		public static void main(String[] args) {
			byte[] byteArray = { 'B', 'H', 'A', 'R', 'A', 'T','H' };
			byte[] byteArray1 = { 80, 65, 78, 75, 65, 74 };

			String str = new String(byteArray);
			String str1 = new String(byteArray1);

			System.out.println(str);
			System.out.println(str1);
		}
		String str = new String(byteArray, StandardCharsets.UTF_8);
		byte[] byteArray1 = { 80, 65, 78, 75, 65, 74 };
		String str = new String(byteArray1, 0, 3, StandardCharsets.UTF_8);
	
	#### Output:
		
			BHARATH
			BHARATH
		
		
### Question #10. Can we use String in switch case?

-	Yes, we can use String in Switch
-	From, Java 7 ... yes we can use
-	Java switch case String make code more readable
-	Java switch case String is case sensitive
-	Java Switch case uses String.equals() method to compare the passed value with case values
-	Make sure to add a NULL check to avoid NullPointerException
-	According to Java 7 documentation for Strings in Switch
	
	-	Java compiler generates more efficient byte code for String in Switch statement 
	-	Than chained if-else-if statements


	#### Code Snippet of String in Switch:
	
		static final String COLOR_RED = "RED";

		public static void main(String[] args) {
			String color = "red";
			switch(color) {
			case COLOR_RED:
				System.out.println("red");
				break;
			default: 
				System.out.println("Defalut and Switch is Case Sensitive");
				break;
			}
		}

	#### Output:
	
		   Defalut and Switch is Case Sensitive

		
### Question #11.	Write a program to print all permutations of String?

### Question #12.	Write a function to find out longest palindrome in a given string?

### Question #13.	Difference between String, StringBuffer and StringBuilder?

-	String is immutable and final in Java
-	String manipulations are resource consuming
-	Java provides two utility classes for String manipulations – StringBuffer and StringBuilder
-	StringBuffer and StringBuilder are mutable classes
-	StringBuffer operations are thread-safe
-	StringBuilder is not Thread Safe
-	StringBuilder performance is fast than StringBuffer

	#### 1.	String 

	-	A String represents a string in the UTF-16 format
	-	+ operator is overloaded for String and used to concatenate two Strings
	-	String internally it uses StringBuffer to perform operator overloading action
	-	String is a final class with all the fields as final except “private int hash”
	-	This field contains the hashCode() function value 
	-	Created only when hashCode() method is called and then cached in this field
	-	hash is generated using final fields of String class with some calculations
	-	Every time hashCode() method is called, it will result in same output
	-	For caller, its like calculations are happening every time but internally it’s cached in hash field


	#### 2.	String vs StringBuffer

	-	Since String is immutable in java, whenever we do String manipulation like concat, substring etc, it generates a new String and discard the older String for garbage collection

	-	These are heavy operations and generate a lot of garbage in heap
	-   So Java has provided StringBuffer and StringBuilder class that should be used for String manipulation

	-  StringBuffer and StringBuilder are mutable objects in java and provides reverse(), append(), insert(), delete() and substring() methods for String manipulation



	#### 3.	StringBuffer vs StringBuilder

	-	StringBuffer was the only choice for String manipulation till Java 1.4
	- 	But it has one disadvantage that all of its public methods are synchronized
	-	StringBuffer provides Thread safety but on a performance cost
	-	In most of the scenarios, we don’t use String in multithreaded environment
	-	So Java 1.5 introduced a new class StringBuilder that is similar with StringBuffer except thread safety and synchronization
	- 	StringBuffer was introduced in Java 1.0 whereas StringBuilder class was introduced in Java 1.5 after looking at shortcomings of StringBuffer



	#### 4.	String vs StringBuffer vs StringBuilder

	-	String is immutable whereas StringBuffer and StringBuider are mutable classes

	-	StringBuffer is thread safe and synchronized whereas StringBuilder is not

	-	Thats why StringBuilder is more faster than StringBuffer

	- 	String concat + operator internally uses StringBuffer or StringBuilder class

	-	For String manipulations in non-multi threaded environment, we should use StringBuilder or else we can use StringBuffer class


### Question #14. Why String is immutable or final in Java


-	String Pool is possible because String is immutable in Java
-	It increases security because any hacker can’t change its value 
-	It’s used for storing sensitive information such as database username, password etc
-	Since String is immutable, it’s safe to use in multi-threading and we don’t need any synchronization
-	Strings are used in Java ClassLoader and immutability provides security that correct class is getting loaded by Classloader


	#### Benefits of String Immutability
	
	##### 1.	Saves lot of Heap space
		
		-	This way Java Runtime saves a lot of java heap space because different String variables can refer to same String variable in the pool
		
	##### 2.	Thread Safe
		
		-   Since String is immutable, it is safe for multithreading 
		-	And a single String instance can be shared across different threads
		-	This avoid the usage of synchronization for thread safety, Strings are implicitly thread safe
				
	##### 3.	Class Loading
	
		-	Strings are used in Java ClassLoader and immutability provides security that correct class is getting loaded by ClassLoader
		-	For example, if we are trying to load java.sql.Connection class but the referenced value is changed to myhacked.Connection class that can do unwanted things to our database
		
	##### 4.	HashMap key  --> hashcode is cached
		
		-	Since String is immutable, its hashcode is cached at the time of creation and it doesn’t need to be calculated again
		-	This makes it a great candidate for key in a Map 
		-	And it’s processing is fast than other HashMap key objects
		-	This is why String is mostly used Object as HashMap keys
	
	##### 5.	Security
		
		-	If String is not immutable then it would cause severe security threat to the application
		-	For example, database username, password are passed as String to get database connection and in socket programming host and port details passed as String
		-	Since String is immutable it’s value can’t be changed otherwise any hacker could change the referenced value to cause security issues in the application
	
	##### 6.	String Intern
	
		-   If String would not have been immutable, then String interning would not have been possible 
		-	Because if any variable would have changed the value, it would have been reflected to other variables also
	

### Question #15.	How to Split String in Java?

-	We can use split(String regex) to split the String into String array
- 	public String[] split(String regex): split() method is used to split the string based on the given regular expression
	
	#### Code Snippet of String split():
	
		String s = "abcaada";
		System.out.println(Arrays.toString(s.split("a")));
	
-	public String[] split(String regex, int limit): split() method is used when we want the string to be split into a limited number of strings
-	Variable that contains name and address with comma as delimiter
-	Now address can have commas in them, so we can use this method

	#### Code Snippet of String split():
	
		String s = "Bharth,Bangalore,INDIA";
		String[] data = s.split(",", 2);
		System.out.println("Name = "+data[0]); //Bharth
		System.out.println("Address = "+data[1]); //Bangalore,INDIA
		
-	The limit parameter controls the number of times the pattern is applied and therefore affects the length of the resulting array
-	If the limit n is greater than zero then the pattern will be applied at most n – 1 times
-	The array’s length will be no greater than n
-	And the array’s last entry will contain all input beyond the last matched delimiter
-	If n is non-positive then the pattern will be applied as many times as possible and the array can have any length
-	If n is zero then the pattern will be applied as many times as possible, the array can have any length, and trailing empty strings will be discarded

	#### Code Snippet of String split():
		
		String line = "I am a Developer";
		
		String[] stringArray = line.split("", 1);
		String[] stringArray = line.split("", string.length()); // Array length will equal to String length // contains all the elements
		String[] stringArray = line.split("", -10); // As many times as possible
		String[] stringArray = line.split("a", - 2); // Zero and non negative apply as many times as possible
		//	if N > 1 then apply n -1 
		// if n = 1 then 1 - 1 = 0 // String Array length will 1 same as input
		// if n = 2 then 2 - 1 = 1	// String Array length will 2
		
		Arrays.asList(stringArray).stream().forEach(System.out::println);
		
	

### Question #16.	Why Char array is preferred over String for storing password?

-	String is immutable in Java and Stored in String pool
-	Once it’s created it stays in the pool until unless garbage collected 
-	So even though we are done with password it’s available in memory for longer duration 
-	And there is no way to avoid it
-	It’s a security risk because ANYONE HAVING ACCESS to MEMORY DUMP can find the PASSWORD as CLEAR TEXT
-	If we use a char array to store password, we can set it to blank once we are done with it
-	So we can control for how long it’s available in memory that avoids the security threat with String

### Question #17. How do you check if two Strings are equal in Java?

-	There are two ways to check if two Strings are equal or not – using “==” operator or using equals method
-	When we use “==” operator, it checks for the reference but in our programming
-	So we should use the equals method to check if two Strings are equal or not
-	There is another function equalsIgnoreCase that we can use to ignore case


	#### Code Snippet of equals and equalsIgnoreCase()
	
		
		String s1 = "abc";
        String s2 = "abc";
        String s3= new String("abc");
        System.out.println("s1 == s2 ? "+(s1==s2)); //true
        System.out.println("s1 == s3 ? "+(s1==s3)); //false
        System.out.println("s1 equals s3 ? "+(s1.equals(s3))); //true

		
### Question #18. What is String Pool?
			
-	String Pool is a pool of Strings stored in Java Heap Memory
-   We know that String is a special class in Java
-	We can create String object using new operator as well as providing values in double quotes
-	String Pool is possible only because of immutable and it’s implementation of String interning concept
-	String pool is also example of Flyweight design pattern
-	String pool helps in saving a lot of space for Java Runtime although it takes more time to create the String
-	Using double quotes to create a String

	- 	It first looks for String with same value in the String pool
	-	If found it just returns the reference else it creates a new String in the pool and then returns the reference

-	Using new operator
	
	-	We force String class to create a new String object in heap space
	-	We can use intern() method to put it into the pool or refer to other String object from string pool having same value

	
	#### Code Snippet of String Constant Pool:
	
		public class StringPool {

			/**
			 * Java String Pool example
			 * @param args
			 */
			public static void main(String[] args) {
				String s1 = "Cat";
				String s2 = "Cat";
				String s3 = new String("Cat");
				
				System.out.println("s1 == s2 :"+(s1==s2));
				System.out.println("s1 == s3 :"+(s1==s3));
			}
		}
		
	#### Output:
		
			s1 == s2 :true
			s1 == s3 :false


	-	Two Objects will created one in heap and another in Pool



### Question #19. What does String intern() method do?

-	When the intern method is invoked

	-	If the pool already contains a string equal to this String object as determined by the equals(Object) method
	-	Then the string from the pool is returned
	-	Otherwise, this String object is added to the pool and a reference to this String object is returned
	-	This method always returns a String that has the same contents as this string but is guaranteed to be from a pool of unique strings


### Question #20. Does String is thread-safe in Java?

-	Strings are immutable, so we can’t change it’s value in program
-	Hence it’s thread-safe and can be safely used in multi-threaded environment


### Question #21. Why String is popular HashMap key in Java?

-	Since String is immutable, its hashcode is cached at the time of creation and it doesn’t need to be calculated again
-	This makes it a great candidate for the key in a Map 
-	And it’s processing is fast than other HashMap key objects
-	This is why String is mostly used Object as HashMap keys 


### Question #22. Thread Safety in Java

-	Multiple threads created from same Object, share  same Object Variables 
-	When Threads are used to Read and Update the shared data, this can lead to Data Inconsistency
-	Reason for data inconsistency:

	-	Because updating any field value is not an atomic process
	-	It requires three steps: 
		
		-	First to Read the Current Value
		-	Second to do the necessary operations to get the Updated Value
		-	Third to assign the updated value to the field reference


	#### Code Snippet of showing problem with increment:
	
		public class ThreadSafety {
			public static void main(String[] args) throws InterruptedException {
				ProcessingThread pt = new ProcessingThread();
				Thread t1 = new Thread(pt, "t1");
				t1.start();
				Thread t2 = new Thread(pt, "t2");
				t2.start();
				//wait for threads to finish processing
				t1.join();
				t2.join();
				System.out.println("Processing count="+pt.getCount());
			}
		}

		class ProcessingThread implements Runnable {
			private int count;
			
			@Override
			public void run() {
				for(int i=1; i < 5; i++){
					processSomething(i);
					count++;
				}
			}

			public int getCount() {
				return this.count;
			}

			private void processSomething(int i) {
				// processing some job
				try {
					Thread.sleep(i*1000);
				} catch (InterruptedException e) {
					e.printStackTrace();
				}
			}		
		}

		
	### Different Ways of achieving Thread Safety in Java
	
	
	1.	Synchronization 
	2.	Using Locks from java.util.concurrent.locks package
	3.	AtomicWrapper Classes from java.util.concurrent.atomic package
	4.	Using Thread Safe Collection Classes like ConcurrentHashMap, ArrayBlockingQueue, CopyOnWriteArrayList
	5.	Using volatile keyword with variable to make sure every read operation is from memory and not from Thread Cache
	
	


--------------------------------------------




	
