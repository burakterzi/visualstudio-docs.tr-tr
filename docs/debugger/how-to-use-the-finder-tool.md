---
title: 'Nasıl yapılır: Bulucu aracını kullanma | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Window Finder Tool
ms.assetid: 5841926b-08c3-4e43-88bd-4223d04f9aef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f96fe87137c6b14e32fb2648e93c54a1c5b094a0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72732171"
---
# <a name="how-to-use-the-finder-tool"></a>Nasıl yapılır: Bulucu Aracı Kullanma
Pencere özelliklerini veya iletilerini göstermek için **pencereyi bul** Iletişim kutusunda Bulucu aracını kullanabilirsiniz. Finder aracı devre dışı bırakılan alt pencereleri de bulabilir ve devre dışı bırakılan alt pencereler çakıştığında, hangi pencerenin vurgulanmasını ayırt edebilir.

 ![&#43; Spy&#43; pencereyi bul iletişim kutusu](../debugger/media/icon_spy--_find.png "Icon_Spy + + _Bul") Pencereyi bul iletişim kutusunda Bulucu aracı

 Yukarıdaki şekilde, aşağıdaki adım 3 ' ten sonra pencere bul iletişim kutusu gösterilmektedir.

### <a name="to-display-window-properties-or-messages"></a>Pencere özelliklerini veya iletilerini görüntüleme

1. Windows 'larınızı hem Spy + + hem de hedef pencere görünür olacak şekilde düzenleyin.

2. **Spy** menüsünde **pencereyi bul**' u seçin.

    [Pencereyi bul Iletişim kutusu](../debugger/find-window-dialog-box.md) açılır.

3. **Bulucu aracını** hedef pencerenin üzerine sürükleyin.

    Aracı sürüklerken, **pencereyi bul** iletişim kutusu seçili penceredeki ayrıntıları görüntüler.

   - veya

     İncelemek istediğiniz pencerenin işleyicisine sahipseniz (örneğin, hata ayıklayıcıdan kopyalanmış), bunu **tanıtıcı** metin kutusuna yazın.

   > [!TIP]
   > Ekran dağınıklığını azaltmak için Spy 'ı **Gizle** seçeneğini belirleyin. Bu seçenek, ana Spy + + penceresini gizleme ve yalnızca diğer uygulamalarınızın üzerine görünen **pencereyi bul** iletişim kutusunu bırakır. **Tamam** ' ı veya **iptal**' i tıklattığınızda veya **Spy + +** seçeneğini belirlediğinizde, Spy + + ana penceresi geri yüklenir.

4. **Göster**altında **Özellikler** veya **iletiler**' i seçin.

5. **Tamam**'a basın.

    **Özellikler**' i seçtiyseniz [Pencere özellikleri iletişim kutusu](../debugger/window-properties-dialog-box.md) açılır. **İletiler**' i seçtiyseniz, bir [iletiler görünümü](../debugger/messages-view.md) penceresi açılır.

## <a name="see-also"></a>Ayrıca bkz.
- [Spy++ Görünümleri](../debugger/spy-increment-views.md)
- [Spy++ kullanma](../debugger/using-spy-increment.md)
- [Spy++ Başvurusu](../debugger/spy-increment-reference.md)