---
title: XML şema Gezgini 'nden çalışma alanına düğüm ekleme
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77e1890df09443e133f9e528905b76374f6070bc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646034"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Nasıl yapılır: XML şema Gezgini 'nden çalışma alanına düğüm ekleme

Bu konu başlığı altında, XML şema **Gezgini**' nden [XML şema Tasarımcısı çalışma alanına](../xml-tools/xml-schema-designer-workspace.md) düğümlerin nasıl ekleneceği açıklanmaktadır. Bu, düğümleri **XML şema** Gezgininden bir xsd tasarımcı görünümüne sürükleyip bırakarak veya **XML şeması Gezgini 'nin** bağlam menüsünü kullanarak elde edilebilir. Ayrıca, **XML şema Gezgini**tarafından gerçekleştirilen bir aramanın sonucu olarak vurgulanan düğümleri ekleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: şema kümesi arama sonucu düğümlerini çalışma alanına ekleme](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).

> [!NOTE]
> [XML şema Tasarımcısı çalışma alanına](../xml-tools/xml-schema-designer-workspace.md)yalnızca genel düğümler eklenebilir.

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>XML Gezgini bağlam menüsü aracılığıyla düğüm eklemek için

1. [Nasıl yapılır: xsd şema dosyası oluşturma ve düzenleme](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)bölümündeki adımları izleyin.

2. XSD Explorer 'daki `PurchaseOrderType` düğümüne sağ tıklayın. **Grafik görünümünde göster '** i seçin.

     @No__t_0 düğümü grafik görünümünün tasarım yüzeyinde görünür.

## <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Bir düğümü bir görünüme sürükleyip bırakmak için

1. Grafik görünümündeki `PurchaseOrderType` düğümüne sağ tıklayın. **XML şema Gezgininde Göster '** i seçin.

     Düğüm, **XML şema Gezgini**'nde vurgulanır.

2. **XML şeması gezgininde** `PurchaseOrderType` düğümüne sağ tıklayın ve **tüm başvuruları göster**' i seçin.

     @No__t_0 düğümü vurgulanır.

3. @No__t_0 düğümünü grafik görünümüne sürükleyin.

     @No__t_0 düğümü ve `PurchaseOrderType` düğümü, grafik görünümünün tasarım yüzeyinde birbirini izleyen bir şekilde görünür. İki düğüm ilişkili olduğundan (`purchaseOrder` öğesi `PurchaseOrderType` türünde), aralarında bir ok çizilir.

## <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Şema Gezgini arama özelliğini kullanarak düğüm eklemek için

1. [XML Explorer](../xml-tools/xml-schema-explorer.md) araç çubuğunun arama metin kutusuna "PurchaseOrder" yazın ve arama düğmesine tıklayın.

     ![XML şema Gezgini anahtar sözcük arama](../xml-tools/media/schemaexplorersearch.gif)

     Arama sonuçları, **XML şema Gezgini** 'nde vurgulanır ve dikey kaydırma çubuğundaki Tick 'ler tarafından işaretlenir.

2. Özet sonuçlar bölmesinde, **çalışma alanına vurgulanan düğümleri Ekle** düğmesine tıklayarak arama sonuçlarını çalışma alanına ekleyin.

     ![XML şema Gezgini arama sonucu](../xml-tools/media/schemaexplorersearchresult.gif)

     @No__t_0 düğümü ve `PurchaseOrderType` düğümü, [Grafik görünümünün](../xml-tools/graph-view.md)tasarım yüzeyinde birbirini izleyen bir şekilde görünür. İki düğüm ilişkili olduğundan (`purchaseOrder` öğesi `PurchaseOrderType` türünde), aralarında bir ok çizilir.

## <a name="see-also"></a>Ayrıca bkz.

- [XML Şema Gezgini](../xml-tools/xml-schema-explorer.md)