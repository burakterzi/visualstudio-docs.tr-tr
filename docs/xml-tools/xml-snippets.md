---
title: XML kod parçacıkları
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c261893b50a217d888300ca01f3bc190bc065c94
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658767"
---
# <a name="xml-snippets"></a>XML kod parçacıkları

XML Düzenleyicisi, XML dosyalarını daha hızlı bir şekilde oluşturmanıza olanak sağlayan *XML parçacıkları*adlı bir özellik sunar. XML parçacıklarını dosyalarınıza ekleyerek yeniden kullanabilirsiniz. XML şeması tanım dili (XSD) şemasına göre XML verileri de oluşturabilirsiniz.

## <a name="reusable-xml-snippets"></a>Yeniden kullanılabilir XML parçacıkları

XML Düzenleyicisi, bazı ortak görevleri kapsayan çok sayıda kod parçacığı içerir. Bu sayede XML dosyalarını daha kolay bir şekilde oluşturabilirsiniz. Örneğin, bir XML şeması yazıyorsanız, "karmaşık tür dizisi öğesi" ve "basit tür öğesi" parçacıkları kullanılarak dosyanıza aşağıdaki XML metni eklenir. Daha sonra `name` değerini gereksinimlerinize uyacak şekilde değiştirirsiniz.

```xml
<xs:element name="name">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="name">
        <xs:simpleType>
          <xs:restriction base="xs:string"></xs:restriction>
        </xs:simpleType>
      </xs:element>
    </xs:sequence>
  </xs:complexType>
</xs:element>
```

Kod parçacıklarını iki şekilde ekleyebilirsiniz. **Kod parçacığı Ekle** komutu, Imleç konumuna XML kod parçacığını ekler. Komutuyla **çevreleme** , XML kod parçacığını seçili metnin çevresinde sarmalanmış. Her iki komut de **düzenleme** menüsünün altındaki **IntelliSense** alt menüsünde veya düzenleyici içindeki sağ tıklama menüsünden kullanılabilir.

Daha fazla bilgi için bkz. [nasıl yapılır: XML kod parçacıkları kullanma](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>Şema tarafından oluşturulan XML parçacıkları

XML Düzenleyicisi, xml şemasından bir XML parçacığı oluşturma özelliğine de sahiptir. Bu özellik, bir öğeyi bu öğe için şema bilgilerden oluşturulan XML öğeleriyle doldurmanıza olanak sağlar. Daha fazla bilgi için bkz. [nasıl yapılır: XML ŞEMASıNDAN XML parçacığı oluşturma](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).

## <a name="create-new-xml-snippets"></a>Yeni XML parçacıkları oluşturma

Visual Studio 'da varsayılan olarak bulunan kod parçacıklarının yanı sıra, kendi XML kod parçacıklarınızı da oluşturabilir ve kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: XML parçacıkları oluşturma](../xml-tools/how-to-create-xml-snippets.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da kod parçacıkları](../ide/code-snippets.md)
- [XML Düzenleyicisi](../xml-tools/xml-editor.md)