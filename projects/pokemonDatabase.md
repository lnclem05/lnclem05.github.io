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
  - Back-End Development
summary: "This assignment entails building a database of Pokemon objects"
---

<div class="text-center p-4">
  <img width="400px" class="rounded float-start pe-4" src="../img/pokemon.webp">
</div>

The Pokemon database project was created in my Program Structure 3 class (ICS 212) at UH Mānoa, a class in which I learned the C and C++ coding languages. This project creates a database the user can interact with. This database holds Pokémon objects and, when prompted by the user, can add Pokémon to the database. Furthermore, it can read a list of Pokémon objects from a text file and import them into the database, as well as printing the current database to a text file. This project was comprised of four files that worked collaboratively: driver.c, iofunctions.c, iofunctions.h, and pokemon.h. 

The drier.c file was a file written in C that interacted with the user by prompting the user to insert a new Pokemon's level and name. If the user inputs a valid level and name, the Pokemon is added to the database, if the input is invalid an error is thrown. 

```cpp
while (stop != -1 && numpokemons < 5){
        printf("\nPlease insert new pokemon's level: ");
        if (scanf("%d", &pokemonbank[numpokemons].level) == 1){
            getchar();
            printf("\nPlease insert new pokemon's name: ");
            fgets(pokemonbank[numpokemons].name, sizeof(pokemonbank[numpokemons]).name , stdin);
            pokemonbank[numpokemons].name[strlen(pokemonbank[numpokemons].name)- 1] = '\0';
            numpokemons++;
            if (numpokemons < 5){
                printf("\nWould you like to input another pokemon? 0 for yes and -1 for no: ");
                if (scanf("%d", &choice) != 1){
                    printf("\nInvalid input\n");
                    stop = -1;
                    val = -1;
                }
                else if (choice != -1 && choice != 0){
                    printf("\nInvalid input\n");
                    stop = -1;
                    val = -1;
                }
                else if (choice == -1){
                    stop = -1;
                    val = 0;
                    valid = 0;
                }
            }
        }
        else{
            printf("\nInvalid input\n");
            stop = -1;
            val = -1;
        }
    }
```

The iofunctions.c file is also written in C and contains two methods writefile and readfile. Writefile prints the current contents of the database to 

Here is some code from the iofunctions.c file that illustrates how a text file can be imported into the database:

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
