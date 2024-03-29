---
title: 'Nasıl yapılır: gizli hata ayıklayıcı komutlarını geri yükleme | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, restoring commands
- debugging [Visual Studio], restoring commands
- commands, debugger
ms.assetid: 76ac9b77-f536-43b5-a9fc-984854b1c566
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a45791843abe3051bacb9655c773ac9dfc6b9045
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72732905"
---
# <a name="how-to-restore-hidden-debugger-commands"></a>Nasıl Yapılır: Gizli Hata Ayıklayıcı Komutlarını Geri Yükleme
Visual Studio 'yu ayarlarken, birincil programlama diliniz için bir varsayılan IDE ayarları kümesi seçmeniz istenir. Bazı diller için varsayılan IDE ayarları, bazı hata ayıklayıcı komutlarını gizleyebilir.

 Varsayılan IDE ayarlarınız tarafından gizlenen bir hata ayıklayıcı özelliğini kullanmak istiyorsanız, aşağıdaki yordamı kullanarak komutu menüye geri ekleyebilirsiniz.

### <a name="to-restore-hidden-debugger-commands"></a>Gizli hata ayıklayıcı komutlarını geri yüklemek için

1. Bir proje açıkken, **Araçlar** menüsünde **Özelleştir**' e tıklayın.

2. **Özelleştir** Iletişim kutusunda **Komutlar** sekmesine tıklayın.

3. **Menü çubuğunda: açılan menüsünde** , geri yüklenen komutu Içermesini Istediğiniz **hata ayıklama** menüsünü seçin.

4. **Komut Ekle...** düğmesine tıklayın.

5. **Ekle komut** kutusunda, eklemek istediğiniz komutu seçin ve **Tamam**' ı tıklatın.

6. Başka bir komut eklemek için önceki adımı tekrarlayın.

7. Menüye komut eklemeyi bitirdiğinizde **Kapat** ' a tıklayın.

    > [!WARNING]
    > Bazı menü öğeleri yalnızca hata ayıklayıcı çalışma modu veya kesme modu gibi belirli modlarda olduğunda görüntülenir. Bu nedenle, bu adımları tamamladığınızda eklediğiniz bir öğe hemen görünür olmayabilir.

## <a name="restoring-commands-not-available-from-the-customize-dialog-box"></a>Özelleştirme Iletişim kutusunda kullanılamayan komutları geri yükleme
 Özellikle hiyerarşik menülerde bulunan bazı komutlar, **Özelleştir** iletişim kutusundan geri yüklenemez. Bu komutları geri yüklemek için yeni bir IDE ayarları koleksiyonu içeri aktarmanız gerekir.

#### <a name="to-import-new-ide-settings"></a>Yeni IDE ayarlarını içeri aktarmak için

1. **Araçlar** menüsünde **Içeri ve dışarı aktarma ayarları**' na tıklayın.

2. **Ayarları içeri ve dışarı aktarma Sihirbazı 'Na hoş geldiniz** sayfasında, **Seçili ortam ayarlarını içeri aktar**' a tıklayın ve ardından **İleri**' ye tıklayın.

3. **Geçerli ayarları Kaydet** sayfasında, mevcut ayarlarınızın kaydedilip edilmeyeceğini belirleyin ve ardından **İleri**' ye tıklayın.

4. **İçeri aktarılacak ayarların bir koleksiyonunu seçin** sayfasında, **varsayılan ayarlar** klasörü altında kullanmak istediğiniz komutları içeren bir geliştirme ayarları koleksiyonu seçin. Hangi koleksiyonun seçeceğini görmüyorsanız, en çok hata ayıklayıcı komutlarını sağlayan **genel geliştirme ayarları** veya  **C++ görsel geliştirme ayarları**' nı deneyin.

5. **İleri**'ye tıklayın.

6. **İçeri aktarılacak ayarları seçin** sayfasında, **Seçenekler**altında, **hata ayıklamayı** seçtiğinizden emin olun. Bu ayarları da içeri aktarmak istemediğiniz sürece diğer onay kutularını temizleyin.

7. **Son**'a tıklayın.

8. **Içeri aktarma Tamam** sayfasında, **Ayrıntılar**altında ayarlarınızı sıfırlamayla ilişkili tüm hataları gözden geçirin.

9. **Kapat**'ı tıklatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklayıcısı Güvenliği](../debugger/debugger-security.md)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)