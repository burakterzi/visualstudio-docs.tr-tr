---
title: Pencere düzenlerini özelleştirme
ms.date: 01/23/2017
ms.topic: conceptual
f1_keywords:
- vs.windows
- vs.environment
helpviewer_keywords:
- windows [Visual Studio], managing
- custom window configurations
- layout [Visual Studio], window management
- document windows [Visual Studio]
- interface modes
- AutoHide windows
- MDI, window interface modes
- multiple monitors
- Tabbed Document mode
- debug mode
- custom layouts
ms.assetid: 7517ff13-76de-4ecf-9c1b-eb9b7ff4d718
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6ca1f34604c314fea6e90130b298be04f3a6189
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652531"
---
# <a name="customize-window-layouts-in-visual-studio"></a>Visual Studio 'da pencere düzenlerini özelleştirme

Visual Studio 'da, Windows 'un konumunu, boyutunu ve davranışını çeşitli geliştirme iş akışları için en iyi şekilde çalışan pencere düzenleri oluşturacak şekilde özelleştirebilirsiniz. Düzeni özelleştirdiğinizde, IDE onu anımsar. Örneğin, **Çözüm Gezgini** yerleştirme konumunu değiştirir ve ardından Visual Studio 'yu kapatırsanız, başka bir bilgisayarda çalışıyor olsanız bile, Visual Studio 'yu bir sonraki açışınızda **Çözüm Gezgini** aynı konuma yerleştirilmeyecektir.

Ayrıca, özel bir düzen yazıp kaydedebilir ve sonra tek bir komutla birlikte mizanpajlar arasında geçiş yapabilirsiniz. Örneğin, düzenleme için bir düzen ve hata ayıklama için bir düzen oluşturabilir ve pencere**düzeni Düzenle** menü komutunu  >  **pencereyi** kullanarak bunlar arasında geçiş yapabilirsiniz.

## <a name="kinds-of-windows"></a>Windows türleri

### <a name="tool-and-document-windows"></a>Araç ve belge pencereleri

IDE 'nin iki temel pencere türü, *araç* penceresi ve *belge pencereleri*vardır. Araç pencereleri **Çözüm Gezgini**, **Sunucu Gezgini**, **Çıkış penceresi**, **hata listesi**, tasarımcılar, hata ayıklayıcı pencereleri vb. içerir. Belge pencereleri, kaynak kodu dosyalarını, rastgele metin dosyalarını, yapılandırma dosyalarını vb. içerir. Araç pencereleri, başlık çubuğuna göre yeniden boyutlandırılabilir ve sürüklenebilir. Belge pencereleri sekmesine göre sürüklenebilir. penceredeki diğer seçenekleri ayarlamak için sekmeye veya başlık çubuğuna sağ tıklayın.

**Pencere** menüsü, IDE 'de Windows yerleştirme, kayan ve gizleme seçeneklerini gösterir. Belirli bir pencereyle ilgili ek seçenekleri görmek için pencere sekmesine veya başlık çubuğuna sağ tıklayın. Belirli araç pencerelerinin aynı anda birden fazla örneğini görüntüleyebilirsiniz. Örneğin, birden fazla Web tarayıcısı penceresi görüntüleyebilir ve **pencere** menüsünde **yeni pencere** ' yi seçerek bazı araç pencerelerinin ek örneklerini oluşturabilirsiniz.

### <a name="preview-tab-document-windows"></a>Önizleme sekmesi (belge pencereleri)

**Önizleme** sekmesinde, dosyaları açmadan düzenleyicide görüntüleyebilirsiniz. Dosyalara tıkladığınızda hata ayıklama sırasında ve bir aramanın sonuçlarına göz **atarken, dosyaları** **Çözüm Gezgini**seçerek önizleyebilirsiniz, bu dosyaları görüntüleyebilirsiniz. Önizleme dosyaları belge sekmesi alanının sağ tarafındaki bir sekmede görüntülenir. Dosyayı değiştirirseniz veya **Aç**seçeneğini belirlerseniz dosya düzenlenmek üzere açılır.

### <a name="tab-groups"></a>Sekme grupları

Sekme grupları, IDE 'de iki veya daha fazla açık belge ile çalışırken sınırlı çalışma alanını yönetme yeteneğinizi genişletmenizi sağlar. Birden çok belge Windows ve araç pencerelerini dikey veya yatay sekme grupları halinde düzenleyebilir ve belgeleri bir sekme grubundan diğerine karıştırabilirsiniz.

