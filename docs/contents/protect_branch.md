Protect matching branches
=========================

![](.//media/image1.png){width="5.768055555555556in"
height="3.9833333333333334in"}

参考
----

[*管理分支保护规则 - GitHub
Docs*](https://docs.github.com/zh/repositories/configuring-branches-and-merges-in-your-repository/defining-the-mergeability-of-pull-requests/managing-a-branch-protection-rule)

[*关于拉取请求审查 - GitHub
Docs*](https://docs.github.com/zh/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/about-pull-request-reviews)

![](.//media/image2.png){width="5.768055555555556in" height="2.775in"}

*[审查拉取请求](https://docs.github.com/zh/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/reviewing-proposed-changes-in-a-pull-request)建议更改*

[*忽略拉取请求审查 - GitHub
Docs*](https://docs.github.com/zh/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/dismissing-a-pull-request-review)

Require approvals
-----------------

针对匹配分支的拉取请求需要审批(写审批人数)

提交时会反馈必须有一个人审核

![](.//media/image3.png){width="5.768055555555556in"
height="0.7798611111111111in"}

Dismiss stale pull request approvals when new commits are pushed
----------------------------------------------------------------

推送新提交时关闭旧拉取请求审批

Require review from Code Owners
-------------------------------

要求代码所有者审阅

Require approval of the most recent reviewable push
---------------------------------------------------

让特定参与者在需要时将代码能推送到分支而不用创建拉取请求

可以添加允许不用拉取请求就能合并代码的开发者

![](.//media/image4.png){width="5.768055555555556in"
height="1.7583333333333333in"}

推送的开发者的拉取请求必须由推送者以外的人审阅。

![](.//media/image5.png){width="5.768055555555556in"
height="0.48194444444444445in"}

Pull Request流程
----------------

目前配置：

![](.//media/image6.png){width="5.768055555555556in"
height="1.9666666666666666in"}

Figure 0‑1

![](.//media/image7.png){width="5.768055555555556in"
height="3.861111111111111in"}

Figure 0‑2

![](.//media/image8.png){width="2.4171861329833773in"
height="2.434064960629921in"}

Figure 0‑3

目的：将Dev的commit合并到main分支。

参与人员：A提交者，B审阅者

A创建Pull Request

![](.//media/image9.png){width="5.768055555555556in"
height="1.7902777777777779in"}

Figure 0‑4 A创建Pull Request

创建Pull Request时，可以在右边窗口点击“齿轮”选择想被看审阅者

![](.//media/image10.png){width="5.768055555555556in"
height="2.920138888888889in"}

Figure 0‑5 A创建Pull Request

在Pull Request里打开刚创建的Dev\#3
，看到需要至少有写入权限的审阅者来审阅。

![](.//media/image11.png){width="5.768055555555556in"
height="5.447916666666667in"}

A创建的Pull Request需要被审阅

写入权限来自：

![](.//media/image12.png){width="5.768055555555556in"
height="4.280555555555556in"}

Figure 0‑6

B审阅代码就点击“Add your review”

![C:\\Users\\ruise\\AppData\\Local\\Temp\\WeChat
Files\\9e40fdd22643929be8729962ce3ab2f.png](.//media/image13.png){width="5.768055555555556in"
height="4.113821084864392in"}

Figure 0‑7

对代码有修改的建议（选择“Request
changes”），并修改改代码，通知对方A查看。

![C:\\Users\\ruise\\AppData\\Local\\Temp\\WeChat
Files\\20b133f84414ff6f6f2b9b45daa6b39.png](.//media/image14.png){width="5.768055555555556in"
height="2.1600524934383203in"}

Figure 0‑8

A能够看到对方B发布的建议，点击“View changes”来查看修改并应用代码。

![](.//media/image15.png){width="5.768055555555556in"
height="3.578472222222222in"}

B认为可以合并了，进行审阅同意

注意，如果出现冲突，要解决冲突才能合并！

![C:\\Users\\ruise\\AppData\\Local\\Temp\\WeChat
Files\\9e40fdd22643929be8729962ce3ab2f.png](.//media/image13.png){width="5.768055555555556in"
height="4.115220909886264in"}

Figure 0‑9

B审阅者要确认文件无误

![](.//media/image16.png){width="5.768055555555556in"
height="0.7291666666666666in"}

Figure 0‑10

同意合并

![](.//media/image17.png){width="5.768055555555556in"
height="2.0854166666666667in"}

Figure 0‑11

[*关于拉取请求合并 - GitHub
Docs*](https://docs.github.com/zh/pull-requests/collaborating-with-pull-requests/incorporating-changes-from-a-pull-request/about-pull-request-merges)

B审阅者这边选择压缩然后合并，可以做到只commit一个提交，保持线性提交

![](.//media/image18.png){width="5.768055555555556in"
height="3.6645833333333333in"}

Figure 0‑12完成

![](.//media/image19.png){width="5.768055555555556in"
height="3.8041666666666667in"}

Figure 0‑13写上注释

![](.//media/image20.png){width="5.768055555555556in"
height="0.6715277777777777in"}

Figure 0‑14最后

其他
====

添加了github action后（针对main分支）：

![](.//media/image21.png){width="5.768055555555556in"
height="2.495833333333333in"}

分支在合并之前保持最新

![](.//media/image22.png){width="5.768055555555556in" height="0.5875in"}

[*状态检查*](https://docs.github.com/zh/pull-requests/collaborating-with-pull-requests/collaborating-on-repositories-with-code-quality-features/about-status-checks)

提交旁边看到状态检查的“待处理”、“通过”或“失败”状态

![](.//media/image23.png){width="5.574586614173229in"
height="2.361111111111111in"}

![](.//media/image24.png){width="5.768055555555556in"
height="1.3534722222222222in"}

![](.//media/image25.png){width="5.768055555555556in"
height="1.511111111111111in"}

环境配置的地方：

![](.//media/image26.png){width="5.768055555555556in" height="2.7125in"}

[*提交签名*](https://docs.github.com/zh/authentication/managing-commit-signature-verification/signing-commits)

![](.//media/image27.png){width="5.768055555555556in"
height="0.5256944444444445in"}

线性历史提交

防止出现分叉

A--B--C--D

\\

E--F

A--B--C--D------m--

\\ /

E--F

A--B--C--D--m'

当有勾选这个选项时，可以让谁可以直接推送到该分支

![](.//media/image28.png){width="5.768055555555556in"
height="3.015972222222222in"}

其他人无法选择红色的框来自己提交

![C:\\Users\\ruise\\AppData\\Local\\Temp\\WeChat
Files\\5b3239ba7abe5a4c5bbb4b157bf5fcc.png](.//media/image29.png){width="5.768055555555556in"
height="1.6803958880139982in"}

不允许在此分支上创建新分支

![](.//media/image30.png){width="5.768055555555556in"
height="0.4354166666666667in"}

![](.//media/image31.png){width="5.768055555555556in"
height="1.2958333333333334in"}

![C:\\Users\\ruise\\AppData\\Local\\Temp\\WeChat
Files\\895f26260a50ffc3aa9afd712e926c4.png](.//media/image32.png){width="3.703472222222222in"
height="3.3006944444444444in"}
