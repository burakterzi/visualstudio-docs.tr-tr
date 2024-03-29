---
title: 'Nasıl Yapılır: Sınıfı Kısmi Sınıflara Bölme (Sınıf Tasarımcısı)'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 42d2cf5c0fa5c08c51ebfbc94d9a03221df46788
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647701"
---
# <a name="how-to-split-a-class-into-partial-classes-in-class-designer"></a>Nasıl yapılır: Sınıf Tasarımcısı bir sınıfı kısmi sınıflara bölme

Bir sınıfın veya yapının bildirimini birkaç bildirim arasında bölmek için `partial` anahtar sözcüğünü (Visual Basic `Partial`) kullanabilirsiniz. İstediğiniz kadar çok sayıda kısmi bildirim kullanabilirsiniz.

Bildirimler bir veya birden çok kaynak dosyasında olabilir. Tüm bildirimlerin aynı derlemede ve aynı ad alanında olması gerekir.

Kısmi sınıflar çeşitli durumlarda faydalıdır. Örneğin, büyük bir projede, bir sınıfı birden çok dosyaya ayırmak, birden fazla programcının proje üzerinde aynı anda çalışmasını sağlar. Visual Studio 'Nun oluşturduğu kodla çalışırken, kaynak dosyayı yeniden oluşturmaya gerek kalmadan sınıfı değiştirebilirsiniz. (Visual Studio 'Nun oluşturduğu kod örnekleri Windows Forms ve Web hizmeti sarmalayıcı kodu içerir.) Bu nedenle, Visual Studio 'Nun oluşturduğu dosyayı değiştirmek zorunda kalmadan otomatik olarak oluşturulan sınıflar kullanan kod oluşturabilirsiniz.

İki tür kısmi yöntem vardır. İçinde C#, bunlar bildirme ve uygulama olarak adlandırılır; Visual Basic, bildirim ve uygulama olarak adlandırılırlar.

**Sınıf Tasarımcısı** kısmi sınıfları ve yöntemleri destekler. Sınıf diyagramındaki tür şekli, kısmi sınıf için tek bir bildirim konumuna başvurur. Kısmi sınıf birden çok dosyada tanımlanmışsa, **Özellikler** penceresinde **yeni üye konumu** özelliğini ayarlayarak hangi bildirim konumunun **Sınıf Tasarımcısı** kullanacağınızı belirtebilirsiniz. Diğer bir deyişle, bir sınıf şekline çift tıkladığınızda **Sınıf Tasarımcısı** **yeni üye konumu** özelliği tarafından tanımlanan sınıf bildirimini içeren kaynak dosyaya gider. Bir sınıf şeklinin içindeki kısmi bir yönteme çift tıkladığınızda **Sınıf Tasarımcısı** kısmi Yöntem bildirimine gider. Ayrıca, **Özellikler** penceresinde, **dosya adı** özelliği bildirim konumunu ifade eder. Kısmi sınıflar için **dosya adı** , bu sınıf için bildirim ve uygulama kodu içeren tüm dosyaları listeler. Ancak, kısmi yöntemler için **dosya adı** yalnızca kısmi Yöntem bildirimini içeren dosyayı listeler.

Aşağıdaki örnekler, her biri farklı bir yordam tanımlayan `Employee` sınıfının tanımını iki bildirime ayırır. Örneklerdeki iki kısmi Tanım, bir kaynak dosyasında veya iki farklı kaynak dosyada olabilir.

> [!NOTE]
> Visual Basic, Visual Studio tarafından üretilen kodu Kullanıcı tarafından yazılan koddan ayırmak için kısmi sınıf tanımları kullanır. Kod ayrı kaynak dosyalarına ayrılmıştır. Örneğin, **Windows form tasarımcısı** `Form` gibi denetimler için kısmi sınıfları tanımlar. Bu denetimlerde oluşturulan kodu değiştirmemelisiniz.

Visual Basic kısmi türleri hakkında daha fazla bilgi için bkz. [kısmi](/dotnet/visual-basic/language-reference/modifiers/partial).

## <a name="example"></a>Örnek

Bir sınıf tanımını ayırmak için, aşağıdaki örnekte gösterildiği gibi `partial` anahtar sözcüğünü (Visual Basic `Partial`) kullanın:

```csharp
// First part of class definition.
public partial class Employee
{
    public void CalculateWorkHours()
    {
    }
}

// Second part of class definition.
public partial class Employee
{
    public void CalculateTaxes()
    {
    }
}
```

```vb
' First part of class definition.
Partial Public Class Employee
    Public Sub CalculateWorkHours()
    End Sub
End Class

' Second part of class definition.
Partial Public Class Employee
    Public Sub CalculateTaxes()
    End Sub
End Class
```

## <a name="see-also"></a>Ayrıca bkz.

- [Kısmi sınıflar ve Yöntemler](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)
- [partial (tür) (C# başvuru)](/dotnet/csharp/language-reference/keywords/partial-type)
- [partial (Yöntem) (C# başvuru)](/dotnet/csharp/language-reference/keywords/partial-method)
- [Kısmi (Visual Basic)](/dotnet/visual-basic/language-reference/modifiers/partial)