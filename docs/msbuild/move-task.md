---
title: "Taşıma görevi | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Move task
- Move task [MSBuild]
ms.assetid: d1405347-1309-4f18-b565-905408093d59
caps.latest.revision: "4"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 521a5239e47ffcab4d93c2cd2a46c30f881b0abd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="move-task"></a>Taşıma Görevi
Dosyayı yeni bir konuma taşır.  
  
## <a name="parameters"></a>Parametreler  
 Parametreleri ayarlayamadı tablo açıklar `Move` görev.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`DestinationFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Kaynak dosyaların taşınacağı dosyaların listesini belirtir. Bu liste belirtilen listesine bire bir eşleme olması bekleniyor `SourceFiles` parametresi. Diğer bir deyişle, belirtilen ilk dosya `SourceFiles` belirtilen ilk konumuna taşınır `DestinationFiles`, vb.|  
|`DestinationFolder`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Dosyaları taşımak istediğiniz dizini belirtir.|  
|`MovedFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Başarıyla taşındı öğeleri içerir.|  
|`OverwriteReadOnlyFiles`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, salt okunur dosyalar işaretlenmiş olsa bile dosyaların üzerine yazar.|  
|`SourceFiles`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Dosyaların belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Her iki `DestinationFolder` parametresi veya `DestinationFiles` parametresi belirtilen, ancak her ikisi de olmalıdır. Eğer her ikisi de belirtilirse görev başarısız olur ve bir hata günlüğe kaydedilir.  

 `Move` Görev istenen hedef dosyaları için gerekli olarak klasörler oluşturur.

 Tabloda listelenen parametreleri sahip olmaya ek olarak, bu görev parametrelerinden devralır <xref:Microsoft.Build.Tasks.TaskExtension> sınıfı, kendisi <xref:Microsoft.Build.Utilities.Task> sınıfı. Bu ek parametreler ve açıklamalarının listesi için bkz: [TaskExtension taban sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevler](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)