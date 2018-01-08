---
title: "Denetimler ekleme ve bunların davranışlarını XAML Tasarımcısı'nda değiştirme | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a80fff74-bf01-41c9-ab85-ada7a873c3a9
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 09eb82bede66b839b7b3facdb61d8fc5d3ed2bd0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="insert-controls-and-modify-their-behavior-in-xaml-designer"></a>XAML Tasarımcısı'de denetimler ekleme ve bunların davranışlarını değiştirme
Denetimler kullanıcıların uygulamanızı ile etkileşim kurmasına olanak sağlar. Bunları gerçekleştirmek için de bilgi toplamak için kullanabileceğiniz bir nesne hale getirmeyi veya bir veri kaynağını sorgulaması gibi eylemler.  
  
 **Bu konuda:**  
  
-   [İçin çalışma yüzeyi denetimleri ekleme](#Insert)  
  
-   [Denetimlerin şeyler yapın](#Modify)  
  
##  <a name="Insert"></a>İçin çalışma yüzeyi denetimleri ekleme  
 Denetimlerden sürükleyebilirsiniz **varlıklar** üzerine panel **çalışma yüzeyi**ve bunları değiştirme **özellikleri** penceresi.  
  
 ![Harmanlama &#45; Varlıklar &#45; FlipView](../designers/media/blend_assetsflipview_xaml.png "blend_AssetsFlipView_XAML")  
  
 Bu video bazı yaygın denetimlerinin nasıl kullanıldığını gösterir.  
  
|Denetim|Kısa bir video izleyin|  
|-------------|-------------------------|  
|`Menu`![ ] (../designers/media/015a263c-0b2b-4253-ac57-b86fcb8c9591.png "015a263c-0b2b-4253-ac57-b86fcb8c9591")|![Yüklenen özellikleri yapılandırmak](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [denetimleri ekleme](https://www.youtube.com/watch?v=ra4AHfgD4Ys&list=PLBDF977B2F1DAB358&index=45)|  
|`Button`![ ] (../designers/media/05df1779-a68f-436b-b834-a91b7995a3ec.png "05df1779-a68f-436b-b834-a91b7995a3ec")|![Yüklenen özellikleri yapılandırmak](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [bir düğme tasarlama](http://www.popscreen.com/v/6A4gb/Microsoft-Expression-Blend-Designing-a-Button)|  
|`Textblock`![ ] (../designers/media/42165963-00f7-4a33-abcd-b0849edebada.png "42165963-00f7-4a33-abcd-b0849edebada")|![Yüklenen özellikleri yapılandırmak](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [bir textblock görüntüleri ekleme](http://www.popscreen.com/v/6A4du/Microsoft-Expression-Blend-Adding-Images-to-a-TextBlock)|  
|`Slider`![ ] (../designers/media/bf689d92-3c74-4218-815c-e98c930ac189.png "bf689d92-3c74-4218-815c-e98c930ac189")|![Yüklenen özellikler yapılandırma](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [bir araç ipucu içeren bir kaydırıcı derleme](http://www.bing.com/videos/search?q=slider%20expression%20blend&qs=n&form=QBVR&pq=slider%20expression%20blend&sc=1-23&sp=-1&sk=#view=detail&mid=F1BB7DB91B2772A8CA2AF1BB7DB91B2772A8CA2A)|  
|`GridSplitter`![ ] (../designers/media/d08d529f-a27e-4a8f-95aa-8a4e8b4ee7be.png "d08d529f-a27e-4a8f-95aa-8a4e8b4ee7be")|![Yüklenen özellikler yapılandırma](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [GridSplitter ile çalışma](http://msdn.microsoft.com/expression/cc188687.aspx)|  
  
### <a name="make-a-control-out-of-an-image-shape-or-path"></a>Bir görüntü, Şekil veya yolu dışında bir denetim olun  
 Herhangi bir nesne bir denetime yapabilirsiniz.  
  
 ![Harmanlama denetimi içine olun iletişim kutusu](../designers/media/blend_makeintocontrol_xaml.png "blend_MakeIntoControl_XAML")  
  
 Örneğin, bir sayfanın Center'da televizyon resmini düşünün. Denetimleri televizyon düğmeleri gibi ara küçük resimleri dışında hale getirebilir. Ardından, kullanıcıların kanalı değiştirmek için bu düğmeleri tıklayın.  
  
 Düğmeleri şimdi denetimleri olduğundan, bu mümkündür. Denetimler ile Kullanıcı etkileşimlerine yanıt verebilir; Bu durumda kullanıcı bir düğmesine tıkladığında.  
  
 Bir denetimi yapmak için bir nesne seçin. Ardından **Araçları** menüsünde tıklatın **olun denetim**.  
  
##  <a name="Modify"></a>Denetimlerin şeyler yapın  
 Kullanıcıların etkileşime girdiğinde denetimleri eylemleri gerçekleştirebilirsiniz. Örneğin, bunlar bir animasyon başlatabilir, bir veri kaynağını güncelleştirmek veya bir çalmasına.  
  
 Kullanım *Tetikleyicileri*, *davranışları*, ve *olayları* şeyler denetimleri yapma.  
  
### <a name="triggers"></a>Tetikleyiciler  
 A *tetikleyici* bir özelliğini değiştirir veya bir olay veya başka bir özellik değişikliği yanıt olarak bir görevi gerçekleştirir. Örneğin, kullanıcılar üzerine geldiğinizde düğme rengini değiştirebilirsiniz.  
  
 !["Tetikleyiciler" paneli](../designers/media/custom_button_blend_propertytriggerinfo.png "custom_button_blend_PropertyTriggerInfo")  
  
 **Kısa bir video izlemek:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [özellik tetikleyici eklemek](http://www.popscreen.com/v/6A4gO/Microsoft-Expression-Blend-Adding-a-Property-Trigger).  
  
### <a name="behaviors"></a>Davranışlar  
 A *davranışı* kod yeniden kullanılabilir bir pakettir. Bunu biraz yapmak birden fazla özelliklerini değiştirin. Sorgu veri hizmeti gibi eylemleri gerçekleştirebilirsiniz. Harmanlama küçük koleksiyonu bunları ile gelir ancak daha ekleyebilirsiniz. Çalışma yüzeyi herhangi bir nesne bir davranış sürükleyin ve sonra özelliklerini ayarlayarak davranışını özelleştirin.  
  
 ![Özellikleri panelinde FluidMoveBehavior](../designers/media/b4_fluidmovebehaviorproperties_sample.png "b4_FluidMoveBehaviorProperties_Sample")  
  
 **Kısa bir video izlemek:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Blend ipuçları: davranışları Kısım 1 için giriş](http://www.bing.com/videos/search?q=Expression%20blend%20behaviors&qs=n&form=QBVR&pq=expression%20blend%20behavior&sc=4-25&sp=-1&sk=#view=detail&mid=CF0DD797ED84DE740904CF0DD797ED84DE740904).  
  
### <a name="events"></a>Olaylar  
 Ultimate esneklik için işleme bir *olay*. Bazı kodlar yazmak zorunda kalırsınız.  
  
 **Kısa bir video izlemek:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [fare olayını eklemek](https://www.youtube.com/watch?v=2PMxAlb-x_E).