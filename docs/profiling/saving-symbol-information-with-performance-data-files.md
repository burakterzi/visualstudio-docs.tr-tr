---
title: Simge bilgilerini performans veri dosyalarıyla kaydetme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packsymbols, in profiling tools reports
- profiling tools, packsymbols
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 74137752900d082c545dd5e5271b7700ec81fa01
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778303"
---
# <a name="saving-symbol-information-with-performance-data-files"></a>Performans Veri Dosyalarıyla Birlikte Sembol Bilgilerini Kaydetme

Dosyaları çözümlemek için Visual Studio IDE kullanıyorsanız ve VSP dosyanızı farklı bir bilgisayara taşımayı planlıyorsanız, performans projesi ayarlarını rapor dosyanızdaki sembolleri kaydetmek veya *seri hale* getirmek için ayarlamanız gerekir. Bu, bir rapor dosyasının boyutunu artırır. İki nedenle sembolleri serileştirmek gereklidir:

- Hedef derlemeler geçici depolamadaki konumlarından kaybolmadan önce bir performans raporuna kod sembolleri eklemek için.

- Sembolleri korumak için, performans raporunun profili oluşturulmuş bilgisayardan taşınabilir olması ve rapor başka bir bilgisayarda analiz için açılırsa farklı sembolleri olabilen aynı bilgileri çıkışları.

Visual Studio IDE 'den veya komut satırından sembolleri seri hale getirebilirsiniz:

- [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE 'de sembolleri seri hale getirmek için, menü çubuğunda **Araçlar** ' ın üzerine gelin ve ardından **Seçenekler**' e tıklayın. **Seçenekler** penceresinde, **performans araçları**' nı seçin ve ardından **sembol bilgilerini otomatik olarak seri hale getirme** onay kutusunu seçin.

- Rapor dosyalarını kaydettiğinizde, PACKSYMBOLS, eşdeğer komut satırı seçeneğidir. Sembolleri seri hale getirmek için **VSPerfReport/summary: all/packsymbols filename. vsp**yazın.

## <a name="troubleshooting-symbol-problems"></a>Sembol sorunlarını giderme

Kendi kodunuzda herhangi bir sembol görmüyorsanız bazı yaygın çözümler kullanılabilir:

- Profiler bileşenlerinin sembol bilgilerini yüklediği konumların ve kullanılan sembol dosyalarının projenizin kullandığı dosyalarla eşleşip eşleşmeksizin, bir komut satırında VSPerfReport/debugsympath komutunu çalıştırın.

- VSPerfReport komutunu/PACKSYMBOLS bayrağıyla çalıştırın veya [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE 'de, genel performans Gezgini seçeneklerinde serileştirme sembol bilgisi seçeneğinin seçili olduğundan emin olun.

- Tür verisi topladıysanız, VSPerfReport komut satırına/SUMMARY: TYPE ekleyin.

  Windows veya diğer Microsoft programlarından sembolleri görmüyorsanız:

- Windows sembol önbelleğinizin yolunu ayarladığınızdan emin olun. Sembol önbelleği yolunu ayarlamak için aşağıdakilerden birini yapın:

  - [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE içindeki Debugger-> Symbols seçeneğini doğru yola ayarlayın.

  - Sembollerinizi dahil etmek için VSPerfReport komut satırına-SymbolPath seçeneğini ekleyin.

- [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]hiçbir sembol görmüyorsanız, sembol sunucusunun ASP sunucusu için doğru şekilde ayarlandığından emin olun.

## <a name="repacking-symbols"></a>Simgeleri yeniden paketleme

Sembolleri bir rapora yeniden paketetmek isterseniz, bunu komut satırı aracı VsPerfReport ' u kullanarak yapabilirsiniz. Aşağıdaki komut satırlarını kullanın:

VsPerfReport-clearpackedsymbols filename. vsp

VsPerfReport-packsymbols-Summary: tüm filename. vsp

## <a name="see-also"></a>Ayrıca bkz.

[Performans araçları verilerini kaydetme ve dışarı aktarma](../profiling/saving-and-exporting-performance-tools-data.md)
[nasıl yapılır: Windows sembol bilgilerine başvuru](../profiling/how-to-reference-windows-symbol-information.md)
[VSPerfReport](../profiling/vsperfreport.md)
