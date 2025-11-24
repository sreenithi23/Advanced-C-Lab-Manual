## EXP NO: 6 - C PROGRAM PRINT THE LOWERCASE ENGLISH WORD CORRESPONDING TO THE NUMBER

### Aim:
To write a C program print the lowercase English word corresponding to the number

### Algorithm:
1. Start and initialize an integer variable n
2. Input number from user
3. Switch Statement cases
   - Case 1: Print "one"
   - Case 2: Print "two"
   - Case 3: Print "three"
   - Case 4: Print "four"
   - Case 5: Print "five"
   - Case 6: Print "six"
   - Case 7: Print "seven"
   - Case 8: Print "eight"
   - Case 9: Print "nine"
   - Default: Print "Greater than 9"
4. Exit the program

### Program:

```c
#include <stdio.h>

int main() {
    int n;
    
    printf("Enter a number (1-9): ");
    scanf("%d", &n);
    
    switch(n) {
        case 1:
            printf("one\n");
            break;
        case 2:
            printf("two\n");
            break;
        case 3:
            printf("three\n");
            break;
        case 4:
            printf("four\n");
            break;
        case 5:
            printf("five\n");
            break;
        case 6:
            printf("six\n");
            break;
        case 7:
            printf("seven\n");
            break;
        case 8:
            printf("eight\n");
            break;
        case 9:
            printf("nine\n");
            break;
        default:
            printf("Greater than 9\n");
    }
    
    return 0;
}
```

### Output:

![alt text](imgs/image-7.png)

### Result:
Thus, the program is verified successfully.

---

## EXP NO: 7 - C PROGRAM TO PRINT TEN SPACE-SEPARATED INTEGERS IN A SINGLE LINE DENOTING THE FREQUENCY OF EACH DIGIT FROM 0 TO 3

### Aim:
To write a C program to print ten space-separated integers in a single line denoting the frequency of each digit from 0 to 3

### Algorithm:
1. Start
2. Declare char array a[50] outer loop for each digit from 0 to 3
3. Initialize counter c to 0
4. For each character in the string print count c for current digit, followed by a space
5. Increment h to move to the next digit
6. End

### Program:

```c
#include <stdio.h>
#include <string.h>

int main() {
    char a[50];
    int h = 0;
    int len;

    printf("Enter a string: ");
    scanf("%s", a);

    len = strlen(a);

    while (h <= 3) {
        int c = 0;
        for (int i = 0; i < len; i++) {
            if (a[i] == '0' + h) {
                c++;
            }
        }
        printf("%d ", c);
        h++;
    }
    printf("\n");

    return 0;
}
```


### Output:

![alt text](imgs/image-5.png)

### Result:
Thus, the program is verified successfully.

---

## EXP NO: 8 - C PROGRAM TO SORT STRINGS IN LEXICOGRAPHICAL ORDER

### Aim:
To write a C program to sort strings in lexicographical order

### Algorithm:
1. Start
2. Declare variables s (pointer to an array of strings) and n (number of strings)
3. Memory Allocation - Dynamically allocate memory for s to store an array of strings
4. Input - Read the number of strings n from the user and dynamically allocate memory for each string in s
5. Sorting - Use bubble sort to compare and swap strings using strcmp to arrange them in lexicographical order
6. Display the sorted strings
7. Memory Deallocation - Free the memory allocated for each string in s and free the memory allocated for s
8. End

### Program:
```c
#include <stdio.h>

struct StringStruct{
    char str[10];
};

int main(void){
    int size;
    scanf("%d", &size);
    struct StringStruct inp[size];
    for(int i = 0 ; i < size ; i++)
        scanf("%s", inp[i].str);
    if(size % 2 == 0){
        for(int i = 0 ; i < size ; i++){
            for(int j = 0 ; j < size ; j++){
                if(i != j)
                    printf("%s %s ", inp[i].str, inp[j].str);
            }
            printf("\n");
        }
    }
    if(size % 2 != 0){
        for(int i = 0 ; i < size ; i++){
            for(int j = 0 ; j < size ; j++){
                if(i != j){
                    for(int k = 0 ; k < size ; k++)
                        if(i != k && j != k)
                            printf("%s %s %s\n", inp[i].str, inp[j].str, inp[k].str);
                }
            }
        }
    }
    return 0;
}
```


### Output:
![alt text](imgs/image-9.png)

### Result:
Thus, the program is verified successfully.

---

## EXP NO: 9 - C PROGRAM PRINT A PATTERN OF NUMBERS FROM 1 TO N AS SHOWN BELOW

### Aim:
To write a C program to print a pattern of numbers from 1 to n as shown below

### Algorithm:
1. Start
2. Declare integer variables n, i, j, min
3. Read the value of n from the user
4. Calculate the length of the side of the square matrix: len = n * 2 - 1
5. Matrix Generation Loop
6. Calculate min as the minimum distance to the borders
7. End

### Program:

```c
#include <stdio.h>

int main() {
    int n;
    
    printf("Enter n: ");
    scanf("%d", &n);
    
    int len = n * 2 - 1;
    
    for(int i = 0; i < len; i++) {
        for(int j = 0; j < len; j++) {
            int min = i < j ? i : j;
            min = min < len - i ? min : len - i - 1;
            min = min < len - j ? min : len - j - 1;
            printf("%d ", n - min);
        }
        printf("\n");
    }
    
    return 0;
}
```


### Output:
![alt text](imgs/image-6.png)

### Result:
Thus, the program is verified successfully.

---

## EXP NO: 10 - C PROGRAM TO FIND A SQUARE OF NUMBER USING FUNCTION WITHOUT ARGUMENTS WITH RETURN TYPE

### Aim:
To write a C program that calculates the square of a number using a function that does not take any arguments, but returns the square of the number

### Algorithm:
1. Start
2. Define a function square() with no parameters. This function will return an integer value
3. Inside the function:
   - Declare an integer variable to store the number
   - Ask the user to input a number
   - Calculate the square of the number (multiply the number by itself)
   - Return the squared value
4. In the main function:
   - Call the square() function and display the result
5. End

### Program:

```c
#include <stdio.h>

int square() {
    int num;
    
    printf("Enter a number: ");
    scanf("%d", &num);
    
    return num * num;
}

int main() {
    int result = square();
    
    printf("Square: %d\n", result);
    
    return 0;
}
```


### Output:
![alt text](imgs/image-8.png)

### Result:
Thus, the program is verified successfully.



























