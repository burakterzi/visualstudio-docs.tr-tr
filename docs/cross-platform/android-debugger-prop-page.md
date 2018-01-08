---
title: "Android hata ayıklayıcıyı özellikleri (C++) | Microsoft Docs"
ms.custom: 
ms.date: 10/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
author: corob
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.workload: xplat-cplusplus
ms.openlocfilehash: d8caf579aa73a77f3c20162ae775411df551f373
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="android-debugger-properties"></a>Android hata ayıklayıcıyı özellikleri

Özellik | Açıklama | Seçenekler
--- | ---| ---
Hata ayıklayıcı türü | Hata ayıklama için hangi kod türünü belirtir. | **Yalnızca yerel**<br>**Java yalnızca**<br>
Hedef hata ayıklama | Öykünücü veya aygıt hata ayıklama için kullanılacak belirtir. Hiçbir Öykünücüler çalıştırıyorsanız, 'Android sanal cihazı (AVD) Yöneticisi' Lütfen kullanan bir cihazı başlatmak için.
Paket başlatmak için | Hata ayıklaması .apk konumunu belirtir. Uygulama hata ayıklaması sırasında belirli paket (APK) başlaması gerektiğini belirtmek için bu seçeneği belirleyin.
Etkinlik Başlat | Uygulamayı başlatmak için kullanılacak Android etkinlik bildiriminde kullanılanla eşleşen gerekiyor. AndroidManifest.xml listesini almak ve dinamik olarak doldurmak için Uygula'e basın.
Ek sembol arama yolları | Hata ayıklama simgeleri için ek arama yolu.
Ek Java kaynak arama yolları | Java kaynak dosyaları için ek arama yolları. (Yalnızca hata ayıklayıcı türü yalnızca Java olduğunda geçerlidir.)