---
title: XML Belge Özellikleri, Özellik Penceresi
ms.date: 03/05/2019
ms.topic: reference
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99102248a9456de3a2b3aeba28e54de4299fae40
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604152"
---
# <a name="xml-document-properties-properties-window"></a>XML belgesi özellikleri, Özellikler penceresi

**Özellikler** PENCERESI, XML düzenleyicisinde etkin olan belge hakkında temel bilgiler sağlar. Kullanılabilir özellikler, şu anda etkin olan XML belgesinin türüne bağlı olarak değişir.

> [!NOTE]
> Tüm XML belgesi özellikleri çözüme kaydedilir. Sonuç olarak, çözümü bir sonraki açışınızda bu değerleri yeniden girmeniz gerekmez.

**Şifreleme**

Dosya için karakter kodlaması. Bu özelliğin değiştirilmesi, XML bildiriminde kodlama özniteliğini de değiştirir ve tam tersi de geçerlidir. Yeni kodlama dosyayı kaydettiğinizde dosyayı kodlamak için kullanılır.

**Giriş**

XSLT stil sayfasıyla ilişkili giriş belgesi. **Başlangıç XSLT** komutları tarafından kullanılır, örneğin, **XML**  > ,**XSLT 'yi hata ayıklama olmadan başlatır**. Bir belge, gezinme ( **...** ) düğmesi kullanılarak seçilebilir.

Bu özellik yalnızca düzenleyicide bir XSLT dosyası açıkken görünür.

**Output**

Bir XML belgesi dönüştürülürken oluşturulan dosya.

Bir dosya belirtilmemişse, dosya uzantısını belirleyen `xsl:output` öğesindeki `method` özniteliğe göre varsayılan bir dosya adı oluşturulur. Varsayılan dosya, geçerli kullanıcının geçici dizininde bulunur.

**Şemaları**

Doğrulama için kullanılacak şemalar. Düğme, kullanılacak şemaları seçmek için kullanılabilecek **xsd şemaları** iletişim kutusunu açar.

Ayrıca, şemaların yolunu da girebilirsiniz. Birden çok şema belirtilirse, her şema yolunun çift tırnak içine alınması gerekir.

**Larýnda**

**XSLT hata ayıklamayı Başlat** ve **XSLT 'yi hata ayıklama komutları olmadan Başlat** kullanıldığında BELGEYI dönüştürmek için kullanılan XSLT dosyası kullanılır. Bu alan boşsa, düzenleyici belgenin `xml-stylesheet` işleme yönergesinde belirtilen değeri kullanır veya bir dosya adı ister.

XSLT dosyası düzenlenirken, bu özellik, **XSLT hata ayıklamayı Başlat** veya **XSLT 'yi hata ayıklama komutu olmadan Başlat** seçiliyken farklı bir stil sayfasının kullanılması gerektiğini belirtmek için kullanılabilir. Örneğin, bir üst stil sayfasına dahil olan bir stil sayfasını düzenlediğinizde bunu yapmak isteyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [XML Düzenleyicisi](../xml-tools/xml-editor.md)