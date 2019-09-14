# Amazon Sagemaker Kullanarak Özelleştirilmiş Nesne Tespit Modeli Oluşturma

Bu atölyede, görüntülerdeki nesneleri tespit için Amazon Sagemaker ve COCO açık veri setini kullanacağız. Veri bilimi yaşam döngüsünün veriyi uygun formatlara dönüştürülmesinden, oluşturulan modelin sunulmasına kadar tüm adımlarını inceleyeceğiz.

Nesne tespiti, verilen bir imajdaki nesneleri bulundukları koordinatlarlarla beraber tanımlamaktır. Klasik bir nesne tespit çözümü girdi olarak imaj alır, çıktı olarak tespit ettiği nesneleri içinde bulundukları kutuların koordinatlarıyla(bounding box) beraber verir. 

Çözümü geliştirebilmek için öncelikle eğitim veri setini indirip işleyeceğiz, algoritmanın veri seti üzerinde çalışabilmesi için bir eğitim görevi yaratıp konfigüre edeceğiz ve algoritmanın oluşturduğu modeli barındırmak için bir endpoint oluşturacağız. Böylece Amazon Sagemaker nesne tespit algoritmasının nasıl çalıştığını inceleyebileceğimiz uçtan uca bir çalışma yapmış olacağız. [COCO açık veri setini](http://cocodataset.org/) ve Single Shot multibox Detector ([SSD](https://arxiv.org/abs/1512.02325)) algoritmasını Amazon Sagemaker platformu üzerinde kullanacağız.

Aynı zamanda oluşturduğunuz modeli nasıl barındırıp dış dünyanın kullanımına API'ler üzerinden sunabileceğinizi de göreceksiniz.

### Ön koşullar
AWS tarafından koordine edilen bir atölye çalışmasındaysanız size gerekli bilgiler iletilecektir.
Değilseniz, bir AWS hesabınız olmalıdır. Yoksa şu linkten oluşturabilirsiniz: https://aws.amazon.com/resources/create-account/

### Adımlar

Atölye çalışması esnasında aşağıdaki adımları tamamlayacağız:

1. <a href="module1/">**Modül 1**</a> - Amazon Sagemaker kullanarak notebook makinasının ayağa kaldırılması
2. <a href="module2/">**Modül 2**</a> - Amazon S3 üzerinde bucket'ımızın oluşturulması
3. <a href="module3/">**Modül 3**</a> - Modelin oluşturulması
4. <a href="module4/">**Modül 4**</a> - Modeli çağıracak AWS Lambda fonksiyonunun yazılması