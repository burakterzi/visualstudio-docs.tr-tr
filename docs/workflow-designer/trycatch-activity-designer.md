---
title: İş Akışı Tasarımcısı-TryCatch etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76a7600cdab94499e13592924efabba2fb4c2faf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649803"
---
# <a name="trycatch-activity-designer"></a>TryCatch Etkinlik Tasarımcısı

**TryCatch** etkinlik Tasarımcısı <xref:System.Activities.Statements.TryCatch> etkinlik oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-trycatch-activity"></a>TryCatch etkinliği
 @No__t_0 etkinliği <xref:System.Activities.Statements.TryCatch.Try%2A> etkinlik, bir **Catch \<TException >** ve <xref:System.Activities.Statements.TryCatch.Finally%2A> etkinliği içerir. **TException** türünde bir <xref:System.Activities.Statements.Catch%601>, bir <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> ve <xref:System.Activities.Statements.Catch%601.Action%2A> içerir. Bunlar birlikte, tipik bir özel durum tabanlı hata işleme mekanizması uygulamak için kullanılır. Bir <xref:System.Activities.Statements.TryCatch> etkinlik <xref:System.Activities.Statements.TryCatch.Try%2A> etkinliğini yürütmeye çalışır. @No__t_0 etkinliği herhangi bir özel durum oluşturursa, <xref:System.Activities.Statements.TryCatch> etkinliği özel durumu eşleştirmek için **Catch < TException \>** koleksiyonunu kullanır. Bir eşleşme varsa, karşılık gelen **Catch \<TException >** <xref:System.Activities.Statements.Catch%601.Action%2A> yürütülür ve özel durum için hata işleme mantığı görevi görür. @No__t_0 bölümündeki etkinlikler başarıyla tamamlanmalı veya <xref:System.Activities.Statements.TryCatch.Catches%2A> etkinlikler başarıyla tamamlandıysanız <xref:System.Activities.Statements.TryCatch> etkinliği <xref:System.Activities.Statements.TryCatch.Finally%2A> etkinliğini yürütür. Daha fazla bilgi için bkz. [Windows iş akışı özel durumları](/dotnet/framework/windows-workflow-foundation/exceptions).

### <a name="using-the-trycatch-activity-designer"></a>TryCatch etkinlik tasarımcısını kullanma

**Araç kutusunun** **hata işleme** kategorisindeki **TryCatch** etkinlik tasarımcısına erişin.

**TryCatch** etkinlik Tasarımcısı **araç kutusundan** sürüklenip İş Akışı Tasarımcısı yüzeyine, örneğin <xref:System.Activities.Statements.Sequence> içinde olduğu gibi, her yerde bırakılmış olarak bırakılabilir. Bu, TryCatch 'in varsayılan <xref:System.Activities.Activity.DisplayName%2A> bir <xref:System.Activities.Statements.TryCatch> etkinlik oluşturur. @No__t_0 değeri, **TryCatch** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir. Diğer özellikler, **TryCatch** etkinlik tasarımcısının yüzeyinde düzenlenmelidir.

Genişletilmiş görünümdeki **TRY**, **catch**ve **finally** kutularını görmek için, **TryCatch** Tasarımcısı ' nın sağ üst köşesindeki Genişlet düğmesine tıklayın. Bir catch eklemek için, **TryCatch** tasarımcısında **Yeni catch Ekle** düğmesine tıklayın. Düğme, bir tür açılan kutusu olarak değişir. Catch eklemek için bir özel durum türü seçin ve ENTER tuşuna basın. **Catch eklendikten sonra, catch**alanı genişler ve bir etkinlik, catch için yürütme mantığını tanımlamak üzere catch 'e bırakılabilir. Genişletilmiş catch alanının sağ tarafında bir metin kutusu olduğunu unutmayın. Bu metin kutusunu kullanarak özel durum değişkenine ad verebilirsiniz. Özel durum değişkeni yalnızca aynı **catch**içindeki etkinlikler için kullanılabilir.

**TryCatch** Tasarımcısı, **catch**düzenlemesini desteklemiyor. Özel durum türünü değiştirmek isterseniz, **catch** 'i silip yeni bir tane eklemeniz gerekir. Bir **catch** , seçilip silinerek veya sağ tıklanarak erişilen bağlam menüsünde **Sil** ' i seçerek silinebilir.

### <a name="the-trycatch-properties"></a>TryCatch özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.TryCatch>properties gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin isteğe bağlı kolay adını belirtir. Varsayılan değer TryCatch ' dir.|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|Etkinlik <xref:System.Activities.Statements.TryCatch> yürütüldüğünde ilk yürütülür.|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|@No__t_1 etkinliği bir özel durum oluşturduğunda denetlenecek **catch** öğelerinin koleksiyonu.<br /><br /> @No__t_0 veya <xref:System.Activities.Statements.TryCatch.Finally%2A> bloğunda bir etkinlikte en az bir etkinlik eklemeniz gerekiyor.|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|@No__t_0 ve <xref:System.Activities.Statements.TryCatch.Catches%2A> koleksiyonundaki gerekli etkinliklerin yürütülmesi tamamlandığında yürütülecek etkinlik.<br /><br /> @No__t_0 veya <xref:System.Activities.Statements.TryCatch.Finally%2A> bloğunda bir etkinlikte en az bir etkinlik eklemeniz gerekiyor.|

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyon](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Throw](../workflow-designer/throw-activity-designer.md)