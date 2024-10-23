# Glimmer-CS--EASY---02-
##1
第二题对我来说其实真的意义还蛮大的，比较对于一个上大学才开始了解C语言的新生来说，跨度确实有点大，毕竟前面还在hello world，突然就整到链表了。我的readme是做完题后很久才写的，可能确实会遗忘一些当时的感受，但我现在来看感觉又不一样了。当时看到第二题感觉压力山大，想着这
不是easy吗？为什么是difficult的。我猜这样设置也许就是为了劝退一些人吧。然后那个时候就先看了翁恺的C语言，但感觉云里雾里的，接着又开始整c primer plus，过了很久之后才开始能看懂题了，然后又看了很多链表，才开始知道了框架，接着自己就开始写了，但可能确实是当时没看仔细，
自身能力又不够，没读懂题，卡了很久才发现题读错了，之后看栈那里又把偶数和偶数位置看岔了，当时确实是要疯掉了，然后环形链表的最后一个节点那里又不知道为什么一直在报segmentation fault，确实很崩溃，不过还是能得出结果，挺有成就感的，也算是解出了答案。但因为改了很多版，
又有很多细节问题没注意，导致最后的代码很乱，当时也就没管了。现在在把所有题都做了之后再回来看，还真点成就感，对比之前的想法我现在也有很多不同的理解，比如栈，我之前就了解了一下概念，看了看视频，心想这不就是个数组吗？然后确实用数组也把它做出来了，但现在感觉其实应该更像
是结构体那种，更像链表，出栈和入栈的理解也才浅薄了，这里数组能做也只是因为确实刚好是数字和字符，感觉如果真的实际应用的话这样能储存的数据也太少了，没有任何意义，像栈在网页上的应用肯定就要复杂一些，确实也说了很多题外话，因为之前遗留的一些问题现在又着手解决，但框架问题
我懒了，要改太多了，拖得太久了，很多思路也对不上了，一些地方也是偷了懒的。
##代码
~~~c
#include<stdio.h>
#include<stdlib.h>
typedef struct Node{
    int value;
    struct Node *next;
}node;
node*tlast=NULL;
node*add(node*head,int date);
int main()
{   int i=0;
    char option;
    node*head=(node*)malloc(sizeof(node));
    head->value=1;
    head->next=NULL;
    int date;
    char buffer[501];
    FILE *file=fopen("D:\\A\\CS-EASY-02-1.txt","r+");
    while (fgets(buffer,500,file)!=NULL)
    {
    option=buffer[0];
    int num=2;
    switch (option)
    {
    case 'H':
        node*front=NULL;
        i=0;
        do{i++;
        date=buffer[num]-'0';
        front=add(front,date);
        num+=2;
    }while(i<3);
        node*plast=front;
        while(plast->next){
                plast=plast->next;
            }
        node*hat=head;
        plast->next=hat;
        head=front;
        continue;
    case 'T':
        node*tail=NULL;
        i=0;
        do{i++;
        date=buffer[num]-'0';
        tail=add(tail,date);
        num+=2;
    }while(i<3);
    node*last=head;
        if(last){
        while(last->next)
        {
            last=last->next;
        }
        last->next=tail;
        }
        continue;
    case 'D':
        int location=buffer[num]-'0';
        num++;
        if(buffer[num]!=' '&&buffer[num]!='\n')
        location=location*10+buffer[num]-'0';
        node*q=NULL;
        node*b=head;
        for(int a=0;b;b=b->next)
        {a++;
            if(a==location)
            {   if(q){
                q->next=b->next;}
                else{
                    head=b->next;
                }
                free(b);
                break;
            }
            q=b;
        }
        continue;
    case 'C':
        node*elast=head;
        if(elast){
        while(elast->next)
        {
            elast=elast->next;
        }
        elast->next=head;
        }
        break;
    }
    }
    fclose(file);
    int list,circle;
        node*q=NULL;
        node*b=head;
        //找到3
        for(int a;b;b=b->next)
        {a=b->value;
            if(a==3)
            {   if(q){
                q->next=b->next;}
                else{
                    head=b->next;
                }
                printf("%d",b->value);
                free(b);
                break;
            }
            q=b;
        }
        node*f=q->next;
        node*g=NULL;
        for(list=0,circle=2;f;f=f->next)
        {list++;
            if(list==circle)
            {   if(g){
                g->next=f->next;}
                else{
                    head=f->next;
                }
                printf("%d",f->value);
                if(f->next==f)
                {
                f=NULL;
                free(f);
                break;
                }
                free(f);
                f=g->next;
                circle++;
                list=1;
            }
            g=f;
        }
}
node *add(node*head,int date)
{
node*p=(node*)malloc(sizeof(node));
        p->value=date;
        p->next=NULL;
        node*last=head;
        if(last)
        {
            while(last->next){
                last=last->next;
            }
            last->next=p;
        }else{
            head=p;
        }
        tlast=last;
        return head;
}
~~~
栈这里我偷懒了的，生成了out，但没用，直接将前面得到的结果复制然后调整了一下格式，也得到了一个结果：**glimmerinheartnofear4dark**
~~~c
#include<stdio.h>
#include<string.h>
//奇入偶出
int main()
{
int d=0;
int s=0;
int w=0;
int j=0;
int number(int b);
char z[100];
char word[]="kiglnmrmeiahenrteof4ardar";
    int numbers[34];
    for(int p,q=0;q<34;q++)
    {
    scanf("%d",&p);
    numbers[q]=p;
    }
    for(int x=0;x<34;x++)
    {   
        if((x+1)%2==0)
        {   d=numbers[x];
            w--;
            for(int a=0;a<d;a++)
            {   
                printf("%c",z[w]);
                w--;
            }
            w++;
        }
        else{s=numbers[x];
            for(int a=0;a<s;a++)
            {   z[w]=word[j];
                w++;
                j++;
            }
            }

    }
}
~~~
这种做法可能不是很符合题意，我也确实不该压题，应该做了就交，有些地方确实不好弄，主要我真是个懒b一点注释没写，这习惯确实没整好。

