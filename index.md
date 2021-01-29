
### 李元祥


## 个人信息
姓名：李元祥

性别：男

大学：云南大学滇池学院

专业班级：18级软件工程

github:LiYuanXiang-github.github.io

#
##      ##期中UML作业


###############################################################################


软件建模作业期中作业：
作答情况：
名字	所作答题目	gitHub主页	学号
李元祥	第一题全部（文字说明&UML模型图）	https://liyuanxiang-github.github.io/
20182123070
葛洲宇	第二题文字说明 	tingwenmoxin.github.io	20182123033
王庆瑞	第二题UML模型图	wqr20182123018.github.io	20182123018
李杰	第三题全部（文字说明&UML模型图）	diechild.github.io	20182123031

第一题
Repositories(仓库)项目代码托管功能
活动图和顺序图说明


//作答人：李元祥
//github地址: https://liyuanxiang-github.github.io/
活动图建模：
一：建模思路：
·根据对github的学习和了解：
得出有项目代码托管功能的使用有以下几个部分：
1 在官网进行账户注册
2 下载github客户端
3 登录客户端
4 建立仓库（Repositories）
5 选择本地文件夹作为本地仓库（用作以后的代码的更新等操作）
6 在客户端提交更新的代码（commit  to  master），此处简记为（CommitRepositorise）
固然有其中的3，4，5，6步骤为最重要的部分之一；步骤1 下载客户端和2注册账号需要使用的次数相对小很多；，
1从中可以直接抽取信息的动作有：登录和注册（LoginAndRegister）;创建仓库（CreateRepositories）,客户端登录（ClientLogin），提交（CommitRepositories）;
2间接可以提取的动作应该有：建立本地文件夹作为本地仓库（CreateLocalFile）,添加代码（AddCodeToLocalFile）
3同时，客户端登录提交代码时，需要先判断是否已有一个仓库（Repositories），如果没有，那么就需要先创建一个，然后再登录客户端；
4在已经建立好一个仓库以后，还需要本地有一个文件夹作为本地仓库；在本地仓库作代码的更新提交；所以，还需要判断是否已经有一个本地文件夹作为本地仓库；如果存在本地仓库，则可以直接进行代码的上传托管（AddCodeToLocalFile）;
5最后还需要在github的客户端进行提交（CommitRepositorise）;

二．建模过程：
1由开始步骤，所有的功能都建立在注册和登录上，固然，初始节点指向注册和登录（LoginAndRegister）这个活动；
	2登陆以后需要判断github是否已经建立仓库，既有判断条件是否有，没有则create一个仓库（CreateRepositories），固然判断以后，一个指向创建仓库（CreateRepositories）,并且箭头上带create指明创建关系；最后在建立完成指向客户端登陆(ClientLogin)，以完成后续的工作；在另外一种情况（即已经有github仓库）下，应该是指向客户端登陆(ClientLogin)；
3在进行客户端登录（ClientLogin）以后，如果要继续上传需要托管的代码，则需要把文件操作到本地仓库，；所以需要判断是否有本地仓库；
4判断是否有本地仓库中，一条线应该指向是添加代码到本地仓库；另一边（没有本地仓库）的情况则是创建一个本地文件夹作本地仓库（CreateLocalFile），在创建完本地仓库后，两条线共同指向添加代码到本地仓库（AddCodeToLocalFile）中；并且用Add作说明表示添加；
5最后，在本地文仓库添加完文件以后，还需要在客户端进行提交，有添加代码到本地仓库（AddCodeToLocalFile）指向提交到仓库（CommitRepositories）的路径；
6提交到仓库（CommitRepositories）完成以后，所有的流程结束，所以有提交到仓库（CommitRepositories）指向终点（Final）；

顺序图建模：

一 建模思路：
	根据上述的活动图大致对该功能有初步的了解；
1根据实际使用中；要完成代码托管功能，则需要先进行登录和注册（LoginAndRegister）对象的操作，可指导其中隐含一个实体对象用户信息数据库（UserInfoDataBase）；利用用户信息的比对从而实现对登录用户的认证，
2对于代码托管，必要有仓库（Repositories）这个对象，仓库最终实现托管的功能；而且由于最终要进行代码托管需要在客户端进行代码托管的更新，上传等操作，固然有客户端登陆（LoginClient）对象；
3最后提交的代码需要先放置在本地的仓库（LocalCodeFile）中，，所以存在有本地仓库这个对象作为一个媒介；
3在该功能中，他的参与者应该主要是用户（User）(虽然可能存在系统管理员等，但是这里主要用用户视角进行描述)，
根据上述描述，有以下的对象：
	1登录和注册（LoginAndRegister）
	2用户信息数据库（UserInfoDataBase）
	3仓库（Repositories）
	4客户端登陆（LoginClient）
	5本地的仓库（LocalCodeFile）
