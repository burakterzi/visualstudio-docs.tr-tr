---
title: Veri bağlantılı denetimler için açıklamalı alt yazıları özelleştirme
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 932d50d44fbfaa810225ef90c2f5361bc26d9b72
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648563"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Visual Studio'nun verilere bağlı denetimler için başlık oluşturma biçimini özelleştirme

Öğeleri [veri kaynakları penceresinden](add-new-data-sources.md#data-sources-window) bir tasarımcıya sürüklediğinizde, yürütmeye özel bir göz önünde bulundurun: başlık etiketlerindeki sütun adları, iki veya daha fazla sözcük birlikte art arda kaydırıldığında daha okunabilir bir dizeye yeniden biçimlendirilir.

::: moniker range="vs-2017"

HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0 içinde **SmartCaptionExpression**, **smartcaptiondeğişim**ve **SmartCaptionSuffix** değerlerini ayarlayarak bu etiketlerin oluşturulma biçimini özelleştirebilirsiniz.  **\Data tasarımcıları** kayıt defteri anahtarı.

::: moniker-end

::: moniker range=">=vs-2019"

HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0 içinde **SmartCaptionExpression**, **smartcaptiondeğişim**ve **SmartCaptionSuffix** değerlerini ayarlayarak bu etiketlerin oluşturulma biçimini özelleştirebilirsiniz.  **\Data tasarımcıları** kayıt defteri anahtarı.

::: moniker-end

> [!NOTE]
> Bu kayıt defteri anahtarı siz oluşturana kadar yok.

Akıllı resim yazısı, **SmartCaptionExpression** değerinin değerine girilen normal ifade tarafından denetlenir. **Veri tasarımcıları** kayıt defteri anahtarı eklendiğinde, Başlık etiketlerini denetleyen varsayılan normal ifade geçersiz kılınır. Normal ifadeler hakkında daha fazla bilgi için bkz. [Visual Studio 'da normal Ifadeler kullanma](../ide/using-regular-expressions-in-visual-studio.md).

Aşağıdaki tabloda, Başlık etiketlerini denetleyen kayıt defteri değerleri açıklanmaktadır.

|Kayıt defteri öğesi|Açıklama|
|-------------------|-----------------|
|**Smartcaptionifadesi**|Desenlerinizi eşleştirmek için kullandığınız normal ifade.|
|**Smartcaptiondeğiştirme**|**SmartCaptionExpression**ile eşleşen grupları görüntüleme biçimi.|
|**SmartCaptionSuffix**|Açıklamalı alt yazısının sonuna eklenecek isteğe bağlı bir dize.|

Aşağıdaki tabloda, bu kayıt defteri değerleri için iç varsayılan ayarlar listelenmektedir.

|Kayıt defteri öğesi|Varsayılan değer|Açıklama|
|-------------------|-------------------|-----------------|
|**Smartcaptionifadesi**|**(\\ \p{Ll}) (\\ \p{Lu}) &#124;_+**|Küçük bir karakterle ve ardından büyük bir karakter veya alt çizgi ile eşleşir.|
|**Smartcaptiondeğiştirme**|**$1 $2**|**$1** , ifadenin ilk parantezleri ile eşleşen tüm karakterleri temsil eder ve **$2** ikinci parantez içinde eşleşen tüm karakterleri temsil eder. Değiştirme ilk eşleşme, bir boşluk ve ikinci eşleşmedir.|
|**SmartCaptionSuffix**|**:**|Döndürülen dizeye eklenen bir karakteri temsil eder. Örneğin, başlık `Company Name` ise, sonek bunu yapar `Company Name:`|

> [!CAUTION]
> Kayıt defteri düzenleyicisinde herhangi bir şey yaparken çok dikkatli olun. Düzenlemeden önce kayıt defterini yedekleyin. Kayıt Defteri Düzenleyicisi 'Ni yanlış kullanırsanız, işletim sisteminizi yeniden yüklemenizi gerektirebilecek önemli sorunlara neden olabilirsiniz. Microsoft, kayıt defteri düzenleyicisini yanlış kullanarak neden olan sorunların çözümlenemeyeceğini garanti etmez. Kayıt Defteri Düzenleyicisi'ni kullanım riski size aittir.
>
> Kayıt defterini yedekleme, düzenlemesi ve geri yükleme hakkında bilgi için bkz. [Gelişmiş kullanıcılar Için Windows kayıt defteri bilgileri](https://support.microsoft.com/help/256986/windows-registry-information-for-advanced-users).

## <a name="modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Veri kaynakları penceresinin akıllı açıklamalı alt yazı davranışını değiştirme

1. **Başlat** ' a ve ardından **Çalıştır**' a tıklayarak bir komut penceresi açın.

2. **Çalıştır** iletişim kutusuna `regedit` yazın ve **Tamam**' a tıklayın.

3. **HKEY_CURRENT_USER**  > **Software**  > **Microsoft**  > **VisualStudio** düğümünü genişletin.

::: moniker range="vs-2017"

4. **15,0** düğümüne sağ tıklayın ve `Data Designers` adlı yeni bir **anahtar** oluşturun.

::: moniker-end

::: moniker range=">=vs-2019"

4. **16,0** düğümüne sağ tıklayın ve `Data Designers` adlı yeni bir **anahtar** oluşturun.

::: moniker-end

5. **Veri tasarımcıları** düğümüne sağ tıklayın ve üç yeni dize değeri oluşturun:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. **SmartCaptionExpression** değerine sağ tıklayın ve **Değiştir**' i seçin.

7. **Veri kaynakları** penceresinin kullanmasını istediğiniz normal ifadeyi girin.

8. **Smartcaptiondeğiştirme** değerine sağ tıklayın ve **Değiştir**' i seçin.

9. Normal ifadenizde eşleşen desenleri göstermek istediğiniz şekilde biçimlendirilen değiştirme dizesini girin.

10. **SmartCaptionSuffix** değerine sağ tıklayın ve **Değiştir**' i seçin.

11. Resim yazısının sonunda görünmesini istediğiniz karakterleri girin.

    Öğeleri **veri kaynakları** penceresinden bir dahaki sefer sürüklediğinizde, başlık etiketleri, belirtilen yeni kayıt defteri değerleri kullanılarak oluşturulur.

## <a name="turn-off-the-smart-captioning-feature"></a>Akıllı resim yazısı özelliğini kapatma

1. **Başlat** ' a ve ardından **Çalıştır**' a tıklayarak bir komut penceresi açın.

2. **Çalıştır** iletişim kutusuna `regedit` yazın ve **Tamam**' a tıklayın.

3. **HKEY_CURRENT_USER**  > **Software**  > **Microsoft**  > **VisualStudio** düğümünü genişletin.

::: moniker range="vs-2017"

4. **15,0** düğümüne sağ tıklayın ve `Data Designers` adlı yeni bir **anahtar** oluşturun.

::: moniker-end

::: moniker range=">=vs-2019"

4. **16,0** düğümüne sağ tıklayın ve `Data Designers` adlı yeni bir **anahtar** oluşturun.

::: moniker-end

5. **Veri tasarımcıları** düğümüne sağ tıklayın ve üç yeni dize değeri oluşturun:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. **SmartCaptionExpression** öğesine sağ tıklayın ve **Değiştir**' i seçin.

7. Değer için `(.*)` girin. Bu, tüm dizeyle eşleşir.

8. **Smartcaptiondeðiþtirme** öğesine sağ tıklayın ve **Değiştir**' i seçin.

9. Değer için `$1` girin. Bu, dizeyi, değiştirilmeden kalacak şekilde tüm dize olan eşleşen değerle değiştirir.

    Öğeleri **veri kaynakları** penceresinden bir dahaki sefer sürüklediğinizde, resim yazısı etiketleri değiştirilmemiş açıklamalı alt yazılar ile oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)