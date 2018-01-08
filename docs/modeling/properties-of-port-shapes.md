---
title: "Bağlantı noktası şekiller özelliklerini | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.dsldesigner.port
helpviewer_keywords: Domain-Specific Language, port shape
ms.assetid: 9d69c4c1-4f72-4876-96b6-9b846e0495a4
caps.latest.revision: "21"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 3cc8f57b0615be6255425e396f0fc4ea3e763810
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="properties-of-port-shapes"></a>Bağlantı Noktası Şekillerinin Özellikleri
Etki alanı sınıflarını oluşturulan Tasarımcısı'nda göstermek için bağlantı noktası şekiller kullanabilirsiniz.  
  
 Daha fazla bilgi için bkz: [bir etki alanına özgü dil tanımlamak nasıl](../modeling/how-to-define-a-domain-specific-language.md). Bu özellikleri kullanma hakkında daha fazla bilgi için bkz: [özelleştirme ve bir etki alanına özgü dil genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Bağlantı noktası şekilleri aşağıdaki tabloda listelenen özellikleri bulunur.  
  
|Özellik|Açıklama|Varsayılan|  
|--------------|-----------------|-------------|  
|Dolgu rengi|Bu şeklin dolgu rengi.|Beyaz|  
|Gradyan modu doldurun|Bu şeklin dolgu gradyanı modu.|Yatay|  
|Geometri|Bu şekil (dikdörtgen, yuvarlak dikdörtgen, elips veya daire) geometri.|Dikdörtgen|  
|Varsayılan bağlantı noktası içermiyor.|Varsa `True`şekli üst, alt, sol kullanacak ve doğru bağlantı noktalarını oluşturulan Tasarımcısı'nda.|False|  
|Anahat rengi|Bu şeklin kenarlık rengi.|Siyah|  
|Kenarlık Çizgi stili|Bu şekil (düz, çizgi, nokta, çizgi nokta, çizgi nokta nokta veya özel) anahat çizgi stili.|Düz|  
|Anahat kalınlığı|Bu şeklin Anahat kalınlığı.|0.03125|  
|Metin rengi|Bu şeklin ile ilişkili metin dekoratörler için kullanılan rengi.|Siyah|  
|Erişim değiştiricisi|Sınıfının erişim düzeyini (`public` veya `internal`).|Ortak|  
|Özel Öznitelikler|Bu şekle oluşturulan kaynak kodu sınıfı öznitelikler eklemek için kullanılır.|\<yok >|  
|Çift oluşturur türetilmiş|Varsa `True`, bir taban sınıf ve bir parçalı sınıf (geçersiz kılmaları özelleştirmeyi desteklemek için) oluşturulur. Daha fazla bilgi için bkz: [geçersiz kılma ve oluşturulan sınıflar genişletme](../modeling/overriding-and-extending-the-generated-classes.md)|False|  
|Özel bir oluşturucuya sahip|Varsa `True`, özel bir oluşturucu kaynak kodunda sağlanacaktır. Daha fazla bilgi için bkz: [geçersiz kılma ve oluşturulan sınıflar genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Devralma değiştiricisi|Tür bir bağlantı noktasından oluşturulan kaynak kodu sınıf devralma açıklar (`none`, `abstract` veya `sealed`).|yok|  
|Temel bağlantı noktası|Bu şeklin temel sınıf.|(hiçbiri)|  
|Ad|Bu şeklin adı.|Geçerli adı|  
|Ad Alanı|Bu şeklin ile bağlantılı olan ad alanı.|Geçerli ad alanı|  
|Araç İpucu türü|Nasıl araç ipucu (sabit, değişken veya hiçbiri) tanımlanır. Sabit, ardından değeri `Fixed Tooltip Text` özelliği araç ipucu olarak kullanılır; ardından değişken durumunda, araç ipucu özel kod içinde tanımlanır.|yok|  
|Notlar|Bu şeklin ile ilişkili resmi olmayan notları.|\<yok >|  
|İlk yükseklik|Bu şeklin inç ilk yüksekliği.|1.|  
|İlk genişliği|Bu şeklin inç başlangıç genişliği.|1,5|  
|Özellik olarak sunulan dolgu rengi<br /><br /> Sunulan dolgu gradyanı modu<br /><br /> Anahat rengini özelliği olarak kullanıma sunulan<br /><br /> Kenarlık Çizgi stili özelliği olarak kullanıma sunulan<br /><br /> Anahat kalınlığı özelliği olarak sunulan<br /><br /> Metin rengi gösterir|Varsa `True`, kullanıcı bir şekli belirtilen özelliğini ayarlayabilirsiniz. Bunu ayarlamak için Şekil tanımı sağ tıklatıp **eklemek açığa**.|False|  
|Açıklama|Oluşturulan Tasarımcısı belgelemek için kullanılır.|\<yok >|  
|Görünen ad|Bu şekil için oluşturulan Tasarımcısı'nda görüntülenen ad.|\<yok >|  
|Sabit araç ipucu metni|Sabit bir araç ipucu için kullanılan metin.|\<yok >|  
|Yardım anahtar sözcüğü|Bu şeklin için F1 Yardımı dizin oluşturmak için kullanılan anahtar sözcük.|\<yok >|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etki alanına özgü dil araçları sözlüğü](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)