---
title: UWP uygulamasını yenileme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- JavaScript debugging, refreshing pages [UWP apps]
- debugging, refreshing pages [UWP apps]
- DOM Explorer, Refresh [UWP apps]
- Refresh [UWP apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- uwp
ms.openlocfilehash: 0b1d19c0b607d2c5a09fddc9d4550230e478d57a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72730304"
---
# <a name="refresh-a-uwp-app-in-visual-studio"></a>Visual Studio 'da UWP uygulamasını yenileme

 Hata ayıklarken kodunuzda değişiklik yapabilir ve sonra **hata ayıklama** araç çubuğundaki **Windows uygulamasını Yenile** düğmesini seçerek bir UWP uygulamasını JavaScript kullanarak yenileyebilirsiniz. Bu düğmenin belirlenmesi, hata ayıklayıcıyı durdurup yeniden başlatmadan uygulamayı yeniden yükler. Yenile özelliği, HTML, CSS ve JavaScript kodunu değiştirmenize ve sonucu hızla görebilmenizi sağlar. Bu özellik UWP uygulamaları için desteklenir.

 Yenileme, uygulamanızın durumunu korumaz veya uygulamanızda aşağıdaki değişiklikleri yansıtmaz:

- Paket bildiriminde belirtilen görüntülerde yapılan değişiklikler dahil olmak üzere Paket bildirim dosyası değişiklikleri.

- Bir SDK başvurusu ekleme veya kaldırma veya Windows Çalışma Zamanı bileşenlerinde değişiklikler (. winmd dosyaları) gibi başvuru değişiklikleri.

- . Resjson dosyalarındaki dizelerdeki değişiklikler gibi kaynak değişiklikleri.

- Yol adı ile sonuçlanan proje dosyası değişiklikleri, yeni proje dosyaları veya silinen dosyalar.

- Seçilen hata ayıklama cihazında yapılan değişiklikler veya bir dosya için paket eyleminde yapılan değişiklikler gibi proje ve öğe özelliği değişiklikleri (Özellikler penceresi).

> [!IMPORTANT]
> Başvuruları değiştirdiğinizde, paket bildirimini değiştirdiğinizde veya yukarıdaki listede başka değişiklikler yaparsanız, HTML, CSS ve JavaScript kaynak dosyalarını güncelleştirmek için hata ayıklayıcıyı durdurup yeniden başlatmanız gerekir.

### <a name="to-refresh-an-app"></a>Bir uygulamayı yenilemek için

1. UWP projeniz Visual Studio 'da açıkken, hata ayıklama hedefi olarak **yerel makine** ' yi seçin.

     ![Hata ayıklama hedef listesini seçin](../debugger/media/js_select_target.png "JS_Select_Target")

3. Uygulamayı hata ayıklama modunda çalıştırmak için F5 tuşuna basın.

4. Visual Studio 'ya geçiş yapın.

5. UWP uygulamanızın giriş sayfasında, bazı HTML 'yi düzenleyin.

7. Windows uygulamasını **Yenile** düğmesine tıklayın ve şuna benzer: ![Windows uygulamasını Yenile düğmesi](../debugger/media/js_refresh.png "JS_Refresh"). (Veya F4 tuşuna basın.)

8. Uygulamaya geçiş yapın. Uygulama yeniden yüklenir ve güncelleştirilmiş HTML, uygulamayı işlemek için kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [Hızlı başlangıç: HTML ve CSS hatalarını ayıklama](../debugger/quickstart-debug-html-and-css.md)