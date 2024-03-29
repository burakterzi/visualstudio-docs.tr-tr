---
title: Gölgelendirici Tasarımcısı
ms.date: 09/21/2018
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.effectdesigner
- vs.graphics.shaderdesigner
ms.assetid: 5db09a16-b82c-4ba3-8ec9-630cdc109397
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd82a5c8bee50c778b87927f1074d71a38a21e9f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72635051"
---
# <a name="shader-designer"></a>Gölgelendirici Tasarımcısı

Bu belgede, *gölgelendiriciler*olarak bilinen özel görsel etkileri oluşturmak, değiştirmek ve dışarı aktarmak Için Visual Studio **Gölgelendirici Tasarımcısı** ile nasıl çalışılacağı açıklanmaktadır.

Üst düzey gölgelendirici dili (HLSL) programlamayı bilmiyor olsanız bile, oyununuz veya uygulamanız için özel görsel etkiler oluşturmak üzere **gölgelendirici tasarımcısını** kullanabilirsiniz. **Gölgelendirici tasarımcısında**gölgelendirici oluşturmak için onu bir grafik olarak yerleştirirsiniz. Yani, verileri ve işlemleri temsil eden tasarım yüzeyi *düğümlerine* ekler ve sonra işlemlerin verileri nasıl işleyeceğini tanımlamak için bunlar arasında bağlantı yaparsınız. Her bir işlem düğümünde, bu noktaya kadar olan efektin bir önizlemesi sağlanır, böylece sonucu görselleştirebilirsiniz. Veriler, gölgelendirici çıkışını temsil eden son bir düğüme doğru düğümler aracılığıyla akar.

## <a name="supported-formats"></a>Desteklenen biçimler

**Gölgelendirici Tasarımcısı** Bu gölgelendirici biçimlerini destekler:

|Biçim Adı|Dosya Uzantısı|Desteklenen Işlemler (görüntüleme, düzenleme, dışarı aktarma)|
|-----------------| - | - |
|Yönlendirilmiş grafik gölgelendirici dili|*. dgsl*|Görüntüleme, düzenleme|
|HLSL gölgelendiricisi (kaynak kodu)|*. HLSL*|İşlemi|
|HLSL gölgelendiricisi (bytecode)|*. cso*|İşlemi|
|C++üst bilgi (HLSL bytecode dizisi)|*. h*|İşlemi|

## <a name="get-started"></a>Kullanmaya başlayın

Bu bölümde, Visual Studio C++ projenize bir DGSL gölgelendiricisi ekleme ve kullanmaya başlamanıza yardımcı olacak temel bilgiler sağlanmaktadır.

> [!NOTE]
> Gölgelendirici grafikleri (. dgsl dosyaları) gibi grafik öğelerinin otomatik derleme tümleştirmesi yalnızca projeler için C++ desteklenir.

### <a name="to-add-a-dgsl-shader-to-your-project"></a>Projenize bir DGSL gölgelendiricisi eklemek için

1. Grafiklerle çalışmanız için gereken Visual Studio bileşeninin yüklü olduğundan emin olun. Bileşen, **görüntü ve 3B model düzenleyicileri**olarak adlandırılır.

   Yüklemek için  >  **Araçlar** ' ı seçerek Visual Studio yükleyicisi açın ve menü çubuğundan**Araçlar ve Özellikler al** ' ı seçin ve ardından **ayrı bileşenler** sekmesini seçin.  **Oyunlar ve grafikler** kategorisi ve ardından **Değiştir**' i seçin.

   ![Görüntü ve 3B model düzenleyicileri bileşeni](media/image-3d-model-editors-component.png)

2. **Çözüm Gezgini**, gölgelendiriciyi eklemek istediğiniz C++ projenin kısayol menüsünü açın ve ardından  > **Yeni öğe** **Ekle** ' yi seçin.

3. **Yeni öğe Ekle** iletişim kutusunda, **yüklü**altında **grafikler**' i seçin ve ardından **Görsel Gölgelendirici Grafiği (. dgsl)** öğesini seçin.

   > [!NOTE]
   > **Yeni öğe Ekle** Iletişim kutusunda **grafik** kategorisini görmüyorsanız ve **resim ve 3B model düzenleyicileri** bileşeni yüklüyse, grafik öğeleri proje türü için desteklenmez.

4. Gölgelendirici dosyasının **adını** ve oluşturulmasını istediğiniz **konumu** belirtin.

5. **Ekle** düğmesini seçin.

### <a name="the-default-shader"></a>Varsayılan gölgelendirici

