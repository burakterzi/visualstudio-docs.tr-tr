---
title: İşlevler görünümü-Izleme verileri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Function view
ms.assetid: 595d91c8-a42b-4644-85b8-39e8140a5dfe
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 423b6d61af93c37e6fa83549ed3fa5d422128165
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779226"
---
# <a name="functions-view---instrumentation-data"></a>İşlevler görünümü-izleme verileri
Işlevler rapor görünümü profil oluşturma verilerini işlev adına göre listeler.

## <a name="general"></a>Genel
 Genel sütunlar, bir görünüm satırındaki işlevi belirler.

|Sütun|Açıklama|
|------------|-----------------|
|**İşlev adı**|İşlevin adı.|
|**İşlev adresi**|İşlevin adresi.|
|**İşlev satır numarası**|Kaynak dosyada bu işlevin başlangıcına ait satır numarası.|
|**Çağrı sayısı**|Bu işleve yapılan çağrıların toplam sayısı.|
|**Kaynak dosya**|Bu işlevin tanımını içeren kaynak dosya.|
|**Modül adı**|İşlevi içeren modülün adı.|
|**Modül yolu**|İşlevi içeren modülün yolu.|
|**İşlem KIMLIĞI**|Profil oluşturma çalıştırmasının işlem KIMLIĞI (PID).|
|**İşlem adı**|İşlemin adı.|
|**Zaman Dışlamalı Araştırma ek yükü**|Bu işlev için, izleme nedeniyle oluşan zaman ek yükü. İşlev tarafından çağrılan işlevlerde ek yükü içermez. Araştırma ek yükü tüm özel zamanlarda çıkarıldı.|
|**Zaman kapsamlı araştırma ek yükü**|Bu işlev için zaman yükü ve alt işlevleri, izleme nedeniyle oluşur. İşlev tarafından çağrılan işlevlerde ek yükü içerir. Araştırma ek yükü tüm kapsamlı bir şekilde çıkarıldı.|

## <a name="elapsed-inclusive-values"></a>Geçen kapsamlı değerler
 Geçen kapsamlı değerler, bir işlevin çağrı yığınında olduğu süreyi belirtir. Bu süre, işlev ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zaman tarafından çağrılan işlevlerde harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen kapsamlı süre**|Bu işleve yapılan çağrıların toplam geçen kapsamlı süresi.|
|**Geçen kapsamlı süre yüzdesi**|Bu işlevin geçen kapsamlı sürede harcanan, profil oluşturma çalıştırmasının toplam geçen iç süresinin yüzdesi.|
|**Ortalama geçen kapsamlı süre**|Bu işleve yapılan çağrının ortalama geçen kapsamlı süresi.|
|**Geçen maksimum kapsamlı süre**|Bu işleve yapılan çağrının geçen en uzun kapsamlı süresi.|
|**Geçen minimum kapsamlı süre**|Bu işleve yapılan çağrının geçen en düşük kapsamlı süre.|

## <a name="elapsed-exclusive-values"></a>Geçen dışlamalı değerler
 Geçen dışlamalı değerler, bir işlevin, işlevin gövdesinde kod yürüttüğünü, yani işlevin çağrı yığınının en üstünde olduğu süreyi belirtir. Bu süre, işletim sistemine yapılan çağrılarında bağlam anahtarları ve giriş/çıkış işlemleri gibi harcanan zamanı içerir, ancak işlev tarafından çağrılan işlevlerde harcanan zamanı içermez.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen dışlamalı süre**|Bu işleve yapılan tüm çağrıların geçen toplam dışlamalı süresi.|
|**Geçen dışlamalı süre yüzdesi**|Bu işlevin geçen toplam kullanım süresi içinde harcanan, profil oluşturma çalıştırmasının toplam geçen dışlamalı sürenin yüzdesi.|
|**Geçen ortalama dışlamalı süre**|Bu işleve yapılan çağrının geçen ortalama dışlamalı süre.|
|**Geçen maksimum dışlamalı süre**|Bu işlev çağrısının geçen maksimum dışlamalı süresi.|
|**Geçen en düşük dışlamalı süre**|Bu işleve yapılan çağrının en az geçen dışlamalı süresi.|

## <a name="application-inclusive-values"></a>Uygulama kapsamlı değerler
 Uygulama kapsamlı değerleri bir işlevin çağrı yığınında olduğu süreyi belirtir. Bu süre, işletim sistemine yapılan çağrılarında bağlam anahtarları ve giriş/çıkış işlemleri gibi harcanan zamanı içermez, ancak işlev tarafından çağrılan işlevlerde harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama kapsamlı süresi**|Bu işleve yapılan tüm çağrıların Toplam uygulama kapsamlı süresi.|
|**Uygulama kapsamlı süresi%**|Bu işlevin toplam uygulama kapsamlı süresi içinde harcanan, profil oluşturma çalıştırmasının toplam geçen iç süresinin yüzdesi.|
|**Ortalama uygulama kapsamlı süresi**|Bu işleve yapılan çağrının ortalama uygulama kapsamlı süresi.|
|**En fazla uygulama kapsamlı süresi**|Bu işleve yapılan çağrının uygulama kapsamlı en fazla süresi.|
|**En az uygulama kapsamlı süre**|Bu işleve yapılan çağrının en düşük uygulama kapsamlı süresi.|

## <a name="application-exclusive-values"></a>Uygulamanın dışlamalı değerleri
 Uygulamanın dışlamalı değeri, bir işlevin çağrı yığınının en üstünde doğrudan yürütüldüğü süreyi belirtir. Bu süre, işletim sistemine yapılan çağrılarında bağlam anahtarları ve giriş/çıkış işlemleri gibi harcanan zamanı içermez ve işlev tarafından çağrılan işlevlerde harcanan zamanı içermez.

|Sütun|Açıklama|
|------------|-----------------|
|**Dışlamalı uygulama süresi**|Bu işleve yapılan tüm çağrıların Toplam uygulama dışlamalı süresi.|
|**Uygulama dışlamalı süresi%**|Bu işlevin toplam uygulama dışlamalı saatinde harcanan profil oluşturma çalıştırmasının toplam geçen dışlamalı sürenin yüzdesi.|
|**Ortalama uygulama dışlamalı süresi**|Bu işleve yapılan çağrının ortalama uygulama dışlamalı süresi.|
|**Maksimum uygulama dışlamalı süresi**|Bu işleve yapılan çağrının en büyük uygulama dışlamalı süresi.|
|**En az uygulama dışlamalı süresi**|Bu işleve yapılan çağrının en düşük uygulama dışlamalı süresi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [İşlevler Görünümü](../profiling/functions-view-sampling-data.md)
- [İşlevler Görünümü-Örnekleme](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [İşlevler görünümü-izleme](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
