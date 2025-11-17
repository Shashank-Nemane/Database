Problem statement:

Create an employee database using structure and display information, design a c program to display the information of all employees in a company sorted by their salaries from highest to lowest.Each employee information including their employee ID and salary is sorted in a database using arrays and structures. The program should read the employee data from the database, organize it based on their salaries and then print the details of each employee in descending order of their salaries .Additionally the program should handle ties in salaries and provide a consistent method for sorting the employees.

Research:

Links:
1)https://www.geeksforgeeks.org/dbms/introduction-of-dbms-database-management-system-set-1/

2)https://www.geeksforgeeks.org/dbms/what-is-database/

3)https://www.geeksforgeeks.org/c/structures-c/

Data:
 Data is raw information — a collection of facts, numbers, or observations about things that happen or exist. On its own, data doesn’t mean much. But when it’s organized and analyzed, it turns into useful information that helps people make decisions and solve problems.
Database:
 A database stores information in an organized way so it’s easy to find, update, and manage. It works with a Database Management System (DBMS), which is software that helps users interact with the data safely and efficiently.

Uses of Database:
Databases are the engine behind every digital experience—whether you are building an app, training AI models, or running infrastructure at scale. Here is a breakdown of the most suitable database types for various technology domains:
1. Databases for Web Development
2. Databases for Mobile Development
3. Databases for Data Engineering
4. Databases for Data Science
5. Databases for Artificial Intelligence

Database management system:

DBMS is a software system that manages, stores, and retrieves data efficiently in a structured format.
It allows users to create, update, and query databases efficiently.
Ensures data integrity, consistency, and security across multiple users and applications.
Reduces data redundancy and inconsistency through centralized control.
Supports concurrent data access, transaction management, and automatic backups
DBMS has 6 components:
1)Hardware 
2)Software
 3)Data
 4)Procedures 
5)Database Access Language
6)People


Analysis:

Structure:
In C programming, a structure is a user-defined data type that lets you combine different kinds of data into a single unit. It’s created using the struct keyword. Each item inside a structure is called a member, and these members can have different data types.
Structures are really useful when you want to represent something complex that has multiple attributes. For example, in sorting candidates for hiring, you could use structures to represent deciding factors, such as CGPA,12th,10th grade,etc.They’re also essential in building more advanced data structures such as linked lists and trees, which are used in many real-world applications.
Sorting:
Sorting means arranging the elements of an array or list in a particular order — for example, from smallest to largest or alphabetically. To do this, a comparison operator is used to decide how each element should be placed relative to the others. In simple terms, sorting helps organize data so it’s easier to search, analyze, or display.
Types of sorting:

We use bubble sort.


Ideate:

A company aims to reduce the number of candidates proceeding to the first round of selection. To achieve this, candidates can be sorted and filtered based on key deciding factors, represented using structures. These factors include CGPA, 12th-grade marks, 10th-grade marks, and other relevant criteria.
By organizing candidate information in a structured format, the company can efficiently compare applicants and shortlist only those who meet the desired academic thresholds for the first round.

Code:

#include<stdio.h>
#include<string.h>
  struct student
    {
     char name[50];
     int roll;
     float cgpa;
     float twelve;
     float tenth;
     };
     struct student temp;
void first(struct student s[],int n1);
void second(struct student s[],int n2);
void third(struct student s[],int n3);
void output(struct student s[],int n);
 int main()
 {int num,i,j;
     printf("Enter no.of students to compare. ");
     scanf("%d",&num);
     printf("\n");
     struct student s[100];
     for(i=0;i<num;i++)
     {
      printf("Enter details for %d student: \n",i+1);
      printf("Enter name : ");
      scanf("%s",&s[i].name);
      roll:
      printf("Enter roll.no. ");
      scanf("%d",&s[i].roll);
      if(s[i].roll<=0)
      {
          printf("Invalid Input , enter again.\n");
          goto roll;
      }
      cgpa:
      printf("Enter CGPA : ");
      scanf("%f",&s[i].cgpa);
      if(s[i].cgpa<=0 || s[i].cgpa>10)
      {
          printf("Invalid Input , enter again.\n");
          goto cgpa;
      }
      twelve:
      printf("Enter 12th marks : ");
      scanf("%f",&s[i].twelve);
      if(s[i].twelve<0 || s[i].twelve>100)
      {
          printf("Invalid Input , enter again.\n");
          goto twelve;
      }
      tenth:
      printf("Enter 10th marks : ");
      scanf("%f",&s[i].tenth);
      if(s[i].tenth<0 || s[i].tenth>100)
      {
          printf("Invalid Input , enter again.\n");
          goto tenth;
      }
      printf("\n");
     }
     first(s,num);
     return 0;
     }  
 void first(struct student s[],int n1)
     {
     int i,j;
     for(i=0;i<n1-1;i++)
     {
     for(j=0;j<n1-i-1;j++)
     {
     if (s[j].cgpa<s[j+1].cgpa)
     {
      temp=s[j];
      s[j]=s[j+1];
      s[j+1]=temp;
     }
     }
     }
        second(s,n1);
     }
     
     
     
   void second(struct student s[],int n2)
     {
     int i,j;
     for(i=0;i<n2-1;i++)
     {
     for(j=0;j<n2-i-1;j++)
     {
     if (s[j].cgpa==s[j+1].cgpa && s[j].twelve<s[j+1].twelve)
     {
      temp=s[j];
      s[j]=s[j+1];
      s[j+1]=temp;
     }
     }
     }
      third(s,n2);
     }
     
  void third(struct student s[],int n3)
     {
     int i,j;
     for(i=0;i<n3-1;i++)
     {
     for(j=0;j<n3-i-1;j++)
     {
     if (s[j].cgpa==s[j+1].cgpa && s[j].twelve==s[j+1].twelve && s[j].tenth<s[j+1].tenth)
     {
      temp=s[j];
      s[j]=s[j+1];
      s[j+1]=temp;
     }
     }
     }
      output(s,n3);
     }
     
   void output(struct student s[],int N)
     {
      int j;
      printf("\n");
      printf("Students sorted in descending order of CGPA then 12th marks then 10th marks  : \n");
      for(j=0;j<N;j++)
     {
      printf("\nRank: %d\n Name : %s \n Roll.no. %d \n CGPA: %.2f \n 12th: %.2f \n 10th: %.2f\n",j+1,s[j].name,s[j].roll,s[j].cgpa,s[j].twelve,s[j].tenth);
     }
     }
    

