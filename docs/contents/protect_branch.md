<style type="text/css">
@import url('//maxcdn.bootstrapcdn.com/font-awesome/4.2.0/css/font-awesome.min.css');

.info-msg,
.success-msg,
.warning-msg,
.error-msg {
  padding: 5px 9px;
  border-radius: 5px 5px 5px 5px;
  border: 1px solid transparent;
  border-color: transparent;
  text-align:center; 
}
.info-msg {
  color: #059;
  background-color: #BEF;
}
.success-msg {
  color: #270;
  background-color: #DFF2BF;
}
.warning-msg {
  color: #9F6000;
  background-color: #FEEFB3;
}
.error-msg {
  color: #D8000C;
  background-color: #FFBABA;
}

</style>

Protect matching branches
-------------------------

![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image1.png)
<br/>
<br/>

参考
----

[*管理分支保护规则 - GitHub
Docs*](https://docs.github.com/zh/repositories/configuring-branches-and-merges-in-your-repository/defining-the-mergeability-of-pull-requests/managing-a-branch-protection-rule)

[*关于拉取请求审查 - GitHub
Docs*](https://docs.github.com/zh/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/about-pull-request-reviews)

![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image2.png)

*[审查拉取请求](https://docs.github.com/zh/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/reviewing-proposed-changes-in-a-pull-request)建议更改*

[*忽略拉取请求审查 - GitHub
Docs*](https://docs.github.com/zh/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/dismissing-a-pull-request-review)


<br/><br/>
## Require approvals

针对匹配分支的拉取请求需要审批(写审批人数)

提交时会反馈必须有一个人审核

![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image3.png)


<br/><br/>
Dismiss stale pull request approvals when new commits are pushed
----------------------------------------------------------------

推送新提交时关闭旧拉取请求审批


<br/><br/>
Require review from Code Owners
-------------------------------

## 要求代码所有者审阅


<br/><br/>
Require approval of the most recent reviewable push
---------------------------------------------------

让特定参与者在需要时将代码能推送到分支而不用创建拉取请求

可以添加允许不用拉取请求就能合并代码的开发者

![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image4.png)

推送的开发者的拉取请求必须由推送者以外的人审阅。

![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image5.png)


<br/><br/>
# 在分支保护下 Pull Request流程

目前配置：

![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image6.png)

<center>Figure 0‑1</center><br/><br/><br/>



![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image7.png)

<center>Figure 0‑2</center><br/><br/><br/>



![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image8.png)
<center>Figure 0‑3</center><br/><br/><br/>


目的：将Dev的commit合并到main分支。
参与人员：<span class="info-msg">A</span>提交者，<span class="warning-msg">B</span>审阅者
创建Pull Request

![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image9.png)

<center>Figure 0‑4 A创建Pull Request</center><br/><br/><br/>





创建Pull Request时，可以在右边窗口点击“齿轮”选择想被看审阅者

![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image10.png)

<center>Figure 0‑5 A创建Pull Request</center><br/><br/><br/>





在Pull Request里打开刚创建的Dev\#3
，看到需要至少有写入权限的审阅者来审阅。

![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image11.png)



<span class="info-msg">A</span>创建的Pull Request需要被审阅

写入权限来自：

![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image12.png)

<center>Figure 0‑6</center><br/><br/><br/>





<span class="warning-msg">B</span>审阅代码就点击“Add your review”

![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image13.png)

<center>Figure 0‑7</center><br/><br/><br/>





对代码有修改的建议（选择“Request
changes”），并修改改代码，通知对方A查看。

![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image14.png)

<center>Figure 0‑8</center><br/><br/><br/>





<span class="info-msg">A</span>能够看到对方<span class="warning-msg">B</span>发布的建议，点击“View changes”来查看修改并应用代码。

![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image15.png)



<span class="warning-msg">B</span>认为可以合并了，进行审阅同意

<span class="error-msg">注意</span>，如果出现冲突，要解决冲突才能合并！

![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image13.png)

<center>Figure 0‑9</center><br/><br/><br/>



<span class="warning-msg">B</span>审阅者要确认文件无误

![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image16.png)

<center>Figure 0‑10</center><br/><br/><br/>



同意合并

![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image17.png)

<center>Figure 0‑11</center><br/><br/><br/>



[*关于拉取请求合并 - GitHub
Docs*](https://docs.github.com/zh/pull-requests/collaborating-with-pull-requests/incorporating-changes-from-a-pull-request/about-pull-request-merges)

<span class="warning-msg">B</span>审阅者这边选择压缩然后合并，可以做到只commit一个提交，保持线性提交

![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image18.png)

<center>Figure 0‑12合并完成</center><br/><br/><br/>



![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image19.png)

<center>Figure 0‑13写上注释</center><br/><br/><br/>



![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image20.png)

<center>Figure 0‑14最后</center><br/><br/><br/>



其他
====

添加了github action后（针对main分支）：

![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image21.png)

分支在合并之前保持最新

![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image22.png)



<br/><br/><br/>

[状态检查](https://docs.github.com/zh/pull-requests/collaborating-with-pull-requests/collaborating-on-repositories-with-code-quality-features/about-status-checks)

提交旁边看到状态检查的“待处理”、“通过”或“失败”状态

![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image23.png)

![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image24.png)


<br/><br/><br/>


环境配置的地方：

![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image25.png)

![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image26.png)



[*提交签名*](https://docs.github.com/zh/authentication/managing-commit-signature-verification/signing-commits)

![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image27.png)

<br/><br/><br/>
线性历史提交

防止出现分叉

A--B--C--D

\\

E--F

A--B--C--D------m--

\\ /

E--F

A--B--C--D--m'
<br/><br/><br/>
当有勾选这个选项时，可以让谁可以直接推送到该分支

![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image28.png)



其他人无法选择红色的框来自己提交

![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image29.png)



不允许在此分支上创建新分支

![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image30.png)

![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image31.png)

![](https://gcore.jsdelivr.net/gh/arbin-ruisen/pic-bed@master/pic/image32.png)
