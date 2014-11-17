//wordCount
//=========
// Ajeet Bains
// 9 Nitrogen 
import java.io.*;
import java.net.*;
import java.util.*;
public class WordCountSubmit {
  public static void main(String[] args) throws IOException, MalformedURLException {
    URL url = new URL("http://basisphoenix.azurewebsites.net/wp-content/uploads/2014/11/battleship.txt");
    Scanner input = new Scanner(url.openStream());
    String txt = "";
// create an ArrayList of type String to store the unique words
//-----> YOUR CODE HERE
    ArrayList<String> list = new ArrayList<String>();
// create an ArrayList of type Integer to store the count of each time the unique word appears
//-----> YOUR CODE HERE
    ArrayList<Integer>listcount = new ArrayList<Integer>();
    while(input.hasNextLine()) {
// get the next line from the input file
      txt = input.nextLine();
// print the original input
      System.out.println(txt);
      System.out.println();
// call your method countUniqueWords
//-----> YOUR CODE HERE
      countUniqueWords(list, listcount, txt);
// print out number of unique words found, like: "Number of unique words: 23"
//-----> YOUR CODE HERE
      System.out.println("number of unique words: "+list.size());
      System.out.println();
      System.out.println("Count\tWord ");
// for each word in your ArrayList of unique words, print the count followed by a tab and the word
//-----> YOUR CODE HERE
      for(int a = 0; a < listcount.size();a++)
      {
        System.out.println(listcount.get(a) + "\t" + list.get(a));
        System.out.println();
      }                    
    }
    input.close();
  }
// COMPLETE method countUniqueWords - use wordList to store the unique words in String input with a length > 3 and
// wordCount to count the number of occurances of each unique word.
//
// Parameters:
// wordList - an ArrayList of type String to store a sorted list of unique words in the String input
// wordCount - an ArrayList of type Integer to store a list of the for each unique word in the String input
// input - String of text to be processed
// Return Type: void
  public static void countUniqueWords(ArrayList<String> wordList, ArrayList<Integer> wordCount, String input) {
    Scanner getWords = new Scanner(input).useDelimiter("[\\W]");
    int index = 0;
    String word = "";
// while getWords has more text
    while(getWords.hasNext())
    {
      word = getWords.next();
// get next word as lower case 
      word = word.toLowerCase();
// if length of word > 3 characters 
      if(word.length() > 3)
      {
        
// if wordList contains the word
        if(wordList.contains(word))
        {
          
// geAt index of the word in the ArrayList
          index = wordList.indexOf(word);
// increment the word count at the same index in ArrayList wordCount
          //add 1 to index
          wordCount.set(index, wordCount.get(index) +1);
          
// else
        }
        else
        {
          wordList.add(word);
          wordCount.add(1);
        }
      }
    }
    
// add word and count of 1 to wordList and wordCount, respectively
//
//-----> YOUR CODE HERE
    getWords.close();
// sort wordList alphabetically, don't forget you will need to swap the values of wordCount
    for(int i=0; i<wordList.size()-1;i++)
    {
      String temp=" ";
      int b=0;
      if(wordList.get(i).compareTo(wordList.get(i+1))>0);
      {
        temp=wordList.get(i);
        wordList.set(i, wordList.get(i+1));
        wordList.set(i+1, temp);
        b=wordCount.get(i);
        wordCount.set(i, wordCount.get(i+1));
        wordCount.set(i+1, b);
        i = 0;
      }
    }
// anytime you swap values in wordList
//-----> YOUR CODE HERE
  }
}



