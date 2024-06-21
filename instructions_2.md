# Introduction
This lesson will guide you to do a simple game: a number guessing game.
It will cover following features:
1. Input
2. Conditionals
3. Loops

# Input
In the first lesson we saw how to use the output to print information in the console. All the information used during first lecture was in the code.

Now we are going to see how to get information from the user.

First of all, we are going to use the same library we used during first lesson, as it is ```iostream``` that stands for input output stream.

```c++
#include <iostream>

int main() {
  char name[10]; // 10 is the number of characters

  std::cout << "Hello. Tell me your name?\n";
  std::cin >> name;
  std::cout << "\n";
  std::cout << "Hello " << name << ", how are you?\n";  
}
```

This code is going to ask for the user name and say hello to him/her.
Check the sentence ```std::cin >> name;```, this sentence is going to store tha characters provided by the user in the variable name (previously declared).

# Conditionals
At this point we already have a way to show messages to the user and to get information from the user. As we are doing a number guessing game, the user must guess a number. We now how to get a number from the user, but we need a way to know if it is the correct number. 

To be able to do this we are going to use conditionals. Conditionals allow as to evaluate a condition and then execute a block of code or not depending on the condition is met or not.

```c++
#include <iostream>

int main() {
  char name[10]; // 10 is the number of characters
  int number_to_guess = 27; // Number user must guess
  int user_number;

  std::cout << "Hello. Tell me your name?\n";
  std::cin >> name;
  std::cout << "\n";
  std::cout << "Hello " << name << ", try to guess a number 0-99?\n";  

  std::cin >> user_number; // We save the number provided by user
  // Make the conditional
  if (number_to_guess == user_number)
  {
    std::cout << "Congratulations you guessed the number!!";
  }
}
```

Lets focus on the condition:
```c++
  if (number_to_guess == user_number)
  {
    std::cout << "Congratulations you guessed the number!!";
  }
}
```
If number_to_guess is the same as user_number, what it means that the user guessed the number, the following block of code, delimited by ```{ }``` will be executed. Otherwise it won't be executed. This way only when the user guess the number the message will apear.

## else statement
At this point if the user does not guess the feedback when he/she does not guess the number. We can give correct feedback using the else statement.
```c++
  if (number_to_guess == user_number)
  {
    std::cout << "Congratulations you guessed the number!!";
  }
  else
  {
    std::cout << "Sorry, that was not the correct number";
  }  
}
```
This way if the number_to_guess is the same as user_number the first block of code is going to be executed and show the congratulations message. If the numbers are not the same the block of code that is going to be executed is the block after the else keyword.

# Loops
We have our first game, but it is a quite diffcult game, trying to guess a number between 0 and 99 with only one try is quite diffcult. 
What we are going to do is give more tries to the user. To do that we are going to introduce a new feature: loops.

Loops allow us to repeat the execution of code. This way we can ask several times the user to guess the number.

```c++
#include <iostream>

int main() {
  char name[10]; // 10 is the number of characters
  int number_to_guess = 27; // Number user must guess
  int user_number; // variable to store number provided by user
  int tries = 5; // Number of tries

  std::cout << "Hello. Tell me your name?\n";
  std::cin >> name;
  std::cout << "Hello " << name << ", ";
  // Build the loop
  while (tries > 0)
  {
    std::cout << "\n";
    std::cout << "try to guess a number 0-99?\n";  
    std::cin >> user_number; // We save the number provided by user
    // Make the conditional
    if (number_to_guess == user_number)
    {
      std::cout << "Congratulations you guessed the number!!";
    }
    else
    {
      std::cout << "Sorry, that was not the correct number";
    }
    tries = tries -1; //reduce the number of tries
  }  
}
```
We have introduce a loop using the ```while``` keyword. This will make the code repeat meanwhile the condition (tries > 0) is met. It is important to reduce the number of tries inside the code of the loop, otherwise the loop would last forever.

At this point you will see that even if you guess the number the program continues. That is because the only condition to finish the loop is the number of tries.

We are going to introduce a new sentence that will make the loop finish using the ```break;``` sentence inside the ```if``` statement.

```c++
#include <iostream>

int main() {
  char name[10]; // 10 is the number of characters
  int number_to_guess = 27; // Number user must guess
  int user_number; // variable to store number provided by user
  int tries = 5; // Number of tries

  std::cout << "Hello. Tell me your name?\n";
  std::cin >> name;
  std::cout << "Hello " << name << ", ";
  // Build the loop
  while (tries > 0)
  {
    std::cout << "\n";
    std::cout << "try to guess a number 0-99?\n";  
    std::cin >> user_number; // We save the number provided by user
    // Make the conditional
    if (number_to_guess == user_number)
    {
      std::cout << "Congratulations you guessed the number!!";
      break;
    }
    else
    {
      std::cout << "Sorry, that was not the correct number";
    }
    tries = tries - 1; //reduce the number of tries
  }  
}
```

We have almost finish the game, now we are going to add a little help for the user, once he/she make a try, if he/she does not guess the name we are going to provide information about the number to be guessed, we need to tell the user if the number to guess is less than or greater than. 

```c++
#include <iostream>

int main() {
  char name[10]; // 10 is the number of characters
  int number_to_guess = 27; // Number user must guess
  int user_number; // variable to store number provided by user
  int tries = 5; // Number of tries

  std::cout << "Hello. Tell me your name?\n";
  std::cin >> name;
  std::cout << "Hello " << name << ", ";
  // Build the loop
  while (tries > 0)
  {
    std::cout << "\n";
    std::cout << "try to guess a number 0-99?\n";  
    std::cin >> user_number; // We save the number provided by user
    // Make the conditional
    if (number_to_guess == user_number)
    {
      std::cout << "Congratulations you guessed the number!!";
      break;
    }
    else
    {
      if (number_to_guess < user_number)
      {
        std::cout << "Sorry, the number is less than your number";
      }
      else
      {
        std::cout << "Sorry, the number is greater than your number";  
      }
    }
    tries = tries -1; //reduce the number of tries
  }  
}
```

# Random
We have been using a predefined number as number to guess. We are going to use a random number as the number to guess. 

First we need to include a new library ```#include <cstdlib>``` that is going to allow the random function.

Then we are going to call the ```rand()``` function. The rand function is going to return a random integer. We need an integer between 0 and 99, so we are going to use a new operator, the modulus operator: ```%```. This operator is going to return the reminder of a division. So the sentence will be ```rand() % 100```. Now instead of putting the number as a fixed number we will use it.

```c++
#include <iostream>
#include <cstdlib>

int main() {
  char name[10]; // 10 is the number of characters
  int number_to_guess = rand() % 100; // Number user must guess
  int user_number; // variable to store number provided by user
  int tries = 5; // Number of tries

  std::cout << "Hello. Tell me your name?\n";
  std::cin >> name;
  std::cout << "Hello " << name << ", ";
  // Build the loop
  while (tries > 0)
  {
    std::cout << "\n";
    std::cout << "try to guess a number 0-99?\n";  
    std::cin >> user_number; // We save the number provided by user
    // Make the conditional
    if (number_to_guess == user_number)
    {
      std::cout << "Congratulations you guessed the number!!";
      break;
    }
    else
    {
      if (number_to_guess < user_number)
      {
        std::cout << "Sorry, the number is less than your number";
      }
      else
      {
        std::cout << "Sorry, the number is greater than your number";  
      }
    }
    tries = tries -1; //reduce the number of tries
  }  
}
```