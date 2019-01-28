# Java String Programing Questions

1.	What is the output of below program?

	Code Snippet:
	
		public class StringAmbiguous {
			public static void method(String argument) {
				System.out.println("String Method Called");
			}
			public static void method(StringBuilder argument) {
				System.out.println("StringBuilder Method Called");
			}
			public static void main(String[] args) {
				method(null);
			}
		}

	Output:
		
		The above program will not compile with error as “The method method(String) is ambiguous for the type StringAmbiguous. 
		For complete clarification read Understanding the method X is ambiguous for the type Y error.
		
		
2.	What is the output of below program?
	
	Code :
		public class StringTest {
			public static void main(String[] args) {
				String s1 = new String("bharath");
				String s2 = new String("BHARATH");
				System.out.println(s1 = s2);
			}
		}
		
	Output:

		BHARATH


3.	What is the output of below code snippet?
	
	Code: 
	
		String s1 = new String("abc");
		String s2 = new String("abc");
		System.out.println(s1 == s2);		
		
	Output: 
		false
		
		
4.	What will be output of below code snippet?

	Code: 

		String s1 = "abc";
		StringBuffer s2 = new StringBuffer(s1);
		
		System.out.println("String Equals: "+s1.equals(s2));
		System.out.println("String Buffer Equals: "+s2.equals(s1));
		
-	It will always print false because s2 is not of type String
-	Because equals method implementation in the String class
	
	-	There is check using instanceof operator to check if the type of passed object is String? 
	-	If not, then return false
		
	Output:
		
		true

5.	What will be the output of below program?

	Code: 
	
		String s1 = "abc";
		String s2 = new String("abc");
		s2.intern();
		System.out.println(s1 ==s2);	

-	Output will be false
-	Intern() method will return the String object reference from the string pool
-	But since we didn’t assigned it back to s2, there is no change in s2 and hence both s1 and s2 are having different reference
-	If we change the code in line 3 to s2 = s2.intern(); then output will be true
		
		
	Output:
		
		
		
6.	How many String objects got created in below code snippet?

	Code: 

		String s1 = new String("Hello");  
		String s2 = new String("Hello");
		
	Output: 
		3
		
-	The answer is 3
-	First – line 1, “Hello” object in the string pool.
-	Second – line 1, new String with value “Hello” in the heap memory.
-	Third – line 2, new String with value “Hello” in the heap memory.
-	Here “Hello” string from string pool is reused.
		
