---
title: Oluşturucu hızlı eylemi oluştur
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 41bb9a0e3921495629a10d6783432e8b4999a117
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661732"
---
# <a name="generate-a-constructor-in-visual-studio"></a>Visual Studio 'da Oluşturucu oluşturma

Bu kod üretimi için geçerlidir:

- C#

- Visual Basic

**Ne:** Bir sınıf üzerinde yeni bir Oluşturucu için kodu hemen oluşturmanıza olanak sağlar.

**Ne zaman:** Yeni bir Oluşturucu tanıtmanız ve bunu otomatik olarak doğru bir şekilde bildirmek ya da var olan bir oluşturucuyu değiştirmek istiyorsunuz.

**Neden:** Bu özelliği kullanmadan önce oluşturucuyu bildirebilirsiniz, ancak bu özellik, doğru parametrelerle otomatik olarak oluşturulur. Ayrıca, mevcut bir oluşturucunun değiştirilmesi, bu özelliği otomatik olarak güncelleştirmek için kullanmadığınız müddetçe tüm CallSites 'ın güncelleştirilmesini gerektirir.

**Nasıl yapılır:** Oluşturucu oluşturmak için çeşitli yollar vardır:

- [Oluşturucu oluştur ve üyeleri Seç](#pick)
- [Seçili alanlardan Oluşturucu oluştur](#selection)
- [Yeni kullanımdan Oluşturucu oluştur](#usage)
- [Mevcut oluşturucuya parametre Ekle](#addparameter)
- [Oluşturucu parametresinden alan/Özellik oluştur ve Başlat](#create)

## <a id = "pick"></a>Oluşturucu oluştur ve üyeleri Seç (C# yalnızca)

1. İmlecinizi bir sınıftaki boş bir satıra yerleştirin:

   ![İmleç boş satıra](media/constructor1-highlight-cs.png)

1. Sonra, aşağıdakilerden birini yapın:

   - **Klavyenizdeki**
      - **Ctrl** + tuşuna basın **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
   - **Tığında**
      - Sağ tıklayın ve **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin.
      - &nbsp; ![Screwdriver](media/screwdriver.png) Sol kenar boşluğunda, metin imleci sınıfında zaten boş satırda görünen simge.

   ![Oluşturucu önizlemesi oluştur](media/constructor1-preview-cs.png)

1. Açılan menüden **Oluşturucu oluştur** ' u seçin.

   **Üyeleri Seç** iletişim kutusu açılır.

1. Oluşturucu parametreleri olarak eklemek istediğiniz üyeleri seçin. Bunları yukarı ve aşağı okları kullanarak sipariş edebilirsiniz. **Tamam ' ı**seçin.

   ![Üyeleri Seç iletişim kutusu](media/constructor1-dialog-cs.png)

   > [!TIP]
   > Oluşturucu parametreleriniz için otomatik olarak null denetimleri oluşturmak üzere **null denetimleri Ekle** onay kutusunu işaretleyebilirsiniz.

   Oluşturucu belirtilen parametrelerle oluşturulur.

   ![Oluşturucu sonucu oluştur](media/constructor1-result-cs.png)

## <a id="selection"></a>Seçili alanlardan Oluşturucu oluştur (C# yalnızca)

1. Oluşturduğunuz oluşturucuda istediğiniz üyeleri vurgulayın:

   ![Üyeleri Vurgula](media/constructor2-highlight-cs.png)

1. Sonra, aşağıdakilerden birini yapın:

   - **Klavyenizdeki**
      - **Ctrl** + tuşuna basın **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
   - **Tığında**
      - Sağ tıklayın ve **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin.
      - &nbsp; ![Screwdriver](media/screwdriver.png) Sol kenar boşluğunda, metin imleci seçimle zaten varsa görüntülenen simge.

      ![Oluşturucu önizlemesi oluştur](media/constructor2-preview-cs.png)

1. Açılan menüden **' TypeName (...) ' oluşturucusunu üret '** i seçin.

   Oluşturucu seçili parametrelerle oluşturulur.

   ![Oluşturucu sonucu oluştur](media/constructor2-result-cs.png)

## <a id="usage"></a>Yeni kullanımdan Oluşturucu oluştur (C# ve Visual Basic)

1. İmlecinizi kırmızı dalgalı çizgi olan çizgiye yerleştirin. Kırmızı dalgalı çizgi, henüz mevcut olmayan bir oluşturucuya yapılan çağrıyı gösterir.

   - C#:

       ![Vurgulanan kodC#](media/constructor-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod VB](media/constructor-highlight-vb.png)

2. Sonra, aşağıdakilerden birini yapın:

   - **Klavyenizdeki**
      - **Ctrl** + tuşuna basın **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
   - **Tığında**
      - Sağ tıklayın ve **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin.
      - Kırmızı dalgalı çizgi üzerine gelin ve ![ampul hatası](media/error-bulb.png) görüntülenen simge.
      - &nbsp; ![ampul hatası](media/error-bulb.png) Sol kenar boşluğunda, metin imleci kırmızı dalgalı çizgi ile zaten varsa görüntülenen simge.

      ![Oluşturucu önizlemesi oluştur](media/constructor-preview-cs.png)

3. Açılan menüden **'*TypeName*' içinde Oluşturucu üret '** i seçin.

   > [!TIP]
   > Seçiminizi yapmadan önce yapılacak [tüm değişiklikleri görmek için](../../ide/preview-changes.md) Önizleme penceresinin altındaki **Değişiklikleri Önizle** bağlantısını kullanın.

   Oluşturucu, kullanımından çıkarılan herhangi bir parametre ile oluşturulur.

   - C#:

       ![Yöntem sonucu üretC#](media/constructor-result-cs.png)

   - Visual Basic:

       ![Yöntem sonucu oluştur VB](media/constructor-result-vb.png)

## <a id="addparameter"></a>Mevcut oluşturucuya parametre Ekle (C# yalnızca)

1. Varolan bir Oluşturucu çağrısına bir parametre ekleyin.

2. İmlecinizi, henüz varolmayan bir Oluşturucu kullandığınızı gösteren kırmızı renkli bir dalgalı çizgi olduğu satıra yerleştirin.

    ![Oluşturucu vurgusu oluştur](media/constructor4-highlight-cs.png)

3. Sonra, aşağıdakilerden birini yapın:

   - **Klavyenizdeki**
      - **Ctrl** + tuşuna basın **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
   - **Tığında**
      - Sağ tıklayın ve **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin.
      - Kırmızı dalgalı çizgi üzerine gelin ve ![ampul hatası](media/error-bulb.png) görüntülenen simge.
      - &nbsp; ![ampul hatası](media/error-bulb.png) Sol kenar boşluğunda, metin imleci kırmızı dalgalı çizgi ile zaten varsa görüntülenen simge.

      ![Oluşturucu önizlemesi oluştur](media/constructor4-preview-cs.png)

4. Açılan menüden **parametre Ekle ' TypeName (...) '** seçeneğini belirleyin.

   Parametresi, kendi kullanımından çıkarılan türü ile oluşturucuya eklenir.

   ![Oluşturucu sonucu oluştur](media/constructor4-result-cs.png)

Ayrıca, varolan bir yönteme bir parametre ekleyebilirsiniz. Daha fazla bilgi için bkz. [bir yönteme parametre ekleme](add-parameter.md).

## <a id="create"></a>Bir Oluşturucu parametresinden alan veya özellik oluşturma ve başlatma (C# yalnızca)

1. Mevcut bir Oluşturucu bulun ve bir parametre ekleyin:

   ![Oluşturucu vurgusu oluştur](media/constructor5-highlight-cs.png)

1. İmlecinizi yeni eklenen parametrenin içine yerleştirin.

1. Sonra, aşağıdakilerden birini yapın:

   - **Klavyenizdeki**
      - **Ctrl** + tuşuna basın **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
   - **Tığında**
      - Sağ tıklayın ve **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin.
      - &nbsp; ![Screwdriver](media/screwdriver.png) Sol kenar boşluğunda görüntülenen ve metin imlece eklenmiş parametreye sahip olan satırda görünen simge.

   ![Oluşturucu önizlemesi oluştur](media/constructor5-preview-cs.png)

1. Açılır menüden **Özellik oluştur ve Başlat** ' ı veya **Oluştur ve Başlat ' ı** seçin.

   Alan veya özellik, türlerinizi eşleştirmek için olarak tanımlanır ve otomatik olarak adlandırılır. Oluşturucu gövdesinde alanı veya özelliği başlatmak için bir kod satırı da eklenir.

   ![Oluşturucu sonucu oluştur](media/constructor5-result-cs.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizle](../../ide/preview-changes.md)