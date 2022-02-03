# Hashing-using-linear-changing
#include<stdio.h>
#include<stdlib.h>
struct hashtable
{
    int data;
    struct hashtable *next;
};
int hash(int n)
{
    return n%10;
}
typedef struct hashtable node;
void insert(node *t[10],int x)
{
    int h=hash(x);
    node *p=(node *)malloc(sizeof(node));
    p->data=x;
    p->next=NULL;
    if(t[h]==NULL)
    {
        t[h]->next=p;
    }
    else
    {
        p->next=t[h]->next;
        t[h]->next=p;
    }
}
void search(node *t[10],int x)
{
    int h=hash(x),flag=0;
    node* temp=t[h]->next;
    while(temp!=NULL)
    {
        if(temp->data==x)
        {
            flag=1;
            break;
        }
        else
        {
            temp=temp->next;
        }
    }
    if(flag==1)
    {
        printf("%d element is found\n",x);
    }
    else
    {
        printf("%d element is not found\n",x);
    }
}
void delete(node* t[10],int x)
{
    int h=hash(x),flag=0;
    node* temp=t[h]->next,*temp1;
    while(temp!=NULL)
    {
        if(temp->data==x)
        {
            flag=1;
            break;
        }
        else
        {
            temp1=temp;
            temp=temp->next;
        }
    }
    if (flag==1)
    {
        temp1->next=temp->next;
        free(temp);
        printf("%d element is deleted\n",x);
    }
    else
    {
        printf("%d element is not found to delete\n",x);
    }
}
void display(node* t[10])
{
    node* temp;
    int i;
    for(i=0;i<10;i++)
    {
        temp=t[i]->next;
        printf("%d<->",i);
        while(temp!=NULL)
        {
            printf("%d->",temp->data);
            temp=temp->next;
        }
        printf("NULL\n");
    }
}
void main()
{
    node* t[10];
    int i,ch,x;
    for(i=0;i<10;i++)
    {
        t[i]=(node *)malloc(sizeof(node));
        t[i]->next=NULL;
    }
    while(1)
    {
        printf("Enter your choice:\n1.Insert\n2.Search\n3.Delete\n4.Display\n5.Exit\n");
        scanf("%d",&ch);
        switch(ch)
        {
            case 1: printf("Enter a value to insert\n");
                    scanf("%d",&x);
                    insert(t,x);
                    break;
            case 2: printf("Enter a value to search\n");
                    scanf("%d",&x);
                    search(t,x);
                    break;
            case 3: printf("Enter a value to delete\n");
                    scanf("%d",&x);
                    delete(t,x);
                    break;
            case 4: display(t);
                    break;
            case 5: printf("while loop is terminated\n");
                    exit(0);
                    break;
            default: printf("enter correct choice\n");
        }
    }
}




OUTPUT:
Enter your choice:
1.Insert
2.Search
3.Delete
4.Display
5.Exit
1
Enter a value to insert
41
Enter your choice:
1.Insert
2.Search
3.Delete
4.Display
5.Exit
1
Enter a value to insert
63
Enter your choice:
1.Insert
2.Search
3.Delete
4.Display
5.Exit
1
Enter a value to insert
64
Enter your choice:
1.Insert
2.Search
3.Delete
4.Display
5.Exit
1
Enter a value to insert
4
Enter your choice:
1.Insert
2.Search
3.Delete
4.Display
5.Exit
1
Enter a value to insert
32
Enter your choice:
1.Insert
2.Search
3.Delete
4.Display
5.Exit
1
Enter a value to insert
1
Enter your choice:
1.Insert
2.Search
3.Delete
4.Display
5.Exit
1
Enter a value to insert
79
Enter your choice:
1.Insert
2.Search
3.Delete
4.Display
5.Exit
4
0<->NULL
1<->1->41->NULL
2<->32->NULL
3<->63->NULL
4<->4->64->NULL
5<->NULL
6<->NULL
7<->NULL
8<->NULL
9<->79->NULL
Enter your choice:
1.Insert
2.Search
3.Delete
4.Display
5.Exit
2
Enter a value to search
94
94 element is not found
Enter your choice:
1.Insert
2.Search
3.Delete
4.Display
5.Exit
2
Enter a value to search
4
4 element is found
Enter your choice:
1.Insert
2.Search
3.Delete
4.Display
5.Exit
3
Enter a value to delete
7
7 element is not found to delete
Enter your choice:
1.Insert
2.Search
3.Delete
4.Display
5.Exit
3
Enter a value to delete
1
1 element is deleted
Enter your choice:
1.Insert
2.Search
3.Delete
4.Display
5.Exit
4
0<->NULL
1<->0->1->NULL
2<->32->NULL
3<->63->NULL
4<->4->64->NULL
5<->NULL
6<->NULL
7<->NULL
8<->NULL
9<->79->NULL
Enter your choice:
1.Insert
2.Search
3.Delete
4.Display
5.Exit
5
while loop is terminated
