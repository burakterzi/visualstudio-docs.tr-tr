---
title: "Nasıl yapılır: eşlenmiş klasörler ekleyip | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.Project.MappedFolder
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, mapped folders
- mapped folders [SharePoint development in Visual Studio]
ms.assetid: 115c8b00-7d4c-4fbe-b42c-e82dca944504
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1d9ec0e71977f48519077c5f50bfab0ae69141c0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-and-remove-mapped-folders"></a>Nasıl yapılır: Eşlenmiş Klasörler Ekleme ve Kaldırma
  Görüntüleri ve düzenleri, son derece katıştırılmış dosya hiyerarşisinde gibi bazı yaygın olarak SharePoint, klasörlerde kullanılır. Bu klasörler daha kolay erişmek için bir SharePoint projesine eşleyebilirsiniz. Eşlenen klasörler SharePoint Server yüklemesinde dosyalarının fiziksel konuma karşılık gelen SharePoint Proje klasörlerdir.  
  
 Bir SharePoint uygulama dağıttığınızda, eşlenmiş klasörü ve tüm alt çözüm paketi (.wsp) sunucusuna kopyalanır içeriğini, SharePoint ve SharePoint klasör ağacında belirtilen konumda çalışıyor. Bu konumu tarafından belirlenir **dağıtım konumu** eşlenen klasörü için ayarlanmış özelliği. Göreli olarak eşlenmiş klasöründeki tüm alt olan **dağıtım konumu** eşlenen klasörünün. Unutmayın **dağıtım konumu** özelliği, eşlenmiş klasörü adını değil öğeleri dağıtıldığı belirler.  
  
 Menü çubuğu veya kısayol menüsünde Proje için komutları kullanarak bir projeye eşlenen klasörler ekleyebilirsiniz. Kullanabilirsiniz **SharePoint Ekle "Görüntüleri" eşlenen klasörü** ve **SharePoint Ekle "Düzenleri" klasörü** olanlar eklemek için komutları eşlenen en sık kullanılan klasörleri. Kullanarak diğer kullanılabilir SharePoint klasörlerden herhangi biri projenize eşleyebilirsiniz **SharePoint eşlenen klasörü Ekle** komut için kısayol menüsünde ve klasörlerde belirterek **SharePoint eşlenen klasörü Ekle** iletişim kutusu.  
  
## <a name="adding-mapped-folders-to-a-project"></a>Bir projeye eşlenmiş klasörler ekleme  
 Aşağıdaki yordam, visual web bölümü projeye iki eşlenen klasörler eklemeyi açıklar. Başlamak için bir visual web bölümü projesi oluşturun.  
  
#### <a name="to-add-mapped-folders-to-a-project"></a>Eşlenen klasörler için bir proje eklemek için  
  
1.  Menü çubuğunda seçin **dosya**, **yeni**, **proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunda, genişletin **Visual Basic** veya **Visual C#** düğümü genişletin **Office/SharePoint** düğümünü ve ardından seçin **SharePoint çözümlerini** düğümü.  
  
3.  Proje şablonları listesinden seçip **SharePoint 2013 Visual Web Bölümü** şablonu.  
  
4.  İçinde **adı** kutusuna **TestProject1**ve ardından **Tamam** düğmesi.  
  
5.  İçinde **SharePoint Özelleştirme Sihirbazı'nı**, seçin **son** varsayılan ayarları korumak için düğmesi.  
  
6.  İçinde **Çözüm Gezgini**, proje düğümünü seçin ve ardından, menü çubuğunda, **proje**, **SharePoint Ekle "Görüntüleri" eşlenen klasörü**.  
  
     Adlı bir klasör **görüntüleri** projenizde görünür ve TestProject1 adlı bir alt klasör içerir. Bu eşlenen klasör visual web bölümü projesi için görüntüleri içerir.  
  
7.  İçinde **Çözüm Gezgini**, proje düğümünü seçin ve ardından, menü çubuğunda, **proje**, **SharePoint eşlenen klasörü Ekle** görüntülenecek **Ekle SharePoint eşlenen klasörü** iletişim kutusu.  
  
8.  Eşleştirme için kullanılabilir olmayan Çalışma klasörleri ağaç görünümünde seçin **kaynakları** klasörünü ve ardından **Tamam** düğmesi.  
  
     Adlı bir klasör **kaynakları** projenizde görüntülenir. Bu klasör, dize kaynak dosyaları gibi öğeleri depolayabilirsiniz. Alt klasörleri eşlenen bir klasörün içeriğini düzenlemek için yararlı olabilir, ancak kullanarak eşlenmiş bir klasör eklediğinizde, bunlar otomatik olarak oluşturulmuştur **SharePoint eşlenen klasörü Ekle** komutu. Bir alt klasör eklemek için **kaynakları** klasörünü ve ardından, menü çubuğunda, **proje**, **yeni klasör**.  
  
## <a name="changing-the-deployment-location-of-a-mapped-folder"></a>Eşlenmiş bir klasörde dağıtım konumunu değiştirme  
 Varsayılan olarak, belirli konumlara {SharePointRoot} belirteci gösterir SharePoint kök yükleme yolu göreli eşlenen klasörler eklenir. Ancak, bu konum değiştirerek değiştirebileceğiniz **dağıtım konumu** eşlenen klasörünün özelliği. Her eşlenmiş klasörü kendi sahip **dağıtım konumu** özelliği.  
  
#### <a name="to-change-the-deployment-location-of-a-mapped-folder"></a>Eşlenmiş bir klasörde dağıtım konumunu değiştirmek için  
  
1.  Daha önce oluşturduğunuz projede eşlenmiş bir klasör seçin.  
  
2.  İçinde **özellikleri** penceresinde, üç nokta seçin (![ASP.NET Mobil Tasarımcı elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil Tasarımcı elips")) düğmesini **dağıtımı Konum** özelliği.  
  
3.  İçinde **SharePoint eşlenen klasörü Ekle** iletişim kutusunda, işaret edecek şekilde eşlenmiş klasörü istediğiniz klasöre gözatın.  
  
4.  Düğümü seçin ve ardından **Tamam** düğmesi.  
  
## <a name="renaming-or-removing-mapped-folders"></a>Yeniden adlandırma veya eşlenen Klasörler kaldırılıyor  
  
#### <a name="to-rename-or-remove-a-mapped-folder"></a>Yeniden adlandırmak veya eşlenmiş bir klasör kaldırmak için  
  
1.  Daha önce oluşturduğunuz projede eşlenmiş bir klasör seçin.  
  
2.  Eşlenen klasörü yeniden adlandırmak için kısayol menüsünü açın, seçin **yeniden adlandırma**, yeni bir ad girin ve ardından Enter tuşuna seçin.  
  
     Alternatif olarak, yeniden adlandırmak, açmak istediğiniz eşlenmiş klasörü seçebilirsiniz **özellikleri** penceresinde ve değeri ayarlayın **klasör adı** özelliği için yeni bir ad.  
  
3.  Eşlenmiş bir klasörde projeden kaldırmak için kısayol menüsünü açın, seçin **silmek**ve ardından **Tamam** kaldırma işlemini onaylamak için iletişim kutusunda düğme.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SharePoint Çözümleri Geliştirme](../sharepoint/developing-sharepoint-solutions.md)  
  
  