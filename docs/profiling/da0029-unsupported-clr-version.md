---
title: 'DA0029: desteklenmeyen CLR sürümü | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.29
- vs.performance.rules.DA0029
helpviewer_keywords:
- vs.performance.29
- vs.performance.DA0029
- vs.performance.rules.DA0029
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: dbc0bfcdb49557e56711b60dca11977a3504d907
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777521"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: desteklenmeyen CLR sürümü

|||
|-|-|
|Kural Kimliği|DA0029|
|Kategori|Profil Oluşturma Araçları kullanımı|
|Profil oluşturma yöntemi|Komut satırından profil oluşturma|
|İleti|Koleksiyon sırasında desteklenmeyen bir CLR sürümü algılandı. Yönetilen semboller doğru şekilde çözümlenmeyebilir.|
|Kural türü|Bilgi.|

## <a name="cause"></a>Sebep
 Profil Oluşturma Araçları tarafından desteklenmeyen [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)] kullanan bir uygulamayı profile çalışıyorsunuz.

## <a name="rule-description"></a>Kural açıklaması
 Bu uyarı, profil oluşturma araçlarının uygulamada çalışan yönetilen kodun sembollerini çözemediği için oluşur. Profil oluşturma araçları, [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)]çalıştıran uygulamalar için yönetilen kod sembollerini çözemez.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
 Yok.
