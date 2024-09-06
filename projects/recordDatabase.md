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

<div class="text-center p-4" style="position: relative; width: 100%; height: auto; margin: 0; padding: 0;">
  <img class="img-fluid" src="../img/bank-record.jpg" style="width: 100%; height: auto; display: block;">
</div>

</div>

The record database project was created in my Program Structure 3 class (ICS 212) at UH Mānoa, a class in which I learned the C and C++ coding languages. This project creates a database the user can interact with. The user has the ability to add and delete bank records, print all records in the database, and find a particular record. This project was composed of four files: database.c, database.h, record.h, and user_interface.c. 

In C programming, header files help keep code organized. Database.h is a header file that contains the function declarations for the methods used in database.c. These functions include addRecord, printAllRecords, findRecord, and deleteRecord.

Database.c is a file written in C that implements the function declarations from the database.h file. It contains a set of functions that manage a database of bank records, each with account numbers, names, and addresses. The functions allow adding new records (addRecord), printing all records (printAllRecords), finding a record by account number (findRecord), and deleting a record by account number (deleteRecord). When one of the functions is called, database.c will print that function's name, and what record it was called on. The function addRecord can be seen below: 

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


