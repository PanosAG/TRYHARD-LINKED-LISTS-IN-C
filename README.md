# TRYHARD-LINKED-LISTS-IN-C
if somebody wants to help me , please...
#include <stdio.h>
struct list {
    int value;
    struct list *next;
};

void PrintList(struct list *l) {
    if(l!=NULL) {
        printf("%d\n",l->value);
        PrintList(l->next);
    }
    else 
    return;
    
}

struct list *FindAndPushDown(int n,struct list *node) {
    struct list *curr,*nxt;
    int keep;
    
    curr=nxt=node;
   
    
    for(curr!=NULL;curr->next!=NULL;curr=curr->next) {
    if(curr->value!=n && curr->next==NULL){
        printf("Unfortunately this number does not exist in this List");
        return;
    }
    else if(curr->value==n && curr->next!=NULL) {
        
        printf("The number appears to be in the list,wait for the results of the current fuction!!\n");
        nxt=curr->next;
        
        while(nxt->next!=NULL && nxt->value < curr->value){
            
            keep=nxt->value;
            nxt->value=curr->value;
            curr->value=keep;
            
            
            
        }
    }
    }
    return node;
    
    
    }

 struct list *ReversedInput(int b,struct list *l) {
    struct list *curr,*nxt;
    struct list *help=NULL;
    int j;
    curr=l;
    
    for(j=1;j<b && curr!=NULL;j++) {
        nxt=curr->next;
        printf("%d node's Data = ",j);
        scanf("%d",&curr->value);
        curr->next=help;
        help=curr;
        curr=nxt;
    }
    return (help);
}






int main()
{
    struct list *head;
    int N,n;
    head=NULL;
    struct list *node;
    node=(struct list *)malloc(sizeof(struct list));
    node=head;
    
    printf("Please type in how many numbers you wish to have ! \n");
    scanf("%d",&N);
    
    //Calling the Reversedinput fuction //
     head=ReversedInput(N,node);
     
     //Prints what is in the reversed list //
     
     printf("Your list : \n");
     
     PrintList(head);
     
     //Shaking up the list//
     printf("Please enter below the number you are searching for: \n ");
    scanf("%d",&n);
     
     head=FindAndPushDown(n,head);
     //Printing the new list//
     
     PrintList(head);
     
     return 0;
    
    
   
}
