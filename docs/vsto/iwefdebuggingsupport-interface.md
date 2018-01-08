---
title: Iwefdebuggingsupport arabirimi | Microsoft Docs
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
ms.assetid: 0bd1c6a6-67a5-4478-b942-8b937b28f723
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 150c8794fb35ca017be7e0873dc0d1b84ebfc38c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iwefdebuggingsupport-interface"></a>IWefDebuggingSupport Arabirimi
  Visual hata ayıklama için Office uygulamaları kolaylaştırmak için Studio gibi bir hata ayıklama ortamı tarafından uygulanır. Word veya Excel gibi Office uygulamasının Visual Studio'dan bu arabirim alır ve yöntemleri bazı noktalarda arabirimde hata ayıklama oturumu sırasında çağırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[  
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),  
    oleautomation  
]  
interface IWefDebuggingSupport : IUnknown  
{  
    HRESULT SetWefProcessId(  
        [in] DWORD dwProcessId);  
    HRESULT GetAutoInsertExtensions(  
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);  
}  
```  
  
## <a name="methods"></a>Yöntemler  
 Aşağıdaki tabloda Iwefdebuggingsupport arabirimi tanımlar yöntemlerini listeler.  
  
|Ad|Açıklama|  
|----------|-----------------|  
|[GetAutoInsertExtensions Metodu](../vsto/getautoinsertextensions-method.md)|Hata ayıklama sırasında otomatik olarak eklenmesini olan Office için uygulamalar hakkındaki bilgileri alır.|  
|[SetWefProcessId Metodu](../vsto/setwefprocessid-method.md)|Web uzantılarının Framework (WEF) içerik çalışacak işlem tanımlayıcısını sağlar.|  
  
  