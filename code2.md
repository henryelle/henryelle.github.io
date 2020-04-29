[Home](https://henryelle.github.io) | [Code] hey you're _here!_ | [Studies](https://henryelle.github.io/studies.html) | [Contact](https://henryelle.github.io/contact.html)
### Source file:
```
Molina Yadier 2017 Cardinals 0.273 0.312 0.439
Molina Yadier 2018 Cardinals 0.261 0.314 0.436
Molina Yadier 2019 Cardinals 0.270 0.312 0.399

DeJong Paul 2017 Cardinals 0.285 0.325 0.532
DeJong Paul 2018 Cardinals 0.241 0.313 0.433
DeJong Paul 2019 Cardinals 0.233 0.318 0.444

Carpenter Matt 2017 Cardinals 0.241 0.384 0.451

Carpenter Matt 2018 Cardinals 0.257 0.374 0.523

Carpenter Matt 2019 Cardinals 0.226 0.334 0.392

Wong Kolton 2017 Cardinals 0.285 0.376 0.412
Wong Kolton 2018 Cardinals 0.249 0.332 0.388
Wong Kolton 2019 Cardinals 0.285 0.361 0.423

Goldschmidt Paul 2017 Diamondbacks 0.297 0.404 0.563
Goldschmidt Paul 2018 Diamondbacks 0.290 0.389 0.533

Goldschmidt Paul 2019 Cardinals 0.260 0.346 0.476
```  

### Code
#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>

    typedef struct _Player
    {
        char lastname[16];
        char firstname[16];
        char team[16];
        int year;
        float battingavg;
        float onbase;
        float slugging;
    } Player;

void GetYear(int *yearselected)
{
    scanf("%d", yearselected);
    //if(&yearselected != 2017 || &yearselected != 2018 || &yearselected != 2019)
        //printf("***ERROR. Enter only 2017, 2018, or 2019.\n");

    //return year;
}

void PrintMenu()
{
    printf("*********************\n");
    printf("*Menu               *\n");
    printf("*********************\n");

    printf("1. Print Player Records\n");
    printf("2. Sort by Batting Average\n");
    printf("3. Sort by On-base Percentage\n");
    printf("4. Sort by Slugging Percentage\n");
    printf("5. Filter by Year\n");
    printf("6. Exit\n");
}

void GetPlayers(Player nextup[], int count, int yearselected)
{
    int i;
    int j;
    //int yearselected = 0;
    
    printf("%16s %16s %16s %16s %16s %16s %16s\n", "First Name", "Last Name", "Team", "Year", "Batting Avg", "OnBase Pct", "Slugging Pct" );
    
    for(i = 0; i < count; i++)
    {
        
        if(yearselected == nextup[i].year)
        {
            for(j = 0; j < count; j++);
            {
            printf("%16s %16s %16s %16d %16.3f %16.3f %16.3f\n", 
                nextup[i].firstname,
                nextup[i].lastname,
                nextup[i].team,
                nextup[i].year,
                nextup[i].battingavg,
                nextup[i].onbase,
                nextup[i].slugging);
            }
        }
        
        if(yearselected == 0)
        {
        printf("%16s %16s %16s %16d %16.3f %16.3f %16.3f\n", 
                nextup[i].firstname,
                nextup[i].lastname,
                nextup[i].team,
                nextup[i].year,
                nextup[i].battingavg,
                nextup[i].onbase,
                nextup[i].slugging);
        }
     
    }
    

}

void SortOBP(Player nextup[], int count)
{
    int pass;
    int j;
    for(pass = 1; pass < count; pass++)
    {
        for(j = 0; j < count - 1; j++)
        {
            Player temp;
            if(nextup[j].onbase < nextup[j + 1].onbase)
            {
                temp = nextup[j];
                nextup[j] = nextup[j + 1];
                nextup[j + 1] = temp;
            }
        }
    }
}

void SortBattingAvg(Player nextup[], int count)
{
    int pass;
    int j;
    for(pass = 1; pass < count; pass++)
    {
        for(j = 0; j < count - 1; j++)
        {
            Player temp;
            if(nextup[j].battingavg < nextup[j + 1].battingavg)
            {
                temp = nextup[j];
                nextup[j] = nextup[j + 1];
                nextup[j + 1] = temp;
            }
        }
    }
}

void SortSlug(Player nextup[], int count)
{
    int pass;
    int j;
    for(pass = 1; pass < count; pass++)
    {
        for(j = 0; j < count - 1; j++)
        {
            Player temp;
            if(nextup[j].slugging < nextup[j + 1].slugging)
            {
                temp = nextup[j];
                nextup[j] = nextup[j + 1];
                nextup[j + 1] = temp;
            }
        }
    }
}

void SortYear(Player nextup[], int count)
{
    int pass;
    int j;
    for(pass = 1; pass < count; pass++)
    {
        for(j = 0; j < count - 1; j++)
        {
            Player temp;
            if(nextup[j].year < nextup[j + 1].year)
            {
                temp = nextup[j];
                nextup[j] = nextup[j + 1];
                nextup[j + 1] = temp;
            }
        }
    }
}


int main(void)
{
    int i;
    FILE *fp;
    Player nextup[24];
    //Player nextup1[24];
    int count = 0;
    fp = fopen("baseballstats.dat", "r");
    int selection = 0;
    int yearselected = 0;

    //for(i = 0; i != -777; i++)

    if(fp)
    {
        while(!feof(fp))
        {
            if(7 == fscanf(fp, "%s %s %d %s %f %f %f",
                               nextup[count].lastname,
                               nextup[count].firstname,
    //GetPlayers(Player);
                               &(nextup[count].year),
                               nextup[count].team,
                               &(nextup[count].battingavg),
                               &(nextup[count].onbase),
                               &(nextup[count].slugging)
                               ))
            {
            count++;
            }
        }
        
        fclose(fp);

        printf("*** Initially: \n");
        GetPlayers(nextup, count, yearselected);

        for(i = 0; i != -1; i++)
        {
        PrintMenu();
        scanf("%d", &selection);

        switch(selection)
        {
            case 1:
                GetPlayers(nextup, count, yearselected);
                break;
            case 2:
                SortBattingAvg(nextup, count);
                break;
            case 3:
                SortOBP(nextup, count);
                break;
            case 4:
                SortSlug(nextup, count);
                break;
            case 5:
                printf("Enter a year to filter by: ");
                GetYear(&yearselected);
                break;
            case 6:
                return 0;
            default:
                printf("\nERROR! That's not a valid selection.\n\n");
                break;
        }
        }
    }
    
}
```
[Home](https://henryelle.github.io) | [Code] hey you're _here!_ | [Studies](https://henryelle.github.io/studies.html) | [Contact](https://henryelle.github.io/contact.html)
More code: [Code](code.md)


