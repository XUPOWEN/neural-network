# GoogleColab
完全雲端運行：使用Google-CoLaboratory訓練神經網路合作實驗室是一個Google研究項目，旨在幫助傳播機器學習培訓和研究成果。它是一個Jupyter筆記本環境，不需要進行任何設定就可以使用，並且完全在雲端運作。

Colaboratory 筆記本儲存在 Google 雲端硬盤( https://drive.google.com/ )中，可以分享，就相當於您使用Google 檔案或表格一樣。

Colaboratory 可免費使用。論文介紹如何使用Google CoLaboratory 訓練神經網路道路。工具連結：https://colab.research.google.com/
谷歌近期上線了協作程式編寫程式碼的內部工具Google CoLaboratory。Colaboratory是一個Google研究項目，旨在幫助傳播機器學習培訓和研究成果。它是一個Jupyter筆記本環境，不需要進行任何設定就可以使用，並且完全在雲端運行。

Colaboratory 筆記本儲存在 Google 雲端硬盤( https://drive.google.com/ ) 中，可以分享，就如同您使用 Google 檔案或表單一樣。Colaboratory 可免費使用。

# CoLaboratory
首先，請造訪CoLaboratory網站（http://g.co/colab），註冊後接受使用該工具的邀請。確認郵件通常需要一天才能回到您的郵箱。 CoLaboratory允許使用Google虛擬機器執行機器學習任務和建立了模型，不需要擔心計算力的問題，而且它是免費的。
開啟CoLaboratory，會出現一個「Hello, Colaboratory」文件，包含一些基本範例。建議嘗試。

使用CoLaboratory在Jupyter Notebook上可以寫好程式碼。寫好一些後執行(Shift + Enter)，程式碼單元下方就會產生輸出。

![image](https://github.com/XUPOWEN/neural-network/blob/main/731851.png)

除了寫程式碼，CoLaboratory還有技巧（trick）。

你可以在notebook中


shell指令前面加上「!」。如：!pip install -q keras。這樣你就可以仔細控制正在使用的Google虛擬機。點擊上方左（選單列下）的黑色按鈕就可以找到它們的程式碼片段。
本文旨在展示如何使用CoLaboratory 訓練神經網路。我們將展示一個在威斯康辛乳腺癌資料集上訓練神經網路的範例，資料集可在UCI 機器學習儲存庫（ http://archive.ics.uci.edu / ） ml/datasets）取得。論文的範例相對較簡單。
這裡所使用的CoLaboratory筆記本連結：https://colab.research.google.com/notebook#fileId=1aQGl_sH4TVehK8PDBRspwI4pD16xIR0r

# 深度學習
深度學習是一種機器學習技術，它利用計算技術程式模擬了生物神經元的運作。各層中的神經元網路不斷將資訊從輸入傳輸到輸出，直到其權重調整到可以產生反映特徵和目標之間存在底層關係的算法。

要想更多地了解神经网络，推荐阅读这篇论文《Artificial Neural Networks for Beginners》（https://arxiv.org/pdf/cs/0308031.pdf）。

# 代碼
打开 CoLaboratory，出现一个新的 untitled.ipynb 文件供你使用。

谷歌允许使用其服务器上的一台 linux 虚拟机，这样你可以访问终端为项目安装特定包。如果你只在代码单元中输入 !ls 命令（记得命令前加!），那么你的虚拟机中会出现一个 datalab 文件夹。

![image](https://github.com/XUPOWEN/neural-network/blob/main/ls.png)

我们的任务是将数据集放置到该机器上，这样我们的 notebook 就可以访问它。你可以使用以下代码：
![image](https://github.com/XUPOWEN/neural-network/blob/main/ls2.png)

输入 !ls 命令，检查机器上是否有该文件。你将看到 datalab 文件夹和 breast_cancer_data.csv 文件。
![image](https://github.com/XUPOWEN/neural-network/blob/main/ls3.png)

数据预处理：
现在数据已经在机器上了，我们使用 pandas 将其输入到项目中。
![image](https://github.com/XUPOWEN/neural-network/blob/main/cctt.png)

CoLaboratory 上的输出结果图示。
现在，分割因变量（Dependent Variables）和自变量（Independent Variables）。
![image](https://github.com/XUPOWEN/neural-network/blob/main/value.png)

Y 包含一列，其中的「M」和「B」分别代表「是」（恶性）和「否」（良性）。我们需要将其编码成数学形式，即「1」和「0」。可以使用 Label Encoder 类别完成该任务。

![image](https://github.com/XUPOWEN/neural-network/blob/main/encoder.png)

（如果数据类别多于两类，则使用 OneHotEncoder）
现在数据已经准备好，我们将其分割成训练集和测试集。在 Scikit-Learn 中使用 train_test_split 可以轻松完成该工作。
![image](https://github.com/XUPOWEN/neural-network/blob/main/%E8%9E%A2%E5%B9%95%E6%93%B7%E5%8F%96%E7%95%AB%E9%9D%A2%202023-11-01%20231746.png)

参数 test_size = 0.2 定义测试集比例。这里，我们将训练集设置为数据集的 80%，测试集占数据集的 20%。
# Keras
是一種建構人工神經網路的高階API。它使用TensorFlow 或Theano 後端執行內部運作。要安裝Keras，必須先安裝TensorFlow。CoLaboratory 已經在虛擬機器上安裝了TensorFlow。

使用以下指令可以檢查是否安裝TensorFlow：
!pip show tensorflow
你也可以使用!pip install tensorflow==1.2，安裝特定版本的TensorFlow。

另外，如果你更喜歡用Theano 後端，可以閱讀該文件： https://keras.io/backend/ 。

# 安裝Keras

!pip install -q keras

![image](https://github.com/XUPOWEN/neural-network/blob/main/keras.png)

使用Sequential 和Dense 類別指定神經網路的節點、連接和規格。如上所示，我們將使用這些自訂網路的參數並進行調整。
為了初始化神經網絡，我們將建立一個Sequential 類別的物件。

![image](https://github.com/XUPOWEN/neural-network/blob/main/ANN.png)

現在，我們要來設計網路。
對於每個隱藏層，我們需要定義三個基本參數：units、kernel_initializer 和activation。units 參數定義每層包含的神經元數量。Kernel_initializer 定義神經元在輸入資料上執行時的初始權重（詳見 https://faroit.github.io/keras-docs/1.2.2/initializations/ ）。activation 定義資料的激活函數。
注意：如果現在這些項非常大也沒事，很快就會變得更加清晰。
## 第一層：
16 個具備統一初始權重的神經元，活化函數為ReLU。此外，定義參數input_dim = 30 作為輸入層的規格。注意我們的資料集中有30 個特徵列。
Cheat：
我們如何決定這一層的單元數？人們往往會說這需要經驗和專業知識。對於初學者來說，一個簡單方式是：x 和y 的總和除以2。如(30+1)/2 = 15.5 ~ 16，因此，units = 16。
## 第二層：
第二層和第一層一樣，不過第二層沒有input_dim 參數。
輸出層：由於我們的輸出是0 或1，因此我們可以使用具備統一初始權重的單一單元。但是，這裡我們使用sigmoid 來活化函數。

![image](https://github.com/XUPOWEN/neural-network/blob/main/classifier.png)

擬合：
運行人工神經網絡，發生反向傳播。你將在CoLaboratory 上看到所有處理過程，而不是在自己的電腦上。

![image](https://github.com/XUPOWEN/neural-network/blob/main/ANNclass.png)

這裡batch_size 是你希望同時處理的輸入量。epoch 指數據通過神經網路一次的整個週期。它們在Colaboratory Notebook 中顯示如下：

![image](https://github.com/XUPOWEN/neural-network/blob/main/demo.png)

進行預測，建構混淆矩陣。

![image](https://github.com/XUPOWEN/neural-network/blob/main/2c2.png)

訓練網路後，就可以在X_test set 上進行預測，以檢查模型在新資料上的效能。在程式碼單元中輸入和執行cm 查看結果。

混淆矩陣
混淆矩陣是模型做出的正確、錯誤預測的矩陣表徵。此矩陣可供個人調查哪些預測和另一種預測混淆。這是一個2×2 的混淆矩陣

![image](https://github.com/XUPOWEN/neural-network/blob/main/square.png)

混淆矩阵如下所示。[cm (Shift+Enter)]

![image](https://github.com/XUPOWEN/neural-network/blob/main/cm.png)

上图表示：70 个真负类、1 个假正类、1 个假负类、42 个真正类。很简单。该平方矩阵的大小随着分类类别的增加而增加。

这个示例中的准确率几乎达到 100%，只有 2 个错误预测。但是并不总是这样。有时你可能需要投入更多时间，研究模型的行为，提出更好、更复杂的解决方案。如果一个网络性能不够好，你需要调整超参数来改进模型。

希望本文可以帮助你开始使用 Colaboratory。该教程的 Notebook 地址：https://colab.research.google.com/notebook#fileId=1aQGl_sH4TVehK8PDBRspwI4pD16xIR0r

原文链接：https://medium.com/@howal/neural-networks-with-google-colaboratory-artificial-intelligence-getting-started-713b5eb07f14
