# Code Smells Section Assignment 

## Group Members: Ryan Funk, Jason Garabedian, Jenny Wong

___

## Smell 1 - Global Data (pg 74 - 75) or Duplicated Code (pg 72)

___

## Smell 2 - Mysterious Name (pg 72) (C#)

```C#
// This is a movement script for a Unity GameObject written in C#
public class MovementScript : MonoBehaviour
{
    public float x = 5f;
    public float y = 180f;
    private Vector2 movementInput;
    public void OnMove(InputValue value)
    {
        movementInput = value.Get<Vector2>();
    }
    void Update()
    {
        float z = movementInput.y;
        float x2 = movementInput.x;
        transform.Translate(Vector3.forward * z * x * Time.deltaTime, Space.Self);
        transform.Rotate(Vector3.up * x2 * y * Time.deltaTime);
    }
}
```

The code above is an example of Myseterious Name code smells. The code is full of randomly named variables that another person reading has no idea of knowing what these actually mean or reference. 
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






