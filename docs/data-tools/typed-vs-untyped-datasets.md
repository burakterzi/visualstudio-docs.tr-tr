---
title: Yazılan ve yazılmayan veri kümelerinin karşılaştırması
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: eff5e0d2f13bfe462ff19d6cfb4e8a32a15a6064
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72639633"
---
# <a name="typed-vs-untyped-datasets"></a>Yazılan ve yazılmayan veri kümelerinin karşılaştırması
Türü belirtilmiş veri kümesi, ilk olarak temel <xref:System.Data.DataSet> sınıfından türetilmiş bir veri kümesidir ve sonra yeni ve türü kesin belirlenmiş bir veri kümesi sınıfı oluşturmak için bir. xsd dosyasında depolanan **veri kümesi Tasarımcısı**bilgileri kullanır. Şemadan alınan bilgiler (tablolar, sütunlar, vb.) oluşturulup ilk sınıf nesne ve özellik kümesi olarak bu yeni veri kümesi sınıfına derlenir. Türü belirtilmiş bir veri kümesi taban <xref:System.Data.DataSet> sınıfından devraldığından, türü belirtilmiş sınıf <xref:System.Data.DataSet> sınıfının tüm işlevlerini varsayar ve bir <xref:System.Data.DataSet> sınıfının örneğini parametre olarak alan yöntemlerle birlikte kullanılabilir.

Bunun aksine, türsüz bir veri kümesinin karşılık gelen yerleşik bir şeması yoktur. Türü belirtilmiş bir veri kümesinde olduğu gibi, türsüz bir veri kümesi tablo, sütun vb. içerir, ancak bunlar yalnızca koleksiyonlar olarak sunulur. (Ancak, tablo ve diğer veri öğelerini türsüz bir veri kümesinde el ile oluşturduktan sonra, veri kümesinin <xref:System.Data.DataSet.WriteXmlSchema%2A> yöntemini kullanarak veri kümesinin yapısını şema olarak dışarı aktarabilirsiniz.)

## <a name="contrast-data-access-in-typed-and-untyped-datasets"></a>Türü belirtilmiş ve türsüz veri kümelerinde kontrast verileri erişimi
Türü belirtilmiş bir veri kümesinin sınıfının, özelliklerinin tablo ve sütunların gerçek adlarını aldığı bir nesne modeli vardır. Örneğin, türü belirtilmiş bir veri kümesiyle çalışıyorsanız, aşağıdaki gibi bir kod kullanarak bir sütuna başvurabilirsiniz:

[!code-csharp[VbRaddataDatasets#4](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_1.cs)]
[!code-vb[VbRaddataDatasets#4](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_1.vb)]

Buna karşılık, türsüz bir veri kümesiyle çalışıyorsanız, eşdeğer kod şu şekilde olur:

[!code-csharp[VbRaddataDatasets#5](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_2.cs)]
[!code-vb[VbRaddataDatasets#5](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_2.vb)]

Yazılan erişim yalnızca Visual Studio **Kod Düzenleyicisi**'nde IntelliSense tarafından tam olarak desteklenmekte, ancak aynı zamanda daha kolay okunabilir. İle çalışmanın yanı sıra, yazılan veri kümesinin sözdizimi, derleme zamanında tür denetlemesi sağlar ve veri kümesi üyelerine değer atarken hata olasılığını büyük ölçüde azaltır. @No__t_0 sınıfınıza bir sütunun adını değiştirip uygulamanızı derlerseniz, derleme hatası alırsınız. **Görev listesi**yapı hatasına çift tıklayarak, eski sütun adına başvuruda bulunan satır veya kod satırlarına doğrudan gidebilirsiniz. Belirlenmiş bir veri kümesindeki tablo ve sütunlara erişim, çalışma zamanında, çalışma zamanında koleksiyonlar aracılığıyla değil, derleme zamanında belirlendiği için, çalışma zamanında biraz daha hızlıdır.

Yazılan veri kümelerinde birçok avantaj olsa da, türsüz bir veri kümesi çeşitli koşullarda yararlı olur. En belirgin senaryo, veri kümesi için kullanılabilir şema olmadığında olur. Bu durum, örneğin, uygulamanız veri kümesi döndüren bir bileşenle etkileşiyorsa, ancak yapısının ne olduğu konusunda bilgi sahibi değilseniz bu durum oluşabilir. Benzer şekilde, statik, öngörülebilir bir yapıya sahip olmayan verilerle çalışırken zamanlar da vardır. Bu durumda, yazılan veri kümesi sınıfını veri yapısındaki her değişiklik ile yeniden oluşturmanız gerektiğinden, türü belirtilmiş bir veri kümesi kullanılması pratik değildir.

Daha genel olarak, bir şemayı kullanılabilir olmadan dinamik olarak veri kümesi oluşturabileceğiniz Birçok zaman vardır. Bu durumda, veri kümesi, verilerin ilişkisel bir şekilde gösterilebileceği sürece, bilgileri saklayabilmeniz için yalnızca uygun bir yapıdır. Aynı zamanda, diğer bir işleme geçirilecek veya bir XML dosyası yazmak gibi bilgileri seri hale getirme yeteneği gibi veri kümesinin özelliğinden yararlanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)