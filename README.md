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