Her bir DGSL gölgelendiricisi oluşturduğunuzda, **son renk** düğümüne bağlanmış yalnızca bir **nokta rengi** düğümüne sahip olan minimal bir gölgelendirici olarak başlar. Bu gölgelendirici tamamlanmış ve işlevsel olsa da, çok fazla değildir. Bu nedenle, çalışma Gölgelendirici oluşturmanın ilk adımı genellikle **nokta rengi** düğümünü silmek veya diğer düğümlere yer açmak Için **son renk** düğümü bağlantısını keser.

## <a name="work-with-the-shader-designer"></a>Gölgelendirici Tasarımcısı ile çalışma

Aşağıdaki bölümlerde, özel gölgelendiriciler ile çalışmak için Gölgelendirici Tasarımcısının nasıl kullanılacağı açıklanır.

### <a name="shader-designer-toolbars"></a>Gölgelendirici Tasarımcısı araç çubukları

Gölgelendirici Tasarımcısı araç çubukları, DGSL gölgelendirici grafikleriyle çalışmanıza yardımcı olan komutlar içerir.

Gölgelendirici Tasarımcısının durumunu etkileyen komutlar, ana Visual Studio penceresindeki **gölgelendirici tasarımcı modu** araç çubuğunda bulunur. Tasarım araçları ve komutları, gölgelendirici Tasarımcısı tasarım yüzeyinde **Gölgelendirici Tasarımcısı** araç çubuğunda bulunur.

**Gölgelendirici tasarımcı modu** araç çubuğu şöyledir:

![Gölgelendirici Tasarımcısı kalıcı araç çubuğu.](../designers/media/digit-dsd-modal-toolbar.png)

Bu tabloda, **gölgelendirici tasarımcı modu** araç çubuğunda soldan sağa göründükleri sırada listelenen öğeler açıklanmaktadır:

|Araç Çubuğu Öğesi|Açıklama|
|------------------|-----------------|
|**Seçin**|Grafikteki düğümlerle ve kenarlarla etkileşimi sunar. Bu modda düğümleri seçip taşıyabilir ya da silebilirsiniz ve kenarları oluşturabilir veya bunları kesebilirsiniz.|
|**Pan**|Bir gölgelendirici grafiğinin pencere çerçevesine göre taşınmasını sağlar. Kaydırmak için tasarım yüzeyinde bir nokta seçin ve taşıyın.<br /><br /> **Seçim** modunda, **Dikey Çevir** modunu geçici olarak etkinleştirmek için **CTRL** tuşuna basılı tutabilirsiniz.|
|**Yakınlaştırma**|Pencere çerçevesine göre daha fazla veya daha az gölgelendirici grafik ayrıntısı görüntülenmesini sağlar. **Yakınlaştırma** modu ' nda tasarım yüzeyinde bir nokta seçin ve yakınlaştırmak için sağa veya aşağı taşıyın ya da uzaklaştırmak için sola veya yukarı kaydırın.<br /><br /> **Seçme** modunda, fare tekerleğini kullanarak yakınlaştırmak veya uzaklaştırmak için **CTRL** tuşuna basılı tutabilirsiniz.|
|**Sığacak kadar Yakınlaştır**|Pencere çerçevesindeki tam gölgelendirici grafiğini görüntüler.|
|**Gerçek zamanlı Işleme modu**|Gerçek zamanlı işleme etkinleştirildiğinde, hiçbir Kullanıcı eylemi gerçekleştirilmediğinde bile Visual Studio tasarım yüzeyini yeniden çizer. Bu mod, zamanla değişen gölgelendiriciler ile çalıştığınızda kullanışlıdır.|
|**Sphere ile Önizleme**|Etkinleştirildiğinde, gölgelendiricinin önizlemesi için bir Sphere modeli kullanılır. Tek seferde yalnızca bir önizleme şekli etkinleştirilebilir.|
|**Küp ile Önizleme**|Etkinleştirildiğinde, gölgelendirici önizlemesi için bir küpün modeli kullanılır. Tek seferde yalnızca bir önizleme şekli etkinleştirilebilir.|
|**Silindir ile Önizleme**|Etkinleştirildiğinde, gölgelendiriciyi önizlemek için bir silindir modeli kullanılır. Tek seferde yalnızca bir önizleme şekli etkinleştirilebilir.|
|**Koni ile Önizleme**|Etkinleştirildiğinde, gölgelendiriciyi önizlemek için koni modeli kullanılır. Tek seferde yalnızca bir önizleme şekli etkinleştirilebilir.|
|**Ekiple Önizleme**|Etkinleştirildiğinde, gölgelendiriciyi önizlemek için bir ekip modeli kullanılır. Tek seferde yalnızca bir önizleme şekli etkinleştirilebilir.|
|**Düzlemle Önizleme**|Etkinleştirildiğinde, gölgelendiriciyi önizlemek için düzlemin bir modeli kullanılır. Tek seferde yalnızca bir önizleme şekli etkinleştirilebilir.|
|**Araç Kutusu**|Ayrıca **araç kutusunu**gösterir veya gizler.|
|**Veri Erişimi**|Alternatif olarak, **Özellikler** penceresini gösterir veya gizler.|
|**Gelişmiş**|Gelişmiş komutları ve seçenekleri içerir.<br /><br /> **Dışarı aktar**: bir gölgelendiricinin birkaç biçimde dışa aktarılmasını mümkün.<br /><br /> **Farklı ver**: gölgelendiriciyi HLSL kaynak kodu veya derlenen gölgelendirici bayt olarak dışa aktarır. Gölgelendiricilerin nasıl dışarı aktarılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: gölgelendiriciyi dışarı aktarma](../designers/how-to-export-a-shader.md).<br /><br /> **Grafik altyapıları**: tasarım yüzeyini göstermek için kullanılan oluşturucunun seçilmesini sağlar.<br /><br /> **D3d11 Ile işle**: Gölgelendirici Tasarımcısı tasarım yüzeyini Işlemek için Direct3D 11 kullanır.<br /><br /> **D3D11WARP Ile işleme**: Gölgelendirici Tasarımcısı tasarım yüzeyini Işlemek için Direct3D 11 Windows Gelişmiş Tarama Platformu (warp) kullanır.<br /><br /> **Görünüm**: Gölgelendirici Tasarımcısı hakkında ek bilgi seçimini sunar.<br /><br /> **Kare hızı**: etkinleştirildiğinde, tasarım yüzeyinin sağ üst köşesindeki geçerli kare hızını görüntüler. Kare hızı, saniye başına çizilen çerçeve sayısıdır. Bu seçenek, **gerçek zamanlı Işleme modu** seçeneğini etkinleştirdiğinizde yararlıdır.|

