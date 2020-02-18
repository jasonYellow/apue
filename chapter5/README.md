本章说明了标准I/O库的相关函数  
1.    
### void setbuf(FILE *fp, char *buf );  
buf:  
nonnull 长度为BUFSIZE的用户缓存全缓存或行缓存  
NULL （无缓存） 不带缓存  

int setvbuf(FILE *fp, char *buf, int mode, size_t size);  
返回：若成功则为0，若出错则为非0  
mode:  
_IOFBF 全缓存  
_IOLBF 行缓存  
_IONBF 不带缓存  
buf:  
nonnull 长度为BUFSIZE的用户缓存  
NULL (无缓存)  
2.  
### int fflush(FILE *fp) ;
返回：若成功则为0，若出错则为EOF  
此函数使该流所有未写的数据都被传递至内核  
3.  
### FILE *fopen(const char *pathname, const char *type);
若成功则为文件指针，若出错则为NULL

pathname，文件名
type，打开方式

字符及其含义：  
打开方式由r,w,a,t,b,+这六个字符拼成，含义如下  
r(read)：读  
w(write)：写  
a(append)：追加  
t(txt)：文本文件，可省略
b(banary)：二进制文件

"r"            打开文字文件只读          
"w"           创建文字文件只写         
"a"           增补, 如果文件不存在则创建一个     
"r+"          打开一个文字文件读/写        
"w+"         创建一个文字文件读/写          
"a+"         打开或创建一个文件增补          
"b"           二进制文件(可以和上面每一项合用)          
"t"           文这文件(默认项)  

使用方式及含义
“rt”　　　　　　只读打开一个文本文件，只允许读数据 
“wt”　　　　　　只写打开或建立一个文本文件，只允许写数据
“at”　　　　　　追加打开一个文本文件，并在文件末尾写数据
“rb”　　　　　　只读打开一个二进制文件，只允许读数据
“wb”　　　　 　  只写打开或建立一个二进制文件，只允许写数据
“ab” 　　　　 　 追加打开一个二进制文件，并在文件末尾写数据
“rt+”　　　　　  读写打开一个文本文件，允许读和写
“wt+”　　　　　 读写打开或建立一个文本文件，允许读写
“at+”　　　　　  读写打开一个文本文件，允许读，或在文件末追加数 据
“rb+”　　　　　  读写打开一个二进制文件，允许读和写 
“wb+”　　　　　 读写打开或建立一个二进制文件，允许读和写
“ab+” 　　　　 　读写打开一个二进制文件，允许读，或在文件末追加数据

①　用”r”打开文件时，该文件必须存在，只读
②　用”w”打开文件时，若文件不存在，则创建，若存在，则将其删除，再创建一个文件
③　用”a”打开文件时，可在其末尾写数据

4.
### FILE *freopen(const char *pathname, const char *type, FILE *fp)
常用来重定向了标准流，用pathname的流代替fp
5.  
### FILE *fdopen(int filedes, const char *type)
打开一个现存的文件描述符
6.  
int fclose(FILE *fp)
