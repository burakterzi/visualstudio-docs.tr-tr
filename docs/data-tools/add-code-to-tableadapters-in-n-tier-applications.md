---
title: N katmanlı uygulamalarda TableAdapter’lara kod ekleme
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 246ba595cf1da7e4713e0ddc03ea015eeb61eb64
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648930"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>N katmanlı uygulamalarda TableAdapter’lara kod ekleme
TableAdapter için kısmi bir sınıf dosyası oluşturarak ve buna kod ekleyerek bir TableAdapter 'ın işlevselliğini genişletebilirsiniz ( *DataSetName. DataSet. Designer* dosyasına kod eklemek yerine). Kısmi sınıflar, belirli bir sınıfın kodunu birden çok fiziksel dosyaya bölünecek şekilde etkinleştirir. Daha fazla bilgi için bkz. [kısmi](/dotnet/visual-basic/language-reference/modifiers/partial) veya [kısmi (tür)](/dotnet/csharp/language-reference/keywords/partial-type).

Bir TableAdapter tanımlayan kod, veri kümesindeki TableAdapter 'ta her değişiklik yapıldığında oluşturulur. Bu kod ayrıca, TableAdapter yapılandırmasını değiştiren herhangi bir sihirbazın çalıştırılması sırasında değişiklik yapıldığında da oluşturulur. Bir TableAdapter 'ın yeniden oluşturulması sırasında kodunuzun silinmesini engellemek için TableAdapter 'ın parçalı sınıf dosyasına kod ekleyin.

Varsayılan olarak, veri kümesini ve TableAdapter kodunu ayırdıktan sonra sonuç, her projedeki ayrı bir sınıf dosyasıdır. Özgün projenin, TableAdapter kodunu içeren *DataSetName. Designer. vb* (veya *DataSetName.Designer.cs*) adlı bir dosyası vardır. **DataSet projesi** özelliğinde belirtilen proje, dataset kodunu Içeren *DataSetName. DataSet. Designer. vb* (veya *DataSetName.DataSet.Designer.cs*) adlı bir dosyaya sahiptir.

> [!NOTE]
> Veri kümelerini ve TableAdapters ayırabilirsiniz ( **veri kümesi proje** özelliğini ayarlayarak), projedeki mevcut kısmi veri kümesi sınıfları otomatik olarak taşınmaz. Mevcut kısmi veri kümesi sınıflarının veri kümesi projesine el ile taşınması gerekir.

> [!NOTE]
> Veri kümesi, doğrulama gerektiğinde <xref:System.Data.DataTable.ColumnChanging> ve <xref:System.Data.DataTable.RowChanging> olay işleyicileri oluşturmak için işlevsellik sağlar. Daha fazla bilgi için bkz. [n katmanlı bir veri kümesine doğrulama ekleme](../data-tools/add-validation-to-an-n-tier-dataset.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>N katmanlı bir uygulamadaki bir TableAdapter 'a Kullanıcı kodu eklemek için

1. *. Xsd* dosyasını içeren projeyi bulun.

2. **Veri kümesi Tasarımcısı**açmak için *. xsd* dosyasına çift tıklayın.

3. Kod eklemek istediğiniz TableAdapter öğesine sağ tıklayın ve ardından **kodu görüntüle**' yi seçin.

     Kod düzenleyicisinde kısmi bir sınıf oluşturulur ve açılır.

4. Kısmi sınıf bildiriminin içine kod ekleyin.

5. Aşağıdaki örnek, `NorthwindDataSet` `CustomersTableAdapter` kodun nereye ekleneceğini gösterir:

    ```vb
    Partial Public Class CustomersTableAdapter
        ' Add code here to add functionality
        ' to the CustomersTableAdapter.
    End Class
    ```

    ```csharp
    public partial class CustomersTableAdapter
    {
        // Add code here to add functionality
        // to the CustomersTableAdapter.
    }
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [N katmanlı veri uygulamalarına genel bakış](../data-tools/n-tier-data-applications-overview.md)
- [N katmanlı uygulamalarda veri kümelerine kod ekleme](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [TableAdapter’lar oluşturma ve yapılandırma](create-and-configure-tableadapters.md)
- [Hiyerarşik Güncelleştirmeye Genel Bakış](hierarchical-update.md)
