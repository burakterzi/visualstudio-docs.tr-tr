---
title: 'Hata: uzak makine uzak bağlantılar iletişim kutusunda görünmüyor | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7d76bf1a889f7c91ced6b85ce16ebeb6e9a1b75
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737508"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Hata: uzak makine uzak bağlantılar iletişim kutusunda görünmüyor
Uzak makine uzak bağlantılar iletişim kutusunda görünmüyorsa, aşağıdaki genel nedenleri kontrol edin.

 Yönetilen Uyumluluk modu kullanıyorsanız, lütfen Visual Studio 2010 belgelerini denetleyin: [Uzaktan hata ayıklama sorunlarını giderme-Visual Studio 2010](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/2ys11ead(v=vs.100)).

### <a name="common-causes-for-this-error"></a>Bu hatanın yaygın nedenleri

- Uzak makine, farklı bir alt ağda bulunan bir makinede çalışıyor. Bu hatayı gidermek için, niteleyici iletişim kutusunda makine adını veya IP adresini el ile yazın

- Uzak makinede uzaktan hata ayıklayıcı çalışmıyor. Bu hatayı düzeltemedi, uzaktan hata ayıklayıcıyı başlatın.

- Güvenlik Duvarı, Visual Studio ile uzak makine arasındaki iletişimi engelliyor. Bu hatayı onarmak için, güvenlik duvarınızı Visual Studio ve uzaktan hata ayıklayıcı 'nın (msvsmon) iletişim kurmasına izin verecek şekilde yapılandırın.

- Virüsten koruma yazılımı, Visual Studio ile uzak makine arasındaki iletişimi engelliyor. Bu hatayı onarmak için, virüsten koruma yazılımını Visual Studio ve uzaktan hata ayıklayıcı 'nın (msvsmon) iletişim kurmasına izin verecek şekilde yapılandırın.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)