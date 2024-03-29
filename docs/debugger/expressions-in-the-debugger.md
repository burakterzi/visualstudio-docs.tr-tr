---
title: Hata Ayıklayıcıdaki İfadeler | Microsoft Docs
ms.date: 02/07/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.expressions
helpviewer_keywords:
- expressions [debugger]
- debugging [Visual Studio], expressions
- expression evaluation, debugger evaluator
- native expression evaluation
- expression evaluators
- debugger, evaluating expressions
- debugging [Visual Studio], expression evaluation
- debugging [Visual Studio], variable evaluation
ms.assetid: 70f9b531-44c7-4d77-980d-5eddbf2bff41
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6040988961e918c66ed08e7620607d100b2e07fe
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736209"
---
# <a name="expressions-in-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcısındaki ifadeler
Visual Studio hata ayıklayıcı, **QuickWatch** iletişim kutusunda, **Gözcü** penceresinde veya **anında** pencereye bir ifade girdiğinizde çalışan ifade değerlendiricileri içerir. Değerlendiricileri ifadesi Ayrıca **kesme noktaları** penceresinde ve hata ayıklayıcıda birçok diğer yerde de çalışır.

Aşağıdaki bölümlerde, Visual Studio tarafından desteklenen diller için ifade değerlendirmesinin sınırlamaları açıklanmaktadır.

## <a name="f-expressions-are-not-supported"></a>F#ifadeler desteklenmiyor
F#ifadeler tanınmıyor. Kod hata ayıklaması F# yapıyorsanız, ifadeleri bir hata ayıklayıcı penceresine veya iletişim kutusuna C# girmeden önce ifadelerinizi sözdizimine çevirmeniz gerekir. İfadelerini F# C#' den ' a çevirirken, tek`=`C# F# kullandığında eşitlik için test etmek üzere`==`işlecini kullandığını unutmayın.

## <a name="c-expressions"></a>C++İfadelerde
İçindeki C++ifadelerle bağlam işleçlerini kullanma hakkında daha fazla bilgi için bkz. [Bağlam işleciC++()](../debugger/context-operator-cpp.md).

### <a name="unsupported-expressions-in-c"></a>İçinde desteklenmeyen IfadelerC++

#### <a name="constructors-destructors-and-conversions"></a>Oluşturucular, Yıkıcılar ve dönüştürmeler
Açıkça veya örtük olarak bir nesne için bir Oluşturucu ya da yıkıcı çağrılamaz. Örneğin, aşağıdaki ifade açıkça bir oluşturucuyu çağırır ve bir hata iletisiyle sonuçlanır:

```C++
my_date( 2, 3, 1985 )
```

Dönüştürmenin hedefi bir sınıf ise, bir dönüştürme işlevi çağrılamaz. Böyle bir dönüştürme bir nesnenin oluşturulmasını içerir. Örneğin, `myFraction` dönüştürme işlevi işleci `FixedPoint`tanımlayan `CFraction`bir örneğidir, aşağıdaki ifade bir hatayla sonuçlanır:

```C++
(FixedPoint)myFraction
```

New veya delete işleçlerini çağrılamaz. Örneğin, aşağıdaki ifade desteklenmez:

```C++
new Date(2,3,1985)
```

#### <a name="preprocessor-macros"></a>Önişlemci makroları
Önişlemci makroları hata ayıklayıcıda desteklenmez. Örneğin, bir sabit `VALUE` şöyle bildirilirse: `#define VALUE 3`, **izleme** penceresinde `VALUE` kullanamazsınız. Bu sınırlamayı önlemek için `#define`, mümkün olan her durumda Enum ve işlevlerle değiştirmelisiniz.

### <a name="using-namespace-declarations"></a>ad alanı bildirimlerini kullanma
`using namespace` bildirimleri kullanamazsınız.  Geçerli ad alanı dışındaki bir tür adına veya değişkenine erişmek için tam adı kullanmanız gerekir.

### <a name="anonymous-namespaces"></a>Anonim ad alanları
Anonim ad alanları desteklenmez. Aşağıdaki koda sahipseniz, izleme penceresine `test` ekleyemezsiniz:

```C++
namespace mars
{
    namespace
    {
        int test = 0;
    }
}
int main()
{
    // Adding a watch on test does not work.
    mars::test++;
    return 0;
}

```

### <a name="BKMK_Using_debugger_intrinisic_functions_to_maintain_state"></a>Durumu korumak için hata ayıklayıcı iç işlevlerini kullanma
Hata ayıklayıcı iç işlevleri, uygulamanın durumunu değiştirmeden ifadelerde belirli C/C++ işlevleri çağırmak için bir yol sağlar.

Hata ayıklayıcı iç işlevleri:

- Güvenli olduğu garanti edilir: bir hata ayıklayıcı iç işlevinin yürütülmesi, hataları ayıklanan işlemi bozmaz.

- Yan etkileri ve işlev değerlendirmesinin izin verilmediği senaryolarda bile tüm ifadelerde izin verilir.

- Bir mini döküm dosyasında hata ayıklama gibi normal işlev çağrılarının mümkün olmadığı senaryolarda çalışın.

  Hata ayıklayıcı iç işlevleri ayrıca değerlendirme ifadelerin daha kullanışlı olmasını sağlayabilir. Örneğin, `strncmp(str, "asd")` kesme noktasında `str[0] == 'a' && str[1] == 's' && str[2] == 'd'`daha kolay yazılması çok daha kolaydır. )

