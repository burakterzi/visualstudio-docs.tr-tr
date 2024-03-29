---
title: Veri kaynakları penceresinden sürüklerken oluşturulacak denetimi ayarla
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Data Sources Window, select controls
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- data [Visual Studio], Data Sources window
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b5c57b73656f75ae9d99211ba28e38935d3164cb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72641034"
---
# <a name="set-the-control-to-be-created-when-dragging-from-the-data-sources-window"></a>Veri Kaynakları penceresinden sürüklendiğinde denetimin oluşturulmasını ayarlama

**Veri kaynakları** penceresinden WPF tasarımcısı veya Windows Forms Tasarımcısı üzerine sürükleyerek veri bağlantılı denetimler oluşturabilirsiniz. **Veri kaynakları** penceresindeki her öğe, tasarımcıya sürüklediğinizde oluşturulan bir varsayılan denetime sahiptir. Ancak, farklı bir denetim oluşturmayı tercih edebilirsiniz.

## <a name="set-the-controls-to-be-created-for-data-tables-or-objects"></a>Veri tabloları veya nesneleri için oluşturulacak denetimleri ayarlama

Veri **kaynakları** penceresinden veri tabloları veya nesneleri temsil eden öğeleri sürüklemeden önce, tüm verileri tek bir denetimde görüntülemeyi veya her bir sütunu ya da özelliği ayrı bir denetimde görüntülemeyi seçebilirsiniz.

Bu bağlamda, *nesne* terimi özel bir iş nesnesi, bir varlık (varlık veri modeli) veya bir hizmet tarafından döndürülen bir nesne anlamına gelir.

### <a name="to-set-the-controls-to-be-created-for-data-tables-or-objects"></a>Veri tabloları veya nesneleri için oluşturulacak denetimleri ayarlamak için

1. **WPF** tasarımcısı veya **Windows Forms** tasarımcısının açık olduğundan emin olun.

2. **Veri kaynakları** penceresinde, ayarlamak istediğiniz veri tablosu veya nesneyi temsil eden öğeyi seçin.

   > [!TIP]
   > **Veri kaynakları** penceresi açık değilse,**diğer Windows**  > **veri kaynaklarını** **görüntüle**  >  ' yi seçerek açabilirsiniz.

3. Öğenin açılan menüsüne tıklayın ve ardından menüdeki aşağıdaki öğelerden birine tıklayın:

    - Her veri alanını ayrı bir denetimde göstermek için **Ayrıntılar**' a tıklayın. Veri öğesini tasarımcıya sürüklediğinizde, bu eylem her bir denetimin etiketleriyle birlikte üst veri tablosu veya nesnesinin her bir sütunu veya özelliği için farklı bir veri bağlantılı denetim oluşturur.

    - Tüm verileri tek bir denetimde göstermek için, listede **DataGrid** veya bir WPF uygulamasında **liste** veya Windows Forms uygulamasında **DataGridView** gibi farklı bir denetim seçin.

    Kullanılabilir denetimlerin listesi, açtığınız tasarımcıya, projenizin hedeflediği .NET sürümüne ve **araç kutusu**'na veri bağlamayı destekleyen özel denetimler eklemiş olmanıza bağlıdır. Oluşturmak istediğiniz denetim kullanılabilir denetimler listesinde yoksa, denetimi listeye ekleyebilirsiniz. Daha fazla bilgi için bkz. [veri kaynakları penceresine özel denetimler ekleme](../data-tools/add-custom-controls-to-the-data-sources-window.md).

    **Veri kaynakları** penceresinde veri tabloları veya nesneleri için denetim listesine eklenebilen özel bir Windows Forms denetimi oluşturmayı öğrenmek için, bkz. [karmaşık veri bağlamayı destekleyen bir Windows Forms Kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).

## <a name="set-the-controls-to-be-created-for-data-columns-or-properties"></a>Veri sütunları veya özellikler için oluşturulacak denetimleri ayarlayın

Bir sütunu temsil eden bir öğeyi veya **veri kaynakları** penceresinden tasarımcıya bir nesne özelliğini sürükleyerek, denetimi oluşturulacak şekilde ayarlayabilirsiniz.

### <a name="to-set-the-controls-to-be-created-for-columns-or-properties"></a>Sütunlar veya özellikler için oluşturulacak denetimleri ayarlamak için

1. **WPF** tasarımcısı veya **Windows Forms** tasarımcısının açık olduğundan emin olun.

2. **Veri kaynakları** penceresinde, sütun veya özelliklerini göstermek için istenen tabloyu veya nesneyi genişletin.

3. Denetimin oluşturulmasını ayarlamak istediğiniz her bir sütunu veya özelliği seçin.

4. Sütun veya özelliğin açılan menüsüne tıklayın ve ardından öğe tasarımcıya sürüklendiğinde oluşturmak istediğiniz denetimi seçin.

     Kullanılabilir denetimlerin listesi, açtığınız tasarımcıya, projenizin hedeflediği .NET sürümüne ve **araç kutusuna**eklediğiniz veri bağlamayı destekleyen özel denetimlere bağlıdır. Oluşturmak istediğiniz denetim kullanılabilir denetimler listesinde ise, denetimi listeye ekleyebilirsiniz. Daha fazla bilgi için bkz. [veri kaynakları penceresine özel denetimler ekleme](../data-tools/add-custom-controls-to-the-data-sources-window.md).

     Veri **kaynakları** penceresinde veri sütunları veya özellikler için denetim listesine eklenebilen özel bir denetim oluşturmayı öğrenmek için bkz. [basit veri bağlamayı destekleyen bir Windows Forms Kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).

     Sütun veya özellik için bir denetim oluşturmak istemiyorsanız, açılan menüden **hiçbiri** ' ni seçin. Bu, üst tabloyu veya nesneyi tasarımcıya sürüklemek istiyorsanız yararlıdır, ancak belirli bir sütunu veya özelliği eklemek istemezsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)