### <a name="split-windows"></a>Pencereleri Böl

Bir belgede iki konumu aynı anda görüntülemeniz veya düzenlemeniz gerektiğinde Windows 'u ayırabilirsiniz. Belgenizi iki bağımsız kayan bölüme bölmek için **pencere** menüsünde **Böl** ' e tıklayın. Tek görünümü geri yüklemek için **pencere** menüsünde **bölmeyi kaldır** ' a tıklayın.

### <a name="toolbars"></a>Araç Çubukları

Araç çubukları sürükleyerek veya **Özelleştir** iletişim kutusu kullanılarak düzenlenebilir. Araç çubuklarını konumlandırma ve özelleştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: özelleştirme menüleri ve araç çubukları](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md).

## <a name="arrange-and-dock-windows"></a>Pencereleri yerleştirme ve yerleştirme

Bir belge penceresi veya araç penceresi *yerleştirilebilir*, böylece IDE pencere çerçevesinde bir konum ve boyut, ya da IDE 'den bağımsız ayrı bir pencere olarak taşınabilir. Araç pencereleri IDE çerçevesinin içinde herhangi bir yere yerleştirilebilir; Bazı araç pencereleri, Düzenleyici çerçevesinde sekmeli pencereler olarak yerleştirilebilir. Belge pencereleri, düzenleyici çerçevesinin içine yerleştirilebilir ve sekme düzeninde geçerli konumlarına sabitlenebilir. Birden çok pencereleri, IDE 'nin üzerinde veya dışında bir şekilde bir araya *getirin* . Araç pencereleri de gizli veya küçültülmüş olabilir.

Pencereleri aşağıdaki yollarla düzenleyebilirsiniz:

- Belge pencerelerini sekme kutusu sol tarafında sabitleyin.

- Windows sekme yerleştirme çerçevesini Düzenle.

- Araç pencerelerini IDE içindeki bir çerçevenin kenarına yerleştirin.

- Belge veya araç pencerelerini IDE üzerinde veya dışında kaydır.

- Araç pencerelerini IDE 'nin kenarı üzerinde gizleyin.

- Pencereleri farklı izleyicilere göre görüntüleyin.

- Pencere yerleşimini varsayılan düzene veya kaydedilmiş bir özel düzene sıfırlayın.

Araç ve belge pencerelerini sürükleyerek, **pencere** menüsündeki komutları kullanarak veya düzenlemek üzere pencerenin başlık çubuğuna sağ tıklayarak düzenleyin.

### <a name="dock-windows"></a>Pencereleri yerleştir

Bir araç penceresinin başlık çubuğunu tıklatıp sürüklediğinizde veya belge penceresi sekmesi göründüğünde, kılavuz elmas görünür. Sürükleme işlemi sırasında fare imleci elmas içindeki oklardan birinin üzerindeyken, fare düğmesini şimdi serbest bırakırsanız pencerenin nereye yerleştirildiğini gösteren bir gölgeli alan görüntülenir.

Bir yerleştirilebilir penceresini yerinde yaslama olmadan taşımak için, pencereyi sürüklerken **CTRL** tuşuna basın.

Bir araç penceresini veya belge penceresini en son yerleştirilen konumuna döndürmek için, pencerenin başlık çubuğunu veya sekmesini çift tıklatırken **CTRL** tuşuna basın.

Aşağıdaki çizimde belge pencereleri için kılavuz elmas gösterilmektedir ve bu, yalnızca düzenleyen çerçevesinin içine yerleştirilebilir:

![Belge penceresi Kılavuzu elmas](../ide/media/documentwindowguidediamonds.png)

Araç pencereleri, IDE 'deki veya Düzen çerçevesindeki bir çerçevenin bir tarafına kadar hızlı olabilir. Bir araç penceresini, pencereyi kolayca yeniden yerleştirmenize yardımcı olması için başka bir konuma sürüklediğinizde kılavuz elmas görünür.

![Araç penceresi Kılavuzu elleri](../ide/media/vs10guidediamond.png)

Aşağıdaki çizimde, mavi gölgeli alanla ilgili yeni bir konuma yerleştirilmiş **Çözüm Gezgini** gösterilmektedir:

![Yeni bir konumda Çözüm Gezgini sabitleme](../ide/media/vs2015_dock_diamond.png)

### <a name="close-and-auto-hide-tool-windows"></a>Araç pencerelerini kapat ve otomatik gizle

