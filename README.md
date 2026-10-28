# Code Smells Section Assignment 

## Group Members: Ryan Funk, Jason Garabedian, Jenny Wong

___

## Smell 1 - Duplicated Code (pg 72)

```C++
//=================================//
    BEFORE: Duplicated Code Smell
//=================================//
//#include <cctype> //add libary header to use toupper()
void input(char answers[], int size) {
    //condense printing
    cout << "Please enter the student's answers for each of the questions.\n"; 
    cout << "Press Enter after typing each answer.\n";
    cout << "Please enter only an A, B, C, D or a, b, c, d for each question.\n";

    for (int i = 0; i < size; i++) {
        cout << "Question " << (i + 1) << ": ";
        cin >> answers[i];

        //add answers[i] = toupper(answers[i]);

        //change while loop to do while loop
        while (answers[i] != 'A' && answers[i] != 'B' 
               && answers[i] != 'C' && answers[i] != 'D'
               && answers[i] != 'a' && answers[i] != 'b'       //remove && answers[i] != 'a' && answers[i] != 'b' 
               && answers[i] != 'c' && answers[i] != 'd') {    //remove && answers[i] != 'c' && answers[i] != 'd'
            cout << "Use only an A, B, C, D or a, b, c, d!\n"; //add if statement to verify valid answers
            cout << "Please try again.\n";                     //condense printing
            cout << "Question " << (i + 1) << ": ";            //remove duplicated code
            cin >> answers[i];                                 //remove duplicated code
        } 
    }
}
//================//
    AFTER: Fixed
//================//
#include <cctype> 
void input(char answers[], int size) {
    cout << "Please enter the student's answers for each of the questions.\n"
         << "Press Enter after typing each answer.\n"
         << "Please enter only an A, B, C, D or a, b, c, d for each question.\n";

    for (int i = 0; i < size; i++) {
        do { 
            cout << "Question " << (i + 1) << ": ";
            cin >> answers[i];
            answers[i] = toupper(answers[i]);

            if(answers[i] != 'A' && answers[i] != 'B' 
               && answers[i] != 'C' && answers[i] != 'D'){
                cout << "Use only an A, B, C, D or a, b, c, d!\n" 
                     << "Please try again.\n";
               }
        } while (answers[i] != 'A' && answers[i] != 'B' 
               && answers[i] != 'C' && answers[i] != 'D');
    }
}
```

The code above is an example of Duplicated Code smells. Duplicated Code smell is repetitive code that appears multiple times throughout a program. It arises from repeated application of the same logic. This can be problematic since it can overtime make code more difficult to maintain, which increases the potential risk of inconsistent changes and errors. 

Duplicated code smell can be prevented by extracting repeated statements into functions or classes and using loops or iteration to name a few.

Reduced readability, increase maintenance difficulty, and increased risk of errors are problems that this duplicated code smell example creates. This duplicated code smell can be fix by using toupper() function to help eliminate the need to check both cases for each letter, and a do while loop that helps eliminate the repeated logic of prompted the user for answers before and during the loop. These changes help to improve the readability, maintainability, and help to reduce the risk of other errors down the line.
___

## Smell 2 - Mysterious Name (pg 72) (C#)

Mysterious Name code smells are caused by when a programmer uses any random name or letter as a variable, while not describing what that variable means, making it very difficult to actually know what it is, and what it affects.

Practices for preventing these code smells are using descript names for variables, or including comments that tell the user or another programmer what those variables actually are.

```C#
// This is a movement script for a Unity GameObject written in C#
public class MovementScript : MonoBehaviour
{
    public float x = 5f; // change x to moveSpeed
    public float y = 180f; // change y to rotationSpeed
    private Vector2 movementInput;
    public void OnMove(InputValue value)
    {
        movementInput = value.Get<Vector2>();
    }
    void Update()
    {
        float z = movementInput.y; // change z to moveInput
        float x2 = movementInput.x; // change x2 to rotateInput
        transform.Translate(Vector3.forward * z * x * Time.deltaTime, Space.Self); // change z to moveInput and x to moveSpeed
        transform.Rotate(Vector3.up * x2 * y * Time.deltaTime); // change x2 to rotateInput and y to rotationSpeed
    }
}
```
___

## Smell 3 - Comments (pg 84) (Python)

```python
# ==========================================
# COUNTER INCREMENT FUNCTION
# ==========================================
# This function is used to increment a count by one.
# It takes an integer parameter and returns an integer.
def increment_counter(current_count):
    # Check if the counter is initialized
    if current_count is not None:
        # Add 1 to the current count variable
        new_count = current_count + 1  # Increments by 1
        
        # Return the newly calculated count back to the caller
        return new_count 
    else:
        # If it is None, return 0
        return 0

```
The code above is an example of the code smell comments. The code is overly commented which means it might be hiding bad code, which this code is. The function is self explanatory and only really needs one comment to explain what is doing, rather than a comment on each line explaining every part of the function. If the code required comments on every line, it should be be refactored using an extract function to make the starting function simpler. In this case, all thats needed is to simplify the syntax of the code and trim the comments to be more concise. 






