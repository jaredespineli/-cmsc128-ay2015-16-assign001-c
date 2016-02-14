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

includes x header and x c file
**/

#include <stdio.h>
#include <string.h>

int mainMenu(int *menuChoice) {	// mainMenu


	printf("\n\n------------MAIN MENU-----------\n");
	printf("[1] Convert Number to Words\n");
	printf("[2] Convert Words to Number\n");
	printf("[3] Convert Words to Currency\n");
	printf("[4] Number Delimiter\n");
	printf("[0] Exit Program\n");
	printf("--------------------------------\n");
	printf("Choice: ");
	scanf("%d", menuChoice);

	return *menuChoice;
}

/**************************************************************************************************************/

void numToWords(){ // function used for converting max_charInput to words
	int input, quotient, temp;
	//int skip = 0;
	char *ones[] = {
		 "", "one", "two", "three", "four", "five", "six", "seven", "eight", "nine"
	}; 
	char *ten_thousand[] = {
		 "", "ten", "eleven", "twelve", "thirteen", "fourteen", "fifteen", "sixteen", "seventeen", "eighteen", "nineteen" 
	};
	char *two_digit[] = { 
		"", "ten", "twenty", "thirty", "forty", "fifty", "sixty", "seventy", "eighty", "ninety"
	};
	char *tens_place[] = {
		"ten", "eleven", "twelve", "thirteen", "fourteen", "fifteen", "sixteen", "seventeen", "eighteen", "nineteen" 
	}; 
	
	printf("===============================\n");
	printf("\nDO NOT PUT COMMAS OR SPACES\n");
	printf("Enter number[0-1000000]: "); // asks for input from the user
	scanf("%d", &input);	
	printf("\n===============================\n");
	
	if(input == 0){ // base case: when input = zero, prints zero
		printf("\nRESULT: zero");
	} else if(input > 1000000){ // invalid when input is greater then 1000000
		printf("\n  INVALID INPUT. LIMIT EXCEEDED \n");
	} else{
		printf("\nRESULT: ");
		
		while(input != 0){ // starts loop when the input is greater than 0
			if((input / 1000000) > 0){ // outputs the million place
				quotient = input / 1000000;
				printf("%s million ", ones[quotient]);
				break;
			} 
			
			if((input / 100000) > 0){ // prints the HUNDRED THOUSAND place
				quotient = input / 100000; 
				input = input % 100000; //to remove the hundred thousands place
				
				if(input == 0) printf("%s hundred thousand ", ones[quotient]);
					else if ((input/10000) == 0 && ((input%10000)/1000) == 0) printf("%s hundred thousand ", ones[quotient]);
						else printf("%s hundred ", ones[quotient]);
			}
			
			if((input / 10000) > 0){ // prints the TEN THOUSAND place
				quotient = input / 10000;
				input = input % 10000; // to remove the thousands place

				if(input == 0) printf("%s thousand ", two_digit[quotient]);
					else if (quotient == 1 && input > 1000){
					temp = input / 1000;
					input = input % 1000; // to remove the thousands place
					printf("%s thousand ", ten_thousand[temp+1]);
		//			skip = 1;
						} else printf("%s ", two_digit[quotient]);
			}
			
			if((input / 1000) > 0){ // prints the THOUSAND place
			//		if(skip == 0){
						quotient = input / 1000;
						input = input % 1000; // to remove the thousands place
						printf("%s thousand ", ones[quotient]);
				//}
			}
			
			if((input / 100) > 0){ // prints the HUNDRED place
					quotient = input / 100;
					input = input % 100; // to remove the hundredth place
					printf("%s hundred ", ones[quotient]);
			}
			
			if((input / 10) > 0){ // prints the TENS place
					quotient = input / 10;
					input = input % 10; // to remove the tenth place
						if(quotient == 1){
						printf("%s ", tens_place[input]);
						break;
							} else printf("%s ", two_digit[quotient]);
			}
			
			if((input / 1) > 0){ // prints the ONES place
					quotient = input / 1;
					input = input % 1; // to remove the ones place
					printf("%s ", ones[quotient]);
			}
		}
	}
	printf("\n");	
}

