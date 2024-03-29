---
title: 'Nasıl yapılır: görünümler ve XML Düzenleyicisi arasında geçiş yapma'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: cb69fbbd-d99c-439e-9498-5df9050f8df0
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f8049806d14abc8e22154a763e982ce5c86304b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601885"
---
# <a name="how-to-switch-between-views-and-the-xml-editor"></a>Nasıl yapılır: görünümler ve XML Düzenleyicisi arasında geçiş yapma

Bu konu başlığı altında, XML şema Tasarımcısı (XSD Designer) görünümleri ve XML Düzenleyicisi arasında nasıl geçiş yapılacağı gösterilmektedir. Bu örnek, [satın alma siparişi şemasını](../xml-tools/sample-xsd-file-simple-schema.md)kullanır.

## <a name="to-switch-between-the-views-and-the-xml-editor"></a>Görünümler ve XML Düzenleyicisi arasında geçiş yapmak için

1. Yeni bir XML şema dosyası oluşturmak ve düzenlemek için [nasıl yapılır: xsd şema dosyası oluşturma ve düzenleme](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)bölümündeki adımları izleyin.

2. XML Düzenleyicisi ' nden XML şema tasarımcısına geçiş yapmak için, XML düzenleyicisinde herhangi bir yere sağ tıklayın ve **Görünüm Tasarımcısı**' nı seçin.

3. Filigranı kullanarak grafik görünümüne geçiş yapmak için, başlangıç görünümündeki düğümler bağlantısı **arasındaki ilişkiyi görmek Için Graf görünümünü kullanın** ' a tıklayın.

4. @No__t_0 düğümünü **XML şema Gezgini** ' nden grafik görünümüne sürükleyin. Grafik görünümünde `USAddress` düğümüne sağ tıklayın ve bağlam menüsünde **Içerik modeli görünümünde göster** ' i seçin.

     @No__t_0 düğümün ayrıntıları ile Içerik modeli görünümü görüntülenir.

5. Araç çubuğunu kullanarak Içerik modeli görünümünden başlangıç görünümüne geçiş yapmak için, XSD araç çubuğundaki **görünümü Başlat** düğmesine tıklayın.

6. Kısayol tuşlarını kullanarak görünümler arasında geçiş yapmak için başlangıç görünümü için **ctrl** +**1** , grafik görünümü için **CTRL** +**2** ve içerik modeli görünümü için **CTRL** +**3** ' e basın.

7. Içerik modeli görünümünden XML düzenleyicisine gitmek için düğüme sağ tıklayın ve bağlam menüsünde **kodu görüntüle** ' yi seçin.