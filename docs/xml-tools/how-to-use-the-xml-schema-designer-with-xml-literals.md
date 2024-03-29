---
title: 'Nasıl yapılır: XML şema tasarımcısını XML değişmez değerleri ile kullanma'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: ed987a54004004fe8c4fbfba686ae1a35d12bb06
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601845"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Nasıl yapılır: XML şema tasarımcısını XML değişmez değerleri ile kullanma

Bu konu, bir Visual Basic projesindeki bir XML sabit değeri ile ilişkili bir şemanın nasıl görüntüleneceğini açıklamaktadır.

## <a name="create-a-new-visual-basic-project"></a>Yeni bir Visual Basic projesi oluştur

1. Visual Studio'yu açın.

2. **Xmldeğişmezleri**adlı yeni bir Visual Basic **konsol uygulaması** projesi oluşturun.

     Yeni proje bir Visual Basic kaynak dosyası ( *Module1. vb*) içerir.

## <a name="add-an-existing-xsd-file"></a>Mevcut bir XSD dosyası Ekle

1. Not defteri 'nde yeni bir metin dosyası açın. XML şeması örnek kodunu, [satın alma siparişi şemasından](../xml-tools/sample-xsd-file-simple-schema.md) kopyalayın ve dosyasına yapıştırın.

2. Dosyayı *PurchaseOrderSchema. xsd*adlı bir konuma kaydedin.

3. **Çözüm Gezgini**, projenin adına sağ tıklayın, **Ekle**' yi seçin ve ardından **Varolan öğe**' yi seçin. **Addexıting öğesi** iletişim kutusu görüntülenir. *PurchaseOrderSchema. xsd* dosyasına gidin, seçin ve ardından **Ekle**' ye tıklayın.

     Xmlharfler projesi artık iki dosya içerir: *Module1. vb* ve *PurchaseOrderSchema. xsd*.

## <a name="add-code"></a>Kod Ekle

Projeye dahil olan XSD dosyasını temel alan bir XML sabit değeri ile Visual Basic kodu eklemek için:

1. *Module1. vb* dosyasındaki kodu aşağıdaki kodla değiştirin:

   ```vb
   Imports <xmlns:ns="http://tempuri.org/PurchaseOrderSchema.xsd">

   Module Module1
      Sub Main()

          Dim XMLLiteral = <ns:PurchaseOrder OrderDate="1900-01-01">
                               <ns:ShipTo country="US">
                                   <ns:name>name1</ns:name>
                                   <ns:street>street1</ns:street>
                                   <ns:city>city1</ns:city>
                                   <ns:state>state1</ns:state>
                                   <ns:zip>1</ns:zip>
                               </ns:ShipTo>
                               <ns:BillTo country="US">
                                   <ns:name>name1</ns:name>
                                   <ns:street>street1</ns:street>
                                   <ns:city>city1</ns:city>
                                   <ns:state>state1</ns:state>
                                   <ns:zip>1</ns:zip>
                               </ns:BillTo>
                           </ns:PurchaseOrder>

      End Sub
   End Module
   ```

2. XML sabit değerinde bir xml düğümüne veya XML ad alanı içeri aktarma öğesine sağ tıklayın ve **şema Gezgininde göster**' i seçin.

   XML **şema Gezgini** , XML şema KÜMESIYLE ilişkili XML sabit değeri olan bir Visual Basic dosyası ile yan yana görüntülenir.