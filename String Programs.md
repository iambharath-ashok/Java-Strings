# Java String Programs


--------------------------------------------------------
## How to Print duplicate characters from String?

-	Given a word Java printDuplicate Method should print 'a'


	Code Snippet:
	
		public static void printRepeated(String s) {
			Set<Character> set = new HashSet<>();
			for (char ch : s.toCharArray()) {
				if(!set.add(ch)) {
					System.out.print(ch);
				}
			}
		}
---------------------------------------------------------

## Duplicate Frequency:

## How do we find duplicate characters in a string?

	Code Snippet:
 
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

## How to get distinct characters and their count in a String?

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

### How to remove all occurrences of a given character from input String? or Write a program to remove a given characters from String? 

	Code Snippet:

		private static void removeCharFromString(String input, char c) {
			String result = input.replaceAll(String.valueOf(c), "");
			System.out.println(result);
		}

--------------------------------------------------------
	
## How to prove String is immutable programatically?

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
## Write a program to count number of words in a String?

	Code Snippet:
	
		
--------------------------------------------------------

## Write a program to check if two Strings are created with same characters? or  Write Java Program To Check Whether Two Strings Are Anagram Or Not?

### What is Anagram:

-	Two are considered Anagram if they contains same set of characters with same count

	### Algorithm:
		
	-	Remove all special Characters including spaces
	-	Lower case all the Characters
	-	

	Code Snippet:
	
		Spublic class AnagramRegularExpression {

			public static boolean isAnagram(String s1, String s2) {
				s1 = cleanString(s1);
				s2 = cleanString(s2);
				return s1.equals(s2);
			}

			private static String cleanString(String s) {
				s = s.toLowerCase().replaceAll("[^\\w][^\\s]", "");
				s = s.chars().mapToObj(ch -> Character.toString((char) ch)).sorted(Comparator.naturalOrder())
						.collect(Collectors.joining(""));
				return s;
			}

			public static void main(String[] args) {
				boolean isAnagram = isAnagram("aajv", "java");
				System.out.println(isAnagram);
			}

		}
	
	Output:
	
		eeehhllort
		eeehhllort
		true

--------------------------------------------------------
## How to find whether String contains given String or Not?
	
	Code Snippet:
	
		public static boolean contains(String string, String subString) {
			return string.toLowerCase().contains(subString.toLowerCase());
		}
		
-------------------------------------------------------
## How to swap two Strings without using a third variable?

	Code Snippet:
	
		String str1 = "abcd";
		String str2 = "xyz";
		
		str1 = str1.concat(str2);
		str2 = str1.substring(0,str1.length()- str2.length()); // Begin Index Inclusive and End Index is Exclusive
		str1 = str1.substring(str2.length()); // Begin Index
		
		System.out.println("String 1:"+str1);
		System.out.println("String 2:"+str2);
		
		public static void swap(String s1, String s2) {
			s1 = s1.concat(s2);
			s2 = s1.substring(0, s1.length() - s2.length());
			s1 = s1.substring(s2.length(), s1.length());
			System.out.println(s1 + " " + s2);
		}
--------------------------------------------------------		
## Provide two ways to check if a String contains only digits?

	Code Snippet:

			public static boolean containsOnlyDigits(String string) {
			
				// First Way:
				return string.matches("\\d+");
				
				//Second Way:	
				try {
					int i = Integer.parseInt(string);
					return true;
				} catch (Exception e) {
					return false;
				}
			}
--------------------------------------------------------
## How do we remove all white spaces from a String in Java?

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
## Write a Java program to reverse a given string with preserving the position of spaces?


	Algorithm:

		1. 	Create a result array
		2.	Copy all Spaces to Result Array or Maintain Spaces exactly in the same position
		3.	Assign last index  to temp variable j 
		4.	Start from starting of original array and copy it to result array in reverse order
		5.	If char at original array is not equal to ' ' then assign that char to result array
		6.	If result array has ' ' with it decrement it next position
		
		
	
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
## How To Convert String To Integer In Java? or How to convert numeric String to an int?


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
		Integer i = Integer.valueOf(s);	

- 	One is Integer.toString() method and another one is String.valueOf() method
-	Both these methods return string representation of the given integer

	Code Snippet:
	
		int i = 2015;
		String s = String.valueOf(i);
		String s =Integer.toString(i);

		
