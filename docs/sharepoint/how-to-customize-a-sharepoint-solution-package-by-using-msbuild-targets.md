---
title: "Nasıl yapılır: MSBuild hedeflerini kullanarak SharePoint çözüm paketini özelleştirme | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, packages
ms.assetid: 7fa6a276-04c8-463e-be95-57c2c6240d76
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4c0fbc4a2feb3abc92c47567dcb0ea3d425ddda1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets"></a>Nasıl yapılır: MSBuild Hedeflerini Kullanarak SharePoint Çözüm Paketini Özelleştirme
  Bir komut isteminde MSBuild hedeflerini kullanarak SharePoint paket dosyalarını (.wsp) Visual Studio nasıl oluşturduğunu özelleştirebilirsiniz. Örneğin, paketleme Ara dizin ve numaralandırılmış dosyaları belirtin MSBuild öğesi gruplarını değiştirmek için MSBuild özelliklerini özelleştirebilirsiniz.  
  
## <a name="customizing-and-running-msbuild-targets"></a>Özelleştirme ve MSBuild hedefleri çalıştırma  
 BeforeLayout ve AfterLayout hedefleri özelleştirirseniz önce paket düzeni, ekleme, kaldırma veya paketlenirler dosyalarını değiştirme gibi görevleri gerçekleştirebilirsiniz.  
  
#### <a name="to-customize-the-beforelayout-target"></a>BeforeLayout hedef özelleştirmek için  
  
1.  Not Defteri gibi bir düzenleyicisini açın ve aşağıdaki kodu ekleyin.  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <Target Name="BeforeLayout">  
        <Message Importance="high" Text="In the BeforeLayout Target"></Message>  
      </Target>  
    </Project>  
    ```  
  
     Bu örnekte bu hedef paketleme önce bir ileti görüntüler.  
  
2.  Dosya adı **CustomLayout.SharePoint.targets**ve SharePoint proje klasörüne kaydedin.  
  
3.  Projeyi açın, kendi kısayol menüsünü açın ve ardından **projeyi**.  
  
4.  İçinde **Çözüm Gezgini**projesi için kısayol menüsünü açın ve ardından **Düzenle***ProjectName***.vbproj** veya **Düzenle***ProjectName***.csproj**.  
  
5.  Sonra `Import` satır proje dosyasının sonuna yakın, aşağıdaki satırı ekleyin.  
  
    ```  
    <Import Project="CustomLayout.SharePoint.targets" />  
    ```  
  
6.  Proje dosyasını kaydedip kapatın.  
  
7.  İçinde **Çözüm Gezgini**projesi için kısayol menüsünü açın ve ardından **projeyi yeniden yükle**.  
  
 Proje yayımladığınızda, paketleme başlamadan önce ileti çıkışında görünür.  
  
#### <a name="to-customize-the-afterlayout-target"></a>AfterLayout hedef özelleştirmek için  
  
1.  Menü çubuğunda seçin **dosya**, **açık**, **dosya**.  
  
2.  İçinde **açık dosya** iletişim kutusu, proje klasöre gidin, CustomLayout.target dosyayı seçin ve ardından **açık** düğmesi.  
  
3.  Hemen önce `</Project>` etiketi, aşağıdaki kodu ekleyin:  
  
    ```  
    <Target Name="AfterLayout">  
      <Message Importance="high" Text="In the AfterLayout Target"></Message>  
    </Target>  
    ```  
  
     Bu hedef paketlenmiş sonra bu örnek bir ileti görüntüler.  
  
4.  Hedefleri dosyasını kaydedip kapatın.  
  
5.  Visual Studio'yu yeniden başlatın ve sonra projeyi açın.  
  
 Proje yayımladığınızda, paketleme başlamadan önce BeforeLayout iletisi görüntülenir ve paketleme bittikten sonra AfterLayout ileti görüntülenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SharePoint Çözümlerini Paketleme ve Dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  