#include<stdio.h>
 
int main() {
    int a[10][3];
    int leaderboard[10][3];
    int points[10]={0,0,0,0,0,0,0,0,0,0};
    int points1[10]={0,0,0,0,0,0,0,0,0,0};
    int rating[10]={0,0,0,0,0,0,0,0,0,0};
    int index;
    int max = 0;
    for (int i=0;i<10;i++) //запись новых значение массива
    for (int j=0;j<3;j++)
    {
        printf("a[%d][%d] = \n", i, j);
        scanf("%d", &a[i][j]);
    }
    for (int i=0;i<10;i++) //вывод значений массива
    {
        for (int j=0;j<3;j++)
        {
            printf("%d ",a[i][j]);
        }
        printf("\n");
    }
    for (int i=0;i<10;i++) // подсчет общего колличества очков спортсменнов
    for (int j=0;j<3;j++)
    {
        points[i] += a[i][j];
    }
   
    for (int i=0;i<10;i++) // копирование массива для дальнейшей модификации
        points1[i] = points[i];
    for (int i=0;i<10;i++) // расчет рейтинга спортсменнов и запись в отдельный массив
    {
        for (int j=0;j<10;j++)
        {
            if(max<points1[j])
            {
                max=points1[j];
                index = j;
            }
        }
        rating[i]=index;
        max=0;
        points1[index]=0;
    }
    for (int i=0;i<10;i++) // вывод массива рейтинга
    {
        printf("rating[%d] = %d\n", i,  rating[i]);
    }
    for (int i = 0;i<9;i++) // определение первого места
    {
        int placepoint=0;
        int placepoint1=0;
        int buffer;
        if(points[rating[i]]==points[rating[i+1]])
        {
          for (int j=0;j<3;j++)
          {
            if(a[rating[i]][j]==10)
                placepoint++;
            if(a[rating[i+1]][j]==10)
                placepoint1++;
          }
          if(placepoint<placepoint1)
            buffer = rating[i];
            rating[i]=rating[i+1];
            rating[i+1]=buffer;
        }    
        placepoint=0;
        placepoint1=0;
    }
    printf("Победитель соревнований спортсмен под номером %d\n", rating[0]);
    printf("Второе место: %d",rating[1]);
    printf("Третье место: %d",rating[2]);
    for (int i=0;i<10;i++) // вывод массива общего колличества очков спортсменов
    {
        printf("points[%d] = %d\n", i,  points[i]);
    }
}
