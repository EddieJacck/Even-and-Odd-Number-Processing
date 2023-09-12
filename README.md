# Even-and-Odd-Number-Processing

#include <iostream>
#include <fstream>
#include <string>

using namespace std;

bool LoggedIn()//function to validate username and password
{
    string Username, Password, UN, PW;
    cout << "Enter UserName: ";
    cin >> Username;
    cout << "Enter Password: ";
    cin >> Password;

    ifstream read("C:\\Users\\WPU-User\\Desktop\\" + Username + ".txt");//read input from file
    getline(read, UN);//get username being entered for validation
    getline(read, PW);//get password being entered for validation

    if (UN == Username && PW == Password)//validate username and password
    {
        return true;
    }
    else
    {
        cout << "\nIncorrect UserName and Password\n";
        return false;
    }
}

bool checkEvenOdd(int num)//function that takes in
//input number and check whether is it an even or odd number
{
    if (num % 2 == 0)//process entered number using division operation
    {
        return true;
    }
    else
    {
        return false;
    }
}

int main()
{

    int choice; // variable declaration

    while (true)//iterate to the start
    {
    	cout << "\nChoose an option below\n\n";
        cout << "To Register, enter 0.\nTo Login, enter 1.\n\nEnter your option: ";
        cin >> choice; // take in the input choice from the user

        if (choice == 0) // check if choice is 0
        {
            string Username, Password;

            cout << "\nTo Register, please fill your credentials below\n";
            cout << "Enter your UserName: ";
            cin >> Username;
            cout << "Enter your Password: ";
            cin >> Password;

            ofstream file("C:\\Users\\WPU-User\\Desktop\\" + Username + ".txt"); // write data to file
            file << Username << endl << Password; // take Username and Password and store them in the text file
            file.close();

            cout << "\n\nRegistration successful.\n";
        }
        else if (choice == 1)
        {
        	bool status = LoggedIn();//assign to function bool LoggedIn.
        	if (!status)//loop to the external function for validation
        		{
        		cout << "Login Unsuccessful.\n";
        	    continue;//loop to the top if login unsuccessful

        	    }
        	    else
        	    {
        	      int num;//declare variable num.
        	      cout << "Login Successful\n\nEnter Number greater than 1: ";
        	      cin >> num;//take in input entered and store it

        	      bool isEven = checkEvenOdd(num);//assign to the external function
        	      if (isEven)//check if the number entered is an even number
        	         {
        	           cout << num << " is an Even Number\n";
        	         }
        	         else
        	         {
        	                cout << num << " is an Odd Number\n";
        	         }
        	    }

        //break;//stops the program from looping to the top.

        }
        else//if the option entered is not recognize
        {
          cout << "Invalid option.\n";
        }
    }
   return 0;
}