> [!TIP]
> Son komutu yeniden çalıştırmak için **Gelişmiş** düğmesini seçebilirsiniz.

### <a name="work-with-nodes-and-connections"></a>Düğümler ve bağlantılarla çalışma

Düğümleri eklemek, kaldırmak, yeniden konumlandırmak, bağlamak ve yapılandırmak için **seçim** modunu kullanın. Bu temel işlemleri gerçekleştirmek için aşağıdaki adımları izleyin:

#### <a name="to-perform-basic-operations-in-select-mode"></a>Seçme modunda temel işlemleri gerçekleştirmek için

- Şöyle:

  - Grafiğe bir düğüm eklemek için **araç kutusunda** seçin ve tasarım yüzeyine taşıyın.

  - Grafikten bir düğüm kaldırmak için, seçin ve ardından **Delete**tuşuna basın.

  - Bir düğümü yeniden konumlandırmak için seçin ve sonra yeni bir konuma taşıyın.

  - İki düğüm bağlamak için bir düğümün çıkış terminalini diğer düğümün giriş terminaline taşıyın. Yalnızca uyumlu türleri olan terminaller bağlanabilir. Terminallerde bir çizgi bağlantıyı gösterir.

  - Bir bağlantıyı kaldırmak için, bağlı terminallerin her biri için kısayol menüsünde **Bağlantıları Kes**' i seçin.

  - Bir düğümün özelliklerini yapılandırmak için düğümü seçin ve ardından **Özellikler** penceresinde özellikler için yeni değerler belirtin.

### <a name="preview-shaders"></a>Gölgelendiriciler önizlemesi

Uygulamanızda bir gölgelendiricinin nasıl görüneceğini anlamanıza yardımcı olmak için, etkinizi nasıl önizlenbileceğinizi yapılandırabilirsiniz. Uygulamanızı yaklaşık olarak oluşturmak, dokular ve diğer malzeme parametrelerini yapılandırmak, zaman tabanlı efektlerin animasyonunu etkinleştirmek ve farklı açılardan önizlemeyi incelemek için çeşitli şekillerden birini seçebilirsiniz.

#### <a name="shapes"></a>Şekiller

Gölgelendirici Tasarımcısı, Gölgelendiricinizi önizlemek için kullanabileceğiniz altı şekil (bir Sphere, bir küp, silindir, koni, bir ekip ve bir düzlem) içerir. Gölgelendiriciye bağlı olarak, belirli şekiller size daha iyi bir önizleme sağlayabilir.

