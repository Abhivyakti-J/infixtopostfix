# infixtopostfix
#include<stdio.h>
#include<ctype.h>
#include<string.h>
#define MAX 10
int top=-1;
char STACK[MAX];
int pr(char c)
{
	if(c=='^')
		return 9;
	if(c=='*' || c=='/')
		return 7;
	if(c=='+' || c=='-')
		return 5;	
}
void main()
{
	char In[100],Post[100],ch;
	int i,j=0,k;
	printf("\nEnter the infix expression: ");
	fflush(stdin);
	gets(In);
	for(i=0;i<strlen(In);i++){
		ch=In[i];
		if(isalpha(ch))
			Post[j++]=ch;
		else
		{
			for(k=top;k>=0 && pr(ch)<=pr(STACK[top]);k--)
			{
				Post[j++]=STACK[top--];
			}
			STACK[++top]=ch;
		}
			
	}
	while(top!=-1)
		Post[j++]=STACK[top--];	
	
	Post[j]='\0';
	printf("\n The Postfix expression is : %s",Post);
}
