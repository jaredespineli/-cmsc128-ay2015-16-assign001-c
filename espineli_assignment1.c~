/**
ESPINELI, JARED A.
2013-56981
CMSC 128 AB-2L
PROGRAMMING ASSIGNMENT #1: PROGRAMMING A NUMBER LIBRARY

Functions included:
numToWords()
wordsToNum()
wordsToCurrency()
numberDelimited()

includes a header and a c file
**/

#include<stdio.h>
#include"espineli_assignment1.h"

int main(){
	int menuChoice=5;
	
		while (mainMenu(&menuChoice) != 0) {	// this will always shows the main menu and will only end the loop if choice = 0

		switch (menuChoice) {	// now this will execute the user choice in menuChoice
			case 1: numToWords();	// accepts and converts a whole number in its word form
				break;
			case 2: wordsToNum();	// accepts and converts a number in word form and returns it in numerical form
				break;
			case 3: wordsToCurrency();	// accepts a word form of a number and adds the chosen currency as the prefix
					break;
			case 4: numberDelimiter();	// accepts a whole number then adds a delimiter based on the number of jumps
				break;
		}
	}
	
}