Bir önizleme şekli seçmek için, **gölgelendirici tasarımcı modları** araç çubuğunda istediğiniz şekli seçin.

#### <a name="textures-and-material-parameters"></a>Dokular ve malzeme parametreleri

Birçok gölgelendiriciler, uygulamanızdaki her bir nesne türü için benzersiz bir görünüm oluşturmak üzere dokuların ve malzeme özelliklerine güvenir. Gölgelendiricinizi uygulamanızda nasıl görüneceğine bakmak için, Önizleme oluşturmak üzere kullanılan dokuları ve malzeme özelliklerini uygulamanızda kullanabileceğiniz dokularla ve parametrelerle eşleşecek şekilde ayarlayabilirsiniz.

Farklı dokuyu bir doku kaydına bağlamak veya diğer malzeme parametrelerini değiştirmek için:

1. **Seç** modunda tasarım yüzeyinde boş bir alan seçin. Bu, **Özellikler** penceresinin Genel gölgelendirici özelliklerini görüntülemesine neden olur.

2. **Özellikler** penceresinde, değiştirmek istediğiniz doku ve parametre özellikleri için yeni değerler belirtin.

Aşağıdaki tabloda, değiştirebileceğiniz Gölgelendirici parametreleri gösterilmektedir:

|Parametre|Özellikler|
|---------------|----------------|
|**Doku 1**  - **doku 8**|**Erişim**: özelliğin model düzenleyicisinden ayarlaneklenmesine izin vermek için **genel** ' e gidin; Aksi takdirde, **özel**.<br /><br /> **Dosya adı**: Bu doku kaydı ile ilişkili doku dosyasının tam yolu.|
|**Malzeme çevresel**|**Erişim**: özelliğin model düzenleyicisinden ayarlaneklenmesine izin vermek için **genel** ' e gidin; Aksi takdirde, **özel**.<br /><br /> **Değer**: dolaylı veya çevresel aydınlatma nedeniyle geçerli pikselin dağıtma rengi.|
|**Malzeme dağıtma**|**Erişim**: özelliğin model düzenleyicisinden ayarlaneklenmesine izin vermek için **genel** ' e gidin; Aksi takdirde, **özel**.<br /><br /> **Değer**: geçerli pikselin nasıl doğrudan aydınlatma kullandığını açıklayan bir renk.|
|**Malzeme yanıltıcı**|**Erişim**: özelliğin model düzenleyicisinden ayarlaneklenmesine izin vermek için **genel** ' e gidin; Aksi takdirde, **özel**.<br /><br /> **Değer**: kendi kendine sunulan aydınlatma nedeniyle geçerli pikselin renk katkısı.|
|**Malzeme yansımalı**|**Erişim**: özelliğin model düzenleyicisinden ayarlaneklenmesine izin vermek için **genel** ' e gidin; Aksi takdirde, **özel**.<br /><br /> **Değer**: geçerli pikselin doğrudan aydınlatmayı nasıl yansıttığını açıklayan bir renk.|
|**Malzeme yansımalı güç**|**Erişim**: özelliğin model düzenleyicisinden ayarlaneklenmesine izin vermek için **genel** ' e gidin; Aksi takdirde, **özel**.<br /><br /> **Değer**: geçerli pikselde Yansımalı vurguların yoğunluğunu tanımlayan üs.|

#### <a name="time-based-effects"></a>Zamana dayalı etkiler

Bazı gölgelendiriciler, etkiyi canlandıra zaman tabanlı bir bileşene sahiptir. Efektin işlem içinde nasıl göründüğünü göstermek için, önizlemenin saniyede birkaç kez güncellenmesi gerekir. Varsayılan olarak, Önizleme yalnızca gölgelendirici değiştirildiğinde güncelleştirilir; zamana dayalı etkileri görüntüleyebilmeniz için bu davranışı değiştirmek için gerçek zamanlı işlemeyi etkinleştirmeniz gerekir.

Gerçek zamanlı işlemeyi etkinleştirmek için, gölgelendirici Tasarımcısı araç çubuğunda **gerçek zamanlı işleme**' yı seçin.

#### <a name="examine-the-effect"></a>Etkiyi inceleyin

Birçok gölgelendiriciler, açı veya yönlü aydınlatmayı görüntüleme gibi değişkenlerden etkilenir. Bu değişkenler değiştiğinde efektin nasıl yanıt verdiğini incelemek için önizleme şeklini serbestçe döndürebilir ve gölgelendiricisinin nasıl davranacağını gözlemleyebilirsiniz.

