# House Price Prediction
電子系在職專班碩二 T107368523 陳建隆

首先拿到資料後先進行特徵分析

先導入需要的模組工具<br />
<img src="https://github.com/chen-chien-lung/Deep-Learning-Regression/blob/master/image/import.png" width="600" height="440"><br />

查找資料內是否有空值，結果顯示並無空值，所以可以必填值。<br />
<img src="https://github.com/chen-chien-lung/Deep-Learning-Regression/blob/master/image/isnull.png" width="600" height="440"><br />

觀察各資料特徵的關係<br />
<img src="https://github.com/chen-chien-lung/Deep-Learning-Regression/blob/master/image/image/Corr.png" width="600" height="440"><br />

因預測的是價格，所以觀察到幾個特徵值的大小並不正比於價格，所以把他們做one hot encode。<br />

Zipcode本身的值大小跟價格沒有正比關係，但特別幾個zipcode的價格是有比較高的現象。<br />
<img src="https://github.com/MachineLearningNTUT2018/regression-t107368523/blob/master/image/zipcode.png" width="600" height="440"><br />

Water_front 屬於有跟沒有，歸為one hot encode類別<br />
<img src="https://github.com/MachineLearningNTUT2018/regression-t107368523/blob/master/image/water_front.png" width="600" height="440"><br />

View也是，並不會因為數值高而有高價格。<br />
<img src="https://github.com/chen-chien-lung/Deep-Learning-Regression/blob/master/image/image/view.png" width="600" height="440"><br />

Condition也是同樣情況。<br />
<img src="https://github.com/chen-chien-lung/Deep-Learning-Regression/blob/master/image/condition.png" width="600" height="440"><br />


如下程式，把上面提及的特徵作one hot encode，其餘特徵作scale。<br />
<img src="https://github.com/chen-chien-lung/Deep-Learning-Regression/blob/master/image/onehot_and_scale.png" width="900" height="350"><br />


並將資料轉成Numpy array形式。<br />
<img src="https://github.com/chen-chien-lung/Deep-Learning-Regression/blob/master/image/to_numpy.png" width="900" height="350"><br />

DNN設計如下<br />
8層的Neural Network，並使用Relu激勵函數，Weight的初始化為Normal。<br />
選用Adam來優化，Batch大小為128，300 epochs。<br />
有使用Callback函數來提停止訓練。<br />
<img src="https://github.com/chen-chien-lung/Deep-Learning-Regression/blob/master/image/DNN.png" width="800" height="700"><br />

有寫一個函數來計算MAE，在訓練完後先來對Train的資料進行計算，如果結果不好就調整網路。<br />
<img src="https://github.com/chen-chien-lung/Deep-Learning-Regression/blob/master/image/cal_MAE.png" width="450" height="150"><br />

用曲線圖來觀察一下整個訓練的情況，主要是觀察是否有Over fitting。<br />
<img src="https://github.com/chen-chien-lung/Deep-Learning-Regression/blob/master/image/plot_loss.png" width="600" height="500"><br />

最後預測測試資料並輸出<br />
<img src="https://github.com/chen-chien-lung/Deep-Learning-Regression/blob/master/image/save_model.png" width="1000" height="180"><br />
