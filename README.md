#include <stdio.h>
#include <string.h>

struct match
{  
  char name[50];
  int wikets,age;
  float average_score;
  char country[50];
  int category;
  int odi,international;
}player[50];
void swap(struct match *xp, struct match *yp)
{
    struct match temp = *xp;
    *xp = *yp;
    *yp = temp;
}
int main() {
  int n,k,temp,count=0,a1[100],rk;
  float max=0,arr[100],temp1;
  char desh[50];
  
   printf("for how many players you want to fill the information\n");
   scanf("%d",&n);
   for(int i=0;i<n;i++)
   {

     printf("enter the information of %d player\n",i+1);
     printf(" name of player:\n");
     scanf("%s",player[i].name);
     printf(" age of player:\n");
     scanf("%d",&player[i].age);
     printf(" country of player:\n");
     scanf("%s",player[i].country);
     printf(" category of player:\n1=batsman\n2=bowler\n3=wicket_keeper\n4=all_rounder\n");
     scanf("%d",&player[i].category); 
       if(player[i].category==1)
       {
         printf("average batting score:\n");
         scanf("%f",&player[i].average_score);

       }
       else if(player[i].category==2)
       {
         printf("enter no of wikets:\n");
         scanf("%d",&player[i].wikets);
       }
     printf("no of odis played:\n");     
     scanf("%d",&player[i].odi);
      printf(" number of international 20-20 played:\n");
     scanf("%d",&player[i].international);
   }
  do{

     printf("\n1:number of batsman of particular country\n2:sorting batsman as per their average batting score\n3:batsman with higest average score\n4:number of bowlers of particular country\n5:maximum no of wickets that taken by bowler\n6:display board information\n7.exit\n ");
  printf("enter above choice:\n");
  scanf("%d",&k);
   switch(k)
   {   
     case 1:
     printf("enter the name of country to know the no of batsman\n");
     scanf("%s",desh);
     for(int i=0;i<n;i++)
     {
     
     if(strcmp(desh,player[i].country)==0)
       {
         if(player[i].category==1)
     
         count++;
       }
     }
     printf("no of batsman of %s is %d",desh,count);


break;
     case 2:
    
      for ( int i=1;i<n;i++)   {
     for (int j=0;j<n-i;j++){
       
       if (player[j].average_score<player[j+1].average_score)
       {
            swap(&player[j], &player[j+1]);
       }          
} } 
     printf("NAME\t\tAVERAGE_SCORE\n");
     for(int i=0;i<n;i++)
     {
       printf("%s\t\t%f\n",player[i].name,player[i].average_score);

     }
break;
case 3:


  for ( int i=1;i<n;i++)   {
     for (int j=0;j<n-i-1;j++){
       
       if (player[j].average_score<player[j+1].average_score)
       {
            swap(&player[j], &player[j+1]);
       }          
} } 




printf(" batsman with higest  average score is %f",player[0].average_score);

break;
case 4:

     printf("enter the name of country to know the no of bowlers\n");
     scanf("%s",desh);
     for(int i=0;i<n;i++)
     {
     
     if(strcmp(desh,player[i].country)==0)
       {
         if(player[i].category==2)
     
         count++;
       }
     }
     printf("no of bowlers of %s is %d",desh,count);

break;
case 5:

for ( int i=1;i<n;i++)   {
     for (int j=0;j<n-i;j++){
       
       if (player[j].wikets<player[j+1].wikets)
       {
            swap(&player[j], &player[j+1]);
       }          
} } 

printf("HIGHEST WICKET BOWLER : \n");
printf("%s : %d",player[0].name,player[0].wikets);






break;


     case 6:

   printf("NAME \t\tAGE \tCOUNTRY\t\tODI_S_PLAYED\t\tINTERNATIONAL 20-20 \t \n");
   for(int i=0;i<n;i++)
   {
     printf("%s\t\t%d\t\t%s\t\t%d\t\t\t%d\n",player[i].name,player[i].age,player[i].country,player[i].odi,player[i].international);
   }
   break;
   }
  }
while(k!=7);
   }
