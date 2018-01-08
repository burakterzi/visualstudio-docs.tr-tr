---
title: StartTrackingContext | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
apiname: StartTrackingContext
apilocation: filetracker.dll
apitype: COM
helpviewer_keywords: StartTrackingContext
ms.assetid: 720cd295-38e7-4974-86db-b8106b1207ba
caps.latest.revision: "5"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 38a04c735584722ba2cac4f608cf558aae03382a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="starttrackingcontext"></a>StartTrackingContext
İzleme bağlamı başlatın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);  
```  
  
#### <a name="parameters"></a>Parametreler  
 [in]`intermediateDirectory`  
 İzleme günlüğü depolanacağı dizin.  
  
 [in]`taskName`  
 İzleme bağlamı tanımlar. Bu ad, günlük dosyası adı oluşturmak için kullanılır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir **HRESULT** ile **başarılı** izleme bağlamı oluşturduysanız biti ayarlanmamış.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** FileTracker.h