---
title: Arabirim yeniden düzenlemesi Ayıkla
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 15da8bdf1a3df60a7ad4816ce578ec5672c85ecf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654423"
---
# <a name="extract-an-interface-refactoring"></a>Arabirim yeniden düzenlemesi Ayıkla

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

**Ne:** Bir sınıf, yapı veya arabirimden var olan üyeleri kullanarak bir arabirim oluşturmanıza olanak sağlar.

**Ne zaman:** Başka sınıflar, yapılar veya arabirimler tarafından devralınabilir bir sınıf, yapı veya arabirimdeki üyelere sahipsiniz.

**Neden:** Arabirimler, nesne odaklı tasarımlar için harika yapılardır. Çeşitli hayvanlar (köpek, kedi, kedi) için, hepsi, yiyecek, DRINK, uyku gibi yaygın yöntemlerle sahip olabilecek bir sınıf olduğunu düşünün. Ihayvan gibi bir arabirim kullanmak, bu yöntemler için köpek, Cat ve Bird ortak bir "imzaya" sahip olmasını sağlar.

## <a name="extract-an-interface-refactoring"></a>Arabirim yeniden düzenlemesi Ayıkla

1. İmlecinizi sınıf adına yerleştirin.

   - C#:

       ![Vurgulanan kod-C#](media/extractinterface-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod Visual Basic](media/extractinterface-highlight-vb.png)

2. Sonra, aşağıdaki eylemlerden birini yapın:

   - **Klavyenizdeki**
      - **CTRL + R**, ardından **CTRL + ı**tuşlarına basın. (Klavye kısayolunuz, seçtiğiniz profile bağlı olarak farklı olabilir.)
      - **Ctrl** + tuşuna basın **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek ve Önizleme penceresi açılır penceresinden **Arabirimi Ayıkla** ' yı seçin.
   - **Tığında**
      - **Arabirimi ayıkla > düzenle > yeniden Düzenle**' yi seçin.
      - Sınıfın adına sağ tıklayın, **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin ve Önizleme penceresi açılır penceresinden **Arabirimi Ayıkla** ' yı seçin.

3. Açılan **Arabirimi Ayıkla** iletişim kutusunda, istenen bilgileri girin:

   ![Ayıklama Arabirimi](media/extractinterface-dialog-same-file.png)

   | Alan | Açıklama |
   | - | - |
   | **Yeni arabirim adı** | Oluşturulacak arabirimin adı. Ad varsayılan olarak I*ClassName*olarak, burada *ClassName* yukarıda seçtiğiniz sınıfın adıdır. |
   | **Yeni dosya adı** | Arabirimi içerecek oluşturulan dosyanın adı. Arabirim adında olduğu gibi, bu ad varsayılan olarak I*ClassName*olur; burada *ClassName* yukarıda seçtiğiniz sınıfın adıdır. Ayrıca **geçerli dosyaya ekleme**seçeneğini de belirleyebilirsiniz. |
   | **Arabirim oluşturmak için ortak üyeleri seçin** | Arabirime Ayıklanacak öğeler. İstediğiniz kadar istediğiniz kadar seçebilirsiniz. |

4. **Tamam ' ı**seçin.

   Arabirim, belirtilen ad dosyasında oluşturulur. Ayrıca, seçtiğiniz sınıf bu arabirimi uygular.

   - C#:

      ![Elde edilen sınıf-C#](media/extractinterface-class-cs.png)

      ![Sonuç arabirimi-C#](media/extractinterface-interface-cs.png)

   - Visual Basic:

      ![Elde edilen sınıf-Visual Basic](media/extractinterface-class-vb.png)

      ![Sonuç arabirimi-Visual Basic](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [.NET Geliştiricileri için İpuçları](../csharp-developer-productivity.md)
