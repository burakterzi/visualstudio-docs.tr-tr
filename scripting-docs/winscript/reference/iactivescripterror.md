---
title: Iactivescripterror | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptError interface
ms.assetid: c8e0288d-38ff-4145-a7e3-f8cdfb72eefe
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca4d3fe5ff90fc0d116814771308fa599052dba9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576897"
---
# <a name="iactivescripterror"></a>IActiveScriptError
Komut dosyası altyapısı işlenmemiş bir hatayla karşılaştığında, bu arabirimi uygulayan bir nesne [IActiveScriptSite:: OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md) yöntemine geçirilir. Daha sonra ana bilgisayar, oluşan hata hakkında bilgi edinmek için bu nesnedeki yöntemleri çağırır.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IActiveScriptError::GetExceptionInfo](../../winscript/reference/iactivescripterror-getexceptioninfo.md)|Bir hata hakkındaki bilgileri alır.|  
|[IActiveScriptError::GetSourcePosition](../../winscript/reference/iactivescripterror-getsourceposition.md)|Kaynak koddaki bir hata oluştuğunda konumunu alır.|  
|[IActiveScriptError::GetSourceLineText](../../winscript/reference/iactivescripterror-getsourcelinetext.md)|Kaynak dosyada bir hata oluştuğu satırı alır.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Etkin Betik Arabirimleri](../../winscript/reference/active-script-interfaces.md)