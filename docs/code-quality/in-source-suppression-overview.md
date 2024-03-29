---
title: Kod Analizi uyarılarını gösterme
ms.date: 12/01/2018
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 50afd9ffd72c37510997176f103f3b269f29fcf2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649306"
---
# <a name="suppress-code-analysis-warnings"></a>Kod Analizi uyarılarını gösterme

Bir uyarının geçerli olmadığını göstermek için genellikle yararlı olur. Bu, takım üyelerinin kodun gözden geçirdiğini ve uyarının bastırılamayacağını gösterir. Kaynak içi gizleme (ISS), bir uyarıyı bastırmak için <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> özniteliğini kullanır. Özniteliği, uyarıyı oluşturan kod kesimine yakın şekilde yerleştirilebilir. Kaynak dosyaya yazarak <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> özniteliğini ekleyebilir veya otomatik olarak eklemek için **hata listesi** bir uyarı üzerinde kısayol menüsünü kullanabilirsiniz.

@No__t_0 özniteliği, yönetilen kod derlemelerinizin Il meta verilerine dahil olan ve yalnızca derleme zamanında CODE_ANALYSIS derleme simgesi tanımlanmışsa koşullu bir özniteliktir.

C++/CLI ' da, özniteliği eklemek için \_MESSAGE veya ca \_SUPPRESS_MESSAGE \_GLOBAL \_SUPPRESS makrolar CA 'sını kullanın.

> [!NOTE]
> Kaynak gizleme verilerinin yanlışlıkla serbest bırakılmasını engellemek için sürüm yapılarında kaynak üzerinde gizlemeleri kullanmamalısınız. Ayrıca, kaynak içi göstermeme işleminin işlem maliyeti nedeniyle uygulamanızın performansı düşebilir.

::: moniker range="vs-2017"