-------------------------------------------------
## Write a Java program to reverse each word of a given string?

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
		
		
	Code Snippet of 3rd Method:

		public static String reverseEachWord(String s) {
		
			String[] words = s.split("\\s+");
			StringBuilder result = new StringBuilder();
			
			for(String word : words) {
				StringBuilder reverseWord = new StringBuilder(word);
				result.append(reverseWord.reverse().append(" "));
			}
			result.deleteCharAt(result.length() - 1);
			
			
			return result.toString();
		}
----------------------------------------
## Write a code to check whether one string is a rotation of another?
	
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
## Write a Java program to count the total number of occurrences of a given character in a string without using any loop? or How to count occurrence of a given character in String?
	
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
## How do we find first repeated and non-repeated character in the given string in Java?

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
## Write a Java program to append a given string to a text file?

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
		
	

		Code Snippet:

			public static void appendString(String s, String fileName) {

				try {
					FileWriter fw = new FileWriter(new File(fileName), true);
					BufferedWriter bw = new BufferedWriter(fw);
					bw.write(s);
					bw.flush();
					bw.close();
				} catch (IOException e) {
					e.printStackTrace();
				}

			}

			public static void main(String[] args) {
				appendString("Bharath", "Guru.txt");
			}
		
--------------------------------------------------------------		
		
## How do we find the number of characters, words and lines in the given text file in Java?
	
	
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
## How do we find the most repeated word in a text file in java?

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

##	Program to count vowels and consonants in String

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



----------------------------------------------------------------
## How to sort String on their length in Java?

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
				
				List<String> collect1 =  asList.stream().sorted((s1, s2) -> Integer.compare(s1.length(), s2.length())).collect(Collectors.toList()); // First Way
				
				// Second Way
				List<String> collect2 = asList.stream().sorted(Comparator.comparingInt(String::length)).collect(Collectors.toList()); 
				// Third Way
				Arrays.sort(randomString, (s1,s2) -> Integer.compare(s2.length(), s1.length()));
				
				return collect2;
			}


---------------------------------------------------------------
## How to check if a String is valid shuffle of two String? or Write a program to give String is Interleaving of other two Strings?


-	Problem: Given a string 's' and two candidate strings 's1' and 's2'
-	Find if 's' is formed by interleaving of 's1' and 's2'
-	Interleaving is defined as formed by picking characters randomly from s1 and s2 but preserving the order of characters in s1 and s2

-	Example: If s1 = 'ABC' and s2 = 'def', then 'AdBeCf' is an interleaved string.
-	'ABCdef' is also an interleaved string and so is 'ABdeCf'.
-	'AdefCB' is not an interleaved string because the order of 'BC' is not maintained.

	### Algorithm:
	
	-	Check if s1 + s2 = s3, if not return false
	-	Initialize the values of i, j , k to keep track index and length
	-	while till ending length of s3 
	-	check if s1 and s2 follows the order in s3
	-	s3 contains out of scope letter then return false
	-	check if i , j , k equals the length of string
	
	-	Time Complexity : O(n)
		
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

---------------------------------------------------------------
## How to convert an Array to String in Java
	
	Code Snippet:
	
		public static String arrayToString(Sting [] array, String delimiter) {
			
			String string = Arrays.asList(array).collect(Collectors.joining(delimiter));
			return string;
			
			// Second Way is to using StringJoiner
			
			public static void main(String[] args) {
				String[] currencies = {"USD", "INR", "AUD", "GBP"};
			
				StringJoiner sj = new StringJoiner("");
				for (String curr: currencies) {
					sj.add(curr);
				}
				return sj.toString();
				
				
				// Third Way 
				StringBuilder sb = new StringBuilder(); 
					for (String s : array) { sb.append(s).append(delimiter); } 
				result = sb.deleteCharAt(sb.length() - 1).toString();
				return result;
			}	
		}
---------------------------------------------------------------
## Write a java program to count the number of words in a string?

	Code Snippet:
	
		String [] words = string.split("\\s+");
		return words.length;
		
--------------------------------------------------------------------		
## How to convert String to Date in java?

	Code Snippet:
	
		public class DateToString {
	
			public static void dateToString() {
				DateTimeFormatter dtf = DateTimeFormatter.ofPattern("yyyy-MMM-dd");
				LocalDate date = LocalDate.now();
				String dateString = date.format(dtf);
				System.out.println(dateString);
			}
			
			public static void stringToDate() {
				DateTimeFormatter dtf = DateTimeFormatter.ofPattern("dd-MMM-yy");
				String stringDate = "09-Feb-18";
				LocalDate parsedDate = LocalDate.parse(stringDate,dtf);
				System.out.println(parsedDate);
			}
			
			public static void main(String[] args) {
				dateToString();
				stringToDate();
			}

		}

