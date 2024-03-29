---
title: '3\. Adım: form özelliklerinizi ayarlama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 634ef037-1525-48c8-ac7f-abf04be69376
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 90fab2724c3d392db7824222da2450a8a4d585c3
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295752"
---
# <a name="step-3-set-your-form-properties"></a>3\. Adım: Form Özelliklerinizi Ayarlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Daha sonra, formunuzun görünüşünü değiştirmek için **Özellikler** penceresini kullanın.

 ![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo") Bu konunun video sürümü için bkz [. öğretici 1: Visual Basic resim görüntüleyici oluşturma-video 1](https://go.microsoft.com/fwlink/?LinkId=205209) veya [öğretici 1: video 1 ' de C# bir resim görüntüleyici oluşturma](https://go.microsoft.com/fwlink/?LinkId=205199). Bu videolar, Visual Studio 'nun önceki bir sürümünü kullanır, bu nedenle bazı menü komutlarında ve diğer kullanıcı arabirimi öğelerinde küçük farklılıklar vardır. Ancak, kavramlar ve yordamlar Visual Studio 'nun geçerli sürümünde benzer şekilde çalışır.

### <a name="to-set-your-form-properties"></a>Form özelliklerinizi ayarlamak için

1. Windows Form Tasarımcısı baktığınızdan emin olun. Visual Studio tümleşik geliştirme ortamında (IDE), **Form1.cs [Design]** (ya da **Form1. vb [Design]** ) sekmesini seçerek Visual Basic).

2. Seçmek için **Form1** form içinde herhangi bir yeri seçin. Şimdi form özelliklerini göstermeli **Özellikler** penceresine bakın. Formlarda çeşitli özellikler vardır. Örneğin, ön plan ve arka plan rengini, formun üstünde görünen başlık metnini, formun boyutunu ve diğer özellikleri ayarlayabilirsiniz.

   > [!NOTE]
   > **Özellikler** penceresi görünmezse, araç çubuğunda kare **ayıklamayı Durdur** düğmesini seçerek programınızı durdurun veya yalnızca pencereyi kapatın. Program durdurulmuşsa ve yine de **Özellikler** penceresini görmüyorsanız, menü çubuğunda **Görünüm**, **Özellikler penceresi**' ni seçin.

3. Form seçildikten sonra, **Özellikler** penceresinde **Text** özelliğini bulun. Listenin nasıl sıralandığına bağlı olarak aşağı kaydırmanız gerekebilir. **Metin**' i seçin, **resim görüntüleyici**yazın ve ardından ENTER ' u seçin.  Formunuz artık başlık çubuğunda metin **resmi görüntüleyicisine** sahip olmalıdır ve **Özellikler** penceresi aşağıdaki resme benzer görünmelidir.

    ![Özellikler penceresi](../ide/media/express-edittextproperty.png "Express_EditTextProperty") Özellikler penceresi

   > [!NOTE]
   > Özellikler, kategorilere ayrılmış veya alfabetik bir görünüme göre sıralanabilir. **Özellikler** penceresindeki düğmeleri kullanarak bu iki görünüm arasında geçiş yapabilirsiniz. Bu öğreticide, alfabetik görünüm aracılığıyla özellikleri bulmak daha kolay.

4. Windows Form Tasarımcısı 'e geri dönün. Formun sağ alt kısmındaki küçük beyaz kare olan ve aşağıdaki gibi görünen formun sağ alt sürükleme tutamacını seçin.

    ![Sürükleme tutamacı](../ide/media/express-bottomrt-drag.png "Express_BottomRT_Drag") Sürükleme tutamacı

    Formu daha geniş ve biraz uzun olacak şekilde yeniden boyutlandırmak için tutamacı sürükleyin.

5. **Özellikler** penceresine bakın ve **Boyut** özelliğinin değiştiğini unutmayın. Formu her yeniden boyutlandırışınızda **size** özelliği değişir. Formun tutamacını, yaklaşık 550, 350 (tam olması gerekmez) form boyutuyla yeniden boyutlandırmak için, bu proje için iyi bir şekilde çalışacak şekilde sürüklemeyi deneyin. Alternatif olarak, değerleri doğrudan **Boyut** özelliğine girebilir ve ardından Enter tuşunu seçebilirsiniz.

6. Programınızı yeniden çalıştırın. Programınızı çalıştırmak için aşağıdaki yöntemlerden herhangi birini kullanacağınızı unutmayın.

   - **F5** tuşunu seçin.

   - Menü çubuğunda **Hata Ayıkla**, **hata ayıklamayı Başlat**' ı seçin.

   - Araç çubuğunda, aşağıdaki gibi görünen **hata ayıklamayı Başlat** düğmesini seçin.

      ![Hata ayıklamayı Başlat araç çubuğu düğmesi](../ide/media/express-icondebug.png "Express_IconDebug") Hata ayıklamayı Başlat araç çubuğu düğmesi

     Daha önce olduğu gibi, IDE de programınızı oluşturup çalıştırır ve bir pencere görüntülenir.

7. Bir sonraki adıma geçmeden önce, IDE çalışırken programınızı değiştirmenize izin vermediğinden programınızı durdurun. Programınızı durdurmak için aşağıdaki yöntemlerden herhangi birini kullanacağınızı unutmayın.

   - Araç çubuğunda **hata ayıklamayı Durdur** düğmesini seçin.

   - Menü çubuğunda **Hata Ayıkla**, **hata ayıklamayı Durdur**' u seçin.

   - **Form1** penceresinin üst köşesindeki X düğmesini seçin.

### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. 4. [Adım: TableLayoutPanel denetimi Ile formunuzu düzenleme](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).

- Önceki öğretici adımına dönmek için bkz. 2. [Adım: Programınızı çalıştırma](../ide/step-2-run-your-program.md).
