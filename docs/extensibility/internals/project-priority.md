---
title: Proje önceliği | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee4c0f41902e74f58684d6806877d352447351bf
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725390"
---
# <a name="project-priority"></a>Proje Önceliği
Proje öğesi genellikle çözümdeki yalnızca bir projenin üyesidir. Bu nedenle, IDE, öğeyi açmak için hangi projenin kullanıldığını kolayca belirleyebilir. Ancak, bir öğe birden fazla projenin üyesiyse, IDE, öğeyi açmak için en iyi projeyi belirlemede bir öncelik şeması kullanır.

 Aşağıdaki listede, proje öncelik şeması gösterilmektedir:

- IDE, belgenin o projenin bir üyesi olup olmadığını anlamak için çözümdeki her proje için <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> yöntemini çağırır.

- Belge projenin üyesiyse proje, projenin işleme göre atadığı bir öncelik ile yanıt verir. Örneğin, bir dil projesi kendi dil kaynak dosyaları için yüksek öncelikli olarak yanıt verir, ancak yapı sürecinin bir parçası olarak kullanılmayan tanınmayan bir dosya türü için daha düşük bir önceliğe sahip olur.

- Bir belge için özel, projeye özgü düzenleyiciler ve tasarımcılar sağlayan projeler de yüksek öncelikli bir öncelik alır.

- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> numaralandırması belge önceliği değerlerini sağlar.

- En yüksek önceliğe sahip projeye belgeyi açmak için bağlam verilir. İki proje eşit öncelik değeri getirse, etkin proje tercih edilir. Çözümdeki bir proje belgeyi açabiliyorsa yanıt verirse, IDE belgeyi çeşitli dosyalar projesine koyar. Daha fazla bilgi için bkz. [çeşitli dosyalar projesi](../../extensibility/internals/miscellaneous-files-project.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Çeşitli Dosyalar Projesi](../../extensibility/internals/miscellaneous-files-project.md)
- [Nasıl Yapılır: Açık Belgeler için Düzenleyicileri Açma](../../extensibility/how-to-open-editors-for-open-documents.md)
- [Proje ve Proje Öğesi Şablonları Ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)