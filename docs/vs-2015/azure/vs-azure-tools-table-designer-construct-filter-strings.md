---
title: Tablo Tasarımcısı için filtre dizeleri oluşturma | Microsoft Docs
description: Tablo Tasarımcısı için filtre dizeleri oluşturma
author: ghogen
manager: jillfra
assetId: a1a10ea1-687a-4ee1-a952-6b24c2fe1a22
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: f1cf5634985683fc86a738d93a6cfa352b52bd24
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74290988"
---
# <a name="constructing-filter-strings-for-the-table-designer"></a>Tablo Tasarımcısı için Filtre Dizelerini Oluşturma
## <a name="overview"></a>Genel Bakış
Visual Studio **Tablo Tasarımcısı**görüntülenen bir Azure tablosundaki verileri filtrelemek için bir filtre dizesi oluşturur ve bunu filtre alanına girersiniz. Filtre dizesi sözdizimi WCF Veri Hizmetleri tarafından tanımlanır ve bir SQL WHERE yan tümcesine benzerdir, ancak bir HTTP isteği aracılığıyla tablo hizmetine gönderilir. **Tablo Tasarımcısı** , sizin için uygun kodlamayı işler, böylece istenen özellik değerini filtrelemek için filtre alanına yalnızca özellik adı, karşılaştırma işleci, ölçüt değeri ve isteğe bağlı olarak Boolean işlecini girmeniz gerekir. [Depolama hizmetleri REST API başvurusu](https://go.microsoft.com/fwlink/p/?LinkId=400447)aracılığıyla tabloyu sorgulamak IÇIN bir URL oluştururken yaptığınız gibi $Filter sorgu seçeneğini de eklemeniz gerekmez.

WCF Veri Hizmetleri, [Açık Veri Protokolü 'nü](https://go.microsoft.com/fwlink/p/?LinkId=214805) (OData) temel alır. Filtre sistemi sorgu seçeneği ( **$Filter**) hakkında daha fazla bilgi için bkz. [OData URI kuralları belirtimi](https://go.microsoft.com/fwlink/p/?LinkId=214806).

## <a name="comparison-operators"></a>Karşılaştırma İşleçleri
Aşağıdaki mantıksal işleçler tüm özellik türleri için desteklenir:

| Mantıksal işleç | Açıklama | Örnek filtre dizesi |
| --- | --- | --- |
| EQ |Eşittir |Şehir EQ ' Redmond ' |
| gt |Büyüktür |Fiyat gt 20 |
| Birleştir |Büyüktür veya eşittir |Fiyat GE 10 |
| lt |Küçüktür |Fiyat lt 20 |
| Le |Küçük veya eşittir |Fiyat Le 100 |
| Savaşı |Eşit değildir |Şehir ne ' Londra ' |
| ve |Ve |Fiyat Le 200 ve fiyat gt 3,5 |
| veya |Veya |Fiyat Le 3,5 veya fiyat gt 200 |
| not |değil |ıısavailable yok |

Bir filtre dizesi oluştururken aşağıdaki kurallar önemlidir:

* Bir özelliği bir değerle karşılaştırmak için mantıksal işleçleri kullanın. Bir özelliği dinamik bir değerle karşılaştırmak mümkün değildir; ifadenin bir tarafı bir sabit olmalıdır.
* Filtre dizesinin tüm bölümleri büyük/küçük harfe duyarlıdır.
* Filtrenin geçerli sonuçları döndürmesi için sabit değerin özelliği ile aynı veri türünde olması gerekir. Desteklenen özellik türleri hakkında daha fazla bilgi için bkz. [Tablo hizmeti veri modelini anlama](https://go.microsoft.com/fwlink/p/?LinkId=400448).

## <a name="filtering-on-string-properties"></a>Dize özelliklerinde filtreleme
Dize özelliklerine filtre uyguladığınızda, dize sabitini tek tırnak işaretleri içine alın.

Aşağıdaki örnek, **partitionkey** ve **rowkey** özellikleri üzerinde filtreliyor; Filtre dizesine ek anahtar olmayan özellikler de eklenebilir:

```
PartitionKey eq 'Partition1' and RowKey eq '00001'
```

Gerekli olmamasına rağmen, her filtre ifadesini parantez içine alabilirsiniz:

```
(PartitionKey eq 'Partition1') and (RowKey eq '00001')
```

Tablo hizmetinin joker sorguları desteklemediğini ve Tablo Tasarımcısı üzerinde desteklenmediğini unutmayın. Ancak, istenen ön ek üzerinde karşılaştırma işleçleri kullanarak önek eşleştirmeyi gerçekleştirebilirsiniz. Aşağıdaki örnek, ' A ' harfiyle başlayan bir LastName özelliği olan varlıkları döndürür:

```
LastName ge 'A' and LastName lt 'B'
```

## <a name="filtering-on-numeric-properties"></a>Sayısal özelliklerde filtreleme
Bir tamsayı veya kayan noktalı sayı üzerinde filtrelemek için, numarayı tırnak işareti olmadan belirtin.

Bu örnek, değeri 30 ' dan büyük olan bir Age özelliği olan tüm varlıkları döndürür:

```
Age gt 30
```

Bu örnek, değeri 100,25 ' den küçük veya buna eşit olan bir AmountDue özelliği olan tüm varlıkları döndürür:

```
AmountDue le 100.25
```

## <a name="filtering-on-boolean-properties"></a>Boole özelliklerine filtre uygulama
Boole değeri filtrelemek için, tırnak işaretleri olmadan **true** veya **false** değerini belirtin.

Aşağıdaki örnek, IsActive özelliğinin **true**olarak ayarlandığı tüm varlıkları döndürür:

```
IsActive eq true
```

Ayrıca, mantıksal işleç olmadan bu filtre ifadesini de yazabilirsiniz. Aşağıdaki örnekte, tablo hizmeti, IsActive 'ın **doğru**olduğu tüm varlıkları da döndürür:

```
IsActive
```

Iactıve 'in false olduğu tüm varlıkları döndürmek için Not işlecini kullanabilirsiniz:

```
not IsActive
```

## <a name="filtering-on-datetime-properties"></a>Tarih saat özelliklerine filtre uygulama
Bir tarih saat değerini filtrelemek için, **DateTime** anahtar sözcüğünü ve ardından tek tırnak işaretleri içinde tarih/saat sabiti ' ni belirtin. Tarih/saat sabiti, [DateTime özellik değerlerini biçimlendirme](https://go.microsoft.com/fwlink/p/?LinkId=400449)bölümünde açıklandığı gıbı Birleşik UTC biçiminde olmalıdır.

Aşağıdaki örnek, CustomerSince özelliğinin 10 Temmuz 2008 ' ye eşit olduğu varlıkları döndürür:

```
CustomerSince eq datetime'2008-07-10T00:00:00Z'
```
