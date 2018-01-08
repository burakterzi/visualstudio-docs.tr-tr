---
title: "Visual Studio'da çözümler ve projeler oluşturma | Microsoft Docs"
ms.custom: 
ms.date: 06/16/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.openprojectfromweb
- vs.newproject
- VS.ToolsOptionsPages.Projects.General
- SolutionItemsProject
helpviewer_keywords:
- solutions [Visual Studio], deleting
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d6e879e8708c55ebb5ebdd5980bd70ea1e4a97d2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="create-solutions-and-projects"></a>Çözümler ve projeler oluşturma

*Projeleri* kaynak kodu dosyaları, bit eşlemler, simgeler gibi ve uygulamanızı oluşturmak için gereken öğeleri tutun Visual Studio ve bileşen ve hizmet başvurular mantıksal kapsayıcılardır. Yeni bir proje oluşturduğunuzda, Visual Studio oluşturur bir *çözüm* proje içerecek şekilde. İsterseniz diğer yeni veya mevcut projeleri çözüme daha sonra ekleyebilirsiniz. Çözümleri de belirli bir projeye bağlı olmayan dosyalar içerebilir.

![Çözüm/proje hiyerarşisi](./media/vside-proj-soln.png)

Çözümler ve projeler adlı bir araç penceresinde görüntüleyebilirsiniz **Çözüm Gezgini**. Aşağıdaki ekran görüntüsünde iki proje içeren bulunan Çözüm Gezgini'nde (UWP BikeSharing.Xamarin) örnek bir çözüm gösterilmektedir: BikeSharing.Clients.Core ve BikeSharing.Clients.Windows. Her proje birden çok dosyaları, klasörleri ve başvurular içerir. Kalın yazı tipiyle proje adı *başlangıç projesi*; diğer bir deyişle, uygulamayı çalıştırdığınızda başlayan projesi. Başlangıç projesi projedir belirtebilirsiniz.

![Çözüm Gezgini projeleri](./media/vside-solution-explorer-projects.png)

Gerekli dosyaları ekleyerek kendiniz bir proje oluşturabileceğiniz olsa da, Visual Studio Proje şablonları bir başlangıç vermek için seçimi sunar. Bir şablondan yeni bir proje oluşturmak, essentials sahip bir proje için bu proje türü sağlar ve dosyalarını yeniden adlandırın ya da yeni veya var olan kod ve diğer kaynakları gerektiği gibi ekleyin.

Başka bir deyişle, çözümler ve projeler Visual Studio'daki uygulamaları geliştirmek için gerekli değildir. Ayrıca üzerinden kopyalanması veya başka bir yerde indirilen kod açabilirsiniz. Daha fazla bilgi için bkz: [projeleri veya çözümler olmadan kod Visual Studio geliştirme](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

> [!NOTE]
> Bu konudaki açıklamaları Visual Studio Community edition temel alır. İletişim kutuları ve menü komutlarını gördüğünüz ayarları veya Visual Studio sürümü bağlı olarak burada açıklananlar farklılık gösterebilir. Ayarlarınızı, örneğin değiştirmek için **genel** veya **Visual C++** ayarları seçebilirsiniz **Araçları**, **içeri ve dışarı aktarma ayarları**ve ardından seçin **tüm ayarlara**.

## <a name="to-create-a-project-from-a-project-template"></a>Bir proje şablonu bir proje oluşturmak için

