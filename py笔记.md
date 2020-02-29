- a = b if b == 2 else c

- py没有自增自减符(++ --)
- is和==的区别，==判断两个变量的值是否相等，is判断两个变量的id(唯一标识，相当于地址)是否相等
- sys.argv 命令行参数，同c/c++文件执行main的argv参数
- sys.exit()，python程序退出，发出SystemExit异常然后退出
</br></br></br>
### python读文件
```
f = open(r'c:\test.txt', 'r')
try:
    data = f.read()
finally:
    f.close()
```
或
```
with open(r'c:\test.txt', 'r') as f:
    data = f.read()
```
</br></br></br>
文件对象有三种读方法：read(), readline()和readlines()
- read()，读取整个文件，返回一个字符串。如果内存不够大，可用read(size)
- readline()，每次读一行，比readlines()慢，仅当内存不够时才使用
- readlines()，读取整个文件，返回一个列表，每行为一个元素
</br></br></br>
python读文件首字节乱码问题
- 在windows上用open打开utf-8编码的txt文件时开头会有一个多余的\ufeff，叫BOM，用来声明编码信息的，但python会把它当做文本解析。
- 解决：修改encoding为utf-8_sig或utf_8_sig
```
open('1.txt', encoding='utf_8_sig' )
```
</br></br></br>
### 正则表达式
- 需要导入模块 import re
- 字符串前r表示raw string，即\不表示转义，如 \n在raw string(原生字符串) 中是两个字符 \和n
- \b 匹配单词边界，如 'er\b'可以匹配"never"中的er，但不能匹配 'verb'中的er；\B匹配非单词边界
- '\' 转义字符，剥夺原含义，赋予新含义
</br></br></br>
- match()：从字符串头开始匹配，如果不符合，则匹配失败，返回None
- research()：匹配整个字符串，直到找到一个匹配，返回第一个匹配字符串
- findall()：找到所有子串，返回字符串列表
</br></br></br>
### pyqt5
按钮触发事件，openfile为自定义函数
```
self.pushButton.clicked.connect(self.openfile) #按钮触发事件
```
</br></br>
获得输入框文本
```
word = self.textEdit_2.toPlainText() #获得输入框文本
```
</br></br>
打开文件选择框并限制文件格式，第三个参数为当前文件路径，第四个参数为文件格式 </br>
文件格式：All Files (*);;PDF Files (*.pdf);;Text Files (*.txt)
```
import os
from PyQt5 import QtCore, QtGui, QtWidgets
from PyQt5.QtWidgets import *
file_name = QFileDialog.getOpenFileName(None, '选择文件', os.getcwd(), 'Excel files(*.xlsx , *.xls, *.csv)') #打开文件界面
```
</br></br>
消息弹框：QmessageBox.information, QmessageBox.question, QmessageBox.warning
```
QMessageBox.information(None, "提示", "请输入正确的文件格式", QMessageBox.Yes)
```
