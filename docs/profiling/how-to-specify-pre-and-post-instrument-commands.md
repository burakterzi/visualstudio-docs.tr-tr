---
title: 'Nasıl yapılır: ön ve araç sonrası komutları belirtme | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.instrument
helpviewer_keywords:
- profiling tools, pre-instrument events
- events [Visual Studio], pre-instrument
- pre-instrument events, performance tools
ms.assetid: 6a8d5340-1d1b-4d81-88dd-8e1f435eb828
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 22ad5558ed01e5bb1b8d12b7a4cc65b4d677d0cd
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778719"
---
# <a name="how-to-specify-pre--and-post-instrument-commands"></a>Nasıl yapılır: ön ve araç sonrası komutları belirtme

Bir performans oturumunda ikili dosyalardan önce veya sonra çalıştırılan komutlar görüntülenir. Komut satırından verilebileceğiniz herhangi bir komut, bir ön izleme veya bir işaretleme sonrası olay olarak belirtilebilir. Örneğin, ikili dosyalar görüntülendikten sonra yürütülen bir toplu iş dosyasında tanımlayıcı ad anahtarı olan bir derlemenin çekilişini otomatikleştiren komutları belirtebilirsiniz.

Profil oluşturma çalıştırmasında veya tek tek ikili dosyalarda tüm belgelenmiş ikili dosyalar için komutlar belirtebilirsiniz. Ancak, daha önce çalıştırmak için yalnızca bir pre-Instrument komutu ve izleme işleminden sonra çalıştırılacak bir araç sonrası komutu belirtebilirsiniz. Tüm ikili dosyalar için ve tek tek ikililer için komut belirtemezsiniz. Tüm ikili dosyalar için komutlar belirttiğinizde, komutlar oturumdaki her bir ikilinin izleme öncesi veya sonrasında çalıştırılır.

Komutların yürütüldüğü çalışma dizini, [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] çalıştırdığınız işletim sistemine ve profili oluşturulmuş uygulamanın hedef platformunda değişir.

Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

## <a name="to-specify-pre-instrument-commands"></a>Araç öncesi komutları belirtmek için

1. Aşağıdaki adımlardan birini gerçekleştirin:

    - Bir performans oturumunda tüm ikili dosyalar için ön gereç komutlarını belirtmek üzere **Performans Gezgini**' deki performans oturumu düğümünü seçin ve ardından **Özellikler**' i seçin.

    - Belirli bir ikiliye ilişkin ön gereç komutlarını belirtmek için, performans oturumunun **hedefler** listesinden ikilinin adına sağ tıklayın ve ardından **Özellikler**' i seçin.

2. **Özellik sayfalarında**, **izleme**' ye tıklayın.

3. Komut **satırı** metin kutusuna komutu, **önceden işaretleme olayları**altında yazın.

    > [!NOTE]
    > **Komut satırı** kutusunun yanındaki üç nokta düğmesini **(...)** tıklatarak uygun. exe,. cmd veya. bat dosyasına gözatıp seçebilirsiniz.

4. **Tamam**'a tıklayın.

     Komutun kaldırılmadan çalıştırılmasını devre dışı bırakmak için, **araçlardan Dışla** onay kutusunu seçin. Derleyici veya bağlayıcı ayarlarını değiştirmek için, proje özelliği sayfalarını kullanın.

## <a name="to-specify-post-instrument-commands"></a>Araç sonrası komutları belirtmek için

1. Aşağıdaki adımlardan birini gerçekleştirin:

    - Bir performans oturumunda tüm ikili dosyalar için araç sonrası komutları belirtmek için **Performans Gezgini**' deki performans oturumu düğümünü seçin ve ardından **Özellikler**' i seçin.

    - Belirli bir ikiliye yönelik son araç komutlarını belirtmek için, performans oturumunun **hedefler** listesinden ikilinin adına sağ tıklayın ve ardından **Özellikler**' i seçin.

2. **Özellik sayfalarında**, **izleme**' ye tıklayın.

3. Komut **satırı** metin kutusuna komutu, **son izleme olayları**altında yazın.

    > [!NOTE]
    > **Komut satırı** kutusunun yanındaki üç nokta düğmesini **(...)** tıklatarak uygun. exe,. cmd veya. bat dosyasına gözatıp seçebilirsiniz.

4. **Tamam**'a tıklayın.

     Komutun kaldırılmadan çalıştırılmasını devre dışı bırakmak için, **araçlardan Dışla** onay kutusunu seçin. Derleyici veya bağlayıcı ayarlarını değiştirmek için, proje özelliği sayfalarını kullanın.

## <a name="see-also"></a>Ayrıca bkz.

[Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)
