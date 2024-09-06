---
layout: project
type: project
image: img/pokemon.webp
title: "Pokemon Database"
date: 2024-09-05
published: true
labels:
  - C
  - Database
  - Back-end Development
summary: "This assignment entails building a database of Pokemon objects"
---

<div class="text-center p-4">
  <img width="400px" class="rounded float-start pe-4" src="../img/software_developer.jpg">
</div>
This project, completed in my ICS212 class at UH Mānoa, creates a database the user can interact with. This database holds Pokémon objects and, when prompted by the user, can add and delete Pokémon to and from the database. Furthermore, it can read a list of Pokémon objects from a text file and import them into the database, as well as printing the current database to a text file.

Here is some code that illustrates how we read values from the line sensors:

```cpp
int readfile(struct pokemon pokearray[], int* num, char filename[])
{
    FILE *infile;
    int val;
    int count;

    count = 0;
    infile = fopen(filename, "r");

    if (infile != NULL){
        while (count < *num){
            if (fscanf(infile, "%d", &pokearray[count].level) != EOF){
                if (fscanf(infile, "%s", pokearray[count].name) != EOF){
                    count++;
                }
                else{
                    val = -1;
                }
            }
            else{
                val = -1;
            }
        }

        fclose(infile);
    }
    else{
        val = -1;
    }

    if (val != -1){
        writefile(pokearray, count, "in.txt");
        *num = count;
        val = 0;
    }
    return val;
}

```

