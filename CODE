#include<stdio.h>
#include<stdlib.h>
#include<stdbool.h>
#include<string.h>

static int count=0;
struct employee
{
    int id;
	char name[100];
	float salary;
	struct employee *next;
}*head=NULL,*last=NULL;



void countEmployee()
{
	printf("\nTotal Employee count = %d",count);
}
void readLinkedList()
{
	FILE* file;
    file = fopen ("database.txt", "r");
    if (file == NULL)
    {
        fprintf(stderr, "\nLocal Employee Database not found.'\n");
    }
	else
	{
		printf("\nLocal Employee Database founded.");
		printf("\nLoading employee data......");
		struct employee *temp=(struct employee *)malloc(sizeof(struct employee));
		head=last=NULL;
		count=0;
		while(fread(temp, sizeof(struct employee), 1, file))
    	{
        	if(head==NULL)
        	{
            	head = last = (struct employee *)malloc(sizeof(struct employee));

        	}
        	else
        	{
            	last->next = (struct employee *)malloc(sizeof(struct employee));
            	last = last->next;
        	}
        	last->id = temp->id;
        	strcpy(last->name, temp->name);
			last->salary = temp->salary;
        	last->next = NULL;
			count++;
        
    	}
		printf("\nLoading completed.\n");
    	fclose(file);
	}
}

void writeLinkedList(){
    
    struct employee* temp = head;
    
    FILE* file;
    file = fopen ("database.txt", "w");
	printf("\nSaving in database.");
    while(temp!=NULL)
    {
        fwrite(temp, sizeof(struct employee), 1, file);
        temp = temp->next;
    }
    
    if(fwrite != 0)
    {
        printf("\nEmployee data updated in the database.");
    }
    else
    {
        printf("\nError While Writing");
    }
    
    fclose(file);
    
}

void create()
{
	struct employee *t;
	int num;
	printf("\nHow many Employee do you want's to add:- ");
	scanf("%d",&num);

	while(num--)
	{
		if(head!=NULL)
		{
			t=(struct employee*)malloc(sizeof(struct employee));
		}
		else
		{
			t=(struct employee*)malloc(sizeof(struct employee));
			head=t;
			last=t;
		}
		fflush(stdin);
		printf("Enter employee name:- ");
		scanf(" %[^\n]s",&t->name);
		fflush(stdin);
		printf("Enter employee id:- ");
		scanf("%d",&t->id);
		printf("Enter employee salary:- ");
		scanf("%f",&t->salary);
        printf("\n");
        if(count>0)
        {
            t->next=NULL;
		    last->next=t;
		    last=t;
        }
        else
        {
            t->next=NULL;
            last=t;
        }
		count++;
	}
	writeLinkedList();

}

bool deleteById()
{
	int id;
	printf("Input id:- ");
	scanf(" %d",&id);

	struct employee *p=NULL,*q=NULL;
	p=head;
	while (p)
	{
		if(p->id==id)
		{
			if(q!=NULL)
			{
				q->next=p->next;
				count--;
				free(p);
				
			}
			else
			{
				head=p->next;
				count--;
				free(p);
				
			}
			printf("\nEmployee removed.");
			writeLinkedList();
			return true;
		}
		q=p;
		p=p->next;
	}
	printf("\nEmployee not found.");
	return false;
	
}

bool deleteByName()
{
	char name[100];
	fflush(stdin);
	printf("Input name:- ");
	scanf(" %[^\n]s",&name);
	fflush(stdin);

	struct employee *p=NULL,*q=NULL;
	p=head;

	while (p)
	{
		if(strcmp(p->name,name)==0)
		{
			if(q!=NULL)
			{
				q->next=p->next;
				count--;
				free(p);
				
			}
			else
			{
				head=p->next;
				count--;
				free(p);
				
			}
			printf("\nEmployee removed.");
			writeLinkedList();
			return true;
		}
		q=p;
		p=p->next;
		
	}
	printf("\nEmployee not found.");
	return false;
	
}


bool searchById()
{
	int id;
	printf("Input id:- ");
	scanf(" %d",&id);
	struct employee *p=NULL;
	p=head;
	while (p)
	{
		if(p->id==id)
		{
			printf("\nEmployee founded, details of employee are\n");
			printf("Name of the employe is:- %sId is:- %d\nSalary is:- %.4f",p->name,p->id,p->salary);
			return true;
		}
		p=p->next;
	}
	printf("\nEmployee not found");
	return false;
	
}


