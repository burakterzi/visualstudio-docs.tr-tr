---
title: Üretilen kod için kod analizi ihlallerini gösterme
ms.date: 05/13/2019
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39daa50254f2d1b69514d4065e582154e9ceb6b5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649402"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Nasıl yapılır: üretilen kod için kod analizi uyarılarını gösterme

Oluşturulan kod, yönetilen kod derleyicileri veya üçüncü taraf araçları tarafından projenize eklenen kodu içerir. Kod analizinin üretilen kodda bulduğu kural ihlallerini görmek isteyebilirsiniz. Ancak, ihlalleri içeren kodu görüntüleyemediğinden ve koruyabileceğinizden, bunları görmek istemeyebilirsiniz.

Bir projenin kod analizi özelliği sayfasında, **üretilen koddan sonuçları gösterme** onay kutusu, üçüncü taraf bir araç tarafından oluşturulan koddan kod analizi uyarılarını gösterip göstermeyeceğinizi seçmenize olanak sağlar.

> [!NOTE]
> Bu seçenek, hatalar ve uyarılar formlarda ve şablonlarda görüntülendiğinde, kod analizi hatalarını ve üretilen koddan gelen uyarıları göstermez. Bir form veya şablon için kaynak kodu görüntüleyebilir ve bakımını yapabilirsiniz.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Bir projede oluşturulan koda yönelik uyarıları gizlemek için

1. **Çözüm Gezgini** ' de projeye sağ tıklayın ve ardından **Özellikler**' e tıklayın.

2. **Kod Analizi** sekmesini seçin.

3. **Oluşturulan koddan sonuçları bastır** onay kutusunu seçin.

> [!NOTE]
> Yalnızca eski analizden gelen uyarıları gizleyebilirsiniz. Şu anda [çözümleyicilerin](roslyn-analyzers-overview.md)kod analizi uyarılarını gizlenemez.
