---
title: 'Hata: Web sunucusu Istenen kaynağı bulamadı | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e5c9b428a03595f387c5ff6fb6f0b8ca35172752
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737257"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Hata: Web Sunucusu İstenilen Kaynağı Bulamadı
Güvenlik konuları nedeniyle, IIS genel bir hata döndürdü.

Olası bir neden sunucunun güvenlik yapılandırması olabilir. IIS 6,0 ve önceki sürümler şüpheli ve hatalı biçimlendirilmiş istekleri filtrelemek için URLScan olarak bilinen bir eklenti programı kullandı. IIS 7,0 ' de aynı amaçla yerleşik Istek filtrelemesi vardır. Her iki durumda da aşırı kısıtlayıcı istek filtreleme, Visual Studio 'Nun sunucuda hata ayıklamasını engelleyebilir.

Bu hatanın bir diğer olası nedeni, IIS için W3SVC hizmetinin başlatılmamasına neden olur. Hizmetler penceresinde (*Services. msc*) Bu hizmetin başlatıldığını (gri) denetleyin.

Bu hatanın çok sayıda olası nedeni vardır. En yaygın nedenler, IIS yüklemesi veya yapılandırması, Web sitesi yapılandırması veya dosya sistemindeki izinlerle ilgili bir sorun içerir. Kaynağa bir tarayıcıyla erişmeyi deneyebilirsiniz. IIS 'nin nasıl yapılandırıldığına bağlı olarak, sunucuda yerel bir tarayıcı kullanmanız veya ayrıntılı bir hata iletisi almak için IIS hata günlüğünü incelemeniz gerekebilir.

 IIS sorunlarını giderme hakkında daha fazla bilgi için bkz. [IIS yönetimi ve yönetimi](/iis/manage/provisioning-and-managing-iis/iis-management-and-administration).

## <a name="see-also"></a>Ayrıca bkz.
- [Hata: Web Sunucusu Kilitli ve DEBUG Fiilini Engelliyor](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)