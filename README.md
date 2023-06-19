#include <stdio.h>

#include <stdlib.h>

#include <conio.h>

void display();

void input();

void logic();

int i, j, height,width,value;

int endGame;

int x, y, flag=0;

int main()

{

    printf("!!Welcome to ROBOT MOVE!!\n");

    printf("Please enter AREA value: ");

    scanf("%d", &value);

    height = value;

    width = height;

    if(value>0){

        printf("Movement key: \n");

        printf("   [W]   \n");

        printf("[A][S][D]\n");

        printf("Enter movement key to start: ");

        endGame = 0;

        x = height / 2;

        y = width / 2;

        while(!endGame){

            display();

            input();

            logic();

        }

        return 0;

    }

}

void display()

{

    if(flag>0){

        system("cls");

        int posx,posy;

        posx = value/2 - x;

        posy = y - value/2;

        printf("[Position]  x | y: %d,%d\ , posy,posx ");

        for (i = 0; i < height; i++) {

            for (j = 0; j < width; j++) {

                if (i == 0 || i == width -1 || j == 0 || j == height -1){

                    printf("0");

                }

                else {

                    if (i == x-1 && j == y-1)

                        printf("R");

                    else{

                        printf(".");

                    }

                }

            }

            printf("\n");

            flag = 0;

        }

        printf("Press [x] to exit game..");

    }

}

void input()

{

    if(kbhit()){

        switch(getch()){

        case 'a':

            flag = 1;

            break;

        case 's':

            flag = 2;

            break;

        case 'd':

            flag = 3;

            break;

        case 'w':

            flag = 4;

            break;

        case 'x':

            system("cls");

            printf("\\\\Bye byeee!!!!\\");

            endGame = 1;

            break;

        }

    }

}

void logic()

{

    switch(flag){

    case 1:

        y--;

        break;

    case 2:

        x++;

        break;

    case 3:

        y++;

        break;

    case 4:

        x--;

        break;

    default:

        break;

    }

    if(x < 0 || x > height || y < 0 || y > width){

        endGame = 1;

    }

}
