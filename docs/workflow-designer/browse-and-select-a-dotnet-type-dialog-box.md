---
title: İş Akışı Tasarımcısı-.NET türüne gözatıp seçin Iletişim kutusu
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5eac3c2a45f1e220415f7512e601f4bf034c4dd7
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189805"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>.NET Türüne Gözat ve Seç İletişim Kutusu

**Özellikler** penceresi, iletişim kutuları veya değişken Tasarımcısı gibi tasarımcılarda, bir veri türleri listesinden **türler için araştır** ' ı seçtiğinizde, **bir .NET türü görüntüle ve Seç** iletişim kutusu (kısaltılmış bir biçimde "tür olarak adlandırılır tarayıcı "). Bu iletişim kutusunda, derlemelerin ve projelerin ağaç görünümünden bir tür seçebilirsiniz.

Bu iletişim kutusu, aşağıdakiler de dahil olmak üzere çeşitli Kullanıcı senaryolarında işe alındı:

- Bir değişkenin veya bağımsız değişkenin türü ayarlanırken.

- Genel etkinlik için bir tür seçerken.

- <xref:System.Activities.Statements.TryCatch> etkinliğine bir catch eklenirken.

> [!NOTE]
> Tür tarayıcısı Visual Basic basit dizi türleri görüntüleyebilir, ancak çok boyutlu dizi türleri gösterebilir. Ayrıntılar için bkz. [pürüzlü Diziler](/previous-versions/visualstudio/visual-studio-2008/hkhhsz9t(v=vs.90)) ve [çok boyutlu diziler](/previous-versions/visualstudio/visual-studio-2008/d2de1t93(v=vs.90)) .

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>Tür tarayıcısından bir değer veya başvuru türü seçme

### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>Tür tarayıcısından bir değer veya başvuru türü seçmek için

1. **Tür adı** kutusuna, kullanmak istediğiniz türün adını girin.

2. Aşağıdakilerden birini yapın:

    - Kullanmak istediğiniz türün adı, **tür adı** kutusundaki ağaçta göründüğünde, seçmek için türe çift tıklayın.

    - Kullanmak istediğiniz türü benzersiz bir şekilde tanımlamak için **tür adı** kutusuna yeterli sayıda karakter yazın ve ardından türü seçmek için ENTER tuşuna basın

### <a name="to-select-a-generic-type-from-the-type-browser"></a>Tür tarayıcısından genel bir tür seçmek için

1. **Tür adı** kutusuna, kullanmak istediğiniz türün adını yazın.

2. Kullanmak istediğiniz türün adı **tür adı** kutusundaki ağaçta göründüğünde, açılan kutuların görünmesine neden olacak şekilde seçmek için türe tıklayın.

     Açılan kutulardan genel ' i kapatmak için kullanmak istediğiniz türü seçin ve ardından **Tamam**' a tıklayın.

## <a name="types-displayed-in-the-type-browser"></a>Tür tarayıcısında görünen türler

Tür tarayıcısında görünen türler, tür tarayıcısının nasıl başlatıldığına bağlı olarak farklılık gösterebilir. Tür tarayıcısı **VS2010**içindeki bir iş akışı projesinden başlatılmışsa, varsayılan olarak başvurulan derlemelerdeki tüm türler ve başvurulan projeler gösterilir. Tür tarayıcısı bir **VS2010** projesi sisteminin dışından (örneğin, yeniden barındırılan bir iş akışı uygulamasında veya tek başına bir iş akışı dosyasında) başlatılmışsa, varsayılan olarak, uygulama etki alanında yüklü derlemelerin tümünün türleri gösterilir.

Tür tarayıcısındaki türler, etkinlik Tasarımcısı geliştiricilerine göre filtrelenebilir. Belirli bir etkinlik için yalnızca türlerin bir alt kümesini görebilirsiniz. Örneğin, <xref:System.Activities.Statements.TryCatch> etkinliğinde, tür tarayıcısında yalnızca <xref:System.Exception> türetilen türler gösterilir.

## <a name="filtering-search-results-in-the-type-browser"></a>Arama sonuçlarını tür tarayıcısında filtreleme

**Tür adı** kutusundaki türlerin listesi, bir eşleşme bulmak için daha fazla karakter yazdığınızda daha kısa olur. Yalnızca FullyQualified adı yazdığınız dize ile başlayan türler veya kısa adı yazdığınız dize ile başlayan ve filtrelenmiş listede görünen türler.

Örneğin:

1. Yazma **işlemi** <xref:System.OperationCanceledException> eşleşir, ancak <xref:System.InvalidOperationException> eşleşmez. <xref:System.InvalidOperationException>eşleştirmek için, System. ı veya geçersiz yazmaya başlayın.

2. **Genel** eşleşmeler yazmak <xref:System.GenericUriParser>, <xref:System.Collections.Generic> ad alanındaki türleri değil. <xref:System.Collections.Generic> ad alanındaki türleri aramak için ad alanının tam adını yazın.

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>Tarayıcı türü iletişim kutusunu kullanarak bir hizmet sözleşmesi seçme

Bir hizmet sözleşmesi türü seçerken tür tarayıcısı yalnızca <xref:System.ServiceModel.ServiceContractAttribute> özniteliğine sahip türleri gösterir.

## <a name="see-also"></a>Ayrıca bkz.

- [Etkinlik Tasarımcılarını kullanma](control-flow-activity-designers.md)