## 4. Modeli çağıracak AWS Lambda fonksiyonunun yazılması

* Şimdi yarattığımız bu model’ı çağıran bir Lambda fonksiyonu yaratacağız. Amacımız aşağıdaki yapıyı kurarak modelimizi web servisler üzerinden ulaşılabilir hale getirmek

<p align="center">
<img src="https://github.com/barisyasin/sagemaker-intro-tr/blob/master/blob/master/Picture8.png">
</p>

+ Konsolda sol üst köşedeki Services butonuna tıklayın, çıkan kutucuğa Lambda yazın ve en üstte gelen linke tıklayın
+ Gelen ekranda Create Function butonuna tıklayın
+ Name alanına sagemakerinvokerfunction yazın
+ Runtime’ı Python 3.6 seçin

<p align="center">
<img src="https://github.com/barisyasin/sagemaker-intro-tr/blob/master/blob/master/Picture9.png">
</p>

+ Role için Create a custom role seçeneğine tıklayın. AWS Lambda’nın Amazon Sagemaker’ı çağırırken kullanacağı rolü oluşturacağınız ekran açılacaktır 
+ Açılan ekranda View Policy Document’e tıkladıktan sonra ortaya çıkan Edit linkine tıklayın. Policy document kutucuğu editable duruma gelecektir. Kutucuğa şu [text’i](code/policy.txt) girin:


```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": "sagemaker:InvokeEndpoint",
            "Resource": "*"
        }
    ]
}
```

+ Allow butonuna tıklayın
+ Create function butonuna tıklayın
+ Yeni ekranda Function Code alanına doğru inin ve [kodu](code/lambda_function.py) aşağıdakiyle değiştirin

```
import os
import io
import boto3
import json
import csv

#grab environment variables
ENDPOINT_NAME = os.environ['ENDPOINT_NAME']
runtime= boto3.client('runtime.sagemaker')

def lambda_handler(event, context):
    print("Received event: " + json.dumps(event, indent=2))
    
    data = json.loads(json.dumps(event))
    payload = data['data']
    print(payload)
    
    response = runtime.invoke_endpoint(EndpointName=ENDPOINT_NAME,
                                       ContentType='text/csv',
                                       Body=payload)
    print(response)
    result = json.loads(response['Body'].read().decode())
    print(result)
    pred = float(result['predictions'][0]['score'])
    print("pred: " + repr(pred))
    return pred
```

+ Biraz daha aşağıdaki Environment Variables alanına gelin. Key alanına ENDPOINT_NAME yazın. Value alanına Notebook’unuzun çalışırken çıktı olarak ürettiği “DEMO-linear-endpoint-XXX” ile başlayan enpoint adını kopyalayın. Endpoint adını öğrenmek için tarayıcı ekranında açılan Notebook’unuza geri dönün. DEMO-linear-endpoint- metnini aratın. Bu metni bulduğunuz ilk kod kutucuğunun altında gördüğünüz üretilmiş endpoint’in adını kopyalayın (DEMO-linear-endpoint-201810060646 gibi bir metin olması gerekiyor). Kod kutucuğu hala işletilmemişse işletilmesini bekledikten sonra bu adımı gerçekleştirin
+ Save butonuna tıklayın




+ Eğer bu atölye çalışmasını kendi AWS hesabınız üzerinde yapıyorsanız açtığınız kanakları kapatmayı unutmayın
+ Jupyter Lab arayüzündeki sol tarafta en altta bulunan "Amazon Sagemaker sample notebooks" butonuna tıklayarak daha fazla notebook örneğine erişip inceleyebilirsiniz.