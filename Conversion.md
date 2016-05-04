
#### char *itoa( int value, char *string,int radix); ####
>value: 欲转换的数据; string: 目标字符串的地址, radix: 转换后的进制数 , 可以是10进制, 16进制等;

	int nNum = 22;
	char szNum[32] = {0};
	itoa(nNum,szNum,16);

#### int atoi (const char * str); ####

	char szNum[] = "12345";
	int nNum = atoi(szNum);

#### double atof (const char* str); ####

	char *szNumA="-100.23";   
	char *szNumB="200e-2";   
	double lfNum;   
	lfNum = atof(szNumA) + atof(szNumB);   

####  int sprintf( char *buffer, const char *format, [ argument] … ); #### 
>buffer: char型指针, 指向将要写入的字符串的缓冲区; format: 格式化字符串; 
>[argument]...: 可选参数, 可以是任何类型的数据; 返回值: 字符串长度(strlen)

	int nNum = 22;
	char szNum[32] = {0};
	int nLength = sprintf(szNum, "%0d", nNum); 

#### stringstream ####
>\#include <sstream\>

	int nNum = 30;
	stringstream ssTmp;
	ssTmp<<nNum; 
	ssTmp<<nNum; 
	//string strTmp = ssTmp.str();
	string strTmp;
	ssTmp>>strTmp;
	ssTmp.clear();	//清空stringstream的状态(比如出错等), 真正清空内容需要使用 .str("") 方法
	ssTmp.str("");
	ssTmp<<strTmp;
	ssTmp>>nNum;

#### int sscanf( string str, string fmt, mixed var1, mixed var2 ... ); ####

	char *szDateTime = "2016,05,04 - 15:30";
	char szDate[32] = {0};
	int nHour, nSec;
	sscanf(szDateTime, "%s - %d:%d", szDate, &nHour, &nSec);