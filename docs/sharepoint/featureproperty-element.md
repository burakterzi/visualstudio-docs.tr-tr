---
title: "FeatureProperty öğesi | Microsoft Docs"
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
helpviewer_keywords: FeatureProperty element
ms.assetid: 36a771a6-98d0-4a40-a278-d76baea82452
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0f1576c23b409226501637ada8d12d2320dd3c37
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="featureproperty-element"></a>FeatureProperty Öğesi
  SharePoint'e dağıtıldığında, sahip bir özellik bulunan özel bir özelliği temsil eder. Bir özellik dağıtıldıktan sonra kodunuzda özelliği erişebilirsiniz.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<FeatureProperty Key = "Key of the property value"  
    Value = "Property value" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|**Key**|Gerekli **xs: String** özniteliği.<br /><br /> Depolamak ve özellik değerini almak için kullanılan anahtar. Her bir özellik özellik içinde benzersiz olduğu bir anahtara sahip olmalıdır.|  
|**Değer**|Gerekli **xs: String** özniteliği.<br /><br /> Özellik değeri.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|SharePoint için dağıtıldığında sahip bir özellik dahil olan özellik değerlerini koleksiyonunu temsil eder.|  
  
## <a name="remarks"></a>Açıklamalar  
 Özellik özellikleri hakkında daha fazla bilgi için bkz: [sağlama paketleme ve dağıtım bilgileri proje öğelerinde](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Öğe Bilgisi  
  
|||  
|-|-|  
|**Namespace**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Şema adı**|SharePoint proje öğesi şeması|  
|**Dosya doğrulama**|ProjectItemModelSchema.xsd|  
|**Boş olamaz**|Hayır|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SharePoint proje öğesi şema başvurusu](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Proje Öğelerinde Paketleme ve Dağıtım Bilgileri Sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
  