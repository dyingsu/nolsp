# nolsp
NoLsp_fix_WSL2_参考的对象类型不支持尝试的操作.exe 

下载此软件(原始链接_www.proxifier.com/tmp/Test20200228/NoLsp.exe) 
管理员身份运行CMD输入：  NoLsp.exe C:\windows\system32\wsl.exe  请自行注意NoLsp.exe程序的位置，以及你的wsl.exe位置。  
产生原因和解决方法分析：  代理软件和wsl2的sock端口冲突，使用netsh winsock reset重置修复。 

Proxifer开发人员解释如下： 如果Winsock LSP DLL被加载到其进程中，则wsl.exe将显示此错误。最简单的解决方案是对wsl.exe使用WSCSetApplicationCategory WinAPI调用来防止这种情况。在后台，该调用在HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WinSock2\Parameters\AppId_Catalog中为wsl.exe创建一个条目。 这将告诉Windows不要将LSP DLL加载到wsl.exe进程中

https://zhuanlan.zhihu.com/p/151392411
