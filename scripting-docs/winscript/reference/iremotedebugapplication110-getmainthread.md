---
title: 'Iremotedebugapplication110:: GetMainThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::GetMainThread
ms.assetid: 9982acc9-3d35-4dcf-8ca9-662469de4072
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8e4ae024429702f3268a01c1e2e1fb4b40294d8
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985283"
---
# <a name="iremotedebugapplication110getmainthread"></a>IRemoteDebugApplication110::GetMainThread
[SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite)çağıran konaklar için ana iş parçacığını döndürür, aksi takdirde E_FAIL döndürür.  
  
> [!IMPORTANT]
> [IRemoteDebugApplication ARABIRIMI](../../winscript/reference/iremotedebugapplication-interface.md) PDM v 11.0 ve üzeri tarafından uygulanır. activdbg100.h içinde bulunur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetMainThread([out] IRemoteDebugApplicationThread **ppThread);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppThread`  
 dışı Ana [ıremotedebugapplicationthread arabirimi](../../winscript/reference/iremotedebugapplicationthread-interface.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IRemoteDebugApplication arabirimi](../../winscript/reference/iremotedebugapplication-interface.md)   
 [IRemoteDebugApplication110 Arabirimi](../../winscript/reference/iremotedebugapplication110-interface.md)