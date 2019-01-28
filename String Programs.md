# Java String Programs


Write a program to print all permutations of String?
Write a function to find out longest palindrome in a given string?
Write a Java program to reverse a String?
How to check if a String is Palindrome?
Write a java program to count the number of words in a string?

--------------------------------------------------------
## Duplicate Frequency:
How do you find duplicate characters in a string?


public class StringDuplicates {

	public static void main(String[] args) {

		String string = "JavaJ2EE";

		 List<Entry<String, Long>> collect = string.chars()
				.mapToObj(c -> Character.toString((char) c))
				.collect(Collectors.groupingBy(Function.identity(), Collectors.counting()))
				.entrySet().stream()
				.filter(m -> m.getValue() > 1)
				.collect(Collectors.toList());
		 
		 System.out.println(collect);
	}

}
--------------------------------------------------------

### How to get distinct characters and their count in a String?

	Code Snippet:
		 
		Map<String, Long> collect2 = string.chars()
		.mapToObj(c -> String.valueOf((char)c))
		.collect(Collectors.groupingBy(Function.identity(), Collectors.counting()));
				 
				 
	Code Snippet:
	
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
--------------------------------------------------------

### How to remove all occurrences of a given character from input String?


	Code Snippet:

		private static void removeCharFromString(String input, char c) {
			String result = input.replaceAll(String.valueOf(c), "");
			System.out.println(result);
		}

--------------------------------------------------------
	
How to prove String is immutable programatically?

	Code Snippet:
	
		public static void main(String[] args) {

			String s1 = "Java"; // "Java" String created in pool and reference assigned to s1
			
			String s2 = s1; //s2 is also having the same reference to "Java" in the pool
			
			System.out.println(s1 == s2); // proof that s1 and s2 have same reference
			
			s1 = "Python"; 
			//s1 value got changed above, so how String is immutable?
			
			//well, in above case a new String "Python" got created in the pool
			//s1 is now referring to the new String in the pool 
			//BUT, the original String "Java" is still unchanged and remains in the pool
			//s2 is still referring to the original String "Java" in the pool
			
			// proof that s1 and s2 have different reference
			System.out.println(s1 == s2); 
			
			System.out.println(s2); 
			// prints "Java" supporting the fact that original String value is unchanged, hence String is immutable
			
		}
--------------------------------------------------------
Write a program to count number of words in a String?

	Code Snippet:
	
		
--------------------------------------------------------
Write a program to check if two Strings are created with same characters?
Write Java Program To Check Whether Two Strings Are Anagram Or Not?

	Code Snippet:
	
		public static String getUniqueCharString(String s1) {
			String cleanedString = s1.toLowerCase().chars().mapToObj(c -> (char)c)
			.map(c -> String.valueOf(c))
			.collect(Collectors.toCollection(TreeSet::new))
			.stream().collect(Collectors.joining(""));
			return cleanedString;
		}
--------------------------------------------------------
How to find whether String contains given String or Not?
	
	Code Snippet:
	
		public static boolean contains(String string, String subString) {
			return string.toLowerCase().contains(subString.toLowerCase());
		}
		
-------------------------------------------------------
How to swap two Strings without using a third variable?

	Code Snippet:
	
		String str1 = "abcd";
		String str2 = "xyz";
		
		str1 = str1.concat(str2);
		str2 = str1.substring(0,str1.length()- str2.length());
		str1 = str1.substring(str2.length()); // Begin Index
		
		System.out.println("String 1:"+str1);
		System.out.println("String 2:"+str2);
--------------------------------------------------------		
Provide two ways to check if a String contains only digits?

	Code Snippet:

			public static boolean containsOnlyDigits(String string) {
			
				// First Way:
				string.matches("\\d+");
				
				//Second Way:	
				try {
					int i = Integer.parseInt(string);
					return true;
				} catch (Exception e) {
					return false;
				}
			}
--------------------------------------------------------
How do you remove all white spaces from a String in Java?

	Code Snippet:
		
		// Using Built in Method : replaceAl()
		public static void main(String[] args) {
		
			String replaceSting = replaceWhiteSpace("343 353534 		43dlfkds", "\\s+");
			System.out.println(replaceSting);
		}
		
		public static String replaceWhiteSpace(String toBeReplaced, String toReplaceWith) {
			return toBeReplaced.replaceAll(toReplaceWith, "");
		}
		
		//Using Manually

		String inputString = sc.nextLine();
        char[] charArray = inputString.toCharArray();
        String stringWithoutSpaces = "";
        
        for (int i = 0; i < charArray.length; i++) 
        {
            if ( (charArray[i] != ' ') && (charArray[i] != '\t') )
            {
                stringWithoutSpaces = stringWithoutSpaces + charArray[i];
            }
        }	
		
	
	
