---
title: "Nasıl yapılır: Visual Basic projesindeki kodu VBA 'de kullanıma sunma"
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- Visual Basic [Office development in Visual Studio], exposing code to VBA
- exposing code to VBA
- host items [Office development in Visual Studio], exposing code to VBA
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e5a0f962d93713137b23e20e35dc75108925859d
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985935"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-basic-project"></a>Nasıl yapılır: Visual Basic projesindeki kodu VBA 'de kullanıma sunma
  İki tür kodun birbirleriyle etkileşime geçmesini isterseniz, kodu bir [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projesindeki Visual Basic for Applications (VBA) kodunda açığa çıkarmak için kullanabilirsiniz.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Visual Basic işlem görsel C# işlemden farklıdır. Daha fazla bilgi için bkz. [nasıl yapılır: Visual C&#35; projesinde kodu VBA 'de kullanıma](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)sunma.

 İşlem, bir konak öğesi sınıfındaki kod için, diğer sınıflardaki kod olduğundan farklıdır:

- [Kodu bir konak öğesi sınıfında kullanıma sunma](#HostItemCode)

- [Konak öğesi sınıfında olmayan kodu açığa çıkarın](#NonHostItem)

## <a name="HostItemCode"></a>Kodu bir konak öğesi sınıfında kullanıma sunma
 VBA kodunu bir konak öğesi sınıfında Visual Basic kodu çağırmak üzere etkinleştirmek için, konak öğesinin **EnableVbaCallers** özelliğini **true**olarak ayarlayın.

 Bir konak öğesi sınıfının bir yöntemini kullanıma sunma ve sonra bunu VBA 'dan çağırma hakkında yönergeler için bkz. [Izlenecek yol: Visual Basic PROJESINDEKI VBA 'dan kod çağırma](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md). Konak öğeleri hakkında daha fazla bilgi için bkz. [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md).

#### <a name="to-expose-code-in-a-host-item-to-vba"></a>Bir konak öğesinde kodu VBA 'de ortaya çıkarmak için

1. Makroları destekleyen ve zaten VBA kodu içeren bir Word belgesini, Excel çalışma kitabını veya Excel şablonunu temel alan belge düzeyi [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projesi açın veya oluşturun.

     Makroları destekleyen belge dosyası biçimleri hakkında daha fazla bilgi için bkz. [VBA ve belge düzeyi özelleştirmelerini birleştirme](../vsto/combining-vba-and-document-level-customizations.md).

    > [!NOTE]
    > Bu özellik Word şablon projelerinde kullanılamaz.

2. Belgedeki VBA kodunun, kullanıcıdan makroları etkinleştirmesini istemeden çalışmasına izin verildiğinden emin olun. Office projesinin konumunu, Word veya Excel için Güven Merkezi ayarlarındaki güvenilir konumlar listesine ekleyerek çalıştırmak için VBA koduna güvenebilirsiniz.

3. VBA 'da göstermek istediğiniz özelliği, yöntemi veya olayı projenizdeki konak öğesi sınıflarından birine ekleyin ve yeni üyeyi **ortak**olarak bildirin. Sınıfın adı uygulamaya göre değişir:

    - Bir Word projesinde, ana bilgisayar öğe sınıfı varsayılan olarak `ThisDocument` olarak adlandırılır.

    - Bir Excel projesinde, konak öğesi sınıfları varsayılan olarak `ThisWorkbook`, `Sheet1`, `Sheet2`ve `Sheet3` olarak adlandırılır.

4. Konak öğesi için **EnableVbaCallers** özelliğini **true**olarak ayarlayın. Bu özellik, konak öğesi tasarımcıda açık olduğunda **Özellikler** penceresinde kullanılabilir.

     Bu özelliği ayarladıktan sonra, Visual Studio otomatik olarak **ReferenceAssemblyFromVbaProject** özelliğini **true**olarak ayarlar.

    > [!NOTE]
    > Çalışma kitabı veya belge zaten VBA kodu içermiyorsa veya belgedeki VBA kodunun çalıştırılmak üzere güvenilir olmaması durumunda, **EnableVbaCallers** özelliğini **true**olarak ayarladığınızda bir hata iletisi alırsınız. Bunun nedeni, Visual Studio 'Nun belgedeki VBA projesini değiştiremeyeceği durumdur.

5. Görüntülenen iletide **Tamam** ' a tıklayın. Bu ileti, projeyi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]çalıştırırken çalışma kitabına veya belgeye VBA kodu eklerseniz, projeyi bir sonraki sefer oluşturduğunuzda VBA kodu kaybedilir. Bunun nedeni, projeyi her oluşturduğunuzda derleme çıkış klasöründeki belgenin üzerine yazılışında olur.

     Bu noktada, Visual Studio projeyi VBA projesinin derlemeye çağırabilmesi için yapılandırır. Visual Studio Ayrıca, VBA projesindeki `ThisDocument`, `ThisWorkbook`, `Sheet1`, `Sheet2`veya `Sheet3` modülüne `CallVSTOAssembly` adlı bir özellik ekler. Bu özelliği, VBA 'da kullanıma sunulan sınıfın ortak üyelerine erişmek için kullanabilirsiniz.

6. Projeyi oluşturun.

## <a name="NonHostItem"></a>Konak öğesi sınıfında olmayan kodu açığa çıkarın
 VBA kodunu bir konak öğesi sınıfında olmayan Visual Basic kodu çağırmak üzere etkinleştirmek için kodu VBA 'da görünür olacak şekilde değiştirin.

### <a name="to-expose-code-that-is-not-in-a-host-item-class-to-vba"></a>Konak öğesi sınıfında olmayan kodu VBA 'ya göstermek için

1. Makroları destekleyen ve zaten VBA kodu içeren bir Word belgesini, Excel çalışma kitabını veya Excel şablonunu temel alan belge düzeyi [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projesi açın veya oluşturun.

     Makroları destekleyen belge dosyası biçimleri hakkında daha fazla bilgi için bkz. [VBA ve belge düzeyi özelleştirmelerini birleştirme](../vsto/combining-vba-and-document-level-customizations.md).

    > [!NOTE]
    > Bu özellik Word şablon projelerinde kullanılamaz.

2. Belgedeki VBA kodunun, kullanıcıdan makroları etkinleştirmesini istemeden çalışmasına izin verildiğinden emin olun. Office projesinin konumunu, Word veya Excel için Güven Merkezi ayarlarındaki güvenilir konumlar listesine ekleyerek çalıştırmak için VBA koduna güvenebilirsiniz.

3. VBA 'ya göstermek istediğiniz üyeyi projenizdeki ortak bir sınıfa ekleyin ve yeni üyeyi **ortak**olarak bildirin.

4. Aşağıdaki <xref:System.Runtime.InteropServices.ComVisibleAttribute> ve <xref:Microsoft.VisualBasic.ComClassAttribute> özniteliklerini VBA 'da kullanıma sunettiğiniz sınıfa uygulayın. Bu öznitelikler, sınıfı VBA 'da görünür hale getirir.

    ```vb
    <Microsoft.VisualBasic.ComClass()> _
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _
    ```

5. VBA 'da kullanıma sunmanıza yardımcı olan sınıfın bir örneğini döndürmek için projenizdeki bir konak öğesi sınıfının **GetAutomationObject** yöntemini geçersiz kılın. Aşağıdaki kod örneği, VBA 'ya `DocumentUtilities` adlı bir sınıfı kullanıma sunduğunuzu varsayar.

    ```vb
    Protected Overrides Function GetAutomationObject() As Object
        Return New DocumentUtilities()
    End Function
    ```

6. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]'de belge (Word için) veya çalışma sayfası (Excel için) Tasarımcısı ' nı açın.

7. **Özellikler** penceresinde, **ReferenceAssemblyFromVbaProject** özelliğini seçin ve değeri **true**olarak değiştirin.

    > [!NOTE]
    > Çalışma kitabı veya belge zaten VBA kodu içermiyorsa veya belgedeki VBA kodunun çalıştırılmak üzere güvenilir olmaması durumunda, **ReferenceAssemblyFromVbaProject** özelliğini **true**olarak ayarladığınızda bir hata iletisi alırsınız. Bunun nedeni, Visual Studio 'Nun belgedeki VBA projesini değiştiremeyeceği durumdur.

8. Görüntülenen iletide **Tamam** ' a tıklayın. Bu ileti, projeyi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]çalıştırırken çalışma kitabına veya belgeye VBA kodu eklerseniz, projeyi bir sonraki sefer oluşturduğunuzda VBA kodu kaybedilir. Bunun nedeni, projeyi her oluşturduğunuzda derleme çıkış klasöründeki belgenin üzerine yazılışında olur.

     Bu noktada, Visual Studio projeyi VBA projesinin derlemeye çağırabilmesi için yapılandırır. Visual Studio, `GetManagedClass` adlı bir yöntemi VBA projesine de ekler. VBA 'da gösterilen sınıfa erişmek için VBA projesinin herhangi bir yerinden bu yöntemi çağırabilirsiniz.

9. Projeyi oluşturun.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Visual Studio 'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [VBA ve belge düzeyi özelleştirmelerini birleştirme](../vsto/combining-vba-and-document-level-customizations.md)
- [İzlenecek yol: Visual Basic projesindeki VBA 'dan kod çağırma](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
- [Nasıl yapılır: Visual C&#35; PROJESINDE kodu VBA 'de kullanıma sunma](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
