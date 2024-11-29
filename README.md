



















#include<stdio.h>
#include<stdlib.h>

struct node
{
    int info;
    struct node *pre;
    struct node *next;
};


struct node* createNode()
{
    struct node *t;
    t=(struct node*) malloc (sizeof(struct node));
    return t;
};

int main()
{
    struct node *head;
    head=createNode();
    head->info=7;
    head->pre=NULL;
    head->next=NULL;


    struct node *second;
    second=createNode();
    second->info=9;
    second->pre=NULL;
    second->next=NULL;


    struct node *third;
    third=createNode();
    third->info=11;
    third->pre=NULL;
    third->next=NULL;


    head->next=second;
    second->next=third;

    third->pre=second;
    second->pre=head;


    struct node *t;
    t=head;
    while(t!=NULL){
        printf("%d\n",t->info);
        t=t->next;
    }
    t=NULL;


    //insert in first
    struct node *newnode;
    newnode = createNode();
    newnode->info=15;
    newnode->pre=NULL;
    newnode->next=NULL;

    newnode->next=head;
    head->pre=newnode;
    head=newnode;


    t=head;
    printf("\n\n");
    while(t!=NULL){
        printf("%d\n",t->info);
        t=t->next;
    }
    t=NULL;



    //insert in last;
    struct node *newnode2;
    newnode2 = createNode();
    newnode2->info=20;
    newnode2->pre=NULL;
    newnode2->next=NULL;


    t=head;
    while(t->next!=NULL)
        t=t->next;
    t->next=newnode2;
    newnode2->pre=t;
    t=NULL;


    t=head;
    printf("\n\n");
    while(t!=NULL){
        printf("%d\n",t->info);
        t=t->next;
    }


    //delete last node
    struct node *t2;
    t=head;
    while(t->next!=NULL){
        t2=t;
        t=t->next;
    }
    t2->next=NULL;
    free(t);


    t=head;
    printf("\n\n");
    while(t!=NULL){
        printf("%d\n",t->info);
        t=t->next;
    }
}