TEST:

Case 1: Comparing cgpa

Enter no.of students to compare. 3

Enter details for 1 student: 
Enter name : shashank
Enter roll.no. 37
Enter CGPA : 9
Enter 12th marks : 100
Enter 10th marks : 70

Enter details for 2 student: 
Enter name : kushal
Enter roll.no. 39
Enter CGPA : 10
Enter 12th marks : 90
Enter 10th marks : 80

Enter details for 3 student: 
Enter name : utkarsh
Enter roll.no. 33
Enter CGPA : 8
Enter 12th marks : 98
Enter 10th marks : 78


Students sorted in descending order of CGPA then 12th marks then 10th marks  : 

Rank: 1
 Name : kushal 
 Roll.no. 39 
 CGPA: 10.00 
 12th: 90.00 
 10th: 80.00

Rank: 2
 Name : shashank 
 Roll.no. 37 
 CGPA: 9.00 
 12th: 100.00 
 10th: 70.00

Rank: 3
 Name : utkarsh 
 Roll.no. 33 
 CGPA: 8.00 
 12th: 98.00 
 10th: 78.00


Case 2: Comparing 12th marks

Enter no.of students to compare. 3

Enter details for 1 student: 
Enter name : shashank
Enter roll.no. 37
Enter CGPA : 9
Enter 12th marks : 80
Enter 10th marks : 70

Enter details for 2 student: 
Enter name : kushal
Enter roll.no. 39
Enter CGPA : 9
Enter 12th marks : 90
Enter 10th marks : 67

Enter details for 3 student: 
Enter name : utkarsh
Enter roll.no. 33
Enter CGPA : 9
Enter 12th marks : 100
Enter 10th marks : 80


Students sorted in descending order of CGPA then 12th marks then 10th marks  : 

Rank: 1
 Name : utkarsh 
 Roll.no. 33 
 CGPA: 9.00 
 12th: 100.00 
 10th: 80.00

Rank: 2
 Name : kushal 
 Roll.no. 39 
 CGPA: 9.00 
 12th: 90.00 
 10th: 67.00

Rank: 3
 Name : shashank 
 Roll.no. 37 
 CGPA: 9.00 
 12th: 80.00 
 10th: 70.00


Case 3: Comparing 10th marks

Enter no.of students to compare. 3

Enter details for 1 student: 
Enter name : shashank
Enter roll.no. 37
Enter CGPA : 9
Enter 12th marks : 80
Enter 10th marks : 90

Enter details for 2 student: 
Enter name : kushal
Enter roll.no. 39
Enter CGPA : 9
Enter 12th marks : 80
Enter 10th marks : 95

Enter details for 3 student: 
Enter name : utkarsh
Enter roll.no. 33
Enter CGPA : 9
Enter 12th marks : 80
Enter 10th marks : 100


Students sorted in descending order of CGPA then 12th marks then 10th marks  : 

Rank: 1
 Name : utkarsh 
 Roll.no. 33 
 CGPA: 9.00 
 12th: 80.00 
 10th: 100.00

Rank: 2
 Name : kushal 
 Roll.no. 39 
 CGPA: 9.00 
 12th: 80.00 
 10th: 95.00

Rank: 3
 Name : shashank 
 Roll.no. 37 
 CGPA: 9.00 
 12th: 80.00 
 10th: 90.00