参与者 ：
	参与者主要是对于用户；
二建模过程：
1（1）用户（User）在登陆时，发送自己的信息给登陆注册对象（LoginAndRegister）,从而激活登陆注册对象（LoginAndRegister），使其进入工作状态；而登陆注册对象（LoginAndRegister）不能对用户信息验证用户身份，将用户信息发送给用户信息表（UserInfoDataBase）中；用户信息表（UserInfoDataBase）在查询后，返回消息给登陆注册对象（LoginAndRegister）结果；
（2）由于用户的信息可能填错，需要进行多次循环的填写用户信息；所以用*[UserInfo ! = true]进行约束，所以也需要对登陆注册对象（LoginAndRegister）返回的信息约束*[UserInfo! = true]；
（3）在登录成功后，需要登录注册对象一直保持登录状态；才能进行后续的代码托管工作；采取SelfMessage进项保持登陆状态；
（4）登陆以后，进行github仓库的建立，即：发送CreateRepositorise消息激活仓库（Repositories）；
（5）登陆后，存在需要撤销对用户信息表（UserInfoDataBase）进行撤销；避免占用服务器太多资源；

2在客户端登陆时，同1中得步骤；

3在登录完成，进行仓库创建以后，还需要发送激活消息给本地仓库，激活本地仓库（LocalCodeFile），在客户端登录（ClientLogin）后，对代码进行提交（CommitRepositories），所以有提交（Commit）操作从客户端（LoginClient）到仓库（Repositories），仓库返回一个消息告诉登录客户端（LoginClient）提交结果（returnCommitStatus）；
4由于用户只需要把代码放在自己的本地仓库（LocalCodeFile）中，然后再在登录客户端（LoginClient）提交，有用户到本地仓库（LocalCodeFile）的消息，并且返回在确认提交后给仓库（Repositories）发送CommitCode消息表示代码的提交；
5当用户提交完所有的代码以后，存在关闭客户端，撤销登录客户端（LoginClient）的消息；


第二题
版本管理
活动图和顺序图说明

//作答人：葛洲宇（文字）/王庆瑞（UML图）
//github地址：tingwenmoxin.github.io/ wqr20182123018.github.io
2、版本管理功能
（1）名词解释：
Git是一个开源的分布式版本控制系统，可以有效、高速地处理从很小到非常大的项目和版本管理。

未跟踪（untracked）：表示文件虽然在git仓库可以管理到的文件夹里，但是并没有呗仓库收录管理。
未修改（unmodified）：表示修改了文件，但还没提交到git仓库中。
已修改（modified）：表示对一个已修改文件的当前版本做了标记，使之包含在下次提交的版本中。
已暂存（staged）：表示数据已经安全的保存在git仓库中。

远程仓库操作：
Clone 克隆：第一次从远程仓库下载代码
Pull 拉取：获取团队其他成员代码提交变动
Push 推送：完成后的代码上传到远程仓库
本地仓库操作：
Checkout 检出：将本地仓库的内容检出到工作区
Add 添加：向暂存区添加代码，准备提交
Commit 提交：把暂存区的代码提交到本地仓库

明：
①查看需要处理的文件，文件的当前状态（git status）
②使用add操作将文件添加到暂存区（文件未添加到暂存区之前，可直接删除，如已提交，则需要通过git rm来删除）
③将暂存区的文件提交commit至仓库，并添加提交信息（此时文件的修改信息就被保存到git系统中）
④重复操作进行多次修改，可查看提交历史记录（git log），并通过git reset--hart来回退到需要的特定版本

第三题
代码查找功能
活动图和顺序图说明
//作答人：李杰（文字&图）
//github地址：diechild.github.io
代码查找功能:
用户在仓库界面输入要查找的代码，仓库界面转到包含代码所对应的文件并在文件中找到与要搜索代码有关的代码，然后把查找到的代码返回到仓库界面提供给用户查看。
