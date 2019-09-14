## 3. Modelin oluşturulması
+ Konsolda sol üst köşedeki Services butonuna tıklayın, çıkan kutucuğa Sagemaker yazın ve en üstte gelen linke tıklayın
+ Soldaki menüden Notebook instances linkine tıklayın
+ Gelen listede oluşturduğunuz Notebook Instance’ın Status’u InService olarak görünüyorsa "Open Jupyter Lab" linkine tıklayın. InService olarak görünmüyorsa birkaç dakika daha bekleyin

<p align="center">
<img src="https://github.com/barisyasin/sagemaker-intro-tr/blob/master/blob/master/Picture4.png">
</p>

* "Open Jupyter Lab" linkine tıkladığınızda tarayıcınızın yeni bir tabında Jupyter Lab ekranı açılacak

* Jupyter’de yukarıdaki tablardan SageMaker Examples’ı seçin
* Introduction to Applying Machine Learning bölmesindeki Breast Cancer Prediction.ipynb notebook’unu bulun ve en sağdaki Use butonuna tıklayın, gelen pop-up ekranında Create copy butonuna tıklayın. Tarayıcınız yeni bir ekranında seçtiğiniz Jupyter notebook açılacaktır

<p align="center">
<img src="https://github.com/barisyasin/sagemaker-intro-tr/blob/master/blob/master/Picture5.png">
</p>

* Açılan notebook’u inceledikten sonra en üst kutucuktaki <your_s3_bucket_name_here> yazan yere not aldığınız bucket adını kopyalayın.

<p align="center">
<img src="https://github.com/barisyasin/sagemaker-intro-tr/blob/master/blob/master/Picture6.png">
</p>

* En alttaki kutucuğa gidin. Satırın en başına # yazarak comment out edin.
* Cell menüsünde Run All’ı seçin. Notebook’daki bütün satırların çalışması bitene kadar bekleyin. Bu işlem yaklaşık 10 dakika sürecektir. O anda çalıştırılan kod satırlarının yanında (*) işareti çıkacaktır

<p align="center">
<img src="https://github.com/barisyasin/sagemaker-intro-tr/blob/master/blob/master/Picture7.png">
</p>

<a name="head4"></a>