Başlık çubuğunun sağ üst köşesindeki **X** simgesine tıklayarak bir araç penceresini kapatabilirsiniz. Pencereyi yeniden açmak için, klavye kısayolunu veya menü komutunu kullanın. Araç pencereleri, *Otomatik Gizle*adlı bir özelliği destekler ve bu, farklı bir pencere kullandığınızda pencerenin bu şekilde kaydırılmasına neden olur. Bir pencere gizli olduğunda, adı IDE 'nin kenarındaki bir sekmede görünür. Pencereyi yeniden kullanmak için pencerenin görünüme geri dönmesi için sekmenin üzerine gelin.

![Otomatik Gizle](../ide/media/vs2015_auto_hide.png)

> [!NOTE]
> Otomatik gizleme 'nin araç pencereleri için tek tek veya sabitlenmiş gruplar halinde çalışıp çalışmadığını belirlemek için otomatik gizleme düğmesini seçin veya temizleyin **seçeneği yalnızca seçenekler** iletişim kutusunda **etkin araç pencerelerini etkiler** . Daha fazla bilgi için bkz. [Genel, ortam, Seçenekler iletişim kutusu](../ide/reference/general-environment-options-dialog-box.md).

> [!NOTE]
> Otomatik gizleme özelliği etkin olan araç pencereleri, pencere odaklanıldığında geçici olarak görünüme kayarak çıkabilir. Pencereyi yeniden gizlemek için geçerli pencerenin dışında bir öğe seçin. Pencere odağı kaybettiğinde, görünüm geri taşınır.

### <a name="specifying-a-second-monitor"></a>İkinci bir izleyici belirtme

İkinci bir monitörünüz varsa ve işletim sisteminiz destekliyorsa, hangi izleyicinin bir pencere görüntüleyeceğini seçebilirsiniz. Diğer izleyicilerinde, *Rafts* içinde birden çok pencere de gruplandırabilirsiniz.

> [!TIP]
> **Çözüm Gezgini** birden çok örneğini oluşturabilir ve bunları başka bir monitöre taşıyabilirsiniz. Pencereye sağ tıklayın ve **yeni Çözüm Gezgini Görünüm**' ü seçin. **CTRL** tuşunu seçerken, tüm pencereleri geri ' ye çift tıklayarak özgün monitöre döndürebilirsiniz.

### <a name="reset-name-and-switch-between-window-layouts"></a>Pencere düzenleri arasında sıfırlama, adlandırma ve geçiş yapma

**Pencere mizanpajını Sıfırla** komutunu kullanarak, ayarlar KOLEKSIYONUNUZ için IDE 'yi özgün pencere düzenine döndürebilirsiniz. Bu komutu çalıştırdığınızda, aşağıdaki eylemler gerçekleşir:

- Tüm pencereler varsayılan konumlarına taşınır.

- Varsayılan pencere düzeninde kapatılan pencereler kapalıdır.

- Varsayılan pencere düzeninde açık olan pencereler açılır.

### <a name="create-and-save-custom-layouts"></a>Özel düzenler oluşturma ve kaydetme

Visual Studio, 10 ' a kadar özel pencere düzenini kaydetmenizi ve aralarında hızlıca geçiş yapmanızı sağlar. Aşağıdaki adımlarda, yerleşik ve kayan araç pencereleri ile birden çok izleyiciden faydalanan özel düzenleri oluşturma, kaydetme, çağırma ve yönetme işlemleri gösterilmektedir.

İlk olarak, her biri ayrı bir en uygun düzene sahip iki projesi olan bir test çözümü oluşturun.

#### <a name="create-a-ui-project-and-customize-the-layout"></a>UI projesi oluşturma ve düzeni özelleştirme

1. Yeni C# bir **WPF uygulaması** projesi oluşturun. Bu projede, bir kullanıcı arabirimi geliştirdiğinizi düşünelim. Tasarımcı penceresinin alanını en üst düzeye çıkarmak ve diğer araç pencerelerini bu şekilde taşımak istiyorsunuz.

2. Birden çok monitörünüz varsa, **Çözüm Gezgini** penceresini ve **Özellikler** penceresini ikinci izleyicisine çekin. Tek bir izleme sisteminde, tasarımcı hariç tüm pencereleri kapatmayı deneyin.

3. **Araç kutusu** penceresini göstermek için **Ctrl** +**alt** +**X** tuşlarına basın. Pencere yerleştirilmişse, yerleştirmek istediğiniz yere kayabilecek şekilde sürükleyin.

