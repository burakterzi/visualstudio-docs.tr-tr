---
title: Komut Penceresi
ms.date: 02/25/2019
ms.topic: reference
dev_langs:
- VB
f1_keywords:
- VS.ImmediateWindow
helpviewer_keywords:
- design-time expression evaluation
- Immediate window
- first-chance exception notifications
ms.assetid: d33e7937-73f3-4c69-9df0-777a8713c6f2
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa5f804c22090fa79586549db00b13d824a54690
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662537"
---
# <a name="immediate-window"></a>Komut penceresi

İfadeleri hata ayıklamak ve değerlendirmek, deyimleri yürütmek ve değişken değerlerini yazdırmak için **hemen** penceresini kullanın. **Komut** penceresi, şu anda seçili olan projeyi oluşturup kullanarak ifadeleri değerlendirir.

**Hemen** penceresini göstermek için, bir projeyi düzenlenmek üzere açın ve ardından **hata ayıkla**  > **Windows**  > **hemen** seçin ya da **CTRL** +**alt** +**I**tuşlarına basın. Ayrıca, **komut** penceresinde **hata ayıkla. hemen** girebilirsiniz.

**Komut** penceresi IntelliSense 'i destekler.

## <a name="display-the-values-of-variables"></a>Değişkenlerin değerlerini görüntüleme

Bir uygulamanın hatalarını ayıklarken, **komut** penceresi özellikle faydalıdır. Örneğin, bir değişken `varA` değerini denetlemek için [Print komutunu](../../ide/reference/print-command.md)kullanabilirsiniz:

```cmd
>Debug.Print varA
```

Soru işareti (?) `Debug.Print` için bir diğer addır, bu nedenle bu komut de yazılabilir:

```cmd
? varA
```

Bu komutun her iki sürümü de `varA` değişkenin değerini döndürür.

> [!TIP]
> **Hemen** penceresinde bir Visual Studio komutu vermek için, komutun işaretini büyüktür işareti (>) ile önceden başlatmalısınız. Birden çok komut girmek için [komut penceresi](command-window.md)geçin.

## <a name="design-time-expression-evaluation"></a>Tasarım zamanı ifade değerlendirmesi

Tasarım zamanında bir işlevi veya alt yordamı yürütmek için **hemen** penceresini kullanabilirsiniz.

### <a name="execute-a-function-at-design-time"></a>Tasarım zamanında işlev yürütme

1. Aşağıdaki kodu bir Visual Basic konsol uygulamasına kopyalayın:

   ```vb
   Module Module1

       Sub Main()
           MyFunction(5)
       End Sub

       Function MyFunction(ByVal input as Integer) As Integer
           Return input * 2
       End Function

   End Module
   ```

2. **Hata Ayıkla** menüsünde **Windows**  > **hemen**' ni seçin.

3. **Hemen** penceresine `?MyFunction(2)` yazın ve **ENTER**tuşuna basın.

    **Komut** penceresi `MyFunction` çalışır ve `4` görüntüler.

İşlev veya alt yordam bir kesme noktası içeriyorsa, Visual Studio uygun noktada yürütmeyi keser. Daha sonra program durumlarınızı incelemek için hata ayıklayıcı pencerelerini kullanabilirsiniz. Daha fazla bilgi için bkz. [Izlenecek yol: tasarım zamanında hata ayıklama](../../debugger/walkthrough-debugging-at-design-time.md).

Office projeleri, Web projeleri, akıllı cihaz projeleri ve SQL projeleri için Visual Studio Araçları dahil olmak üzere bir yürütme ortamının başlatılması gereken proje türlerinde tasarım zamanı ifade değerlendirmesi kullanamazsınız.

### <a name="design-time-expression-evaluation-in-multi-project-solutions"></a>Çoklu proje çözümlerinde tasarım zamanı ifade değerlendirmesi

Tasarım zamanı ifade değerlendirmesi için bağlam oluştururken, Visual Studio Çözüm Gezgini Şu anda seçili olan projeye başvurur. Çözüm Gezgini bir proje seçilmezse, Visual Studio işlevi başlangıç projesine göre değerlendirmeye çalışır. İşlev geçerli bağlamda değerlendirilemez, bir hata iletisi alırsınız. Bir projede çözüm için başlangıç projesi olmayan bir işlevi değerlendirmeye çalışıyorsanız ve bir hata alırsanız, Çözüm Gezgini ' de projeyi seçip değerlendirmeyi yeniden deneyin.

## <a name="enter-commands"></a>Komutları girin

Visual Studio komutlarını **komut** penceresinde verirken büyüktür işaretini (>) girin. Daha önce kullandığınız komutlarınız arasında gezinmek için **yukarı ok** ve **aşağı ok** tuşlarını kullanın.

|Görev|Çözüm|Örnek|
|----------|--------------|-------------|
|Bir ifadeyi değerlendirin.|İfadeyi bir soru işaretiyle (?) önyüz.|`? a+b`|
|Komut modunu anında modda (tek bir komut yürütmek için) geçici olarak girin.|Komutu, işareti daha büyük (>) ile önceden girerek girin.|`>alias`|
|Komut penceresi geçin.|Pencereye daha büyük (>) işaretiyle `cmd` girin.|`>cmd`|
|Anında pencereye geri dönün.|@No__t_0, büyüktür işareti (>) olmadan pencereye girin.|`immed`|

## <a name="mark-mode"></a>İşaret modu

**Hemen** penceredeki herhangi bir önceki satıra tıkladığınızda, işaret moduna otomatik olarak kaydırma yapabilirsiniz. Bu, herhangi bir metin düzenleyicisinde yaptığınız gibi önceki komutların metnini seçmenizi, düzenlemenizi ve kopyalamanızı sağlar ve bunları geçerli satıra yapıştırabilirsiniz.

## <a name="examples"></a>Örnekler

Aşağıdaki örnek, bir Visual Basic projesi için en çok dört ifadeyi ve **Bu penceredeki sonuçları** gösterir.

```cmd
j = 2
Expression has been evaluated and has no value

? j
2

j = DateTime.Now.Day
Expression has been evaluated and has no value

? j
26
```

## <a name="first-chance-exception-notifications"></a>Birinci şans özel durum bildirimleri

Bazı ayar yapılandırmalarında, ilk şans özel durum bildirimleri **komut** penceresinde görüntülenir.

### <a name="toggle-first-chance-exception-notifications-in-the-immediate-window"></a>İlk şans özel durum bildirimlerini hemen pencerede aç

1. **Görünüm** menüsünde **diğer pencereler**' e tıklayın ve **Çıkış**' a tıklayın.

2. **Çıkış** penceresinin metin alanına sağ tıklayın ve ardından **özel durum iletileri**' ni seçin veya seçimini kaldırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklayıcısı ile Kodlarda gezinme](../../debugger/navigating-through-code-with-the-debugger.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Hata ayıklayıcıya ilk bakış](../../debugger/debugger-feature-tour.md)
- [İzlenecek Yol: Tasarım Zamanında Hata Ayıklama](../../debugger/walkthrough-debugging-at-design-time.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
- [Visual Studio'da Normal İfadeler Kullanma](../../ide/using-regular-expressions-in-visual-studio.md)
