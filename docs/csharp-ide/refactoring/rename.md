---
title: "Rename - yeniden düzenlemesi (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: 60e2a623-b56d-4591-93dc-e51429e4e1ba
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.rename
dev_langs: CSharp
ms.workload: dotnet
ms.openlocfilehash: 3cc15e155683feb7e7bbcc26285d00e5538765f8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="rename-a-code-symbol-in-c"></a>C# kod sembolü yeniden adlandırma #
**Ne:** alanları, yerel değişkenleri, yöntemleri, ad alanları, özellikleri ve türleri gibi kodu sembolleri tanımlayıcıları yeniden adlandır olanak sağlar.

**Ne zaman:** güvenli bir şekilde bir şey tüm örneklerini bulun ve yeni bir ad kopyala/yapıştır zorunda kalmadan yeniden adlandırmak istediğiniz.  

**Neden:** Kopyala ve yeni bir ad arasında projenin tamamında yapıştırma misiniz olasılıkla neden hatalar.  Bu yeniden düzenleme aracı doğru bir şekilde yeniden adlandırma eylemi gerçekleştirir.

**Nasıl:**

1. Vurgula veya metin imleci yeniden adlandırılacak öğesi içinde:

   ![Vurgulanmış kodu](media/rename_highlight.png)

1. Ardından, aşağıdakilerden birini yapın:
   * **Klavye**
     * Tuşuna **Ctrl + R**, ardından **Ctrl + R**.  (Bağlı olarak hangi profilinde seçtiğiniz klavye kısayolu farklı olabileceğini unutmayın.)
   * **Fare**
     * Seçin **Düzenle > yeniden düzenlemeniz > yeniden adlandırma**.
     * Kod sağ tıklatıp **yeniden adlandırma**.

1. Öğeyi yeni bir ad yazarak yeniden adlandırın.

   ![Animasyon yeniden adlandırma](media/rename_animated.gif)

   > [!TIP]
   > Ayrıca açıklamaları ve bu yeni ad kullanmak üzere diğer dizeleri güncelleştirebilirsiniz yanı [Önizleme değişiklikleri](../../ide/preview-changes.md) önce kaydetme, içinde onay kutularını kullanarak **yeniden adlandırmak** üstünde görünür kutusunu IDE'yi sağında.

1. Değişiklikle memnun kaldığınızda, tıklatın **Uygula** düğmesini veya tuşuna **Enter** ve değişiklikler uygulanır.

> [!NOTE]
> Bir çakışma neden olacağından, zaten bir ad kullanırsanız **yeniden adlandırma** IDE'yi kutusunda sizi uyaracaktır.
>
> ![Çakışma yeniden adlandırma](media/rename_conflict.png)

## <a name="see-also"></a>Ayrıca Bkz.  
[Yeniden düzenlemesi (C#)](../refactoring-csharp.md)  
[Değişiklikleri Önizleme](../../ide/preview-changes.md)