1. Visual Studio'da yeni bir proje oluşturmak için birden çok yolu vardır. Başlangıç sayfasında, bir proje şablonu adını **arama proje şablonları** kutusunda ya da seçin **yeni proje oluştur** açmak için bağlantı **yeni proje** iletişim kutusu. Ayrıca seçebilirsiniz **dosya**, **yeni**, **proje...**  menüsünde çubuğunu ya da seçin **yeni proje** araç çubuğunda.

  ![Başlangıç sayfası](./media/vside-newproject1.png)

  İçinde **yeni proje** iletişim kutusu, kullanılabilir proje şablonları görünür altında bir listede **şablonları** kategorisi. Şablonları programlama dili ve Visual C#, JavaScript ve Azure Data Lake gibi proje türüne göre düzenlenir.

  ![Yeni Proje iletişim kutusu](./media/vside-newproject-templates-list.png)

  > [!NOTE]
  > Görüntülenen listede kullanılabilir diller ve proje şablonları kullanmakta olduğunuz Visual Studio ve yüklü iş yükleri sürümüne bağlıdır. Ek iş yüklerinin yükleme hakkında bilgi edinmek için [değiştirmek Visual Studio iş yükleri ve bileşenleri ekleyerek veya kaldırarak tarafından 2017](../install/modify-visual-studio.md).

1. Dil adının yanındaki üçgen seçerek kullanmak istediğiniz programlama dili için şablonları listesini görüntüleyin ve bir proje türü seçin.

  Aşağıdaki örnek Visual C# web projeleri için kullanılabilir proje şablonları gösterir.

  ![Proje şablonları](./media/vside-newproject-projects-list.png)

1. Yeni proje için bir ad girin **adı** kutusu. Sisteminizde varsayılan konumda projeyi kaydedin veya seçmek seçebileceğiniz **Gözat** başka bir konum bulmak için düğmesi.

  Ayrıca isteğe bağlı olarak çözüm adını değiştirin veya yeni proje için bir Git deposu seçerek eklemek seçebileceğiniz **eklemek için kaynak denetimi**.

1. Seçin **Tamam** çözüm ve proje oluşturmak için düğmesi.

1. Ek bir proje çözüme eklemek istiyorsanız, Çözüm Gezgini'nde çözüm düğümünü seçin ve menü çubuğunda, ardından **proje**, **Yeni Öğe Ekle**.

## <a name="create-a-project-from-existing-code-files"></a>Varolan kod dosyalarından proje oluşturma

Kod kaynak dosyaları koleksiyonu varsa, bunları projeye kolayca ekleyebilirsiniz.

1. Menüsünde, **dosya**, **yeni**, **proje ilk var olan kodu**.

1. İçinde **varolan kod dosyalarından proje oluştur** Sihirbazı'nı istediğiniz proje türü seçin **ne tür bir proje oluşturmak ister misiniz?** aşağı açılan liste kutusunu ve ardından **sonraki**  düğmesi.

1. Sihirbazı'nda, dosyaların konumuna göz atın ve ardından yeni projede için bir ad girin **adı** kutusu. İşiniz bittiğinde seçin **son** düğmesi.

> [!NOTE]
> Bu seçenek, dosyaların görece basit koleksiyonlar için en iyi çalışır. Şu anda yalnızca Visual C++, Apache Cordova, Visual Basic ve Visual C# proje türleri desteklenir.

## <a name="add-files-to-a-solution"></a>Bir çözüme dosyaları ekleme

Birden çok proje için geçerli bir dosya varsa, belirli bir proje altında daha sonra bunları çözüme ekleyebilirsiniz yerine çözüm için Benioku dosyası ya da diğer dosyaları gibi mantıksal olarak çözüm düzeyinde ait. Çözüm, çözüm düğümünün (sağ tıklatma) bağlam menüsünde bir öğe eklemek için **Çözüm Gezgini**, seçin **Ekle**, **yeni öğe**, veya **Ekle**, **Varolan öğeyi**.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Belirli bir .NET Framework sürümünü hedefleyen bir .NET projesi oluşturma

Bir proje oluşturduğunuzda, belirli bir sürümünü kullanmak için proje istediğiniz .NET Framework'ün belirtebilirsiniz. .NET framework sürüm belirtmek için **.NET Framework** sürümü açılır menüde **yeni proje** iletişim kutusu.

![.NET framework sürüm Seçici](./media/vside-newproject-framework.png)

> [!NOTE]
> Proje .NET Core şablonu oluşturuyorsanız, açılan seçtiğiniz .NET Framework sürüm göz ardı edilir.