|Alan|İç işlevler|
|----------|-------------------------|
|**Dize uzunluğu**|strlen, wcslen, strnlen, wcsnlen|
|**Dize karşılaştırması**|strcmp, wcscmp, stricmp, _stricmp, _strcmpi, wcsıcmp, _wcscmpi, _wcsnıcmp, strncmp, wcsncmp, strnıcmp, wcsnıcmp|
|**Dize arama**|strchr, wcschr, strstr, wcsstr|
|**Win**|GetLastError (), TlsGetValue ()|
|**Windows 8**|WindowsGetStringLen (), Windowsgetstrıngrawbuffer ()<br /><br /> Bu işlevler, hata ayıklamakta olan işlemin Windows 8 üzerinde çalışıyor olmasını gerektirir. Windows 8 cihazından oluşturulan döküm dosyalarının hata ayıklaması, Visual Studio bilgisayarının Windows 8 çalıştırıyor olmasını da gerektirir. Ancak, Windows 8 cihazının uzaktan hata ayıklaması yapıyorsanız, Visual Studio bilgisayarı Windows 7 çalıştırıyor olabilir.|
|**Malın**|__log2<br /><br /> Belirtilen bir tamsayının, en yakın küçük tamsayıya yuvarlanmış olan günlük 2 değerini döndürür.|

## <a name="ccli---unsupported-expressions"></a>C++/CLı-desteklenmeyen Ifadeler

- İşaretçileri veya Kullanıcı tanımlı yayınları içeren yayınlar desteklenmez.

- Nesne karşılaştırma ve atama desteklenmiyor.

- Aşırı yüklenmiş işleçler ve aşırı yüklenmiş işlevler desteklenmez.

- Kutulama ve kutudan çıkarma desteklenmez.

- `Sizeof` işleci desteklenmiyor.

## <a name="c---unsupported-expressions"></a>C#-Desteklenmeyen Ifadeler

### <a name="dynamic-objects"></a>Dinamik nesneler
Statik olarak dinamik olarak yazılan hata ayıklayıcı ifadelerinde değişkenleri kullanabilirsiniz. <xref:System.Dynamic.IDynamicMetaObjectProvider> uygulayan nesneler izleme penceresi değerlendirildiğinde dinamik bir görünüm düğümü eklenir. Dinamik görünüm düğümü nesne üyelerini gösterir ancak üyelerin değerlerini düzenlememe izin vermez.

Dinamik nesnelerin aşağıdaki özellikleri desteklenmez:

- Bileşik işleçler `+=`, `-=`, `%=`, `/=`ve `*=`

- Sayısal yayınlar ve tür bağımsız değişken yayınları dahil olmak üzere çok sayıda yayını

- İkiden fazla bağımsız değişkenle Yöntem çağrıları

- İkiden fazla bağımsız değişkene sahip Özellik alıcıları

- Bağımsız değişkenlerle özellik ayarlayıcıları

- Dizin oluşturucuya atama

- `&&` ve `||` Boole işleçleri

### <a name="anonymous-methods"></a>Anonim Yöntemler
Yeni anonim yöntemlerin oluşturulması desteklenmez.

## <a name="visual-basic---unsupported-expressions"></a>Visual Basic-desteklenmeyen Ifadeler

### <a name="dynamic-objects"></a>Dinamik nesneler
Statik olarak dinamik olarak yazılan hata ayıklayıcı ifadelerinde değişkenleri kullanabilirsiniz. <xref:System.Dynamic.IDynamicMetaObjectProvider> uygulayan nesneler izleme penceresi değerlendirildiğinde dinamik bir görünüm düğümü eklenir. Dinamik görünüm düğümü nesne üyelerini gösterir ancak üyelerin değerlerini düzenlememe izin vermez.

Dinamik nesnelerin aşağıdaki özellikleri desteklenmez:

- Bileşik işleçler `+=`, `-=`, `%=`, `/=`ve `*=`

- Sayısal yayınlar ve tür bağımsız değişken yayınları dahil olmak üzere çok sayıda yayını

- İkiden fazla bağımsız değişkenle Yöntem çağrıları

- İkiden fazla bağımsız değişkene sahip Özellik alıcıları

- Bağımsız değişkenlerle özellik ayarlayıcıları

- Dizin oluşturucuya atama

- `&&` ve `||` Boole işleçleri

### <a name="local-constants"></a>Yerel sabitler
Yerel sabitler desteklenmez.

### <a name="import-aliases"></a>Diğer adları içeri aktar
İçeri aktarma diğer adları desteklenmez.

### <a name="variable-declarations"></a>Değişken bildirimleri
Hata ayıklayıcı Windows 'da açık yeni değişkenler bildiremezsiniz. Bununla birlikte, **hemen** penceresi içinde yeni örtük değişkenler atayabilirsiniz. Bu örtük değişkenler hata ayıklama oturumunun kapsamına alınır ve hata ayıklayıcının dışında erişilebilir değildir. Örneğin, `o = 5` örtük olarak `o` yeni bir değişken oluşturur ve 5 değerini bu değere atar. Türü hata ayıklayıcı tarafından çıkarsanmadığı takdirde bu tür örtük değişkenler **Object** türündedir.

### <a name="unsupported-keywords"></a>Desteklenmeyen anahtar sözcükler

- `AddressOf`

- `End`

- `Error`

- `Exit`

- `Goto`

- `On Error`

- `Resume`

- `Return`

- `Select/Case`

- `Stop`

- `SyncLock`

- `Throw`

- `Try/Catch/Finally`

- `With`

- `End Sub` veya `Module`gibi ad alanı veya modül düzeyi anahtar sözcükleri.

## <a name="see-also"></a>Ayrıca bkz.
- [C++ Dilinde Biçim Belirticileri](../debugger/format-specifiers-in-cpp.md)
- [Bağlam İşleci (C++)](../debugger/context-operator-cpp.md)
- [C# Dilinde Biçim Belirticileri](../debugger/format-specifiers-in-csharp.md)
- [Sözde değişkenler](../debugger/pseudovariables.md)
