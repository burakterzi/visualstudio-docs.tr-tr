---
title: '9\. Adım: diğer özellikleri deneme'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 07c0a3e24ac089bf29501dfd4e101baef73318fb
ms.sourcegitcommit: 4f82de3fb0cfae226aef1abb40c47e63d2036a5c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919135"
---
# <a name="step-9-try-other-features"></a>9\. Adım: diğer özellikleri deneme
Daha fazla bilgi edinmek için simgeleri ve renkleri değiştirmeyi, oyun zamanlayıcısı ve sesler eklemeyi deneyin. Oyunu daha zorlu hale getirmek için tahtayı büyütmeyi ve zamanlayıcıyı ayarlamayı deneyin.

Örneğin tamamlanmış bir sürümünü indirmek için, bkz. [tüm eşleşen oyun öğreticisi örneği](https://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba).

## <a name="to-try-other-features"></a>Diğer özellikleri denemek için

- Simgelerin ve renklerin yerine kendi tercih ettiklerinizi kullanın.

    > [!TIP]
    > Etiketin [ForeColor](<xref:System.Windows.Forms.Control.ForeColor%2A>) özelliğine bakmaya çalışın.

- Oyuncunun oyunu kazanmasının ne kadar sürdüğünü izleyen bir oyun zamanlayıcısı ekleyin.

    > [!TIP]
    > Bunu yapmak için, <xref:System.Windows.Forms.TableLayoutPanel> üzerindeki formda geçen süreyi görüntüleyecek bir etiket ekleyebilirsiniz ve süreyi izlemek için forma başka bir zamanlayıcı ekleyebilirsiniz. Oyuncu oyuna başladığında zamanlayıcıyı başlatmak ve son iki simgeyi eşleştirdikten sonra zamanlayıcıyı durdurmak için kod kullanın.

- Oyuncu bir eşleşme bulduğunda çalacak bir ses, eşleşmeyen iki simgeyi açtığında çalacak başka bir ses ve program simgeleri yeniden gizlediğinde çalacak üçüncü bir ses ekleyin.

    > [!TIP]
    > Ses çalmak için <xref:System.Media> ad alanını kullanabilirsiniz. Daha fazla bilgi için bkz. [Windows FormsC#uygulamasında ses yürütme ()](https://www.youtube.com/watch?v=qOh4ooHg1UU&feature=youtu.be) veya [Visual Basic ses yürütme](https://www.youtube.com/watch?v=-4oPDeQrtMs&feature=youtu.be) .

- Oyun tahtasını büyüterek oyunu zorlaştırın.

    > [!TIP]
    > TableLayoutPanel 'e satırlar ve sütunlar eklemeniz yeterlidir. Ayrıca, oluşturduğunuz simge sayısını göz önünde bulundurmanız gerekir.

- Oyuncunun tepki verirken çok yavaş davranması ve belirli bir süre dolmadan önce ikinci simgeyi seçmemesi durumunda ilk simgeyi gizleyerek oyunu daha zorlu hale getirin.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Yararlanabileceğiniz harika ve ücretsiz video öğrenme kaynakları vardır. Visual Basic 'da programlama hakkında daha fazla bilgi için bkz. [Visual Basic temelleri: mutlak yeni başlayanlar Için geliştirme](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). İçinde C#programlama hakkında daha fazla bilgi edinmek için bkz [ C# . temel bilgiler: mutlak yeni başlayanlar için geliştirme](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

- Önceki öğretici adımına dönmek için bkz. 8. [Adım: oyuncunun kazandığını doğrulamak için yöntem ekleme](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).
