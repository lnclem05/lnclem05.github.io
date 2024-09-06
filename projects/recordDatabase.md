---
layout: project
type: project
image: img/bank-record.jpg
title: "Bank Record Database"
date: 2014
published: true
labels:
  - Database
  - C
  - Back-End Development
summary: "Building a database of bank records"
---
<div class="text-center p-4">
  <img width="500px" img height = "400px" class="rounded float-start pe-4" src="../img/bank-record.jpg">
</div>
The record database was a solo project I created in my Program Structure 3 class (ICS 212) at UH Mānoa, a class in which I learned the C and C++ coding languages. This project creates a bank record database connected by a linked list that the user can interact with. The user has the ability to add and delete bank records, print all records in the database, and find a particular record. This project was composed of four files: database.c, database.h, record.h, and user_interface.c. 

In C programming, header files help keep code organized. Record.h is a header file that contains the data structure of a record such as account number, name, address, and a pointer to the next record in the database. The record structure can be seen here:

```cpp
struct record
{
    int accountno;
    char name[30];
    char address[50];
    struct record* next;
};
```

Database.h is a header file that contains the function declarations for the methods used in database.c. These functions include addRecord, printAllRecords, findRecord, and deleteRecord.

Database.c is a file written in C that implements the function declarations from the database.h file. It contains a set of functions that manage a database of bank records, each with account numbers, names, and addresses. The functions allow adding new records to the linked list (addRecord), printing all records (printAllRecords), finding a record by account number (findRecord), and deleting a record from the linked list by account number (deleteRecord). When one of the functions is called, database.c will print that function's name, and what record it was called on. The function addRecord can be seen below: 

```cpp
void addRecord(struct record ** record, int num, char name[], char address[]){
    if (debugmode == 1){
        printf("\n===============================================");
        printf("\nstruct record** records");
        printf("\naddRecord executed");
        printf("\nnum == %d", num);
        printf("\nname[] == %s", name);
        printf("\naddress[] == %s", address);
        printf("\n===============================================");
    }
}
```

User_interface.c is also written in C and interacts with the user to create a database of records connected by a linked list. It allows users to input commands such as adding, printing, finding, and deleting records associated with account numbers. It contains the functions main as well as getaddress which returns the address typed by the user without any new line characters. The function's code can be seen below:

```cpp
void getaddress(char add[], int len){
    char buffer[80];
    int size;
    char scan;

    size = 0;

    printf("\nPlease enter an address and when finished type a '.': ");
    do{
        scan = fgetc(stdin);
        buffer[size] = scan;
        size++;
    }
    while (scan != '.' && size < len - 1);

    buffer[size - 1] = '\0';

    /*store it in name*/
    strncpy(add, buffer, size);
    add[size - 1] = '\0';

    if (debugmode == 1){
        printf("\n===============================================");
        printf("\ngetaddress executed");
        printf("\nchar name[] == %s", add);
        printf("\nint len == %d", len);
        printf("\n===============================================");
    }
}
```

This project taught me how to design and manage a simple database, improving my understanding of core concepts like linked lists and data validation. It also strengthened my ability to handle user input, ensuring that the program responds correctly to both valid and invalid data. Additionally, completing this project in C challenged me to learn new ways of input validation. This required me to improve my troubleshooting capabilities, an essential skill for larger, more complex projects.




