---
title: 'CA2003: lifleri görmeyin iş parçacığı olarak davranmayın | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 943b52f9703e60f14756bde97ce6f27c0c6f5296
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672510"
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003: Lifleri iş parçacığı olarak görmeyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotTreatFibersAsThreads|
|CheckId|CA2003|
|Kategori|Microsoft. güvenilirliği|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Yönetilen bir iş parçacığı Win32 iş parçacığı olarak kabul ediliyor.

## <a name="rule-description"></a>Kural Tanımı
 Yönetilen bir iş parçacığının Win32 iş parçacığı olduğunu varsaymayın. Bu bir fiber ' dır. Ortak dil çalışma zamanı (CLR), yönetilen iş parçacıklarını SQL 'e ait gerçek iş parçacıkları bağlamında lifleri görmeyin olarak çalıştırır. Bu iş parçacıkları SQL Server işlemindeki AppDomain 'ler ve hatta veritabanları arasında paylaşılabilir. Yönetilen iş parçacığı yerel depolama alanı kullanılarak çalışır, ancak yönetilmeyen iş parçacığı yerel depolama birimini kullanamaz veya kodunuzun geçerli işletim sistemi iş parçacığında yeniden çalışacağını varsayabilirsiniz. İş parçacığının yerel ayarı gibi ayarları değiştirmeyin. P/Invoke aracılığıyla Createcriticalhandle bölümünü veya CreateMutex 'i çağırmayın, çünkü bir kilidi çağıran iş parçacığının da kiliden çıkması gerekir. Fibers kullandığınızda bu durum söz konusu olmadığından, Win32 kritik bölümleri ve zaman uyumu sağlayıcılar SQL 'de kullanılamaz olacaktır. Durumu yönetilen bir System. Thread nesnesi üzerinde güvenle kullanabilirsiniz. Buna yönetilen iş parçacığı yerel depolama alanı ve iş parçacığının geçerli kullanıcı arabirimi (UI) kültürü dahildir. Ancak, programlama modeli nedenleriyle, SQL kullandığınızda bir iş parçacığının geçerli kültürünü değiştiremeyeceksiniz; Bu, yeni bir izin ile zorlanır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 İş parçacıklarının kullanımını inceleyin ve kodunuzu uygun şekilde değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuralı göstermemelisiniz.
