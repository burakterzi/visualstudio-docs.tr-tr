---
title: Bir TableAdapter ile veritabanına doğrudan erişme
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Visual Basic], accessing with a TableAdapter
- DBDirect methods
- datasets [Visual Basic], adding to projects
- data [Visual Studio], saving
- TableAdapter.Delete method
- GenerateDbDirectMethods property
- TableAdapter.Insert method
- TableAdapter.GenerateDBDirectMethods property
- TableAdapter.Update method
- saving data
- TableAdapters
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e8d5d8e3091b464084df065bb7b889db9fc2194f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648508"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Bir TableAdapter ile veritabanına doğrudan erişme

@No__t_0, `UpdateCommand` ve `DeleteCommand` ek olarak, TableAdapters doğrudan veritabanına karşı çalıştırılabilen yöntemlerle oluşturulur. Verileri doğrudan veritabanında işlemek için bu yöntemleri (`TableAdapter.Insert`, `TableAdapter.Update` ve `TableAdapter.Delete`) çağırabilirsiniz.

Bu doğrudan yöntemleri oluşturmak istemiyorsanız, TableAdapter 'ın `GenerateDbDirectMethods` özelliğini **Özellikler** penceresinde `false` olarak ayarlayın. TableAdapter 'ın ana sorgusuna ek olarak bir TableAdapter 'a herhangi bir sorgu eklenirse, bu `DbDirect` yöntemlerini üretmeyin tek başına sorgulardır.

## <a name="send-commands-directly-to-a-database"></a>Komutları doğrudan bir veritabanına gönder

Gerçekleştirmeyi denediğiniz görevi gerçekleştiren TableAdapter `DbDirect` yöntemini çağırın.

### <a name="to-insert-new-records-directly-into-a-database"></a>Yeni kayıtları doğrudan bir veritabanına eklemek için

- Her bir sütunun değerlerini parametre olarak geçirerek TableAdapter 'ın `Insert` yöntemini çağırın. Aşağıdaki yordam bir örnek olarak Northwind veritabanındaki `Region` tablosunu kullanır.

    > [!NOTE]
    > Kullanılabilir bir örneğiniz yoksa, kullanmak istediğiniz TableAdapter örneğini oluşturun.

     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]

### <a name="to-update-records-directly-in-a-database"></a>Kayıtları doğrudan bir veritabanında güncelleştirmek için

- TableAdapter 'ın `Update` yöntemini çağırın, her sütun için yeni ve orijinal değerlerini parametre olarak geçirerek.

    > [!NOTE]
    > Kullanılabilir bir örneğiniz yoksa, kullanmak istediğiniz TableAdapter örneğini oluşturun.

     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-csharp[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]

### <a name="to-delete-records-directly-from-a-database"></a>Kayıtları doğrudan veritabanından silmek için

- Her bir sütunun değerlerini `Delete` yönteminin parametreleri olarak geçirerek TableAdapter 'ın `Delete` yöntemini çağırın. Aşağıdaki yordam bir örnek olarak Northwind veritabanındaki `Region` tablosunu kullanır.

    > [!NOTE]
    > Kullanılabilir bir örneğiniz yoksa, kullanmak istediğiniz TableAdapter örneğini oluşturun.

     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-csharp[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)