---
title: Düzenle ve devam et ile kesme modunda düzenlemeleri uygulama | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05340b4922262eb134aca8fef4bf215342e5a997
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734026"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue-visual-basic"></a>Nasıl yapılır: Düzenle ve devam et ile kesme modunda düzenleme uygulama (Visual Basic)
Kodunuzu kesme modunda düzenlemek için Düzenle ve devam et ' i kullanabilir ve sonra yürütmeyi durdurup yeniden başlatmadan devam edebilirsiniz.

Hata ayıklama sırasında Düzenle ve devam et ile ilgili sınırlamalar için bkz. [desteklenen kodC# değişiklikleri (ve Visual Basic)](../debugger/supported-code-changes-csharp.md).

### <a name="to-edit-code-in-break-mode"></a>Kodu kesme modunda düzenlemek için

1. Aşağıdakilerden birini yaparak kesme moduna girin:

    - Kodunuzda bir kesme noktası ayarlayın, ardından **Hata Ayıkla** menüsünden **hata ayıklamayı Başlat** ' ı seçin ve uygulamanın kesme noktasına gelmesini bekleyin.

         veya

    - Hata ayıklamayı başlatın ve **Hata Ayıkla** menüsünden **Tümünü kes** ' i seçin.

         veya

    - Bir özel durum oluştuğunda, **özel durum Yardımcısı**üzerinde **düzenlemesi etkinleştir** ' i seçin.

2. İstediğiniz ve desteklenen kod değişikliklerini yapın.

     Daha fazla bilgi için bkz. [desteklenen kod değişiklikleriC# (ve Visual Basic)](../debugger/supported-code-changes-csharp.md).

    > [!NOTE]
    > Düzenle ve devam et tarafından izin verilmeyen bir kod değişikliği yapmaya çalışırsanız, düzenlemeniz mor dalgalı bir çizgiyle altı çizili olur ve Görev Listesi bir görev görüntülenir. Geçersiz kod değişikliğini geri yüklemediğiniz takdirde kod yürütmeye devam edemeyeceksiniz.

3. **Hata Ayıkla** menüsünde, yürütmeyi sürdürmek için **devam** ' a tıklayın.

     Kodunuz artık projeye eklenen ve uygulanan düzenlemelerinizle yürütülür.

## <a name="see-also"></a>Ayrıca bkz.
- [Desteklenen kod değişiklikleri (C# ve Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Düzenle ve Devam Et (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