--------------------------------------------------------
Write a java program to reverse a given string with preserving the position of spaces?
	
	Code Snippet:
	
		public static void main(String[] args) {
		
			String str = "I Am Not String";
			
			
			char[] inputStringArray = str.toCharArray();
			char[] resultArray = new char[inputStringArray.length];
			
			
			for(int i =0; i<inputStringArray.length; i++) {
				if(inputStringArray[i] == ' ') { 
					resultArray[i]= ' ';
				}
			}
			
			int j = resultArray.length-1;
			
			//Second for loop :
			//we copy every non-space character of inputStringArray 
			//from first to last at 'j' position of resultArray
			
			for (int i = 0; i < inputStringArray.length; i++)
			{
				if (inputStringArray[i] != ' ') 
				{
					//If resultArray already has space at index j then decrementing 'j'
					
					if(resultArray[j] == ' ')
					{
						j--;
					}
					
					resultArray[j] = inputStringArray[i];
					
					j--;
				}
			}
			String string = String.valueOf(resultArray);
			System.out.println(string);
			
		
		}
		
--------------------------------------------------------
How To Convert String To Integer In Java?

-	There are two methods available in java to convert string to integer
-	One is Integer.parseInt() method and another one is Integer.valueOf() method
-	Both these methods are static methods of java.lang.Integer class
-	Both these methods throw NumberFormatException if input string is not a valid integer
-	The main difference between Integer.parseInt() and Integer.valueOf() method is that
-	parseInt() method returns primitive int where as valueOf() method returns java.lang.Integer object
	
	
	Code Snippet:
	
		String s = "2015";
        int i = Integer.parseInt(s);
		
		String s = "2015";
		int i = Integer.valueOf(s);	

- 	One is Integer.toString() method and another one is String.valueOf() method
-	Both these methods return string representation of the given integer

	Code Snippet:
	
		int i = 2015;
		String s = String.valueOf(i);
		String s =Integer.toString(i);

		
-------------------------------------------------
Write a Java program to reverse each word of a given string?

	Algorithm :
	
		Step 1: Split String in to Array
		
		Step 2: Create empty reverseString 
		
		Step 3: For each word reverse them
		
		Step 4: Append each reverse word to reverseString
	

	Code Snippet:
	
		String [] strArray = str.split(" ");
		
		String reverseSt= "";
		for(String string : strArray) {
			
			String reverseWord = "";
			
			for(int i = string.length() -1; i>=0; i--) {
				reverseWord = reverseWord + string.charAt(i);
			}
			reverseSt = reverseSt + reverseWord + " ";
		}

		System.out.println(reverseSt);
	
	
	Code Snippet using String Builder:
	
		public static void main(String[] args) {
			String string = "Java Concept Of The Day";
			String reverseString = reverseEachWord(string);
			System.out.println(reverseString);
		}
		
		public static String reverseEachWord(String string) {
			String [] wordsArray = string.split("\\s+");
			StringBuilder reverseString = new StringBuilder();
				for(String words: wordsArray) {
				StringBuilder reverseWord = new StringBuilder();
				for(int i = words.length()-1; i>=0; i--) {
					reverseWord.append(words.charAt(i));
				}
				reverseString.append(reverseWord).append(" ");
			}
			return reverseString.toString();
		}
----------------------------------------
		
Write a code to check whether one string is a rotation of another?
	
	Algorithm:
	
		Step 1: Check whether two strings are equal in length
		
				str1.length() == str2.length()
				
		Step 2: Add String1 strings s3 = s1 + s1
		
		Step 3:	Check whether s3 contains s2
		
			s3.contains(s2)
	
	
	Code Snippet:
	
		public static void main(String[] args)
		{
			String s1 = "JavaJ2eeStrutsHibernate";
			String s2 = "StrutsHibernateJavaJ2ee";
			//Step 1
			if(s1.length() != s2.length())
			{
				System.out.println("s2 is not rotated version of s1");
			}
			else
			{
				//Step 2
				String s3 = s1 + s1;
				//Step 3
				if(s3.contains(s2))
				{
					System.out.println("s2 is a rotated version of s1");
				}
				else
				{
					System.out.println("s2 is not rotated version of s1");
				}
			}
		}
--------------------------------------------------------------
Write a java program to count the total number of occurrences of a given character in a string without using any loop?

	
	Code Snippet 1: 
		
		String s = "Java is java again java again";
		
		char ch= 'j';
		long count = s.chars()
			.mapToObj(c -> String.valueOf((char)c))
			.filter(st -> st.equals(Character.toString(ch)))
			.count();
		
		System.out.println(count);
		
		
	Code Snippet:

		String s = "Java is java again java again";
        char c = 'a';
        int count = s.length() - s.replace("a", "").length();
					// Total - Total without  char
--------------------------------------------------------------------