--------------------------------------------------------------------
		
## Java program to find the percentage of uppercase, lowercase, digits and special characters in a String?


	Code Snippet:
		
		public class CharctersPercentage {

			public static void findPercentage(String s) {

				int consonants = 0, digits = 0, upperCase = 0, lowerCase = 0, vowels = 0, specialChar = 0,
						totalChars = s.length();
				List<String> vowelsList = new ArrayList<>(Arrays.asList("a", "e", "o", "i", "u", "A", "E", "O", "I", "U"));

				for (char ch : s.toCharArray()) {
					if (vowelsList.contains(Character.toString(ch)))
						vowels++;
					else if (Character.isLetter(ch))
						consonants++;
					if (Character.isUpperCase(ch))
						upperCase++;
					else if (Character.isLowerCase(ch))
						lowerCase++;
					else if (Character.isDigit(ch))
						digits++;
					else
						specialChar++;
				}

				System.out.println("Upper Case Per: " + (float) upperCase * 100 / totalChars);
				System.out.println("Lower Case Per: " + (float) lowerCase * 100 / totalChars);
				System.out.println("special Chars Per: " + (float) specialChar * 100 / totalChars);
				System.out.println("Digits Per: " + (float) digits * 100 / totalChars);
				System.out.println("Vowels Per: " + (float) vowels *  100 / totalChars);
				System.out.println("consonants Per: " + (float) consonants * 100 / totalChars);

			}

			public static void main(String[] args) {
				findPercentage("India ");
			}

		}


---------------------------------------------------------------
## Write a program to check if a String contains another String e.g. indexOf()?

-	we need to write a function to search for the existence of a string (target) in another string (source)
-   The function takes two strings as the input and returns the index where the second string is found
-	If the target string cannot be found, then return -1
-	We can related its behavior to indexOf() method from java.lang.String class
-	This question is also asked as Code and algorithm to check if a given short string is a substring of a main string
-	Get a linear solution (O(n)) if possible?

-	Use int indexOf(String)
-	Use int lastIndexOf(String)
-	Use boolean contains(String) 
	
	Code Snippet:
	
		String input = "Java is the best programming language"; 
		boolean isPresent = input.indexOf("Java") != -1 ? true : false;
		isPresent = input.indexOf("java") != -1 ? true : false;
		boolean isFound = input.contains("Java");

		
		
-------------------------------------------------------------------
## Write a program to print all permutations of String?

	Code Snippet:
	
		public class PermutationOfString {

			public static void printPermutation(String s) {
				permutation("", s);
			}

			public static void permutation(String permutation, String input) {
				if (input.length() == 0) {
					System.out.println(permutation);
				} else {
					for (int i = 0; i < input.length(); i++) {
						permutation(permutation + input.charAt(i),
								input.substring(0, i) + input.substring(i + 1, input.length()));
					}
				}
			}
			
			public static void main(String[] args) {
				printPermutation("Bharath");
			}

		}
-----------------------------------------------------------		
## Write a function to find out longest palindrome in a given string?

	Code Snippet:
	
		public class PalDemo {

			public static void main(String[] args) {
				PalDemo pd = new PalDemo();
				
				String pal = pd.findLongestPalindrome("bananas");
				System.out.println("" + pal);
				
				pal = pd.findLongestPalindrome("abaradar121");
				System.out.println("" + pal);

			}
			
			public String findLongestPalindrome(String s) {
				// Validations
				if (s.isEmpty()) {
					return "Please enter a String";
				}
			
				if (s.length() == 1) {
					return s;
				}
				// Validations end
				// Start with one char (starting) as a longest palindrome
				String longest = s.substring(0, 1);
				for (int i = 0; i < s.length(); i = i+1) {
					
					// get longest palindrome for odd length (center is i)
					String tmp = checkForEquality(s, i, i);
					if (tmp.length() > longest.length()) {
						longest = tmp;
					}
			
					// get longest palindrome for even length (center is i, i+1)
					tmp = checkForEquality(s, i, i + 1);
					if (tmp.length() > longest.length()) {
						longest = tmp;
					}
				}
			
				return longest;
			}
			
			
			/**
			 * In this method equality is checked starting from
			 * the center moving one character left and one character
			 * right from the center. If both chars are equal then the
			 * next set of chars are checked.  
			 *     
			 */
			public String checkForEquality(String s, int begin, int end) {
				while (begin >= 0 && end <= s.length() - 1 && s.charAt(begin) == s.charAt(end)) {
					begin--;
					end++;
				}
				return s.substring(begin + 1, end);    
			}
		}

