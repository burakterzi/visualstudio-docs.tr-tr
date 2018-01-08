---
title: "GetFrameworkPath görevi | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkPath task [MSBuild]
- MSBuild, GetFrameworkPath task
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
caps.latest.revision: "11"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ba676aa3aeef0cffb5b6de6b086c7a75c5ffb458
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="getframeworkpath-task"></a>GetFrameworkPath Görevi
Yolunu alır [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] derlemeler.  
  
## <a name="task-parameters"></a>Görev parametreleri  
 Aşağıdaki tabloda parametrelerinin açıklanmaktadır `GetFrameworkPath` görev.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`FrameworkVersion11Path`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Framework sürüm 1.1 derlemeleri için yolu varsa içeriyor. Aksi takdirde döndürür `null`.|  
|`FrameworkVersion20Path`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Framework sürüm 2.0 derlemeleri için yolu varsa içeriyor. Aksi takdirde döndürür `null`.|  
|`FrameworkVersion30Path`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Framework sürüm 3.0 derlemeleri için yolu varsa içeriyor. Aksi takdirde döndürür `null`.|  
|`FrameworkVersion35Path`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Framework sürüm 3.5 derlemeleri için yolu varsa içeriyor. Aksi takdirde döndürür `null`.|  
|`FrameworkVersion40Path`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Framework sürüm 4.0 derlemeleri için yolu varsa içeriyor. Aksi takdirde döndürür `null`.|  
|`Path`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Varsa son framework derlemeleri yolunu içerir. Aksi takdirde döndürür `null`.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çeşitli sürümleri [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] olan yüklüyse, bu görev sürüm döndüren [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] üzerinde çalışmak üzere tasarlanmıştır.  
  
 Yukarıda listelenen parametreleri ek olarak, bu görev parametrelerinden devralır <xref:Microsoft.Build.Tasks.TaskExtension> sınıfı, kendisi <xref:Microsoft.Build.Utilities.Task> sınıfı. Bu ek parametreler ve açıklamalarının listesi için bkz: [TaskExtension taban sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `GetFrameworkPath` yolunu depolamak için görev [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] içinde `FrameworkPath` özelliği.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="FrameworkPath" />  
        </GetFrameworkPath>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevler](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)