//04191272 张若愚
#include<stdio.h>
#include<string.h>
#include<stdlib.h>
#include<conio.h>
#include<ctype.h>
#include<time.h>
#include<windows.h>
typedef struct shops
{
        char name[10];
        char position[3];
        float square;
        float rent;
        float income;
        struct shops *next;
}shops;
void loading()//等待界面 
{
	int i=0;
	while(i<1)
	{
		printf("                                                   l");
		Sleep(500);
		printf("o");
		Sleep(500);
		printf("a");
		Sleep(500);
		printf("d");
		Sleep(500);
		printf("i");
		Sleep(500);
		printf("n");
		Sleep(500);
		printf("g");
		Sleep(500);
		printf(".");
		Sleep(500);
		printf(".");
		Sleep(500);
		printf(".");
		Sleep(500);
		system("cls");
		i++;
	}
};
void TFU()//动态结束界面 
{
	Sleep(2000);
	printf("                         			Thanks ");
	Sleep(500);
	printf("for ");
	Sleep(500);
	printf("using!");
	Sleep(2000);
}
void spewel()//动态欢迎界面 
{
	Sleep(2000);
	printf("                         		Welcome ");
	Sleep(500);
	printf("to ");
	Sleep(500);
	printf("the ");
	Sleep(500);
	printf("management ");
	Sleep(500);
	printf("system\n");
	Sleep(2000);
	system("cls");
}; 


void pass()//密码系统 
{
	char password[8];
	char s[19];
	int a,i=0,j=0;
	char ch;
	do
	{
		printf("                                            please enter the password\n");
		while((ch = getch())!='\r')//判断是否是回车 
		{
			if(ch == 8&& i > 0)//实现backspace键的功能，其中backspace键的ascii码是8
			{
				putchar('\b');
				putchar(' ');
				putchar('\b'); 
				i--; 
			}
			if(!isdigit(ch)&&!isalpha(ch)) //判断是否是数字或字符 ,在ctype.h中
			continue;
			putchar('*');
			s[i++] = ch;
		} 
		s[i]='\0';
		FILE *fp=NULL;
		fp=fopen("E:\\程序\\password.txt","r");//只读方式打开 
		if(fp==NULL)
		{
			printf("unknow error\n");
		}		
		fscanf(fp,"%s",password);
		a=strcmp(s,password);
		if (a==0)
		{ 
			printf("\n\n\n                                                  right!");
			system("pause");
			system("cls");
			return ;
		}
		else 
		{
			j++;
			printf("\n                                    wrong!you can try 3times in total");//设置输入错误三次后自动退出 
			system("pause");
			system("cls");
			i=0;
			continue;	
		}
	}while(j<=2);
	system("cls");
	printf("                         You had enter the wrong password three times,the system forced withdraw!\n");//设置输入错误三次后自动退出
	system("pause");
	system("cls");
	exit(0); 
};
void welcome ()//欢迎界面 包括功能选择 
{
	printf("\n\n\n"); 
	printf("                                     **************************************\n");
	printf("                         	     ***welcome to the management system***\n");
	printf("                         	     **************************************\n");
	printf("\n");
	printf("                                       please choose the operation\n\n");
	printf("                                       1-show the all shops'information\n\n"); 
	printf("                                       2-add the new shops'information\n\n");
	printf("                                       3-delete the old shops'information\n\n");
	printf("                                       4-find the shops'information\n\n");
	printf("                                       5-sort the all shops'information\n\n");
	printf("                                       6-adjust the information\n\n");
	printf("                                       7-change the password\n\n");
	printf("                                       8-exit the system\n\n");

};

void print()//展示功能 
{
	int i=1;
	system("cls");
	loading();
	char ming[10],wei[3];
    float square;
    float rent;
    float income;
    printf("                    	name  position  square     rent      income\n");
	FILE *fp=NULL;
	fp=fopen("E:\\程序\\output.txt","r");//只读方式打开 
	if(fp==NULL)
	{
		printf("unknow error\n");
	}
	
	while(fscanf(fp,"%s %s %f %f %f",ming,wei,&square,&rent,&income)!=EOF)
	{
		printf("                     %d. %-10s %-3s   %-9.1f %-9.1f %-9.1f\n",i,ming,wei,square,rent,income);
		i++;
	}
	fclose(fp);
};
void add()//增添功能 
{
	char ming[10],wei[3];
    float square;
    float rent;
    float income;
	int a=1;
	FILE *fp=NULL;
	fp=fopen("E:\\程序\\output.txt","a+");//追加打开防止对原文件造成破坏 
	if(fp==NULL)
	{
		printf("unknow error\n");
	}
	while(a)
	{
		system("cls");
		printf("please enter the name of the shop\n");
		scanf("%s", ming);
		printf("please enter the position of the shop\n");
		scanf("%s", wei);
		printf("please enter the square of the shop\n");
		scanf("%f",&square);
		printf("please enter the rent of the shop\n");
		scanf("%f",&rent);
		printf("please enter the income of the shop\n");
		scanf("%f",&income);
		printf("do you want to add more?1--yes,0--no\n");//可多次输入 
		scanf("%d",&a);
		fprintf(fp,"%s %s %.1f %.1f %.1f\n",ming,wei,square,rent,income);
	}
	fclose(fp);
};

