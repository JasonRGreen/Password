# Password
This program pompts the user to enter a password that   must be 6 characters long, have one lowercase and uppercase letter, and    contains one numerical digit
#include <iostream>
#include <string>

using namespace std;

int main()
{
	string password;																// first/original password
	string password2;																// password input for confirmation
	int lowercasecounter;															// counts the number of lowercase characters
	int uppercasecounter;															// counts uppercase characters
	int digitcounter;																// counts the number of digits

	
/*All inside a loop so that if the user makes a mistake they can try again*/
	do
	{ 	lowercasecounter = 0;
		uppercasecounter = 0;
		digitcounter = 0;

		cout <<"Enter your password: ";
	    cin >> password;
		
		for(size_t i = 0; i<password.size(); i++ )
		{

			if(islower(password[i]))												// when the character is a lowercase increment counter by 1
			lowercasecounter++;
	
			if (isupper(password[i]))												// when the character is an uppercase increment counter by 1
			uppercasecounter++;
	
			if (isdigit(password[i]))												// when the character is a digit increment counter by 1
			digitcounter++;
		}
		
		if (password.size()<6)														// when string size is less than 6 characters
			cout << "Password needs to have 6 or more characters. \n";
	    if (lowercasecounter == 0)													// when the counter is 0 or there are no lowercase characters
			cout << "Password needs to contain at least one lowercase letter. \n";
	    if (uppercasecounter == 0)													// when the counter is 0 or there are no uppercase characters
			cout << "Password needs to contain at least one uppercase letter. \n";
	    if (digitcounter == 0)														// when the counter is 0 or there are no digits
			cout << "Password needs to contain at least one digit. \n";

	} while ((password.size()<6 || lowercasecounter==0 || uppercasecounter==0 || digitcounter==0));
		

	/*when the user inputs a password that meets all the conditions*/
	if (password.size()>=6 && lowercasecounter!=0 && uppercasecounter !=0 && digitcounter !=0)
		cout << "Now re-enter your password for verification: ";
	
	/*once all conditions are met the user must re-enter their passord*/
		cin >> password2;														
	
	if (password != password2)														//passwords must match or the user will be asked to do it all over again
			cout << "Password does not match. Start over. \n";
		else 
			cout << "You have now entered a valid password \n"; 


	

	return 0;
}