18) How do you find first repeated and non-repeated character in the given string in java?

	Algorithm:
		Step 1 : Define one HashMap called charCountMap with Character as key and Integer as value. This map will hold the characters and their count in the given string.

		Step 2 : Convert inputString to char array called strArray.

		Step 3 : Iterate through all chars of strArray and update their occurrences in charCountMap.

		Step 4 : Iterate through all chars of strArray and check their count in charCountMap. Any first occurring character with 1 as it’s count will be the first non-repeated character in inputString.

		Step 5 : Iterate through all chars of strArray and check their count in charCountMap. Any first occurring character with >1 as it’s count will be the first repeated character in inputString.
	
	Code:
	
		public static void main(String[] args) {

			String str = "JavaConceptOfTheDay";

			Map<String, Long> collect = str.chars().mapToObj(ch -> String.valueOf((char) ch))
					.collect(Collectors.groupingBy(Function.identity(), Collectors.counting()));

			String firstNon = null, repetativeChar = "";
			for (char ch : str.toCharArray()) {
				if (collect.get(Character.toString(ch)) == 1) {
					firstNon = Character.toString(ch);
					break;
				}

			}
			for (char ch : str.toCharArray()) {

				if (collect.get(Character.toString(ch)) > 1) {
					repetativeChar = String.valueOf(ch);
					break;
				}
			}
			System.out.println(firstNon);
			System.out.println(repetativeChar);

		}
	
---------------------------------------------------------------------
19) Write a Java program to append a given string to a text file?

-	FileWritter needs to open in Append mode
-	By default FileWriter will open the file in overwriting mode 

	CodeSnippet:
	
		FileWriter fileWriter = new FileWriter(“Pass File Name Here”);     //Overwrites the text file
		FileWriter fileWriter = new FileWriter(“Pass File Name Here”, false);     //Overwrites the text file
		FileWriter fileWriter = new FileWriter(“Pass File Name Here”, true);     //Appends to the text file
		
		
	Algorithm:

		Step 1 : Open an existing text file in an append mode by passing ‘true’ while constructing the FileWriter object

			FileWriter fileWriter = new FileWriter(“Pass File Name Here”, true);

		Step 2 : Bundle FileWriter object in BufferedWriter if we are writing lots of text

			READ :  How To Find All Pairs of Elements In An Array Whose Sum Is Equal To A Given Number?
			BufferedWriter bufferedWriter = new BufferedWriter(fileWriter);

		Step 3 : Use PrintWriter object if we are writing the text in multiple lines by wrapping BufferedWriter object in PrintWriter

			PrintWriter printWriter = new PrintWriter(bufferedWriter);

		Step 4 : Use printWriter.println() method to write each line into a file

			printWriter.println(“Pass the string to be written here”);

		Step 5 : Close the resources
		
	

			
		
--------------------------------------------------------------		
		
20) How do you find the number of characters, words and lines in the given text file in Java?
	
	
	Algorithm:
	
		Step 1 : Create BufferedReader object to read the text file

			BufferedReader reader = new BufferedReader(new FileReader(“Pass The File Location Here”));

		Step 2 : Initialize charCount, wordCount and lineCount to 0

			int charCount = 0;
			int wordCount = 0;
			int lineCount = 0;

		Step 3 : Read all the lines of the text file one by one into currentLine using reader.readLine() method

			String currentLine = reader.readLine();

		Step 4 : Update lineCount each time we read the line into currentLine

			lineCount++;

		Step 5 : We get the number of words in a line by splitting the currentLine by space

			String[] words = currentLine.split(” “);

		Step 6 : Update the wordCount by adding the number of words in a line

			wordCount = wordCount + words.length;

		Step 7 : Update charCount by iterating through words array as below

			for (String word : words)
			{
				   charCount = charCount + word.length();
			}

		Step 8 : Close BufferedReader object
				
	Code Snippet:
	
		public static void main(String[] args) {
			int wordCount = 0, charCount=0, lineCount = 0;
			try(BufferedReader reader = Files.newBufferedReader(Paths.get("files/input.txt"))) {
				String line = "";
				
				while((line = reader.readLine())!=null) {
					lineCount++;
						String [] strings = line.split(" ");
						wordCount  += strings.length;
						
						for(String string :strings ) {
							charCount  += string.length();
						}
				}
			} catch (IOException e) {
				e.printStackTrace();
			}
		}
--------------------------------------------------------------
		
