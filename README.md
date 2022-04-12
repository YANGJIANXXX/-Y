     V0
#include<stdio.h>
#include<string.h>
int main()
{
	char str[]="3+4";
	int left=str[0]-'0';
	int right=str[2]-'0';
	int res=left+right;
	printf("res=%d\n",res);
}
     
     
     
      V1           
#include<stdio.h> 
#include<string.h>
int main()
{
	int i; 
	char strExp[]="2*2/4*1/1*2*3/2";
	int res=strExp[0]-'0';
	for(i=1;i<strlen(strExp);i++)
	{
		if(strExp[i]=='*')
		{
			int r=strExp[i+1]-'0';
			res=res*r;
			i++;
		}
		else if(strExp[i]=='/')
		{
			int r=strExp[i+1]-'0';
			res=res/r;
			i++;
		}
	}
	printf("res=%d",res);
	return 0;
}

       V2
#include<stdio.h> 
#include<string.h>
int main()
{
	int i; 
	char strExp[]="1+2+2+1+2+5+4-1-3+4-8";
	int res=strExp[0]-'0';
	for(i=1;i<strlen(strExp);i++)
	{
		if(strExp[i]=='+')
		{
			int r=strExp[i+1]-'0';
			res=res+r;
			i++;
		}
		else if(strExp[i]=='-')
		{
			int r=strExp[i+1]-'0';
			res=res-r;
			i++;
		}
	}
	printf("res=%d",res);
	return 0;
}


      V3
#include<stdio.h>
#include<string.h>
int main()
{
	char strExp[]="2+2*3+2/2-1";
	char strTmp[strlen(strExp)];
	int strTmpIndex=-1;
	for(int i=0;i<strlen(strExp);i++)
	{
		if(strExp[i]=='*')
		{
			int left=strTmp[strTmpIndex]-'0';
			int right=strExp[i+1]-'0';
			strTmp[strTmpIndex]=left*right+'0';
			i++; 
		}
		else if(strExp[i]=='/')
		{
			int left=strTmp[strTmpIndex]-'0';
			int right=strExp[i+1]-'0';
			strTmp[strTmpIndex]=left/right+'0';
			i++; 
		}
		else strTmp[++strTmpIndex]=strExp[i];
	}
	int res=strTmp[0]-'0';
	for(int i=1;i<strlen(strTmp);i++)
	{
		if(strTmp[i]=='+')res+=strTmp[++i]-'0';
		else if(strTmp[i]=='-')
		res-=strTmp[++i]-'0'; 
	}
	printf("%d\n",res);
	return 0;
}
               v4
	       
	       #include<stdio.h>
#include<string.h>
#include<stdlib.h>
#define N 40
char c[N];//装表达式 
float a[N/2];//装操作数 
char b[N/2];//装运算符 
int PDSZ(int x)//判断是否为数字 
{
	if(x>='0'&&x<='9')
		return 1;
	else
		return 0;
} 
int PDYSF(char y)//判断是否为运算符 
{
	if(y=='+'||y=='-'||y=='*'||y=='/')
		return 1;
	else
		return 0;
}
int JS()//计算
{
	int j=0,k=0;
	float sum;
	char *p=c;
	a[0]=atof(p);
	while(*p!='\0')
	{
		while((*p>='0'&&*p<='9')||*p=='.')
			p++;
		if(p!='\0')
		{
			b[j]=*p;
			p++;
			a[j+1]=atof(p);
			j++;
		}
	}
	c[j]='\0';
	sum=a[0];
	while(b[k]!='\0')
	{ 
		switch(b[k]) 
		{
			case '+':sum=sum+a[k+1];break;
			case '-':sum=sum-a[k+1];break;
			case '*':sum=sum*a[k+1];break;
			case '/':sum=sum/a[k+1];break;
		} 
		k++;
	}
	printf("%f",sum);
	return 0;
	
}
int YZ()//验证 
{
	int x=0,y=0,z;
	z=strlen(c)-1;
	if((c[0]>='0'&&c[0]<='9')&&(c[z]>='0'&&c[z]<='9'))
		while(c[x]!='\0')
		{
			if(PDYSF(c[x])==1&&PDYSF(c[x+1])==1)
			{
				y=1;
				break;
			}
			if(c[x]=='/'&&c[x+1]=='0')
			{
				y=1;
				break;
			}
			x++;
		}
	else
		y=1;
	if(y==0)
		return 0;
	else
	{
		printf("输入不正确,请重新输入\n");
		return 1;
	}
}
int main()
{
	while(1)
	{	
		gets(c);
		if(YZ()!=1)
			break;
	}
	JS();
	return 0;
}

	       
	       
