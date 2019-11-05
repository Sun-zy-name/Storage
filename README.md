#include <stdio.h>
#include <stdlib.h>
#include<string.h>
#define Mytype char
#define N 100
typedef struct link
{
	Mytype data;
	struct link* next;
}*Link;
Link Createlink(int n,char arr[])
{
	int i;
	Link head, p, q;
	head = p = (Link)malloc(sizeof(struct link));
	for (i = 0; i < n; ++i) {
		q = (Link)malloc(sizeof(struct link));
		q->data = arr[i];
		p->next = q;
		p = q;
	}
	p->next = NULL;
	return head;
}
void reverse(Link head)
{
	Link p, t, q;
	p = NULL;
	t = head->next;
	q = t->next;
	if (t == NULL || q == NULL)
		return;
	while (q != NULL)
	{
		t->next = p;
		p = t;
		t = q;
		q = q->next;
	}
	t->next = p;
	head->next = t;
}
void showLink(Link head)
{
	Link curr = head->next;
	while (curr != NULL)
	{
		printf("%c", curr->data);
		curr = curr->next;
	}
}
int lengtha(char a[]) 
{
	int n = 0;
	while (a[n] != '\0')   
		n++;  
	return n;
}
int main()
{
	int n, j = 0;
	char arr[N];
	char c = ' 1 ';
	
	scanf_s("%s", arr, N);
	n = lengtha(arr);
	
	Link head = Createlink(n, arr);
	reverse(head);
	showLink(head);

	return 0;
}
