---
title: İş Akışı Tasarımcısı-etkinlik Tasarımcısı atama
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44d4136aabd5bd383cc3718dc5c6c1676f94e45d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650726"
---
# <a name="assign-activity-designer"></a>Assign Etkinlik Tasarımcısı

Bir <xref:System.Activities.Statements.Assign> etkinliği oluşturmak ve yapılandırmak için **atama** etkinliği Tasarımcısı kullanılır.

## <a name="the-assign-activity"></a>Atama etkinliği

@No__t_0 etkinliği bir değişkene veya bağımsız değişkene bir değer atar.

### <a name="using-the-assign-activity-designer"></a>Atama etkinliği tasarımcısını kullanma

**Ata** etkinlik Tasarımcısı **, araç kutusu sekmesine** tıklanarak **erişilen araç kutusu**' nda (alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu veya Ctrl + Alt + X ' i seçerek) bulunan **temel öğeler** kategorisinde bulunabilir.

**Atama** etkinliği Tasarımcısı **araç kutusundan** sürüklenip, <xref:System.Activities.Statements.Sequence> içinde olduğu gibi, her zaman etkinliklerin yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir. **Atama** etkinliği Tasarımcısı ' nın atılması, varsayılan ata **DisplayName** ile bir <xref:System.Activities.Statements.Assign> etkinliği oluşturur. @No__t_0, **atama** Tasarımcısı ' nın üstbilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-assign-properties"></a>Atama özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.Assign> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler özellik kılavuzunda düzenlenebilir ve bazıları İş Akışı Tasarımcısı yüzeyinde düzenlenebilirler.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin kolay adı. Varsayılan değer atama ' dır. @No__t_0 değeri kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.Assign.To%2A>|Doğru|@No__t_0 atandığı değişken veya bağımsız değişken. Değer geçerli bir Visual Basic tanımlayıcısı olmalıdır. Özelliği ayarlamak için, **assign** Activity Designer 'daki **to** kutusuna veya özellik kılavuzunda bir Visual Basic ifadesi yazın.|
|<xref:System.Activities.Statements.Assign.Value%2A>|Doğru|Değişkene atanan değer. @No__t_0 ayarlamak için, eylem **atama** Tasarımcısı ' nın **değer** kutusuna veya özellik kılavuzunda bir Visual Basic ifadesi yazın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Temel Türler](../workflow-designer/primitives-activity-designers.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)