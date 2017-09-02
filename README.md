# idea

#include <iostream>
#include <cstdlib>
using namespace std;
struct Node
{ int info;
  Node *next;
}*start,*ptr,*newptr,*rear,*save;
Node *Create_New_Node(int n)
{
	ptr= new Node;
	ptr->info=n;
	ptr->next=NULL;
	return ptr;
}
void Insert_Beg(Node *np)
{
	if(start==NULL)
	{
		start=np;
		rear=np;
	}
	else
	{
		save=start;
		start=np;
		start->next=save;
	}
}
void Insert_End(Node *np)
{
	if(start==NULL)
	{
		start=np;
		rear=np;
	}
	else
	{
		rear->next=np;
		rear=np;
	}
}
void DelNode()
{
	if(start==NULL)
	{
		cout<<"List is underflow";
		exit(0);
	}
	else
	{
		ptr=start;
		start=start->next;
		delete ptr;
	}
}
void Display(Node *np)
{
	while(np!=NULL)
	{
		cout<<np->info<<"\t";
		np=np->next;
	}
}

int main()
{
    int n,info;
    char ch='y';
    start=NULL;
    cout<<"1. Insertion at Begining\n";
    cout<<"2. Insertion at End \n";
    cout<<"3. Deletion of node \n";
    cout<<"4. Display List \n";
    while(ch=='y')
    {
    	cout<<"Enter your choice \n";
        cin>>n;
    	switch(n)
    	{
    		case 1:
    		cout<<"Enter value for the new node \n";
    		cin>>info;
    		newptr=Create_New_Node(info);
    		if(newptr==NULL)
    		{
    			cout<<"\n Node can't created";
    			exit(0);
    		}
    		Insert_Beg(newptr);
    		break;
    		case 2:
    		cout<<"Enter value for the new Node \n";
    		cin>>info;
    		newptr=Create_New_Node(info);
    		if(newptr==NULL)
    		{
    			cout<<"Node can't created ";
    			exit(0);
    		}
    		Insert_End(newptr);
    		break;
    		case 3:
    		DelNode();
    		break;
    		case 4:
    		Display(start);
    		break;
    		default:
    		cout<<"Invalid choice";
    	}
    	cout<<"\nDo you want more operation \n";
    	cin>>ch;
    }
	return 0;
}