Şekli döndürmek için **alt**tuşuna basın ve basılı tutun ve tasarım yüzeyinde herhangi bir noktayı seçin ve taşıyın.

### <a name="export-shaders"></a>Gölgelendiricileri dışarı aktar

Uygulamanızda bir gölgelendirici kullanabilmeniz için, bunu DirectX 'in anladığı bir biçimde dışarı aktarmanız gerekir.

Gölgelendiricileri HLSL kaynak kodu olarak veya derlenen gölgelendirici bayt olarak dışarı aktarabilirsiniz. HLSL kaynak kodu, *. HLSL* dosya adı uzantısına sahip bir metin dosyasına aktarılmıştır. Gölgelendirici bytecode 'u *. cso* dosya adı uzantısına sahip bir ham ikili dosyaya ya da gölgelendirici bayt kodunu bir diziye kodlayan bir C++ üst bilgi ( *. h*) dosyasına aktarılabilir.

Gölgelendiricilerin nasıl dışarı aktarılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: gölgelendiriciyi dışarı aktarma](../designers/how-to-export-a-shader.md).

## <a name="keyboard-shortcuts"></a>Klavye kısayolları

|Komut|Klavye kısayolları|
|-------------| - |
|**Seçme** moduna geçiş yap|**Ctrl** +**G**, **CTRL** +**Q**<br /><br /> **Malar**|
|**Yakınlaştırma** moduna geç|**Ctrl** +**G**, **CTRL** +**Z**<br /><br /> **Kadar**|
|**Pan** moduna geç|**Ctrl** +**G**, **CTRL** +**P**<br /><br /> **Ek**|
|Tümünü seç|**Ctrl**+**A**|
|Geçerli seçimi sil|**Delete**|
|Geçerli seçimi iptal et|**Escape** (**ESC**)|
|Yakınlaştır|**Fare tekerleği ileri** + **CTRL**<br /><br /> Artı Işareti ( **+** )|
|Uzaklaştır|**@No__t_1** **fare tekerleği geriye doğru**<br /><br /> Eksi Işareti ( **-** )|
|Tasarım yüzeyini yukarı kaydır|**Fare tekerleği geriye doğru**<br /><br /> **Seç**|
|Tasarım yüzeyini aşağı kaydır|**Fare tekerleği ileri**<br /><br /> **Seç**|
|Tasarım yüzeyini sola kaydır|@No__t_1**fare tekerleğini geriye doğru** **Kaydır**<br /><br /> **Fare tekerleği sol**<br /><br /> @No__t_1**Pageaşağı** **Kaydır**|
|Tasarım yüzeyini sağa kaydır|@No__t_1**fare tekerleğini Ileri** **Kaydır**<br /><br /> **Fare tekerleği sağ**<br /><br /> @No__t_1**PageUp** **Kaydır**|
|Klavye odağını başka bir düğüme taşı|**Ok** tuşları|
|Klavye odağının bulunduğu düğümü seçin (düğümü seçim grubuna ekler)|**Shıft** +**boşluk çubuğu**|
|Klavye odağına sahip olan düğüm seçimini değiştirme|**Ctrl** +**boşluk çubuğu**|
|Geçerli seçimi değiştirin (hiçbir düğüm seçilmezse, klavye odağına sahip düğümü seçin)|**'Nu**|
|Geçerli seçimi yukarı taşı|**Shıft** +**yukarı ok**|
|Geçerli seçimi aşağı taşı|**Shıft** +**aşağı ok**|
|Geçerli seçimi sola taşı|**Shıft** +**sol ok**|
|Geçerli seçimi sağa taşı|**Shıft** +**sağ ok**.|

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Oyunlar ve uygulamalar için 3B varlıklarla çalışma](../designers/working-with-3-d-assets-for-games-and-apps.md)|Dokular ve görüntüler, 3B modeller ve gölgelendirici efektleri ile çalışmak için kullanabileceğiniz Visual Studio araçlarına genel bir bakış sağlar.|
|[Görüntü Düzenleyicisi](../designers/image-editor.md)|Dokularla ve görüntülerle çalışmak için Visual Studio Görüntü Düzenleyicisi ' nin nasıl kullanılacağını açıklar.|
|[Model Düzenleyicisi](../designers/model-editor.md)|3D modellerle çalışmak için Visual Studio Model Düzenleyicisi ' nin nasıl kullanılacağını açıklar.|
