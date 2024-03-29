---
title: N katmanlı uygulamalarda Veri Kümelerine kod ekleme
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending DataSets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 0002339b0a1aa2200894d701f04f343193376c4b
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72807037"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>N katmanlı uygulamalarda Veri Kümelerine kod ekleme

Veri kümesi için kısmi bir sınıf dosyası oluşturarak ve buna kod ekleyerek bir veri kümesinin işlevselliğini genişletebilirsiniz ( *DataSetName*'e kod eklemek yerine). DataSet. Designer dosyası). Kısmi sınıflar, belirli bir sınıfın kodunu birden çok fiziksel dosyaya bölünecek şekilde etkinleştirir. Daha fazla bilgi için bkz. [kısmi](/dotnet/visual-basic/language-reference/modifiers/partial) veya [kısmi sınıflar ve Yöntemler](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).

Veri kümesini tanımlayan kod, veri kümesi tanımına her değişiklik yapıldığında oluşturulur (yazılan veri kümesinde). Bu kod ayrıca, bir veri kümesinin yapılandırmasını değiştiren herhangi bir sihirbazın çalıştırılması sırasında değişiklikler yaptığınızda da oluşturulur. Bir veri kümesinin yeniden oluşturulması sırasında kodunuzun silinmesini engellemek için, veri kümesinin kısmi sınıf dosyasına kod ekleyin.

Varsayılan olarak, veri kümesini ve TableAdapter kodunu ayırdıktan sonra sonuç, her projedeki ayrı bir sınıf dosyasıdır. Özgün projenin, TableAdapter kodunu içeren *DataSetName. Designer. vb* (veya *DataSetName.Designer.cs*) adlı bir dosyası vardır. **DataSet projesi** özelliğinde belirtilen proje, *DataSetName. DataSet. Designer. vb* (veya *DataSetName.DataSet.Designer.cs*) adlı bir dosya içerir. Bu dosya veri kümesi kodunu içerir.

> [!NOTE]
> Veri kümelerini ve TableAdapters ayırabilirsiniz ( **veri kümesi proje** özelliğini ayarlayarak), projedeki mevcut kısmi veri kümesi sınıfları otomatik olarak taşınmaz. Mevcut veri kümesi kısmi sınıflarının veri kümesi projesine el ile taşınması gerekir.

> [!NOTE]
> Doğrulama kodunun eklenmesi gerektiğinde, türü belirtilmiş veri kümesi <xref:System.Data.DataTable.ColumnChanging> ve <xref:System.Data.DataTable.RowChanging> olay işleyicilerini oluşturmak için işlevsellik sağlar. Daha fazla bilgi için bkz. [n katmanlı bir veri kümesine doğrulama ekleme](../data-tools/add-validation-to-an-n-tier-dataset.md).

## <a name="to-add-code-to-datasets-in-n-tier-applications"></a>N katmanlı uygulamalardaki veri kümelerine kod eklemek için

1. *. Xsd* dosyasını içeren projeyi bulun.

2. Veri kümesini açmak için **. xsd** dosyasını seçin.

3. Kod eklemek istediğiniz veri tablosuna (başlık çubuğundaki tablo adı) sağ tıklayın ve ardından **kodu görüntüle**' yi seçin.

     Kod düzenleyicisinde kısmi bir sınıf oluşturulur ve açılır.

4. Kısmi sınıf bildiriminin içine kod ekleyin.

     Aşağıdaki örnek, NorthwindDataSet 'teki CustomersDataTable öğesine kod nereye ekleneceğini gösterir:

    ```vb
    Partial Public Class CustomersDataTable
        ' Add code here to add functionality
        ' to the CustomersDataTable.
    End Class
    ```

    ```csharp
    partial class CustomersDataTable
    {
        // Add code here to add functionality
        // to the CustomersDataTable.
    }
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [N katmanlı veri uygulamalarına genel bakış](../data-tools/n-tier-data-applications-overview.md)
- [N katmanlı uygulamalarda TableAdapter’lara kod ekleme](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [TableAdapter’lar oluşturma ve yapılandırma](create-and-configure-tableadapters.md)
- [Hiyerarşik Güncelleştirmeye Genel Bakış](hierarchical-update.md)
- [Visual Studio 'da veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