/**************************************************************************************************************/

void wordsToNum(){
	char max_charInput[100];//maximum character size for the input
	char max_charPerWord_Input[20];//maximum character size for each word in the input
	char *array_of_words[20];//array of words contained in the input

	char *ones[10] = {
		"zero", "one", "two", "three", "four", "five", "six", "seven", "eight", "nine"
	};
	char *tens[10] = {
		"ten", "eleven", "twelve", "thirteen", "fourteen", "fifteen", "sixteen", "seventeen", "eighteen", "nineteen"
	};
	char *twentys[10] = {
		"" , "", "twenty", "thirty", "fourty", "fifty", "sixty", "seventy", "eighty", "ninety"
	};
	char *place[3] = {
		"hundred", "thousand", "million"
	};


	long num=0;
	int temp=0, i=0, size=0, x=0, flag=0, final_length=0;
	
	printf("===============================\n");
	printf("\nUSE LOWERCASE LETTERS ONLY\n");
	printf("Enter x number[zero-one million] in word form: "); // asks for input from the user
	getchar();
	fgets(max_charInput, 100, stdin);	
	printf("\n===============================\n");
	
	final_length = strlen(max_charInput);
	max_charInput[final_length-1] = '\0';//removing newline
	printf("\n\tWORD:%s\n", max_charInput);
	array_of_words[i] = strtok(max_charInput," ");//separates each input by spaces
	
	//splits the array of words in the input using strtok and store each in the array of words
	while(array_of_words[i]!=NULL){
	  array_of_words[++i] = strtok(NULL," ");
	   size++;//getting the max_charInput[allowable number] of words
	}
	for(i=0 ; i<size ; i++){//loops while there is still words checked
		if(flag==1){//for thousands place
			flag=0;
			temp=num;//storing the max_charInput to temp
			num=0;
		}
		strcpy(max_charPerWord_Input, array_of_words[i]);//copies the word from the array of words to max_charPerWord_Input
		for(x=0 ; x<10 ; x++){// compare the input word to one-nine
			if(strcmp(max_charPerWord_Input, ones[x])==0){
				num+=x;//adds the equivalent max_charInput to num
				break;
			}
		}
		for(x=0 ; x<10 ; x++){// compare the input word to ten-nineteen 
			if(strcmp(max_charPerWord_Input, tens[x])==0){
				num = num + 10 + x;//adds the equivalent max_charInput to num
				break;
			}
		}
		for(x=0 ; x<10 ; x++){// compare the input word to twent-ninety
			if(strcmp(max_charPerWord_Input, twentys[x])==0){
				num = num + (x*10);//adds the equivalent max_charInput to num
				break;
			}
		}
		for(x=0 ; x<3 ; x++){//comparing the current to the words of max_charInput places
			if(strcmp(max_charPerWord_Input, place[x])==0){
				switch(x){
					case 0: num = num * 100;//adding/multiplying the equivalent max_charInput to num to get the right max_charInput	
							break;
					case 1: num = num * 1000;
							flag=1;//to check if 3 digits are already converted
							break;
					case 2: num = num * 1000000;
							break;
				}
				break;
			}
		}
	}
			num = num + temp ;
			printf("\tRESULT: %ld\n", num);

}

/**************************************************************************************************************/

