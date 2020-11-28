
### 个人信息

姓名：李元祥

性别：男

大学：云南大学滇池学院

专业班级：18级软件工程

github:LiYuanXiang-github.github.io


Figure 1 :
GitHub System用例图说明：
作者：李元祥，李杰
用例图建模过程分析：
一：根据GitHub中的功能，我们对其进行如下描述，GitHub System中总共有以下的几大用例：
1.	查找文件/文档（Search Files）
2.	文件查阅（Review Files）
3.	文件管理(Manage Files)（对文件管理有三点，即对文件进行添加（Add Files）,删除(Delete File),修改(Modify)）
4.	文件下载（Download Files）
5.	系统管理(System Manage)；
其中GitHub中主要有两大参与者：
1.	用户（User）
2.	管理员（Administrator）
二：模型分析：
1.	Search Files, Review Files,Download Files,Manage Files属于管理员（Administrator）和用户（User）的共同的用例
2.	System Manage应该是只有管理员才拥有的用例

三：模型建立： 
User和Administrator共同指向Search Files, Review Files,Download Files,Manage Files，而Administrator单独指向System Manage。



Figure 2 :
Files Manage用例图说明：
作者：李元祥
用例图建模过程分析：
一：根据上述的Files Manage中的功能分析，对其进行如下描述 Files Manage中总共有以下的几大用例：
1.	添加文件（Add Files）
2.	删除文件（Delete Files）
3.	修改文件(Modify Files)
4.	创建新文件(Create new Files)
5.	提交文档(Commit Cocuments)
6.	提交代码(Commit Code)
7.	提交删除(Commit Delete)
8.	提交修改(Commit Modify)
9.	查找文件(Search Files)
其中Files Manage中主要有两大参与者：
1．	用户（User）
2．	管理员（Administrator）
二：模型分析
1.	管理员（Administrator）和用户（User）都共同有添加文件（Add Files），删除文件（Delete Files），
修改文件(Modify Files)的用例；
2	.对于添加文件（Add Files），应该是被创建新文件（Create new Files）以后才能添加，而后应该是对文件进行文档提交（Commit Cocuments）和代码提交（Commit Code）；
3.	对于删除文件（Delete Files），应该依赖于查找文件（Search Files）以后,才能进行修改。而后进删除提交（Commit Delete），固然有删除提交（Commit Delete）被包含于删除文件（Delete Files）；
4.	对于修改文件（Modify Files），应该依赖于查找文件（Search Files）以后,才能进行修改。而后进删除提交（Commit Midify），固然有删除提交（Commit Modify）被包含于删除文件（Modify Files）；
三．模型建立： 
1.	用户（User）和管理员（Administrator）都共同指向与添加文件（Add Files），删除文件（Delete Files），修改文件(Modify Files)。
2.	添加文件（Add Files）指向被依赖于创建新文件(Create new  Files)；删除文件（Delete Files），
修改文件(Modify Files)指向与添加文件（Add Files），并且是extend关系；
3.	删除文件（Delete Files）和修改文件（Modify Films）中都有共同指向与查找文件（Search Files）的依赖关系，且分别指向对应的删除提交（Commit Delete）或者（Commit Modify）；




Figure 3 :
Search and Review Files用例图说明：
作者：王庆瑞，葛洲宇
用例图建模过程分析：
一：根据上述的Search and Review Files中的功能分析，对其进行如下描述 Files Manage中总共有以下的几大用例：
1.	查找文件（Search Files）
2.	阅读文件（Review Files）
3.	模糊查找（Fuzzy Saerch）
4.	精确查找（Exact Search）
5.	下载后查看（Download after Review）
6.	在线查看（Online Review）
其中Search and Review Files中主要有两大参与者：
1.	  用户（User）
2.	管理员（Administrator）
二：模型分析
1.	管理员（Administrator）和用户（User）都共同有查找文件（Search Files）和阅读文件（Review Files）
2.	对于查找文件（Search Files），存在精确查找（Exact Search）找和模糊查询（Fuzzy Saerch）的泛化关系；
3.	对于阅读文件（Review Files），存在下载后查看（Download after Review）和在线查看（Online Review）的泛化关系
4.	由于阅读前应该是先查找文件（Search Files）到然后再阅读文件（Review Files），固然存在阅读文件（Review Files）依赖查找文件（Search Files）；

三．	模型建立： 
1.	用户（User）和管理员（Administrator）都共同指向查找文件（Search Files）和阅读文件（Review Files）
2.	阅读文件（Review Files）依赖指向于查找文件（Search Files）；
3.	精确查找（Exact Search）和模糊查询（Fuzzy Saerch）指向泛化于查找文件（Search Files）；
4.	下载后查看（Download after Review）和在线查看（Online Review）指向泛化于阅读文件（Review Files）；




Figure 4 :
Download Files用例图说明：
作者：李元祥
用例图建模过程分析：
一：根据上述的Download Files中的功能分析，对其进行如下描述 Files Manage中总共有以下的几大用例：
1.	查找文件（Search Files）
2.	下载文件（Download Files）
3.	克隆或下载文件（Clone or Download）
4.	源文件下载（Raw）
5.	桌面打开（Open  in  Desktop）
6.	Zip下载（DwonloadZip）
其中Download Files中主要有两大参与者：
1	 用户（User）
2	管理员（Administrator） 
二：模型分析
1.	管理员（Administrator）和用户（User）都共同有下载文件（Download Files）
2.	下载文件（Download Files）的下载之前应该有查找文件（Search Files）固然有依赖关系;下载文件（Download Files）分为两种，分别是克隆或下载文件（Clone or Download）和源文件下载（Raw），存在的是泛化关系。
3.   克隆或下载文件（Clone or Download）中又分为桌面打开（Open  in  Desktop）以及Zip下载（DwonloadZip）两种方式；
三．模型建立： 
1.	用户（User）和管理员（Administrator）都共同指向下载文件（Download Files）
2.	下载文件（Download Files）指向查找文件（Search Files），为依赖关系;
3.	克隆或下载文件（Clone or Download）和源文件下载（Raw）共同指向下载文件（Download Files）并且是泛化关系；
4.	桌面打开（Open  in  Desktop）以及Zip下载（DwonloadZip）指向克隆或下载文件（Clone or Download），并且是extend关系；

