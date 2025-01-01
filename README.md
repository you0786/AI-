# AI-期末報告
組員:11224142 陳政佑 11225041 許帛勳 

Colaboratory
Colaboratory 是一個免費的 Jupyter 筆記本環境，不需要進行任何設定就可以使用，並且完全在雲端運行。借助 Colaboratory，我們可以在瀏覽器中編寫和執行程式碼、保存和共享分析結果，以及利用強大的運算資源，包含 GPU 與 TPU 來運行我們的實驗程式碼。

Colab 能夠輕鬆地與 Google Driver 與 Github 鏈接，我們可以使用 Open in Colab 插件快速打開 Github 上的 Notebook，或者使用類似於 https://colab.research.google... 這樣的鏈接打開。如果需要將 Notebook 儲存回 Github，直接使用 File→Save a copy to GitHub 即可。譬如筆者所有與 Colab 相關的程式碼歸置在了 AIDL-Workbench/colab。

依賴安裝

Colab 提供了便捷的依赖安装功能，允许使用 pip 或者 apt-get 命令进行安装：
![image](https://github.com/user-attachments/assets/c62129f0-9625-4ae7-a3b9-6582b1a4733b)

在 Colab 中还可以设置环境变量：

![image](https://github.com/user-attachments/assets/8a7f7901-17b7-4de8-8073-aac3d33c4554)



硬件加速

我们可以通过如下方式查看 Colab 为我们提供的硬件：

![image](https://github.com/user-attachments/assets/2fa81552-1033-4893-b889-8a8e1f773111)

如果需要为 Notebook 启动 GPU 支持：Click Edit->notebook settings->hardware accelerator->GPU，然后在代码中判断是否有可用的 GPU 设备：


![image](https://github.com/user-attachments/assets/52536730-0c21-4fe2-b39c-e97245e80130)


我们可以通过构建经典的 CNN 卷积层来比较 GPU 与 CPU 在运算上的差异：

![image](https://github.com/user-attachments/assets/c87ac932-9125-4920-80da-b8309b769b19)

本地运行


Colab 还支持直接将 Notebook 连接到本地的 Jupyter 服务器以运行，首先需要启用 jupyter_http_over_ws 扩展程序：

![image](https://github.com/user-attachments/assets/0d8f455c-f1f4-4e47-a58e-ac313b9493a2)

然后在正常方式启动 Jupyter 服务器，设置一个标记来明确表明信任来自 Colaboratory 前端的 WebSocket 连接：

![image](https://github.com/user-attachments/assets/24799027-6723-4f8a-beaf-36b51e0e3df6)

然后在 Colab 的 Notebook 中选择连接到本地代码执行程序即可。

数据与外部模块

Colab 中的 notebook 和 py 文件默认都是以 /content/ 作为工作目录，需要执行一下命令手动切换工作目录，例如：

![image](https://github.com/user-attachments/assets/6e5958f9-7c36-49bd-ac9f-ec194ea417b8)

Google Driver

在过去进行实验的时候，大量训练与测试数据的获取、存储与加载一直是令人头疼的问题；在 Colab 中，笔者将 Awesome DataSets https://url.wx-coder.cn/FqwyP) 中的相关数据通过 AIDL-Workbench/datasets 中的脚本持久化存储在 Google Driver 中。

在 Colab 中我们可以将 Google Driver 挂载到当的工作路径：

![image](https://github.com/user-attachments/assets/a708227a-28ca-418a-bfc6-52c5fdf6de63)

然后通过正常的 Linux Shell 命令来创建与操作：

![image](https://github.com/user-attachments/assets/4141a628-e0fd-432f-86a4-7e13ab1c986f)

外部 Python 文件

Colab 允许我们上传 Python 文件到工作目录下，或者加载 Google Driver 中的 Python：

![image](https://github.com/user-attachments/assets/5fe5cee4-8688-4d82-b7c9-85b0ec04f181)

文件上传与下载

Colab 还允许我们在运行脚本时候直接从本地文件上传，或者将生成的模型下载到本地文件：

![image](https://github.com/user-attachments/assets/2d1ff05d-da92-4014-9369-4471011edfe1)

BigQuery

如果我们使用了 BigQuery 提供了大数据的查询与管理功能，那么在 Colab 中也可以直接引入 BigQuery 中的数据源：

![image](https://github.com/user-attachments/assets/a2b7c1ad-3371-4062-8376-07fa01b4a8c3)

控件使用

网格

Colab 为我们提供了 Grid 以及 Tab 控件，来便于我们构建简单的图表布局：

![image](https://github.com/user-attachments/assets/46d968b2-edb1-4587-aa1a-5421caaadfeb)

![image](https://github.com/user-attachments/assets/85004cb3-d0dd-4c5e-8726-fe424b566145)

TabBar 提供了页签化的布局：

![image](https://github.com/user-attachments/assets/6debe08e-ca85-4312-83c5-0d2a678a8ba6)

![image](https://github.com/user-attachments/assets/528e3130-b4af-44a6-a6bf-2d987a416202)

表单
值得称道的是，Colab 还提供了可交互的表单式组件，来方便我们构建可动态输入的应用：

![image](https://github.com/user-attachments/assets/9601bbc2-ea45-4207-bf85-0561989fab79)


