---
title: Hata ayıklama için bir .NET Framework sürümü belirtin | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1f6107d6396c6228be1d511e81003fbe7faf06c9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72732633"
---
# <a name="specify-an-older-net-framework-version-for-debugging-c-visual-basic-f"></a>Hata ayıklama için eski bir .NET Framework sürümü belirtinC#(, Visual Basic F#,)

Visual Studio hata ayıklayıcı, Microsoft .NET Framework 'ün eski sürümlerinin yanı sıra geçerli sürümü de hata ayıklamayı destekler. Visual Studio 'dan bir uygulama başlatırsanız hata ayıklayıcı, hata ayıklaması yaptığınız uygulamanın doğru .NET Framework sürümünü her zaman tanımlayabilir. Ancak, uygulama zaten çalışıyorsa ve **iliştirme 'yi**kullanarak hata ayıklamayı başlatırsanız, hata ayıklayıcı .NET Framework eski bir sürümünü her zaman tanımlayamayabilir. Bu durumda, şöyle bir hata iletisi alırsınız.

``` cmd
The debugger has made an incorrect assumption about the .NET Framework version your application is going to use.
```

Bu hatanın göründüğü nadir durumlarda, bir kayıt defteri anahtarını, hangi sürümün kullanılacağı hata ayıklayıcıya göstermek için ayarlayabilirsiniz.

### <a name="to-specify-a-net-framework-version-for-debugging"></a>Hata ayıklama için bir .NET Framework sürümünü belirtmek için

1. Makinenizde yüklü .NET Framework sürümlerini bulmak için Windows\Microsoft.NET\Framework dizinine bakın. Sürüm numaraları şuna benzer:

    `V1.1.4322`

    Doğru sürüm numarasını belirleyip bunu bir yere göz önünde yapın.

2. **Kayıt defteri Düzenleyicisi 'ni** (regedit) başlatın.

3. **Kayıt defteri Düzenleyicisi**'NDE, HKEY_LOCAL_MACHINE klasörünü açın.

4. Şuraya gidin: HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine \\ {449EC4CC-30D2-4032-9256-EE18EB41B62B}

    Anahtar yoksa, HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine öğesine sağ tıklayın ve **Yeni anahtar**' a tıklayın. Yeni anahtarı `{449EC4CC-30D2-4032-9256-EE18EB41B62B}` adlandırın.

5. {449EC4CC-30D2-4032-9256-EE18EB41B62B} sayfasına gittikten sonra **ad** sütununa bakın ve CLRVersionForDebugging anahtarını bulun.

   1. Anahtar yoksa, {449EC4CC-30D2-4032-9256-EE18EB41B62B} öğesine sağ tıklayın ve **Yeni dize değeri**' ne tıklayın. Ardından yeni dize değerine sağ tıklayın, **Yeniden Adlandır**' a tıklayın ve `CLRVersionForDebugging` yazın.

6. **CLRVersionForDebugging**öğesine çift tıklayın.

7. **Dize Düzenle** kutusuna **değer** kutusuna .NET Framework sürüm numarasını yazın. Örneğin: V 1.1.4322

8. **Tamam**'a tıklayın.

9. **Kayıt defteri düzenleyicisini**kapatın.

     Hata ayıklamaya başladığınızda yine de bir hata iletisi alırsanız, sürüm numarasını kayıt defterine doğru girdiğinizden emin olun. Ayrıca, Visual Studio tarafından desteklenen .NET Framework bir sürümünü kullandığınızı doğrulayın. Hata ayıklayıcı geçerli .NET Framework sürümü ve önceki sürümlerle uyumludur, ancak gelecekteki sürümlerle uyumlu olmayabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklayıcısı Ayarları ve Hazırlığı](../debugger/debugger-settings-and-preparation.md)