bool searchByName()
{
	char name[100];
	fflush(stdin);
	printf("Input name:- ");
	scanf(" %[^\n]s",&name);
	// printf("%s",name);
	fflush(stdin);
	struct employee *p=NULL;
	p=head;
	while (p)
	{
		if(strcmp(p->name,name)==0)
		{
			printf("\nEmployee founded, details of employee are\n");
			printf("Name of the employe is:- %sId is:- %d\nSalary is:- %.4f",p->name,p->id,p->salary);
			return true;
			
		}
		p=p->next;
	}
	printf("\nEmployee not found");
	return false;
	
}

bool updateDetails()
{
	struct employee *p=NULL;
	p=head;
	int id;
	printf("Input id:- ");
	scanf("%d",&id);
	while (p)
	{
		if(p->id==id)
		{
			printf("Employee found.\n");
			bool flag=true;
			while(flag)
			{
				int choice;
				fflush(stdin);
				printf("\n0.Exit \n1.Update Name:- \n2.Update Id:- \n3.Update salary:- \n");
				scanf("%d",&choice);
				if(choice==1)
				{
					fflush(stdin);
					printf("Enter new name:- ");
					scanf(" %[^\n]s",&p->name);
					fflush(stdin);
					printf("Name updated:- \n");
				}
				else if(choice==2)
				{
					printf("Enter new id:- ");
					scanf(" %d",&p->id);
					printf("Id updated:- \n");
				}
				else if(choice==3)
				{
					printf("Enter new salary:- ");
					scanf(" %f",&p->salary);
					printf("Salary updated:- \n");
				}
				else if(choice==0)
				{
					flag=false;
				}
				else
				{
					printf("Wrong choice \n");
					flag=false;
				}
			}
			writeLinkedList();
			printf("Exiting...\n");
			return true;
	
		}
		p=p->next;
	}
	printf("Employee not found.\n");
	return false;
	
}



void display()
{
	if(count==0)
	{
		printf("\nEmpty database");
		return ;
	}
	struct employee *p;
	p=head;
    printf("\n");
	while(p!=NULL)
	{
		printf("Name of the employe is:- %s\nId is:- %d\nSalary is:- %.4f",p->name,p->id,p->salary);
		printf("\n\n");
		p=p->next;
	}
}


int main()
{
	int terminate=50;
	printf("\nLoading Program......");
	printf("\nChecking for local database.");
	readLinkedList();
	while(terminate--)
	{
		printf("\n\n--------------------Menu--------------------");
		printf("\nChoose any one from below options\n");
		printf("\n1. Load Employee data from database\n2. Save Employee data to database");
		printf("\n3. Create or add employee data\n4. Upadate Employee data");
		printf("\n5. Search Employee\n6. Remove Employee data\n7. Display Employee data");
		printf("\n8. Employee count\n9. Exit\n");
		printf("\nChoose option:- ");
		int choice,s=0;
		scanf("%d",&choice);
		switch (choice)
		{
		case 1:
			readLinkedList();
			break;
		case 2:
			writeLinkedList();
			break;
		case 3:
			create();
			break;
		case 4:
			updateDetails();
			break;
		case 5:
			printf("\n1. Search by Name: \n2. Search by id:");
			printf("\nchoose option:- ");
			scanf("%d",&s);
			if(s==1)
				searchByName();
			else if(s==2)
				searchById();
			else
				printf("\nWrong input.");
			break;
		case 6:
			printf("\n1. Delete by name:\n2. Delete by id:");
			printf("\nchoose option:- ");
			scanf("%d",&s);
			if(s==1)
				deleteByName();
			else if(s==2)
				deleteById();
			else
				printf("\nWrong input.");
			break;
		case 7:
			display();
			printf("\nPress any key to continue");
			fflush(stdin);
			getchar();
			break;
		case 8:
			countEmployee();
			break;
		case 9:
			writeLinkedList();
			return 0;
		default:
			printf("\nWrong input, try again.");
			break;
		}

	}

}