void wordsToCurrency(){
	char max_charInput[100];//maximum character size for the input
	char max_charCurrency[5];//maximum character size for max_charCurrency in the input
	char max_charPerWord_Input[20];//maximum character size for each word in the input
	char *array_of_words[20];//array of words contained in the input

	char *ones[10] = {
		"zero", "one", "two", "three", "four", "five", "six", "seven", "eight", "nine"
	};
	char *tens[10] = {
		"ten", "eleven", "twelve", "thirteen", "fourteen", "fifteen", "sixteen", "seventeen", "eighteen", "nineteen"
	};
	char *twentys[10] = {
		"", "", "twenty", "thirty", "fourty", "fifty", "sixty", "seventy", "eighty", "ninety"
	};
	char *place[3] = {
		"hundred", "thousand", "million"
	};
	char *array_max_charCurrency[3] = {
		"JPY", "PHP", "USD"
	};

	long num=0;
	int temp=0, i=0, size=0, x=0, flag=0, len=0;
	
	printf("===============================\n");
	printf("\nUSE LOWERCASE LETTERS ONLY [i.e four hundred fifty four PHP/USD/JPY]\n");
	printf("Enter number[zero-one million] in word form with max_charCurrency in the end: "); // asks for input from the user
	getchar();
	fgets(max_charInput, 100, stdin);	
	printf("\n===============================\n");	

	len = strlen(max_charInput);
	max_charInput[len-1] = '\0';//
	printf("\n\tWORD:%s\n", max_charInput);
	array_of_words[i] = strtok(max_charInput," ");//splits the collection of words by spaces
	
	
	/**splits the collection of words through strtok and storing each word to the array of words**/
	while(array_of_words[i]!=NULL)
	{
	   array_of_words[++i] = strtok(NULL," ");
	   size++;//getting the number of words
	}
	for(i=0;i<size;i++){//while there is still word
		if(flag==1){//if thousand word is encountered
			flag=0;
			temp=num;//storing the number to temp
			num=0;
		}
		strcpy(max_charPerWord_Input, array_of_words[i]);//copies the word from the array of words to max_charPerWord_Input
		//printf("%s\n", max_charPerWord_Input);

		for(x=0;x<10;x++){//compare the input word to one-nine
			if(strcmp(max_charPerWord_Input, ones[x])==0){
				num+=x;//adds the equivalent max_charInput to num
				break;
			}
		}
		for(x=0;x<10;x++){//compare the input words to ten-nineteen
			if(strcmp(max_charPerWord_Input, tens[x])==0){
				num = num + 10 + x;//adds the equivalent max_charInput to num
				break;
			}
		}
		for(x=0;x<10;x++){//compare the input words to twenty-ninety
			if(strcmp(max_charPerWord_Input, twentys[x])==0){
				num = num + (x*10);//adds the equivalent max_charInput to num
				break;
			}
		}
		for(x=0;x<3;x++){//comparing the current to the words of max_charInput places
			if(strcmp(max_charPerWord_Input, place[x])==0){
				switch(x){
					case 0: num = num * 100;//adding/multiplying the equivalent max_charInput to num to get the right max_charInput
							break;
					case 1: num = num * 1000;
							flag=1;//check if 3 digits are already converted
							break;
					case 2: num = num * 1000000;
							break;
				}
				break;
			}
		}
		for(x=0;x<3;x++){//compare each word to the array of currency containingPHP, JPY, USD
			if(strcmp(max_charPerWord_Input, array_max_charCurrency[x])==0){
				strcpy(max_charCurrency, max_charPerWord_Input);//copies the currency input by the user to currency
				break;
			}
		}
	}
	num = temp + num;
	printf("\tNumber: %ld %s\n", num, max_charCurrency);
}

/**************************************************************************************************************/

void numberDelimiter(){ // function for adding x single character delimiter to the  
	char number[10], temp[10];
	char delimiter, str;
	int jump;
	int i, k, sizeNum;

	printf("===============================\n");
		printf("Enter number[0-1000000] without commas or anything : \n"); //gets the input from the user
		scanf("%s", number);
		getchar();
		
		printf("Enter a single-character delimiter[i.e , - ; etc.]: "); // gets the delimiter to be used
		scanf("%c", &delimiter);
		
		printf("Enter the number of jumps of places for the delimiter: "); // gets the number of jumps where the delimiter will appear
		scanf("%d", &jump);
		
	printf("\n===============================\n");	

			sizeNum = strlen(number); // to get the string length
			jump = sizeNum - jump; //used to get the position of the jump in the number given by the user
			k = jump + 1; // 

			strcpy(temp, number); // used to copy one string to another string
			
				for(i=jump; i<sizeNum+1; i++){ // loop
					str = temp[i]; // tempory storage of the copied string
					if(i == jump){
						number[i] = delimiter; // used to replaced the stored string with a delimiter
					}
					number[k] = str; // 
					k++; // used to traverse the array by incrementing the index
				}
				
	printf("\n\tOUTPUT: %s\n", number);
	getchar();
}
