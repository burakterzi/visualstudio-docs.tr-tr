---
title: Tümü için null denetimleri Ekle (parametreler)
ms.date: 09/17/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 573a9e56d3aedd55bc571eaaa363b42a53019566
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74782309"
---
# <a name="add-null-checks-for-all-parameters"></a>Tüm parametreler için null denetimleri ekleme 

Bu yeniden düzenleme için geçerlidir: 

- C# 

**Ne:** Tüm null yapılabilir, işaretli olmayan parametrelerin null listesini kontrol eden `if` deyimlerini oluşturur ve ekler. 

**Ne zaman:** Geçerli tüm Yöntem parametreleri için hızlı bir şekilde null denetimleri eklemek istiyorsunuz.

**Neden:** Birçok parametre için null denetimleri yazmak zaman alabilir ve tekrararda olabilir. Bu yeniden düzenlemenin kullanılması hızlıdır ve programı daha sağlam hale getirir.  

## <a name="how-to"></a>Nasıl yapılır 

1. İmlecinizi yöntemin içindeki herhangi bir parametrenin üzerine yerleştirin.

2. **Ctrl**+tuşuna basın **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.

   ![Hızlı Eylemler ve yeniden düzenlemeler](media/add-null-checks-for-all-parameters.png)
   
3. **Tüm parametreler için null denetimleri ekleme**seçeneğini belirleyin.

   ![Tümü için null denetimleri Ekle](media/add-null-checks-for-all.png) 

## <a name="see-also"></a>Ayrıca bkz. 

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
