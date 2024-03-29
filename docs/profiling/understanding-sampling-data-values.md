---
title: Örnekleme veri değerlerini anlama | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- Profiling Tools, sampling
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 289f92deaceca32a44249ed77c17187743a34fa4
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778056"
---
# <a name="understand-sampling-data-values"></a>Örnekleme veri değerlerini anlama

Visual Profil Oluşturma Araçları Studio 'nun *örnekleme* profili oluşturma yöntemi, bilgisayar işlemcisini ayarlanan aralıklarla keser ve işlev çağrı yığınını toplar. *Çağrı yığını* , işlemcide yürütülen işlevlerle ilgili bilgileri depolayan dinamik bir yapıdır.

Profil Oluşturucu analizi, işlemcinin hedef işlemde kod yürütmediğini belirler. İşlemci hedef işlemde kod yürütülemiyor, örnek atılır.

İşlemci hedef kodu yürütüp, profil oluşturucu çağrı yığınında her bir işlevin örnek sayılarını arttırır. Örneğin alındığı sırada, çağrı yığınında yalnızca bir işlev şu anda kodu yürütüyor. Yığındaki diğer işlevler, alt öğelerinin dönebilmeleri için bekleyen işlev çağrılarının hiyerarşisinde üstlerdir.

Örnek olay için, profil oluşturucu Şu anda yönergelerini yürüten işlevin *dışlamalı* örnek sayısını artırır. Dışlamalı bir örnek aynı zamanda işlevin toplam (*kapsamlı*) örneklerinin bir parçası olduğundan, şu anda etkin olan işlevin kapsamlı örnek sayısı da artırılır.

 Profiler, Çağrı yığınındaki diğer tüm işlevlerin dahil edilen örnek sayısını artırır.

## <a name="inclusive-samples"></a>Kapsamlı örnekler

Hedef işlevin yürütülmesi sırasında toplanan örneklerin toplam sayısı.

Bu, işlev kodunun doğrudan yürütülmesi sırasında toplanan örnekleri ve hedef işlev tarafından çağrılan alt işlevlerin yürütülmesi sırasında toplanan örnekleri içerir.

## <a name="exclusive-samples"></a>Dışlamalı örnekler

Hedef işlevin yönergelerinin doğrudan yürütülmesi sırasında toplanan örneklerin sayısı.

Dışlamalı örnekler, hedef işlev tarafından çağrılan işlevlerin yürütülmesi sırasında toplanan örnekleri içermez.

## <a name="inclusive-percent"></a>Kapsamlı yüzde

Profil oluşturma çalıştırmasında, işlevin veya veri aralığının kapsamlı örnekleri olan toplam kapsamlı örnek sayısının yüzdesi.

## <a name="exclusive-percent"></a>Dışlamalı yüzde

Profil oluşturma çalıştırmasında, işlevin veya veri aralığının özel örnekleri olan toplam dışlamalı örnek sayısının yüzdesi.

## <a name="see-also"></a>Ayrıca bkz.

[Nasıl yapılır: koleksiyon yöntemlerini seçme](../profiling/how-to-choose-collection-methods.md)
[performans araçları verilerini analiz etme](../profiling/analyzing-performance-tools-data.md)
