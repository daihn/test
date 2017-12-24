#MessageBox

<pre>
#include <Windows.h>

int WINAPI WinMain(HINSTANCE hInstance, HINSTANCE hPrevInstance, PSTR szCmdLine, int iCmdShow)
{
	MessageBox(NULL, TEXT("hello world"), TEXT("title"),MB_OK);
	return 0;
}
</pre>
- 效果如下:

![MessageBox](https://github.com/daihn/test/blob/master/pic/MessageBox.PNG?raw=true)

[来自SegmentFault社区的markdown学习资料](https://segmentfault.com/markdown)


##MessageBox 原型：
- 注釋：_In_說明該參數是輸入的，_opt_說明該參數是可選的
<pre>
int WINAPI MessageBox(
  _In_opt_  HWND hWnd,
  _In_opt_  LPCTSTR lpText,
  _In_opt_  LPCTSTR lpCaption,
  _In_      UINT uType
);
</pre>

- hWnd表示該窗口的父窗口
- lpText 消息內容
- lpcaption 消息框標題
- uType 了顯示消息框中的按鈕於圖標的不同類型

######例如：
-  MB_OK 只有確定鍵
-  MB_ICONWARINNING 會有感嘆號出現

[uType详细功能网址](http://bbs.fishc.com/thread-46730-1-1.html)

##两个小例子

- 1.含有中止，重试，忽略的对话框

<pre>
#include <Windows.h>

int WINAPI WinMain(HINSTANCE hInstance, HINSTANCE hPrevInstance, PSTR szCmdLine, int iCmdShow)
{
	MessageBox(NULL, TEXT("hello world"), TEXT("title"),MB_ABORTRETRYIGNORE);
	return 0;
}
</pre> 

- 现象：

![1](https://github.com/daihn/test/blob/master/pic/MessageBox1.PNG?raw=true)


- 2.点yes对话框退出

<pre>
#include <Windows.h>

int WINAPI WinMain(HINSTANCE hInstance, HINSTANCE hPrevInstance, PSTR szCmdLine, int iCmdShow)
{
	int result;

	while(true)
	{
		result = MessageBox(NULL, TEXT("hello world"), TEXT("title"),MB_YESNO);
		if(result == IDYES)
		{
			break;
		}
	}
	return 0;
}
</pre>

##匈牙利命名法
- iAge   	int
- szString 	以‘/0’为结尾的字符串
- pBuffer 	指针
- msgstr  	以msg型结构
- hWnd     	句柄
- aValue  	数组