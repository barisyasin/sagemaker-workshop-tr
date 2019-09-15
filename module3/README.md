## 3. Modelin oluşturulması
+ Konsolda sol üst köşedeki Services butonuna tıklayın, çıkan kutucuğa Sagemaker yazın ve Amazon Sagemaker linkine tıklayın

<img src="images/img001.png" alt="" width="700px" />

+ Soldaki menüden Notebook instances linkine tıklayın

<img src="images/img002.png" alt="" width="700px" />

+ Gelen listede oluşturduğunuz Notebook Instance’ın Status’u InService olarak görünüyorsa "Open Jupyter Lab" linkine tıklayın. InService olarak 
görünmüyorsa birkaç dakika daha bekleyin

<img src="images/img003.png" alt="" width="700px" />

+ "Open Jupyter Lab" linkine tıkladığınızda tarayıcınızın yeni bir tabında Jupyter Lab ekranı açılacak
+ Açılan ekranın sol tarafındaki "Git Clone" butonuna tıklayın

<img src="images/img004.png" alt="" width="700px" />

+ Çıkan pop-up'a https://github.com/barisyasin/sagemaker-workshop-tr.git adresini girin ve Clone butonuna tıklayın.

<img src="images/img006.png" alt="" width="700px" />

+ Bir kaç saniye bekledikten sonra sol taraftaki File Browser tabında repository klasörünün geldiğini göreceksiniz. Eğer gelmezse yine aynı tabdaki Refresh File List butonuna tıklayın.

<img src="images/img007.png" alt="" width="700px" />

+ sagemaker-workshop-tr/code/object_detection_birds.ipynb python notebook dosyasının üzerine çift tıklayarak açın

+ Notebook dosyasını genel olarak gözden geçirin

+ Notebook içinde <your_s3_bucket_name_here> yazan yere not aldığınız bucket adını kopyalayın.

<img src="images/img008.png" alt="" width="700px" />

+ En üstteki menüden Run-->Run All Cells'i seçin ve notebook'unuzda bulunan bütün satırların işletilmesinin tamamnlanmasını bekleyin. Tamamlanan satırların sol üst köşesinden o satırın işletilme sırasını gösteren bir sayı bulunur. İşletilmekte olan veya henüz işletilmemiş hücrelerin sol üst köşesinde ise [*] sembolü bulunur.

<img src="images/img009.png" alt="" width="700px" />

+ Training aşaması biraz zaman alacaktır. Bu esnada Amazon Sagemaker ortamını daha iyi tanımak için şu adımları yerine getirebilirsiniz: 
    + Notebook'u satır satır okuyarak hücrelerin çıktıları inceleyebilirsiniz.
    + od_model.fit(inputs=data_channels, logs=True) hücresinin altına yazılan logları takip edebilirsiniz. Sözkonusu satır modelimizin trainingini yapan ve en uzun sürmesi beklenen satırdır.
    + Sagemaker konsolundan notebook makinası tarafından başlatılan Training job'ları gözlemleyebilirsiniz.

    <img src="images/img010.png" alt="" width="700px" />
    <img src="images/img011.png" alt="" width="700px" />
    <img src="images/img012.png" alt="" width="700px" />
    <img src="images/img013.png" alt="" width="700px" />

    + Sagemaker konsolundan notebook makinası tarafından oluşturulan Endpoint'leri inceleyebilirsiniz
+ Training tamamlandığında modeli genişletilmiş veri setiyle tekrar eğitilmeden önceki haliyle karşılaştırın.
    + Önceki mAP:

    <img src="images/beforemap.png" alt="" width="400px" />

    + Sonraki mAP:

    <img src="images/aftermap.png" alt="" width="400px" />

    + Önceki tahmin 1-2:

    <img src="images/before01.png" alt="" width="400px" />

    + Sonraki tahmin 1-2:

    <img src="images/after01.png" alt="" width="400px" />

    + Önceki tahmin 3-4:

    <img src="images/before02.png" alt="" width="400px" />

    + Sonraki tahmin 3-4:

    <img src="images/after02.png" alt="" width="400px" />

    + Önceki tahmin 5:

    <img src="images/before03.png" alt="" width="400px" />

    + Sonraki tahmin 5:

    <img src="images/after03.png" alt="" width="400px" />
   
    