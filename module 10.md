## EXP NO: 16 - C PROGRAM TO SEARCH A GIVEN ELEMENT IN THE GIVEN LINKED LIST

### Aim:
To write a C program to search a given element in the given linked list

### Algorithm:
1. Define the structure for a node in a linked list
2. Define the search function to find a specific character in the linked list
3. Initialize the head of the linked list as needed
4. Call the search function and perform other linked list operations as needed

### Program:

```c
#include <stdio.h>
#include <stdlib.h>

struct node {
    int data;
    struct node *next;
};

struct node *head = NULL;

int search(int val) {
    struct node *temp = head;
    int pos = 0;
    
    while(temp != NULL) {
        if(temp->data == val) {
            return pos;
        }
        temp = temp->next;
        pos++;
    }
    
    return -1;
}

int main() {
    int n, val, search_val;
    struct node *temp, *newnode;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    for(int i = 0; i < n; i++) {
        printf("Enter element %d: ", i + 1);
        scanf("%d", &val);
        
        newnode = (struct node *)malloc(sizeof(struct node));
        newnode->data = val;
        newnode->next = NULL;
        
        if(head == NULL) {
            head = newnode;
            temp = head;
        } else {
            temp->next = newnode;
            temp = newnode;
        }
    }
    
    printf("Enter element to search: ");
    scanf("%d", &search_val);
    
    int pos = search(search_val);
    
    if(pos != -1) {
        printf("Element found at position %d\n", pos);
    } else {
        printf("Element not found\n");
    }
    
    return 0;
}
```

### Output:
![alt text](imgs/image-15.png)

### Result:
Thus, the program to search a given element in the given linked list is verified successfully.

---

## EXP NO: 17 - PROGRAM TO INSERT A NODE IN A LINKED LIST

### Aim:
To write a C program to insert a node in a linked list

### Algorithm:
1. Define the structure for a node in a linked list
2. Define the insert function to insert a new node with character data at the end of the linked list
3. Initialize the head of the linked list as needed
4. Call the insert function and perform other linked list operations as needed

### Program:

```c
#include <stdio.h>
#include <stdlib.h>

struct node {
    int data;
    struct node *next;
};

struct node *head = NULL;

void insert(int val) {
    struct node *newnode, *temp;
    
    newnode = (struct node *)malloc(sizeof(struct node));
    newnode->data = val;
    newnode->next = NULL;
    
    if(head == NULL) {
        head = newnode;
    } else {
        temp = head;
        while(temp->next != NULL) {
            temp = temp->next;
        }
        temp->next = newnode;
    }
}

void display() {
    struct node *temp = head;
    
    printf("Linked list: ");
    while(temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->next;
    }
    printf("\n");
}

int main() {
    int n, val;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    for(int i = 0; i < n; i++) {
        printf("Enter element %d: ", i + 1);
        scanf("%d", &val);
        insert(val);
    }
    
    display();
    
    return 0;
}
```

### Output:
![alt text](imgs/image-16.png)

### Result:
Thus, the program to insert a node in a linked list is verified successfully.

---

## EXP NO: 18 - C PROGRAM TO TRAVERSE A DOUBLY LINKED LIST

### Aim:
To write a C program to traverse a doubly linked list

### Algorithm:
1. Initialize a temporary pointer (temp) to the head of the list
2. Use a while loop to traverse the list until the end (temp == NULL) is reached
3. Inside the loop, print the data of the current node
4. Move to the next node by updating the temp pointer to point to the next node (temp = temp->next)

### Program:

```c
#include <stdio.h>
#include <stdlib.h>

struct node {
    int data;
    struct node *next;
    struct node *prev;
};

struct node *head = NULL;

void traverse() {
    struct node *temp = head;
    
    printf("Doubly linked list: ");
    while(temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->next;
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
        newnode->next = NULL;
        newnode->prev = NULL;
        
        if(head == NULL) {
            head = newnode;
            temp = head;
        } else {
            temp->next = newnode;
            newnode->prev = temp;
            temp = newnode;
        }
    }
    
    traverse();
    
    return 0;
}
```

### Output:
![alt text](imgs/image-17.png)

### Result:
Thus, the program to traverse a doubly linked list is verified successfully.

---

## EXP NO: 19 - C PROGRAM TO INSERT AN ELEMENT IN DOUBLY LINKED LIST

### Aim:
To write a C program to insert an element in doubly linked list

### Algorithm:
1. Create a new node (newNode) and allocate memory for it
2. Set the data of the new node to the provided value
3. If the list is empty, set the new node as the head
4. If the list is not empty, traverse the list to find the last node
5. Set the new node's prev pointer to the last node and update the last node's next pointer to the new node

### Program:

