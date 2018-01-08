---
title: "Korumalı arasındaki farklar ve Grup çözümleri | Microsoft Docs"
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
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
ms.assetid: 43beb7e7-0cd9-4a8f-bb72-6b1e0cba5be8
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6c13d27f8c79f1bc638741d8877ac95a0dff4885
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>Korumalı Çözümler ve Grup Çözümleri Arasındaki Farklılıklar
  Bir SharePoint çözüm derlediğinizde, SharePoint sunucusuna dağıtır ve hata ayıklamak için bir hata ayıklayıcı ekler. Çözüm hata ayıklamak için kullanılan işlem Korumalı çözüm özelliğinin ayarına bağlıdır: Korumalı çözüm ya da Grup çözümü.  
  
 Daha fazla bilgi için bkz: [Korumalı çözüm değerlendirmeleri](../sharepoint/sandboxed-solution-considerations.md).  
  
## <a name="farm-solutions"></a>Küme çözümleri  
 IIS çalışan işlemi (W3WP.exe) barındırılan, küme çözümleri tüm grubu etkileyebilir kodu çalıştırın. SharePoint geri çeker veya IIS çalışan işlem tarafından kilitlenmiş dosyaları bırakılamıyor amacıyla özellik dağıtır önce korumalı Çözümle özelliği "grubu çözüm için" olarak ayarlanmış bir SharePoint projenin hata ayıklamasını yaparken, sistemin IIS uygulama havuzu geri dönüştürüldüğünde. SharePoint Proje site URL'si hizmet veren yalnızca IIS uygulama havuzu geri dönüştürülmeden.  
  
## <a name="sandboxed-solutions"></a>Korumalı alana alınan çözümler  
 SharePoint kullanıcı kodu çözüm çalışan işlem (SPUCWorkerProcess.exe) barındırılan, korumalı çözümler yalnızca çözüm site koleksiyonunu etkileyebilir kodu çalıştırın. Korumalı çözümler IIS çalışan işlemindeki çalıştırmayın çünkü IIS uygulama havuzu ne IIS sunucusunu yeniden başlatmanız gerekir. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]hata ayıklayıcı SharePoint SPUserCodeV4 hizmetinde otomatik olarak tetikler SPUCWorkerProcess işlemi ve denetimleri ekler. Çözüm en son sürümünü yüklemek için Geri Dönüşüm SPUCWorkerProcess işlemi için gerekli değildir.  
  
## <a name="either-type-of-solution"></a>Her iki tür bir çözüm  
 Her iki çözüm türüyle [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ayrıca istemci tarafı komut dosyası hata ayıklamayı etkinleştirmek için tarayıcıya hata ayıklayıcı ekler. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Bu amaçla altyapısı ayıklamasını kullanır. Komut dosyası hata ayıklamayı etkinleştirmek için istendiğinde varsayılan tarayıcı ayarlarını değiştirmeniz gerekir.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]hata ayıklayıcı geçerli site çalıştıran yalnızca W3WP veya SPUCWorkerProcess işlemleri için ekler. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Ayrıca yönetilen COM Plus ve iş akışı motorları hata ayıklama ekler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SharePoint çözümlerinde hata ayıklama](../sharepoint/debugging-sharepoint-solutions.md)   
 [Derleme ve SharePoint çözümlerini hata ayıklama](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Korumalı Çözümle İlgili Konular](../sharepoint/sandboxed-solution-considerations.md)  
  
  