> [!NOTE]
> Bir projeyi Visual Studio 2017 ' a geçirirseniz, çok sayıda kod analizi uyarısıyla aniden karşılaşabilirsiniz. Uyarıları gidermeye hazırsanız,**Kod analizini çalıştır  >  Çalıştır ' ı ve etkin sorunları Gizle**' yi seçerek bunların hepsini gizleyebilirsiniz.
>
> ![Visual Studio 'da Kod analizini çalıştırma ve sorunları gösterme](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> Bir projeyi Visual Studio 2019 ' a geçirirseniz, çok sayıda kod analizi uyarısıyla aniden karşılaşabilirsiniz. Uyarıları gidermeye hazırsanız,  >  derlemeyi **Çözümle** **ve etkin sorunları Gizle**' yi seçerek bunların tümünün görüntülenmesini sağlayabilirsiniz.

::: moniker-end

## <a name="suppressmessage-attribute"></a>SuppressMessage özniteliği

**Hata listesi**bir kod analizi uyarısında bağlam veya sağ tıklama menüsünden **Gizle** ' yi seçtiğinizde, kodunuzda veya projenin global gizleme dosyasına bir <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> özniteliği eklenir.

@No__t_0 özniteliği aşağıdaki biçimdedir:

```vb
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]
```

```cpp
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")
```

Özniteliğin özellikleri şunları içerir:

- **Kategori** -kuralın tanımlandığı kategori. Kod analizi kural kategorileri hakkında daha fazla bilgi için bkz. [yönetilen kod uyarıları](../code-quality/code-analysis-for-managed-code-warnings.md).

- **CheckId** -kuralın tanımlayıcısı. Destek, kural tanımlayıcısı için hem kısa hem de uzun bir ad içerir. Kısa ad CAXXXX; Long adı CAXXXX:

- **Bloklama** -iletinin nasıl bastırılamamasının nedenini belgelemek için kullanılan metin.

- **MessageID** -her ileti için bir sorunun benzersiz tanıtıcısı.

- **Scope** -uyarının gizlendiği hedef. Hedef belirtilmemişse, özniteliğinin hedefine ayarlanır. Desteklenen [kapsamlar](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) şunları içerir:

  - `module`

  - `resource`

  - `type`

  - `member`

  - `namespace`-bu kapsam, ad alanının kendisiyle karşı uyarıları göstermez. Ad uzayı içindeki türlere karşı uyarıları göstermez.

  - `namespaceanddescendants`-(Visual Studio 2019 için yeni) bu kapsam, bir ad alanındaki uyarıları ve tüm alt sembolleri bastırır. @No__t_0 değeri eski analiz tarafından yok sayılır.

- **Target** -uyarının bastırılmakta olduğu hedefi belirtmek için kullanılan bir tanımlayıcı. Tam nitelikli bir öğe adı içermelidir.

## <a name="suppressmessage-usage"></a>SuppressMessage kullanımı

Kod Analizi uyarıları <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> özniteliğinin uygulandığı düzeyde bastırılır. Örneğin, öznitelik derleme, modül, tür, üye veya parametre düzeyinde uygulanabilir. Bunun amacı, gizleme bilgilerinin ihlalin gerçekleştiği koda sıkı bir şekilde tam olarak daha katı bir biçimde.

Gizleme 'nin Genel biçimi kural kategorisini ve kural adının isteğe bağlı olarak okunabilir bir gösterimini içeren bir kural tanımlayıcısını içerir. Örneğin:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

Kaynak gizleme gizleme meta verilerini en aza indirmek için kesin performans nedenleriyle, kural adı atlanabilir. Kural kategorisi ve kural KIMLIĞI birlikte yeterince benzersiz bir kural tanımlayıcısı oluşturur. Örneğin:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

Bakım nedenleriyle, kural adının atlanması önerilmez.

## <a name="suppress-selective-violations-within-a-method-body"></a>Yöntem gövdesinde seçmeli ihlalleri gösterme

Gizleme öznitelikleri bir yönteme uygulanabilir, ancak bir yöntem gövdesi içine Katıştırılamaz. Bu, yöntemine <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> özniteliğini eklediğinizde belirli bir kuralın tüm ihlallerinin gizlenme anlamına gelir.

Bazı durumlarda, örneğin, gelecekteki kodun kod analizi kuralından otomatik olarak muaf olmaması gibi, ihlalin belirli bir örneğini bastırmak isteyebilirsiniz. Belirli kod analizi kuralları, bunu <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> özniteliğinin `MessageId` özelliğini kullanarak yapmanıza olanak sağlar. Genel olarak, belirli bir sembolde (yerel bir değişken veya parametre) ihlallerin bilinen kuralları `MessageId` özelliğine göre yapılır. [CA1500: VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500.md) , böyle bir kurala bir örnektir. Ancak, yürütülebilir koddaki (simge dışı) ihlallerin eski kuralları `MessageId` özelliğine uymaz. Ayrıca, .NET Compiler Platform ("Roslyn") Çözümleyicileri, `MessageId` özelliğine uymaz.

Bir kuralın belirli bir sembol ihlalini engellemek için, <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> özniteliğinin `MessageId` özelliğinin sembol adını belirtin. Aşağıdaki örnek, `name` değişkeni ve bir `age` değişkeni için &mdash;one [CA1500: VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500.md) için iki ihlal içeren kodu gösterir. Yalnızca `age` sembolü için ihlal bastırılır.

```vb
Public Class Animal
    Dim age As Integer
    Dim name As String

    <CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId:="age")>
    Sub PrintInfo()
        Dim age As Integer = 5
        Dim name As String = "Charlie"

        Console.WriteLine("Age {0}, Name {1}", age, name)
    End Sub

End Class
```

```csharp
public class Animal
{
    int age;
    string name;

    [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId = "age")]
    private void PrintInfo()
    {
        int age = 5;
        string name = "Charlie";

        Console.WriteLine($"Age {age}, Name {name}");
    }
}
```

## <a name="generated-code"></a>Oluşturulan kod

Yönetilen kod derleyicileri ve bazı üçüncü taraf araçları, hızlı kod geliştirmeyi kolaylaştırmak için kod üretir. Kaynak dosyalarda görünen derleyici tarafından oluşturulan kod genellikle `GeneratedCodeAttribute` özniteliğiyle işaretlenir.

Kod Analizi uyarılarını ve oluşturulan kod için hataları bastırıp bastırmayacağını seçebilirsiniz. Bu tür uyarıları ve hataları gösterme hakkında daha fazla bilgi için bkz. [nasıl yapılır: üretilen kod uyarılarını gösterme](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

> [!NOTE]
> Kod Analizi, tüm derlemeye veya tek bir parametreye uygulandığında `GeneratedCodeAttribute` yoksayar.

## <a name="global-level-suppressions"></a>Küresel düzeyde gizlemeler

Yönetilen Kod Analizi Aracı, derleme, modül, tür, üye veya parametre düzeyinde uygulanan `SuppressMessage` özniteliklerini inceler. Ayrıca, kaynaklara ve ad alanlarına karşı ihlalleri da tetikler. Bu ihlallerin genel düzeyde uygulanması ve kapsamı belirlenmiş ve hedeflenmiş olması gerekir. Örneğin, aşağıdaki ileti bir ad alanı ihlalini bastırır:

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> @No__t_0 kapsama sahip bir uyarıyı bastırdığınızda, bu uyarı ad alanının kendisine karşı bastırır. Ad uzayı içindeki türlere karşı uyarıyı göstermez.

Herhangi bir gizleme açık bir kapsam belirtilerek ifade edilebilir. Bu gizlemeler küresel düzeyde canlı olmalıdır. Bir tür dekorasyon yaparak üye düzeyinde gizleme belirtemezsiniz.

Genel düzey gizlemeler, açıkça sağlanmış Kullanıcı kaynağıyla eşleşmeyen derleyici tarafından üretilen koda başvuran iletileri göstermenin tek yoludur. Örneğin, aşağıdaki kod derleyiciye yayılan bir oluşturucuya karşı bir ihlalin bastırır:

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` her zaman tam olarak nitelenmiş öğe adını içerir.

## <a name="global-suppression-file"></a>Genel gizleme dosyası

Genel gizleme dosyası, bir hedef belirtmeyen küresel düzeyde gizlemeler veya gizlemeleri olan gizlemeleri korur. Örneğin, derleme düzeyi ihlallerin gizlemeleri bu dosyada depolanır. Ayrıca, bir form arkasındaki kod için proje düzeyi ayarları kullanılamadığından bazı ASP.NET gizlemeleri bu dosyada depolanır. **Hata listesi** penceresinde **Gizle** komutunun **Proje gizleme dosyasını** ilk kez seçtiğinizde, genel bir gizleme dosyası oluşturulur ve projenize eklenir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope>
- <xref:System.Diagnostics.CodeAnalysis>
- [Kod Çözümleyicileri kullanma](../code-quality/use-roslyn-analyzers.md)