---------------------------------------------------------------

## Write a Java program to reverse a String?

	Code Snippet:
	
		public class ReverseRecursive {
	
	
			static String  reverseString = "";
			public static String reverseRecursive(String s) {
				if(s.isEmpty()) {
					return s;
				}
				System.out.println(s.substring(1));
				return reverseRecursive(s.substring(1)) + s.charAt(0);
			}
			
			public static void main(String[] args) {
				reverseRecursive("abcdefghij");
			}

		}

	Order Of Algorithm :
	
		Time complexity: O(n)
------------------------------------------------
## How to Reverse a String using Iterative method?

	Code Snippet:
	
		public static String reverString (String s) {
			String reverseString = "";
			for(int j = s.length() -1; j >= 0; j--) {
				reverseString += s.charAt(j);
			}
			System.out.println(reverseString);
			return reverseString;
		}
	
	Order of Algorithm:
	
		Time Complexity : O(n)

------------------------------------------------
		
## How to check if a String is Palindrome?


	Code Snippet:
	
		public static boolean isPalindrome(String s) {
			for(int i = 0, j= s.length() -1; i < s.length()/2; j--,i++) {
				if(s.charAt(i) == s.charAt(j)) {
					continue;
				} else {
					return false;
				}
			}
			return true;
		}
		
	Order of Algorithm:

		Time Complexity: O(log n)
------------------------------------------------
## How to find duplicate characters in a String?

-	Given String is "Programming" then wer program should print
	
		g : 2
		r : 2
		m : 2

-	Sol: User Java 8 or Create Character Count Map 

---------------------------------------------------

## How to replace each given character to other e.g. blank with %20?

-	For example if the input is "Java is Great" and asked to replace space with %20 then it should be "Java%20is%20Great".

	
	Code Snippet:
	
		public class ReplaceCharWithString {
	
			public static String replaceChar(String s, String charToReplace, String replacingChar) {
				s= s.replaceAll(charToReplace, replacingChar);
				return s;
			}
			
			public static void main(String[] args) {
				String replacedString = replaceChar("Java is Great","\\s+","%20");
				System.out.println(replacedString);
			}
		}
-----------------------------------------------------------

## How  to return highest occurred character in a String? or Find Most Repeated Characters?

	Code Snippet:
	
		public class MostRepeatedChars {

			public static void main(String[] args) {
				String string = "accccddddeeeeeffff";
				
				// Using Java 8 
				Entry<Character, Long> entry = string.chars().mapToObj(ch -> (char) ch)
						.collect(Collectors.groupingBy(Function.identity(), Collectors.counting())).entrySet().stream()
						.sorted(Entry.<Character, Long>comparingByValue().reversed()).findFirst().orElseGet(null);

				System.out.println(entry);

				
				// Using Map with Character Counting
				Map<Character, Integer> map = new HashMap<>();
				for (char ch : string.toCharArray()) {
					Integer charCount = map.get(ch);
					if (charCount == null) {
						map.put(ch, 1);
						continue;
					}
					map.put(ch, ++charCount);
				}

				
				String key = ""; 
				int value = 0;
				for (Iterator<Entry<Character, Integer>> iterator = map.entrySet().iterator(); iterator.hasNext(); ) {
					Entry<Character, Integer> entryKeyValue = iterator.next();
					if(entryKeyValue.getValue() > value) {
						value = entryKeyValue.getValue();
						key = entryKeyValue.getKey().toString();
					}
				}
				
				System.out.println("key: "+ key + ", value: "+ value);

			}

		}