> [!TIP]
> Bir proje şablonu seçmeden önce .NET Framework sürümünü ayarlarsanız, Visual Studio yalnızca o .NET Framework sürümü ile uyumlu şablonları göster.

.NET Framework sürümlerini .NET Framework 4'ten önceki erişmek için .NET Framework 3.5, sisteminizde yüklü olması gerekir.

## <a name="create-empty-solutions"></a>Boş çözümleri oluşturma

Projeleri olmayan boş çözümleri de oluşturabilirsiniz. Bu çözüm ve baştan projeleri oluşturmak istediğiniz durumlarda tercih edilebilir.

### <a name="to-create-an-empty-solution"></a>Boş bir çözüm oluşturmak için

1. Menüsünde, **dosya**, **yeni**, **proje...** .

1. Sol (**şablonları**) bölmesinde seçin **diğer proje türleri**, **Visual Studio çözümleri** genişletilmiş listesinde.

1. Orta bölmede seçin **boş çözüm**.

1. Girin **adı** ve **konumu** , çözümünüz için değerler seçin **Tamam**.

Boş bir çözüm oluşturduktan sonra yeni veya mevcut projeleri veya öğeleri için seçerek ekleyebileceğiniz **Yeni Öğe Ekle** veya **varolan öğeyi Ekle** üzerinde **proje** menüsü.

Proje ya da çözüm gerek kalmadan, daha önce belirtildiği gibi kod dosyaları açabilirsiniz. Bu şekilde kodu geliştirme hakkında bilgi edinmek için [projeleri veya çözümler olmadan kod Visual Studio geliştirme](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="create-a-temporary-project-c-and-visual-basic"></a>(C# ve Visual Basic) geçici bir proje oluşturun

Oluşturduğunuz bir. Proje NET tabanlı bir disk konumu belirtmeden geçici bir proje mi. Geçici projeler .NET projelerle denemek etkinleştirin. Geçici bir projeyle çalışırken herhangi bir zamanda kaydetmek veya atmak tercih edebilirsiniz.

Geçici bir proje oluşturmak için ilk Git **Araçları**, **seçenekleri**, **projeler ve çözümler**, **genel**ve işaretini**Oluşturduğunuzda Yeni projeler Kaydet** onay kutusu. Ardından açın **yeni proje** iletişim kutusunda her zamanki gibi.

## <a name="delete-a-solution-project-or-item"></a>Çözüm, proje veya öğesini sil

Çözümler ve içeriklerini kalıcı olarak silebilir ancak Visual Studio IDE kullanarak değil. Visual Studio içindeki öğeleri silme yalnızca bunları geçerli çözüme ya da projeye kaldırır. Bir çözüm ya da başka bir bileşeni, sistemden kalıcı olarak silmek mi .sln ve .suo çözüm dosyalarını içeren klasörü silmek için dosya Gezgini'ni kullanın. Ancak, bir çözümü kalıcı olarak silmeden önce yeniden gerektiğinde tüm projeleri veya dosyaları yedekle önerilir.

> [!NOTE]
> .Suo dosyanın varsayılan dosya Gezgini ayarlar altında görüntülenmeyen gizli bir dosyadır. Gizli dosyaları göstermek için **Görünüm** menüsünde dosya Gezgini'nde, select **gizli öğeleri** onay kutusu.

### <a name="to-permanently-delete-a-solution"></a>Bir çözümü kalıcı olarak silmek için

1. İçinde **Çözüm Gezgini**, silmek istediğiniz çözüm bağlam menüsünde seçin **dosya Gezgini'nde klasör Aç**.

1. Dosya Gezgini'nde, bir düzey yukarı gidin.

1. Çözümü içeren klasörü seçin ve ardından **silmek** anahtarı.

## <a name="see-also"></a>Ayrıca bkz.

[Çözümler ve projeler](../ide/solutions-and-projects-in-visual-studio.md)  
[Microsoft'un açık kaynak depoları github'da](https://github.com/Microsoft)  
[Visual Studio Örnekleri](../ide/visual-studio-samples.md)  
[Geliştirici kod örnekleri](https://code.msdn.microsoft.com/)  