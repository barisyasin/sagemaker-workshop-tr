# Amazon Sagemaker Kullanarak Özelleştirilmiş Nesne Tespit Modeli Oluşturma

Nesne tespiti, verilen bir imajdaki nesneleri imajda bulundukları koordinatlarlarla beraber tanımlamaktır. Klasik bir nesne tespit çözümü girdi olarak imaj alır, çıktı olarak tespit ettiği nesneleri içinde bulundukları kutuların koordinatlarıyla(bounding box) beraber verir. 
<img src="images/img001.png" alt="" width="700px" style="background-color:black;"/>


Bu atölyede, görüntülerdeki kuşların türlerini ve görüntüdeki yerini tespit için Amazon Sagemaker ve Caltech Birds açık veri setini kullanacağız. 

Veri bilimi yaşam döngüsünün veriyi uygun formatlara dönüştürülmesinden, oluşturulan modelin sunulmasına kadar birçok aşamasını göreceğiz.

<img src="images/img002.png" alt="" width="700px" style="background-color:black;"/>


Amazon SageMaker, geliştiricilere ve veri bilimcilere Machine Learning(ML) modellerini hızla geliştirme, eğitme ve dağıtma kabiliyeti sunan bir servis. Bu servisi kullanarak yapabileceklerinizden bazıları:
+ Verilerinizi etiketleme ve hazırlama
<img src="images/img003.png" alt="" width="700px" style="background-color:black;"/>
+ Algoritma seçme, modeli eğitme, dağıtım için ayarlayıp optimize etme
<img src="images/img004.png" alt="" width="700px" style="background-color:black;"/>
+ Tahmin yapma ve dağıtma(üretim, dev-test vb. ortamlar) 
<img src="images/img005.png" alt="" width="700px" style="background-color:black;"/>

Çözümü geliştirebilmek için öncelikle eğitim veri setini indirip işleyeceğiz, algoritmanın veri seti üzerinde çalışabilmesi için bir eğitim görevi yaratıp konfigüre edeceğiz ve algoritmanın oluşturduğu modeli barındırmak için bir endpoint oluşturacağız. Böylece Amazon Sagemaker nesne tespit algoritmasının nasıl çalıştığını inceleyebileceğimiz uçtan uca bir çalışma yapmış olacağız. [Caltech birds açık veri setini](http://www.vision.caltech.edu/visipedia/CUB-200-2011.html) ve Single Shot multibox Detector ([SSD](https://arxiv.org/abs/1512.02325)) algoritmasını Amazon Sagemaker platformu üzerinde kullanacağız.

### Ön koşullar
AWS tarafından koordine edilen bir atölye çalışmasındaysanız size gerekli bilgiler iletilecektir.
Değilseniz, bir AWS hesabınız olmalıdır. Yoksa şu linkten oluşturabilirsiniz: https://aws.amazon.com/resources/create-account/

### Adımlar

Atölye çalışması esnasında aşağıdaki adımları tamamlayacağız:

1. <a href="module1/">**Modül 1**</a> - Amazon Sagemaker kullanarak notebook makinasının ayağa kaldırılması
2. <a href="module2/">**Modül 2**</a> - Amazon S3 üzerinde bucket'ımızın oluşturulması
3. <a href="module3/">**Modül 3**</a> - Modelin oluşturulması ve barındırılması



Introduction
Object detection is the process of identifying and localizing objects in an image. A typical object detection solution takes an image as input and provides a bounding box on the image where an object of interest is found. It also identifies what type of object the box encapsulates. To create such a solution, we need to acquire and process a traning dataset, create and setup a training job for the alorithm so that it can learn about the dataset. Finally, we can then host the trained model in an endpoint, to which we can supply images.

This notebook is an end-to-end example showing how the Amazon SageMaker Object Detection algorithm can be used with a publicly available dataset of bird images. We demonstrate how to train and to host an object detection model based on the Caltech Birds (CUB 200 2011) dataset. Amazon SageMaker's object detection algorithm uses the Single Shot multibox Detector (SSD) algorithm, and this notebook uses a ResNet base network with that algorithm.


We will also demonstrate how to construct a training dataset using the RecordIO format, as this is the format that the training job consumes. This notebook is similar to the Object Detection using the RecordIO format notebook, with the following key differences:

We provide an example of how to translate bounding box specifications when providing images to SageMaker's algorithm. You will see code for generating the train.lst and val.lst files used to create recordIO files.
We demonstrate how to improve an object detection model by adding training images that are flipped horizontally (mirror images).
We give you a notebook for experimenting with object detection challenges with an order of magnitude more classes (200 bird species, as opposed to the 20 categories used by Pascal VOC).
We show how to chart the accuracy improvements that occur across the epochs of the training job.
Note that Amazon SageMaker Object Detection also allows training with the image and JSON format, which is illustrated in the image and JSON Notebook.

Setup
Before preparing the data, there are some initial steps required for setup.

This notebook requires two additional Python packages:

OpenCV is required for gathering image sizes and flipping of images horizontally.
The MXNet runtime is required for using the im2rec tool.