21) How do you find the most repeated word in a text file in java?

	Code Snippet:
	
		public static void main(String[] args) {
		
			try(Stream<String> stream = Files.lines(Paths.get("")) ) {
				
				List<String> lines = stream.collect(Collectors.toList());
				Stream<String[]> map = lines.stream().map(line -> line.split(" "));
				Stream<String> flatMap = map.flatMap(s -> Arrays.stream(s));
				Map<String, Long> collect = flatMap.collect(Collectors.groupingBy(Function.identity(), Collectors.counting()));
				Entry<String, Long> entry = collect.entrySet().stream().sorted(Map.Entry.<String, Long>comparingByValue().reversed()).findFirst().get();
				
			}catch (Exception e ) {
				
			}
		}
		
	Code Snippet:
		
		public static void main(String[] args) 
		{    
			//Creating wordCountMap which holds words as keys and their occurrences as values
			HashMap<String, Integer> wordCountMap = new HashMap<String, Integer>();
			BufferedReader reader = null;
			try
			{
				//Creating BufferedReader object
				reader = new BufferedReader(new FileReader("C:\\sample.txt"));
				//Reading the first line into currentLine
				String currentLine = reader.readLine();
				while (currentLine != null)
				{    
					//splitting the currentLine into words
					String[] words = currentLine.toLowerCase().split(" ");
					//Iterating each word
					for (String word : words)
					{
						//if word is already present in wordCountMap, updating its count
						if(wordCountMap.containsKey(word))
						{    
							wordCountMap.put(word, wordCountMap.get(word)+1);
						}
						//otherwise inserting the word as key and 1 as its value
						else
						{
							wordCountMap.put(word, 1);
						}
					}
					//Reading next line into currentLine
					currentLine = reader.readLine();
				}
				//Getting the most repeated word and its occurrence
				String mostRepeatedWord = null;
				int count = 0;
				Set<Entry<String, Integer>> entrySet = wordCountMap.entrySet();
				for (Entry<String, Integer> entry : entrySet)
				{
					if(entry.getValue() > count)
					{
						mostRepeatedWord = entry.getKey();
						count = entry.getValue();
					}
				}
				System.out.println("The most repeated word in input file is : "+mostRepeatedWord);
				System.out.println("Number Of Occurrences : "+count);
			} 
			catch (IOException e) 
			{
				e.printStackTrace();
			}
			finally
			{
				try 
				{
					reader.close();           //Closing the reader
				}
				catch (IOException e) 
				{
					e.printStackTrace();
				}
			}
		}    

--------------------------------------------------------------

22.	Program to count vowels and consonants in String

	Code Snippet:
	
		public static void main(String args[]) { 
			System.out.println("Please enter some text");
			Scanner reader = new Scanner(System.in); 
			String input = reader.nextLine(); 
			char[] letters = input.toCharArray(); 
			int count = 0; 
			for (char c : letters){ 
				switch (c) { 
					case 'a': 
					case 'e': 
					case 'i': 
					case 'o': 
					case 'u': 
					count++; 
					break; default: // no count increment 
				} 
			} 
			System.out.println("Number of vowels in String [" + input + "] is : " + count); 
		}


--------------------------------------------------------------




-------------------------------------------------------------------
15) How to convert String to Date in java?
16) How to Optimize Java String Creation?
18) Java program to find the percentage of uppercase, lowercase, digits and special characters in a String

----------------------------------------------------------------
How to sort String on their length in Java? (solution)

	Code Snippet:
	
		public static void main(String[] args) {
				
				String string = "Write a program to check if a String contains another String e.g. indexOf()? (solution)\r\n" + 
						"\r\n" + 
						"Read more: https://javarevisited.blogspot.com/2015/01/top-20-string-coding-interview-question-programming-interview.html#ixzz5dnbssH2h";
				List<String> sortedList = getSortedStringList(string);
				System.out.println(sortedList);
			}
			
			public static List<String> getSortedStringList(String string) {
				List<String> asList = Arrays.asList(string.split("\\s+"));
				
				List<String> collect1 =  asList.stream().sorted((s1, s2) -> Integer.compare(s1.length(), s2.length())).collect(Collectors.toList());
				List<String> collect2 = asList.stream().sorted(Comparator.comparingInt(String::length)).collect(Collectors.toList());
				Arrays.sort(randomString, (s1,s2) -> Integer.compare(s2.length(), s1.length()));
				return collect2;
			}


---------------------------------------------------------------
Write a program to check if a String contains another String e.g. indexOf()?
How to check if a String is valid shuffle of two String?
	
	
	private static boolean isInterleaved(String str1, String str2, String strToCheck) {
   
	  int i=0, j=0, k=0;
	   
	  if(str1.length() + str2.length() != strToCheck.length()){
	   return false;
	  }
	   
	  while(k < strToCheck.length()){
		
		   if( i < str1.length() && str1.charAt(i) == strToCheck.charAt(k)){
			i++;
			
		   }else if(j < str2.length() && str2.charAt(j) == strToCheck.charAt(k)){
			j++;
			
		   }else{
			return false;
		   }	
		   k++;
		  }
		   
		  if(!(i == str1.length() && j == str2.length() && k == strToCheck.length())){
		   return false;
	  }
	   
	  return true;
	 }




