-----------------------------------------------------------
## How to remove all duplicates from a given string? 

	Code Snippet of Completely Removing all the Duplicates:
	
		public class RemoveAllDuplicates {
	
			public static void removeAllDuplicates(String input) {
				Set<Character> chSet = new LinkedHashSet<>();
				
				for(char ch : input.toCharArray()) {
					if(chSet.contains(ch)) {
						chSet.remove(ch);
					} else {
						chSet.add(ch);
					}
				}
				String removedDuplicates = chSet.stream().map(ch -> Character.toString(ch)).collect(Collectors.joining(""));
				System.out.println(removedDuplicates);
			}
			
			public static void main(String[] args) {
				removeAllDuplicates("bharath");
			}

		}


	Code Snippet of Partially Removing Duplicates:
	
		public class RemoveDuplicatesPartially {
	
			public static void main(String[] args) {
				removeDuplicates("bharath");
			}
			
			public static void removeDuplicates(String input) {
				LinkedHashSet<String> stringSet = input.chars().mapToObj(ch -> String.valueOf((char)ch))
						.collect(Collectors.toCollection(LinkedHashSet::new));
				String removedString = stringSet.stream().collect(Collectors.joining(""));
				System.out.println(removedString);
			}

		}
-----------------------------------------------------------
## How to remove characters from the first String which are present in the second String?

	Code Snippet:
	
		public class RemoveCharFromFirstString {
	
			public static void removeChars(String orginal, String second) {
				orginal = orginal.toLowerCase();
				for(char ch : second.toLowerCase().toCharArray()) {
					orginal = orginal.replace(Character.toString(ch), "");
				}
				System.out.println(orginal);
			}
			
			public static void main(String[] args) {
				removeChars("India is great","in");
			}
		}

-----------------------------------------------------------
## How do you check if a given String contains valid parentheses?

	Code Snippet:
	
		public class ValidParanthesis {
	
			public static boolean isValidParenthesis(String input) {
				Stack<Character> stack = new Stack<>();
				for(char ch : input.toCharArray()) {
					switch(ch) {
					
					case '{':
					case '[':
					case '(':
						stack.push(ch);
					break;
					case ']':
						if(stack.isEmpty() || stack.peek() != '[') {
							return false;
						}
						stack.pop();
						break;
					case '}':
						if(stack.isEmpty() || stack.peek() != '{') {
							return false;
						}
						stack.pop();
						break;
					case ')':
						if(stack.isEmpty() || stack.peek() != '(') {
							return false;
						}
						stack.pop();
						break;	
					default:
						break;
					}
				}
				
				return stack.isEmpty();
			}

			
			public static void main(String[] args) {
				boolean isValid = isValidParenthesis("[({})]");
				System.out.println(isValid);
			}
		}

------------------------------------------------------------------

## How to find all possible sub-strings in a String in Java ? 


	Code  Snippets:
	
		public class PrintAllSubStrings {
			
			public static void printSubStrings(String s) {
				
				for(int i = 1; i < s.length(); i++) {
					for(int j = 0; j < s.length() - i;j ++) {
						String subString = s.substring(j, i + j);
						System.out.println(subString);
					}
				}
			}

			
			public static void main(String[] args) {
				printSubStrings("abcd");
			}
		}

		
	Output:
	
		a
		b
		c
		ab
		bc
		abc

	Order of Algorithm:
	
		Time Complexity: O(n^2)
	
		

## Java program to calculate length of a String using recursion?

	Code Snippet:
	
		public class StringDemo {
 
			public static void main(String[] args) {
		 
				System.out.println("Enter a String: ");
				Scanner sc = new Scanner(System.in);
				String s = sc.nextLine();
				sc.close();
				System.out.println("Length of the string is: " + length(s));
			}
		 
			private static int length(String str) {
				if (str.equals(""))
					return 0;
				else
					return length(str.substring(1)) + 1;
			}
		 
		}
		
## Java program to find longest substring without repeating characters in the given string

	Code Snippet:
		
		
		public class LongSubStringWithOutRepeatation {

			public static int findSubstring(String s) {
				s = "helloabcd";
				int j = 0;
				int lenSubstr = 0;
				HashSet<Character> subset = new HashSet<Character>();
				for (int i = 0; i < s.length(); i++) {
					char c = s.charAt(i);
		 
					if (!subset.contains(c)) {
						subset.add(c);
						lenSubstr = Math.max(lenSubstr, subset.size());
					} else {
						while (j < i) {
		 
							if (s.charAt(j) == c) {
								j++;
								break;
							} else {
								subset.remove(s.charAt(j));
								j++;
							}
						}
		 
						subset.add(c);
					}
				}
				System.out.println("Original String = " + s);
				System.out.println("Length of Longest substring = " + lenSubstr);
				
				return lenSubstr;
			}
			
			public static void main(String[] args) {
				findSubstring("Bharath");
			}
			
		}
			