void dele()//删除功能 
{
	system("cls");
	int flag,i=1,j=1;
	char name[10];
    char position[3];
    float square;
    float rent;
    float income;
	shops *head,*p,*q,*d;
	char name2[10];
	head=(shops *)malloc(sizeof(shops));
	p=q=head;
	FILE *fp=NULL;
	fp=fopen("E:\\程序\\output.txt","a+");
	if(fp==NULL)
	{
		printf("UNKNOW ERROR\n");
		return;
	}
	while(fscanf(fp,"%s %s %f %f %f",name,position,&square,&rent,&income)!=EOF)//将文件中的数据存入链表 
	{
		q=(shops *)malloc(sizeof(shops));
		strcpy(q->name,name);
		strcpy(q->position,position);
		q->square=square;
		q->rent=rent;
		q->income=income;
		p->next=q;
		p=q;
	}
	p->next=NULL;
	fclose(fp);
	FILE *fq=NULL;
	fq=fopen("E:\\程序\\output.txt","w+");
	printf("please enter the name of the shop you want to delete\n");
	scanf("%s",name2);
	shops *c=head->next;
	while(c!=NULL)
    {
    	flag=strcmp(c->name,name2);//查找要删除的结点 
		if(flag==0)
		{
			break;
		}
		else 
		{
			c=c->next;
			i++;
		} 
	}
	d=head->next;
	if(flag!=0) 
	{
		printf("NOT FOUND");
		while(d)
		{
			fprintf(fp,"%s %s %.1f %.1f %.1f\n",d->name,d->position,d->square,d->rent,d->income);//"w"打开文件 退出时要将链表中的数据重新存入 
		    d=d->next ;
		}
		return;
	}
	
	while(d!=NULL)
	{
		if(j!=i)
		{
			fprintf(fp,"%s %s %.1f %.1f %.1f\n",d->name,d->position,d->square,d->rent,d->income);
		    d=d->next ;
		    j++;
		}
		else
		{
			d=d->next; 
			j++;
	    }
	}
	printf("success");
	fclose(fq);
};
void find()//查询功能 
{
	system("cls");
	int flag,i=1,j=1;
	char name[10];
    char position[3];
    float square;
    float rent;
    float income;
	char name2[10];
	shops *head,*p,*q,*d;
	head=(shops *)malloc(sizeof(shops));
	head->next=NULL;
	p=q=head;
	
	FILE *fp=NULL;
	fp=fopen("E:\\程序\\output.txt","r");
	if(fp==NULL)
	{
		printf("UNKNOW ERROR\n");
		return;
	}
	
	while(fscanf(fp,"%s %s %f %f %f",name,position,&square,&rent,&income)!=EOF)
	{
		q=(shops *)malloc(sizeof(shops));
		strcpy(q->name,name);
		strcpy(q->position,position);
		q->square=square;
		q->rent=rent;
		q->income=income;
		p->next=q;
		q->next=NULL;
		p=q;
	}
	fclose(fp);
	printf("please enter the name of the shop you want to find\n");
	scanf("%s",name2);
	loading();
	shops *c=head->next;
	while(c!=NULL)
    {
    	flag=strcmp(c->name,name2);
		if(flag==0)
		{
			printf("                    			    name  position  square   rent   income\n");
			printf("                                             %s     %s     %.1f     %.1f  %.1f\n",c->name,c->position,c->square,c->rent,c->income);
			return;
		}
		else 
		{
			c=c->next;	
		} 
	}
	if(flag!=0) 
	{
		printf("NOT FOUND\n");
	}
};
void sort()//排序功能 
{
	system("cls");
	
	shops shops1[1000];//结构体数组 
	shops tt[1];
	int i=1,j=1,a,b,test;
	FILE *fp=NULL;
	
	fp=fopen("E:\\程序\\output.txt","r+");
	if(fp==NULL)
	{
		printf("UNKNOW ERROR\n");
		return;
	}
	while(!feof(fp))
	{
		fscanf(fp,"%s %s %f %f %f",shops1[i].name,shops1[i].position,&shops1[i].square,&shops1[i].rent,&shops1[i].income);
		i++;
	}
	i--;
	test=i;
	printf("please enter the data you want to sort 1-square,2-income\n");
	scanf("%d",&a);
	printf("please enter the way to sort  1-ascending,2-descending\n");
	scanf("%d",&b);
	loading();
	printf("                    	name  position  square     rent     income\n");
	if(a==1&&b==1)
	{		
		for(i=1;i<test;i++)
			for(j=1;j<test-i;j++)
			{
				if(shops1[j].square > shops1[j+1].square)
				{
					tt[0]=shops1[j];
					shops1[j]=shops1[j+1];
					shops1[j+1]=tt[0];
				}
		    }
		for(i=1;i<test;i++)
		{
			printf("                     %d. %-10s %-3s  %-9.1f %-9.1f %-9.1f\n",i,shops1[i].name,shops1[i].position,shops1[i].square,shops1[i].rent,shops1[i].income);
		}
	} 
	else if(a==1&&b==2)
	{		
		for(i=1;i<test;i++)
			for(j=1;j<test-i;j++)
			{
				if(shops1[j].square < shops1[j+1].square)
				{
					tt[0]=shops1[j];
					shops1[j]=shops1[j+1];
					shops1[j+1]=tt[0];
				}
		    }
		for(i=1;i<test;i++)
		{
			printf("                     %d. %-10s %-3s  %-9.1f %-9.1f %-9.1f\n",i,shops1[i].name,shops1[i].position,shops1[i].square,shops1[i].rent,shops1[i].income);
		}
	} 
	else if(a==2&&b==1)
	{		
		for(i=1;i<test;i++)
			for(j=1;j<test-i;j++)
			{
				if(shops1[j].income > shops1[j+1].income)
				{
					tt[0]=shops1[j];
					shops1[j]=shops1[j+1];
					shops1[j+1]=tt[0];
				}
		    }
		for(i=1;i<test;i++)
		{
			printf("                     %d. %-10s %-3s  %-9.1f %-9.1f %-9.1f\n",i,shops1[i].name,shops1[i].position,shops1[i].square,shops1[i].rent,shops1[i].income);
		}
	} 
	else if(a==2&&b==2)
	{		
		for(i=1;i<test;i++)
			for(j=1;j<test-i;j++)
			{
				if(shops1[j].income < shops1[j+1].income)
				{
					tt[0]=shops1[j];
					shops1[j]=shops1[j+1];
					shops1[j+1]=tt[0];
				}
		    }
		for(i=1;i<test;i++)
		{
			printf("                     %d. %-10s %-3s  %-9.1f %-9.1f %-9.1f\n",i,shops1[i].name,shops1[i].position,shops1[i].square,shops1[i].rent,shops1[i].income);
		}
	} 
	else printf("WRONG INSTRUCT");
	fclose(fp);
};
void adjust()//修改功能 
{
	system("cls");
	int flag,i=1,j=1;
	char name[10];
    char position[3];
    float square;
    float rent;
    float income;
	shops *head,*p,*q,*d;
	char name2[10];
	head=(shops *)malloc(sizeof(shops));
	p=q=head;
	FILE *fp=NULL;
	fp=fopen("E:\\程序\\output.txt","a+");
	if(fp==NULL)
	{
		printf("UNKNOW ERROR\n");
		return;
	}
	while(fscanf(fp,"%s %s %f %f %f",name,position,&square,&rent,&income)!=EOF)
	{
		q=(shops *)malloc(sizeof(shops));
		strcpy(q->name,name);
		strcpy(q->position,position);
		q->square=square;
		q->rent=rent;
		q->income=income;
		p->next=q;
		p=q;
	}
	p->next=NULL;
	fclose(fp);
	FILE *fq=NULL;
	fq=fopen("E:\\程序\\output.txt","r+");
	printf("please enter the name of the shop you want to adjust\n");
	scanf("%s",name2);
	shops *c=head->next;
	while(c!=NULL)
    {
    	flag=strcmp(c->name,name2);
		if(flag==0)
		{
			break;
		}
		else 
		{
			c=c->next;
			i++;
		} 
	}
	d=head->next;
	if(flag!=0) 
	{
		printf("NOT FOUND");
		while(d)
		{
			fprintf(fp,"%s %s %.1f %.1f %.1f\n",d->name,d->position,d->square,d->rent,d->income);
		    d=d->next ;
		}
		return;
	}
	while(d!=NULL)
	{
		if(j!=i)
		{
			fprintf(fp,"%s %s %.1f %.1f %.1f\n",d->name,d->position,d->square,d->rent,d->income);
		    d=d->next ;
		    j++;
		}
		else
		{
			printf("please enter the information you want to adjust\n");
			printf("name position square rent income(divide the data by the space)\n");
			scanf("%s %s %f %f %f",d->name,d->position,&d->square,&d->rent,&d->income);
			fprintf(fp,"%s %s %.1f %.1f %.1f\n",d->name,d->position,d->square,d->rent,d->income);
			d=d->next; 
			j++;
	    }
	}
	printf("success");
	fclose(fq);
};
void identify()//验证系统 
{
	system("cls");
	char a[50][50]={"######","#o####", "#    #","#### #","#    #","# ####"};
	printf("                                       we need to indetify you are human\n");
	printf("                              use the 'W' 'A' 'S' 'D' to help 'o' get out the maze\n");
	int i,x,y,p,q;
	char ch;
	x=1,y=1,p=1,q=5;
	for( i=0; i<=5; i++)
	{
		puts(a[i]);
	}
	while(x!=5||y!=1)
	{
		ch=getch();//不回显函数，直接读取无需回车 
		if(ch=='s')
		{
			if(a[x+1][y]!='#')
			{ 
				a[x][y]=' ';
				x++;
				a[x][y]='o';
			}
		}
		if(ch=='w')
		{
			if(a[x-1][y]!='#')
			{
				a[x][y]=' ';
				x--;
				a[x][y]='o';
			}
		}
		if(ch=='a')
		{
			if(a[x][y-1]!='#')
			{
				a[x][y]=' ';
				y--;
				a[x][y]='o';
			}
		}
		if(ch=='d')
		{
			if(a[x][y+1]!='#')
			{
				a[x][y]=' ';
				y++;
				a[x][y]='o';
			}
		}
		system("cls");
		for(i=0;i<=5;i++)
		{
			puts(a[i]);
		}
	}
	loading();
	printf("\n\n\n                                                  right!\n");
	system("pause");
	system("cls");
	return;
}
void change()//修改密码 
{
	char a[8];
	system("cls");
	identify();
	
	FILE *fp=NULL;
	fp=fopen("E:\\程序\\password.txt","w");
	if(fp==NULL)
	{
		printf("unknow error\n");
		return;
	}
	printf("                                        please enter the new password\n");
	scanf("%s",a);
	fprintf(fp,"%s",a);
	printf("                                                     success\n");
	fclose(fp);
};
void windows();
void choose()//选择系统 
{
	int a;
	scanf("%d",&a);
	switch(a) 
    {
        case 1:
        {
            print();
            system("pause");
            system("cls");
            welcome();
            choose();
            break;
        }
        case 2:
        {
            add();
            system("pause");
            system("cls");
            welcome();
            choose();
            break;
        }
        case 3:
        {
            dele();
            system("pause");
            system("cls");
            welcome();
            choose();
            break;
        }
        case 4:
        {
            find();
            system("pause");
            system("cls");
            welcome();
            choose();
            break;
        }
        case 5:
        {
            sort();
            system("pause");
            system("cls");
            welcome();
            choose();
            break;
        }
        case 6:
        {
            adjust();
            system("pause");
            system("cls");
            welcome();
            choose();
            break;
        }
        case 7:
    	{
        	change();
			system("pause");
            system("cls");
            welcome();
            choose();
            break;	
		}
		case 8:
		{
			system("cls");
			windows();
		}
        default:printf("无效指令");
    }
};
void windows()//调用API函数MessageBox
{
	int select=MessageBoxA(NULL, "真的要退出吗", "提示", MB_YESNO);
	if(IDYES == select)
	{
		TFU();
		system("cls");
		exit(0);
	}
	else
	{
		welcome();
		choose();
	}
}
int main() 
{
	system("color B1");//调色美观 
	spewel();
    pass();
    welcome ();
    choose();
    return 0;
}
//OS=win7,IDE=Dev-C++ 5.11