```c
#include <stdio.h>
#include <stdlib.h>

struct node {
    int data;
    struct node *next;
    struct node *prev;
};

struct node *head = NULL;

static struct node* create_node(int val) {
    struct node *newnode = (struct node *)malloc(sizeof(struct node));
    if (!newnode) {
        fprintf(stderr, "Memory allocation failed\n");
        exit(1);
    }
    newnode->data = val;
    newnode->next = NULL;
    newnode->prev = NULL;
    return newnode;
}

void insert_end(int val) {
    struct node *newnode = create_node(val);
    if(head == NULL) {
        head = newnode;
        return;
    }
    struct node *temp = head;
    while(temp->next != NULL) {
        temp = temp->next;
    }
    temp->next = newnode;
    newnode->prev = temp;
}

void insert_begin(int val) {
    struct node *newnode = create_node(val);
    if (head == NULL) {
        head = newnode;
        return;
    }
    newnode->next = head;
    head->prev = newnode;
    head = newnode;
}

void insert_at_pos(int val, int pos) {
    if (pos <= 1 || head == NULL) {
        insert_begin(val);
        return;
    }
    struct node *temp = head;
    int idx = 1;
    while (temp->next != NULL && idx < pos - 1) {
        temp = temp->next;
        idx++;
    }
    if (temp->next == NULL) {
        // position beyond length -> append at end
        insert_end(val);
        return;
    }
    struct node *newnode = create_node(val);
    newnode->next = temp->next;
    newnode->prev = temp;
    temp->next->prev = newnode;
    temp->next = newnode;
}

void display() {
    struct node *temp = head;
    
    printf("Doubly linked list: ");
    while(temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->next;
    }
    printf("\n");
}

int main() {
    int n, val;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    for(int i = 0; i < n; i++) {
        printf("Enter element %d: ", i + 1);
        scanf("%d", &val);
        insert_end(val);
    }
    
    printf("Before insertion:\n");
    display();

    int choice, pos;
    printf("Choose insertion type (1-begin, 2-end, 3-position): ");
    scanf("%d", &choice);
    printf("Enter value to insert: ");
    scanf("%d", &val);
    if (choice == 1) {
        insert_begin(val);
    } else if (choice == 2) {
        insert_end(val);
    } else if (choice == 3) {
        printf("Enter position (1-based): ");
        scanf("%d", &pos);
        insert_at_pos(val, pos);
    } else {
        printf("Invalid choice, inserting at end by default.\n");
        insert_end(val);
    }

    printf("After insertion:\n");
    display();
    
    return 0;
}
```

### Output:
![alt text](imgs/image-19.png)

### Result:
Thus, the program to insert an element in doubly linked list is verified successfully.

---

## EXP NO: 20 - C FUNCTION TO DELETE A GIVEN ELEMENT IN THE GIVEN LINKED LIST

### Aim:
To write a C function that deletes a given element from a linked list

### Algorithm:
1. Check if the Linked List is Empty
   - If the head of the linked list is NULL, print a message indicating the list is empty and exit the function
2. Traverse the Linked List
   - Start from the head node and iterate through the list to find the node that contains the given element (data)
3. Handle Deletion of the First Node
   - If the element to be deleted is found in the head node:
     - Update the head of the linked list to point to the next node (i.e., head = head->next)
     - Free the memory allocated to the node to be deleted
     - Exit the function
4. Traverse and Delete from the Middle or End
   - If the element is not in the head node, continue traversing the list by checking each node's next pointer
   - When the node with the element is found, update the previous node's next pointer to point to the next node of the node to be deleted (prev->next = current->next)
   - Free the memory allocated to the node to be deleted
5. Handle the Case when the Element is Not Found
   - If the element is not found in any node, print a message indicating the element is not present in the list
6. End the Function

### Program:




EXP NO:20 C FUNCTION TO DELETE A GIVEN ELEMENT IN THE GIVEN LINKED LIST




Aim:
To write a C function that deletes a given element from a linked list.

Algorithm:
1.	Check if the Linked List is Empty:
o	If the head of the linked list is NULL, print a message indicating the list is empty and exit the function.
2.	Traverse the Linked List:
o	Start from the head node and iterate through the list to find the node that contains the given element (data).
3.	Handle Deletion of the First Node:
o	If the element to be deleted is found in the head node:
	Update the head of the linked list to point to the next node (i.e., head = head->next).
	Free the memory allocated to the node to be deleted.
	Exit the function.
4.	Traverse and Delete from the Middle or End:
o	If the element is not in the head node, continue traversing the list by checking each node’s next pointer.
o	When the node with the element is found, update the previous node’s next pointer to point to the next node of the node to be deleted (prev->next = current->next).
o	Free the memory allocated to the node to be deleted.
5.	Handle the Case when the Element is Not Found:
o	If the element is not found in any node, print a message indicating the element is not present in the list.
6.	End the Function.


Program:

```c
#include <stdio.h>
#include <stdlib.h>

struct node {
    int data;
    struct node *next;
};

struct node *head = NULL;

void delete(int val) {
    struct node *temp, *prev;
    
    if(head == NULL) {
        printf("List is empty\n");
        return;
    }
    
    if(head->data == val) {
        temp = head;
        head = head->next;
        free(temp);
        printf("Element deleted\n");
        return;
    }
    
    temp = head;
    while(temp != NULL && temp->data != val) {
        prev = temp;
        temp = temp->next;
    }
    
    if(temp == NULL) {
        printf("Element not found\n");
        return;
    }
    
    prev->next = temp->next;
    free(temp);
    printf("Element deleted\n");
}

void display() {
    struct node *temp = head;
    
    printf("Linked list: ");
    while(temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->next;
    }
    printf("\n");
}

int main() {
    int n, val, del_val;
    struct node *temp, *newnode;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    for(int i = 0; i < n; i++) {
        printf("Enter element %d: ", i + 1);
        scanf("%d", &val);
        
        newnode = (struct node *)malloc(sizeof(struct node));
        newnode->data = val;
        newnode->next = NULL;
        
        if(head == NULL) {
            head = newnode;
            temp = head;
        } else {
            temp->next = newnode;
            temp = newnode;
        }
    }
    
    printf("Before deletion:\n");
    display();
    
    printf("Enter element to delete: ");
    scanf("%d", &del_val);
    delete(del_val);
    
    printf("After deletion:\n");
    display();
    
    return 0;
}
```

### Output:
![alt text](imgs/image-18.png)

### Result:
Thus, the function that deletes a given element from a linked list is verified successfully.





