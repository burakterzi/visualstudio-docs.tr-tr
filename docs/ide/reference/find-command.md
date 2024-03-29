---
title: Bul Komutu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.find
helpviewer_keywords:
- Find command
- Edit.Find command
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ab914d62053b5cbefe92ee0ce8356c10dad82e6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748753"
---
# <a name="find-command"></a>Bul Komutu
**Bul ve Değiştir** penceresinin **dosyalarda bul** sekmesinde bulunan seçeneklerin bir alt kümesini kullanarak dosyaları arar.

## <a name="syntax"></a>Sözdizimi

```cmd
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]
```

## <a name="arguments"></a>Arguments
`findwhat` gerekiyor. Eşleştirilecek metin.

## <a name="switches"></a>Anahtarlar
/Case veya/C\
İsteğe bağlı. Eşleşmeler yalnızca, büyük harf ve küçük harf karakterlerinin `findwhat` bağımsız değişkeninde belirtilen olanlarla tam olarak eşleşmesi durumunda meydana gelir.

/doc veya/d\
İsteğe bağlı. Yalnızca geçerli belgeyi arar. Kullanılabilir arama kapsamlarından yalnızca birini belirtin, `/doc`, `/proc`, `/open` veya `/sel`.

/markall veya/M\
İsteğe bağlı. Geçerli belge içinde arama eşleşmesi içeren her satıra bir grafik koyar.

/Open veya/O\
İsteğe bağlı. Tüm açık belgeleri bir belge gibi arar. Kullanılabilir arama kapsamlarından yalnızca birini belirtin, `/doc`, `/proc`, `/open` veya `/sel`.

/Options veya/t \
İsteğe bağlı. Geçerli bulma seçeneği ayarlarının listesini görüntüler ve arama yapmaz.

/proc veya/p\
İsteğe bağlı. Yalnızca geçerli yordamı arar. Kullanılabilir arama kapsamlarından yalnızca birini belirtin, `/doc`, `/proc`, `/open` veya `/sel`.

/Reset süpürmeden veya/e\
İsteğe bağlı. Bulma seçeneklerini varsayılan ayarlarına döndürür ve arama yapmaz.

/sel veya/s\
İsteğe bağlı. Yalnızca geçerli seçimi arar. Kullanılabilir arama kapsamlarından yalnızca birini belirtin, `/doc`, `/proc`, `/open` veya `/sel`.

/up veya/U\
İsteğe bağlı. Dosyadaki geçerli konumdan dosyanın başlangıcına doğru arar. Varsayılan olarak, aramalar dosyadaki geçerli konumda başlar ve dosyanın sonuna doğru arar.

/Regex veya/r \
İsteğe bağlı. @No__t_0 bağımsız değişkeninde, sabit karakterler yerine metin desenlerini temsil eden gösterimler olarak önceden tanımlanmış özel karakterler kullanır. Normal ifade karakterlerinin tüm listesi için bkz. [normal ifadeler](../../ide/using-regular-expressions-in-visual-studio.md).

/joker veya/L\
İsteğe bağlı. Bir karakteri veya karakter dizisini göstermek için `findwhat` bağımsız değişkeninde gösterimler olarak önceden tanımlanmış özel karakterleri kullanır.

/Word veya/w\
İsteğe bağlı. Yalnızca tam sözcükleri arar.

## <a name="example"></a>Örnek
Bu örnek, kodun Şu anda seçili olan bölümünde "somestring" sözcüğü için büyük/küçük harfe duyarlı bir arama gerçekleştirir.

```cmd
>Edit.Find somestring /sel /case
```

## <a name="see-also"></a>Ayrıca bkz.

- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)