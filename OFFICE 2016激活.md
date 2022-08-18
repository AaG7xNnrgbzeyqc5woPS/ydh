3. OFFICE激活：

第一步、找到你的OFFICE目录

我的是OFFICE 2016 32位版，目录为：

C:\Program Files (x86)\Microsoft Office\Office16

进去这个目录，可以看见有个OSPP.VBS文件

如果是OFFICE 2016 64位版，目录应为：

C:\Program Files\Microsoft Office\Office16

第二步、powershell中cd “C:\Program Files (x86)\Microsoft Office\Office16”（双引号中对应你的实际目录）

第三步、输入cscript ospp.vbs /sethst:192.168.50.1（你的路由IP）

第四步、输入cscript ospp.vbs /act

接下来享受激活的WINDOWS和OFFICE吧（使用系统自身批处理命令激活，因此不可能有后门，不用担心病毒和信息窃取之类的）。如果失败，请检查WINDOWS和OFFICE具体版本信息。

===========================
OFFICE激活实验：
零：使用普通权限打开 PowerShell
一、cd “C:\Program Files (x86)\Microsoft Office\Office16”
二、cscript ospp.vbs /sethst:192.168.2.2
三、cscript ospp.vbs /act

Office Professional Plus 2016
GVLK: XQNVK-8JYDB-WJ9W3-YJ8YR-WFG99 

#--------------------
office kms active code:
https://docs.microsoft.com/en-us/deployoffice/vlactivation/gvlks

#将 KMS 主计算机配置为激活 Office 的批量许可版本
#https://docs.microsoft.com/zh-cn/deployoffice/vlactivation/configure-a-kms-host-computer-for-office

# Office 批量激活概述
# https://docs.microsoft.com/zh-cn/deployoffice/vlactivation/plan-volume-activation-of-office
# 

# 使用 KMS 激活 Office 的批量许可版本
# https://docs.microsoft.com/zh-cn/deployoffice/vlactivation/activate-office-by-using-kms