4. Visual Studio 'Yu hata ayıklama moduna almak için **F5** tuşuna basın. **Oto**, **çağrı yığınının**ve **Çıkış** hata ayıklama pencerelerinin konumunu istediğiniz şekilde ayarlayın. Oluşturmakta olduğunuz düzen hem düzenleme modu hem de hata ayıklama modu için geçerlidir.

5. Hem hata ayıklama modu hem de düzenleme modundaki mizanpajlarınız istediğiniz gibi **olduğunda pencere düzeni  >  pencere** **düzenini kaydet**' i seçin. Bu düzeni "tasarımcı" olarak çağırın.

     Yeni mizanpajınızı, **Ctrl** +**alt** +**1... 0**' ın ayrılmış listesinden sonraki klavye kısayoluna atandığını unutmayın.

#### <a name="create-a-database-project-and-layout"></a>Veritabanı projesi ve düzeni oluşturma

1. Çözüme yeni bir **SQL Server veritabanı** projesi ekleyin.

2. **Çözüm Gezgini** yeni projeye sağ tıklayın ve **Nesne Gezgini Görünüm**' ü seçin. Bu, veritabanınızdaki tablolara, görünümlere ve diğer nesnelere erişmenizi sağlayan **SQL Server Nesne Gezgini** penceresini görüntüler. Bu pencereyi kayabilir ya da yuvalanmış bırakabilirsiniz. Diğer araç pencerelerini istediğiniz şekilde ayarlayın. Ek realronizme için gerçek bir veritabanı ekleyebilirsiniz, ancak bu izlenecek yol için gerekli değildir.

3. Mizanpajınızı istediğiniz **şekilde tercih ettiğinizde** , ana menüden pencere  >  pencere**yerleşimini kaydet**' i seçin. Bu düzeni "DB Project" olarak çağırın. (Bu proje için bir hata ayıklama modu düzeniyle ilgili değildir.)

#### <a name="switch-between-the-layouts"></a>Düzenler arasında geçiş yapma

Düzenler arasında geçiş yapmak için klavye kısayollarını kullanın veya ana menüden pencere**düzenini uygula** >  **pencere** düzeni ' ni seçin.

![Pencere Düzen menüsünü Uygula](../ide/media/vs2015_applywindowlayout.png)

Kullanıcı arabirimi düzeni uygulandıktan sonra, düzenin hem düzenleme modunda hem de hata ayıklama modunda nasıl korundığına göz önünde bulabilirsiniz.

Evde çok sayıda izleme kurulumuna sahipseniz ve tek bir izleme dizüstü bilgisayarı evinizde, her makine için optimize edilmiş düzenler oluşturabilirsiniz.

> [!NOTE]
> Tek izlemeli bir sisteme çok monitörlü bir düzen uygularsanız, ikinci monitöre yerleştirdiğiniz kayan pencereler artık Visual Studio penceresinin arkasında gizlenir. **Alt + Tab**tuşlarına basarak bu pencereleri öne çıkarabilirsiniz. Daha sonra Visual Studio 'Yu birden çok izleyiciyle açarsanız, düzeni yeniden uygulayarak pencereleri belirtilen konumlarına geri yükleyebilirsiniz.

#### <a name="manage-and-roam-your-layouts"></a>Düzenlerinizi yönetme ve dolaşımda

Pencere**düzenlerini yönet** >  **pencere** ' yi seçerek özel düzeninizi kaldırabilir, yeniden adlandırabilir veya yeniden sıralayabilirsiniz. Bir düzeni taşırsanız, anahtar bağlama otomatik olarak listedeki yeni konumu yansıtacak şekilde ayarlanır. Bağlamalar başka bir şekilde değiştirilemez ve bu nedenle, bir seferde en fazla 10 düzen saklayabilirsiniz.

![Pencere düzenlerini Yönet](../ide/media/managewindowlayouts.png)

Kendinize hangi klavye kısayolunun atandığını hatırlatmak için, pencere**düzeni uygula** >  **pencere** öğesini seçin.

Bu düzenler, Visual Studio sürümleri arasında ve ayrıca ayrı makinelerde Blend örnekleri arasında ve tüm Express sürümlerinden diğer Express kuruluşlarına otomatik olarak dolaşımda yapılır. Ancak, düzenler Visual Studio, Blend ve Express arasında dolaşımda değildir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: IDE 'de gezinme](../ide/how-to-move-around-in-the-visual-studio-ide.md)