---
title: Çalışan işlemlere performans araçları iliştirme
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.attach
helpviewer_keywords:
- performance tools, attach process
- profiling tools, detach process
- profiling tools, attach process
- performance tools, detach process
- profiler
ms.assetid: 56a99c39-e7f6-4f48-ae56-04ab8e022bf7
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4c4ae54d6b90166de31c338a5e606eaf31ecd6cc
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779174"
---
# <a name="how-to-attach-and-detach-performance-tools-to-running-processes"></a>Nasıl yapılır: performans araçlarını çalıştırma işlemlerine bağlama ve ayırma
Profil Oluşturucu, örnekleme yapmak ve performans verilerini toplamak için çalışan bir işlemden eklemek ya da ayırmak için kullanılabilir. Bu yöntemi, uygulama yükleme süresi hakkında veri toplamayı önlemek veya belirli bir duruma ulaştıktan sonra bir işlemin performansını izlemek istediğinizde bir işlemi profil için kullanabilirsiniz.

> [!NOTE]
> Aşağıdaki adımlar, [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] tümleşik geliştirme environmnent (IDE) içinden işlemleri eklemek ve ayırmak için geçerlidir. Komut satırı araçlarını kullanma hakkında daha fazla bilgi için, bkz. [komut satırından profil](../profiling/using-the-profiling-tools-from-the-command-line.md). Hizmetleri profil oluşturma hakkında daha fazla bilgi için bkz. [profil hizmetleri](../profiling/command-line-profiling-of-services.md).

 Profil için kullanılabilen süreçler, bilgisayarın yöneticisi tarafından ayarlanan Kullanıcı erişim Izinlerine bağlıdır. Örneğin, bir kullanıcı hesabı, aşağıdakilerden herhangi biri için izne sahip olabilir:

- Yönetici, sürücüyü ve hizmeti başlatılmak üzere ayarladığınızda gelişmiş profil oluşturma özellikleri.

- Yalnızca örnek profil oluşturma (etki alanı kullanıcıları).

- Herkes için profil oluşturma erişimini engelleyin.

  Daha fazla bilgi için bkz. [profil oluşturma ve Windows Vista güvenliği](../profiling/profiling-and-windows-vista-security.md) ve [VSPerfCmd](../profiling/vsperfcmd.md)içindeki yönetici seçenekleri.

### <a name="to-attach-to-a-running-process"></a>Çalışan bir işleme iliştirmek için

1. **Hata Ayıkla** menüsünde **Profiler**' ın üzerine gelin ve **Performans Gezgini**ve ardından **Ekle**' ye tıklayın.

     **Işleme profil oluşturucu Ekle** iletişim kutusu görüntülenir.

2. Eklemek istediğiniz işlemin adına tıklayın.

3. **Ekle**' ye tıklayın.

### <a name="to-detach-from-a-running-process"></a>Çalışan bir işlemden ayrılmak için

1. **Hata Ayıkla** menüsünde, **Profil Oluşturucu**üzerine gelin ve **Performans Gezgini**ve ardından **Ayır**' a tıklayın.

     **Işleme profil oluşturucu Ekle** iletişim kutusu görüntülenir.

2. Ayırmak istediğiniz görüntü adına tıklayın.

3. **Ayır**'a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Veri toplamayı denetleme](../profiling/controlling-data-collection.md)
- [Performans oturumuna genel bakış](../profiling/performance-session-overview.md)
- [Nasıl yapılır: Başlangıç ve bitiş performans verilerini toplama](../profiling/how-to-start-and-end-performance-data-collection.md)
- [Profil oluşturma ve Windows Vista güvenliği](../profiling/profiling-and-windows-vista-security.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
