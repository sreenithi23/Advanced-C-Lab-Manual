## EXP NO: 26 - C PROGRAM TO DISPLAY STACK ELEMENTS USING LINKED LIST

### Aim:
To write a C program to display stack elements using linked list

### Algorithm:
1. Define a structure Node with two members: data to store the integer value and next to point to the next node in the linked list
2. Declare a global variable head representing the starting node of the linked list
3. Define a function display to print the elements of the linked list
4. Declare a pointer p and initialize it with the head of the linked list
5. Use a while loop to traverse the linked list
6. Print the data of the current node
7. Move to the next node using the next pointer

### Program:

```c
#include <stdio.h>
#include <stdlib.h>

struct node {
    int data;
    struct node *next;
};

struct node *head = NULL;

void display() {
    struct node *p = head;
    
    if(p == NULL) {
        printf("Stack is empty\n");
        return;
    }
    
    printf("Stack elements: ");
    while(p != NULL) {
        printf("%d ", p->data);
        p = p->next;
    }
    printf("\n");
}

int main() {
    int n, val;
    struct node *temp, *newnode;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    for(int i = 0; i < n; i++) {
        printf("Enter element %d: ", i + 1);
        scanf("%d", &val);
        
        newnode = (struct node *)malloc(sizeof(struct node));
        newnode->data = val;
        newnode->next = head;
        head = newnode;
    }
    
    display();
    
    return 0;
}
```

### Output:
![alt text](imgs/image-25.png)

### Result:
Thus, the program to display stack elements using linked list is verified successfully.

---

## EXP NO: 27 - C PROGRAM TO POP AN ELEMENT FROM THE GIVEN STACK USING LINKED LIST

### Aim:
To write a C program to pop an element from the given stack using liked list

### Algorithm:
1. Check for Empty Stack
2. If head is equal to NULL, Print "Stack is empty."
3. Else Proceed to the next step
4. Set head to point to the next node in the stack

### Program:

```c
#include <stdio.h>
#include <stdlib.h>

struct node {
    int data;
    struct node *next;
};

struct node *head = NULL;

void pop() {
    struct node *temp;
    
    if(head == NULL) {
        printf("Stack is empty\n");
        return;
    }
    
    temp = head;
    printf("Popped element: %d\n", temp->data);
    head = head->next;
    free(temp);
}

int main() {
    int n, val;
    struct node *newnode;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    for(int i = 0; i < n; i++) {
        printf("Enter element %d: ", i + 1);
        scanf("%d", &val);
        
        newnode = (struct node *)malloc(sizeof(struct node));
        newnode->data = val;
        newnode->next = head;
        head = newnode;
    }
    
    printf("Before pop:\n");
    struct node *p = head;
    while(p != NULL) {
        printf("%d ", p->data);
        p = p->next;
    }
    printf("\n");
    
    pop();
    
    printf("After pop:\n");
    p = head;
    while(p != NULL) {
        printf("%d ", p->data);
        p = p->next;
    }
    printf("\n");
    
    return 0;
}
```

### Output:
![alt text](imgs/image-26.png)

### Result:
Thus, the program to pop an element from the given stack using liked list is verified successfully.

---

## EXP NO: 28 - C PROGRAM TO DISPLAY QUEUE ELEMENTS USING LINKED LIST

### Aim:
To write a C program to display queue elements using linked list.
Algorithm:
1.	Check if Queue is Empty
3.	Display Queue Elements
4.	Print the data of the current node pointed to by front
5.	Update front to point to the next node.
6.	End the display function.
 
### Program:

```c
#include <stdio.h>
#include <stdlib.h>

struct node {
    int data;
    struct node *next;
};

struct node *front = NULL;
struct node *rear = NULL;

void display() {
    struct node *temp = front;
    
    if(front == NULL) {
        printf("Queue is empty\n");
        return;
    }
    
    printf("Queue elements: ");
    while(temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->next;
    }
    printf("\n");
}

int main() {
    int n, val;
    struct node *newnode;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    for(int i = 0; i < n; i++) {
        printf("Enter element %d: ", i + 1);
        scanf("%d", &val);
        
        newnode = (struct node *)malloc(sizeof(struct node));
        newnode->data = val;
        newnode->next = NULL;
        
        if(front == NULL) {
            front = rear = newnode;
        } else {
            rear->next = newnode;
            rear = newnode;
        }
    }
    
    display();
    
    return 0;
}
```

### Output:
![alt text](imgs/image-27.png)

### Result:
Thus, the program to display queue elements using linked list is verified successfully.

---

## EXP NO: 29 - C PROGRAM TO INSERT ELEMENTS IN QUEUE USING LINKED LIST

### Aim:
To write a C program to insert elements in queue using linked list

### Algorithm:
1. Allocate Memory for New Node
2. Set Data and Next Pointer
3. Check if Queue is Empty
4. Set both front and rear to point to the new node p
5. Set the next pointer of the current rear to point to the new node p
6. End of Enqueue Operation

### Program:

```c
#include <stdio.h>
#include <stdlib.h>

struct node {
    int data;
    struct node *next;
};

struct node *front = NULL;
struct node *rear = NULL;

void enqueue(int val) {
    struct node *p;
    
    p = (struct node *)malloc(sizeof(struct node));
    p->data = val;
    p->next = NULL;
    
    if(front == NULL) {
        front = rear = p;
    } else {
        rear->next = p;
        rear = p;
    }
    
    printf("%d inserted to queue\n", val);
}

int main() {
    int n, val;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    for(int i = 0; i < n; i++) {
        printf("Enter element %d: ", i + 1);
        scanf("%d", &val);
        enqueue(val);
    }
    
    printf("Queue elements: ");
    struct node *temp = front;
    while(temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->next;
    }
    printf("\n");
    
    return 0;
}
```

### Output:
![alt text](imgs/image-28.png)

### Result:
Thus, the program to insert elements in queue using linked list is verified successfully.

---

## EXP NO: 30 - C FUNCTION TO FIND THE PEEK OF QUEUE USING LINKED LIST

### Aim:
The aim of this function is to retrieve the "peek" (the front element) of a queue implemented using a linked list

### Algorithm:
1. Check if the queue is empty
   - If the queue is empty (i.e., the front pointer is NULL), return an error or a message indicating that the queue is empty
2. Access the front element
   - If the queue is not empty, return the data stored in the front node of the linked list (i.e., the element at the head of the queue)

### Program:

```c
#include <stdio.h>
#include <stdlib.h>

struct node {
    int data;
    struct node *next;
};

struct node *front = NULL;
struct node *rear = NULL;

int peek() {
    if(front == NULL) {
        printf("Queue is empty\n");
        return -1;
    }
    
    return front->data;
}

int main() {
    int n, val;
    struct node *newnode;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    for(int i = 0; i < n; i++) {
        printf("Enter element %d: ", i + 1);
        scanf("%d", &val);
        
        newnode = (struct node *)malloc(sizeof(struct node));
        newnode->data = val;
        newnode->next = NULL;
        
        if(front == NULL) {
            front = rear = newnode;
        } else {
            rear->next = newnode;
            rear = newnode;
        }
    }
    
    int front_val = peek();
    if(front_val != -1) {
        printf("Front element (peek): %d\n", front_val);
    }
    
    return 0;
}
```

### Output:
![alt text](imgs/image-29.png)

### Result:
Thus, the program to retrieve the "peek" (the front element) of a queue implemented using a linked list is verified successfully.


