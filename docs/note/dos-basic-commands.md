# 基本的DOS命令

***DOS（磁盘操作系统 Disk Operating System）***

## 1. 开启DOS控制台的几种方式

1. 通过Windows开始菜单里的Windows系统文件夹下的命令提示符文件打开
2. 通过快捷键**Windows+R**打开运行窗口，输入cmd，回车
3. 在任意的文件夹下，按住Shift键+鼠标右键，点击在此处打开Powershell窗口
4. 单击资源管理器的地址栏，输入cmd，回车

**以管理员方式运行**：右键命令提示符文件选择以管理员身份运行

## 2. 常用的Dos命令

```bash
# 盘符切换
d: 或 D:
# 查看当前目录下的所有文件
dir
# 切换目录cd（change directory）
cd /d e:	# 从其他盘进入e盘
cd ..	# 返回上一级目录
cd tmp	# 进入tmp目录
# 清理屏幕cls（clear screen）
cls
# 退出终端
exit
# 查看IP配置信息，本地网卡的MAC地址
ipconfig
# 测试网络是否正常，ping命令
ping www.baidu.com
# 创建文件夹md
md test
# 创建文件
cd>a.txt
# 删除文件
del a.txt
# 删除目录
rd test
```

## 3. cmd界面复制粘贴

1. 在cmd界面单击鼠标右键即可粘贴
2. **复制**：使用快捷键**Ctrl+C**或**Ctrl+Insert**
3. **粘贴**：使用快捷键**Ctrl+V**或**Shift+Insert**

