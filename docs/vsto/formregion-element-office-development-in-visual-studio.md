---
title: "&lt;formRegion&gt; öğesi (Visual Studio'da Office Geliştirme) | Microsoft Docs"
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
helpviewer_keywords: application manifests [Office development in Visual Studio], <formRegion> element
ms.assetid: d397cf31-c0ef-47f0-860a-cd816e4bf6eb
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: bc425459cee4b4398ead78939283ab4db6efc134
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltformregiongt-element-office-development-in-visual-studio"></a>&lt;formRegion&gt; öğesi (Visual Studio'da Office Geliştirme)
  `formRegion` Öğesinin `vstov4` ad alanı VSTO eklenti ile ilişkilendirilen bir Microsoft Office Outlook form bölgesi tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<formRegion  
  name>  
  <messageClass  
    name/>  
</formRegion>  
```  
  
## <a name="elements-and-attributes"></a>Öğeleri ve öznitelikleri  
 `formRegion` Öğesinin `vstov4` ad alanı Outlook VSTO eklenti ile ilişkili bir form bölgesi tanımlar. Yalnızca Outlook VSTO form bölgeleri içeren eklentileri için gereklidir.  
  
 Birden çok da olabilir `formRegion` içinde tanımlanan öğeleri bir `formRegions` öğesi için tek bir VSTO eklentisi.  
  
 `formRegion` Öğesi aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`name`|Gerekli. Form bölgesi adı tanımlar.|  
  
 `formRegion` Öğe aşağıdaki alt öğeleri vardır.  
  
### <a name="messageclass"></a>iletisınıfı  
 `messageClass` Öğesi form bölgesiyle ilişkilendirilen Outlook form tanımlar.  
  
 `messageClass` Öğesi aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`name`|Gerekli. Form bölgesiyle ilişkilendirilen form tanımlar.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği gösterilmektedir bir `formRegion` Outlook VSTO kullanılarak dağıtılan eklenti için bir uygulama bildirimi öğesinde [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Bu bir form bölgesini ile ilişkili üç ileti sınıfları vardır. Bu kod örneği sağlanan daha büyük bir örneğin parçasıdır [uygulama bildirimleri Office çözümleri için](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<vstov4:formRegion  
    name="OutlookAddIn1.FormRegion1">  
  <vstov4:messageClass name="IPM.Note" />  
  <vstov4:messageClass name="IPM.Contact" />  
  <vstov4:messageClass name="IPM.Appointment" />  
</vstov4:formRegion>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Outlook Form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)   
 [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)   
 [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Uygulama Bildirimi](/visualstudio/deployment/clickonce-application-manifest)  
  
  