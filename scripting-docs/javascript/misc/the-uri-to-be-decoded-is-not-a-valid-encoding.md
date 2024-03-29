---
title: Kodu çözülecek URI geçerli bir kodlama değil | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5025
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 99df8739137971e32c14f265460ff3f4a9c03816
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572259"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>Kodu çözülecek URI geçerli bir kodlamada değil
Yanlış biçimlendirilmiş bir URI 'yi (Tekdüzen Kaynak tanımlayıcısı) çözmeye çalıştınız. URI 'Ler özel bir sözdizimine sahiptir; bir URI 'de kullanılmadan önce, alfasayısal olmayan çoğu karakter kodlanmalıdır. Normal bir [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] dizesinden bir URI oluşturmak için `encodeURI` ve `encodeURIComponent` yöntemlerini kullanabilirsiniz.  
  
 Bütün bir URI, bileşen ve ayırıcıların sırasından oluşur. Genel form:  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Açılı ayraçlar içindeki adlar bileşenleri temsil eder ve ":", "/", ";" ve "?", ayırıcı olarak kullanılan ayrılmış karakterlerdir.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Yalnızca geçerli URI 'Leri çözmeye çalışırken emin olun. Normal [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] dizelerinin kodunu çözemezsiniz, çünkü geçersiz karakterler içeriyor olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [decodeURI işlevi](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent İşlevi](../../javascript/reference/decodeuricomponent-function-javascript.md)