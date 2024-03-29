---
title: Görsel C++ kodla çalışma (sınıf Tasarımcısı) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.cpplimitation
helpviewer_keywords:
- Visual C++, Class Designer
- Class Designer, Visual C++ support
- Class Designer, limitations
- Class Designer, tasks in Visual C++
- Visual C++, class diagrams
- C++, class diagrams
- C++, Class Designer
ms.assetid: f5b40921-2ef7-4de0-b595-45b44c79ffa6
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cb2b5a55f778b8025ea9da25713eca903f9cbf74
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296213"
---
# <a name="working-with-visual-c-code-class-designer"></a>Visual C++ Kodu ile Çalışma (Sınıf Tasarımcısı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sınıf Tasarımcısı, projenizdeki kod öğelerinin görsel gösterimini sağlayan *sınıf diyagramı* adlı bir görsel tasarım yüzeyi görüntüler. Bir projedeki sınıfları ve diğer türleri tasarlamak ve görselleştirmek için sınıf diyagramlarını kullanabilirsiniz.

 Sınıf Tasarımcısı aşağıdaki C++ kod öğelerini destekler:

- Sınıf (birden fazla devralma ilişkisine sahip olması dışında, yönetilen bir sınıf şekline benzer)

- Anonim Sınıf (Sınıf Görünümü, anonim tür için üretilen adı görüntüler)

- Şablon sınıfı

- Yapı

- Enum

- Makro (makronun işleme sonrası görünümünü görüntüler)

- Genişletiyor

> [!NOTE]
> Bu, modelleme projesinde oluşturabileceğiniz UML sınıf diyagramı ile aynı değildir. Daha fazla bilgi için bkz. [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md).

## <a name="troubleshooting-type-resolution-and-display-issues"></a>Tür çözümleme ve görüntüleme sorunlarını giderme

### <a name="location-of-source-files"></a>Kaynak dosyalarının konumu
 Sınıf Tasarımcısı, kaynak dosyaların konumunu izlememez. Bu nedenle, proje yapınızı değiştirir veya kaynak dosyalarını projenize taşırsanız, Sınıf Tasarımcısı türü (özellikle bir typedef, Taban sınıfları veya ilişkilendirme türleri kaynak türü) kaybedebilir. **Sınıf Tasarımcısı bu tür görüntülenemiyor**gibi bir hata alabilirsiniz. Bunu yaparsanız, yeniden görüntülemek için değiştirilen veya yeniden konumlandırılan kaynak kodu yeniden sınıf diyagramına sürükleyin.

### <a name="update-and-performance-issues"></a>Güncelleştirme ve performans sorunları
 Visual C++ projelerinde, kaynak dosyadaki bir değişikliğin sınıf diyagramında görünmesi 30 ila 60 saniye sürebilir. Bu gecikme **, seçimde hiçbir tür bulunamamış**bir hata Sınıf Tasarımcısı oluşturulmasına da neden olabilir. Bunun gibi bir hata alırsanız hata iletisindeki **iptal** ' e tıklayın ve kod öğesinin sınıf görünümü görünmesini bekleyin. Bunu yaptıktan sonra, Sınıf Tasarımcısı türü görüntüleyebilmelidir.

 Bir sınıf diyagramı kodda yaptığınız değişikliklerle güncelleştirmezse, diyagramı kapatıp yeniden açmanız gerekebilir.

### <a name="type-resolution-issues"></a>Tür çözümleme sorunları
 Sınıf Tasarımcısı, aşağıdaki nedenlerden dolayı türleri çözemeyebilir:

- Tür, sınıf diyagramını içeren projeden başvurulmayan bir projede veya derlemede yer alır. Bu hatayı düzeltmek için, türü içeren proje veya derlemeye bir başvuru ekleyin. Daha fazla bilgi için bkz. [nib nasıl yapılır: Başvuru Ekle Iletişim kutusunu kullanarak başvuru ekleme veya kaldırma](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).

- Tür doğru kapsamda olmadığından Sınıf Tasarımcısı bulamıyor. Kodda `using`, `imports`veya `#include` deyimlerinin eksik olmadığından emin olun. Ayrıca, türü (veya ilgili bir tür), başlangıçta bulunduğu ad alanından taşıdığınızdan emin olun.

- Tür yok (veya açıklama alındı). Bu hatayı düzeltmek için, türü açıklama veya silme yaptığınızdan emin olun.

- Tür, bir #import yönergesi tarafından başvurulan bir kitaplıkta bulunur. Olası bir geçici çözüm, oluşturulan kodu (. tlh dosyası) üst bilgi dosyasına bir #include yönergesine el ile eklemektir.

  **'\<element > ' sınıf diyagramında bir veya daha fazla şekil için**bir tür çözümleme sorunu için görmem muhtemel hata kodu bulunamadı. Bu hata iletisi, kodunuzun hatalı olduğunu göstermez. Yalnızca bu sınıf tasarımcısının kodunuzun görüntülenemiyor olduğunu gösterir. Aşağıdaki ölçüleri deneyin.

- Türün var olduğundan emin olun. Kaynak kodu istemeyerek dışarı veya silmediğinden emin olun.

- Sınıf Tasarımcısı girdiğiniz türü desteklediğinden emin olun. [Kod öğelerine yönelik C++ sınırlamalara](#limitations)bakın.

- Türü çözmeyi deneyin. Tür, sınıf diyagramını içeren projeden başvurulmayan bir projede veya derlemede olabilir. Bu hatayı düzeltmek için, türü içeren proje veya derlemeye bir başvuru ekleyin. Daha fazla bilgi için bkz. [nib nasıl yapılır: Başvuru Ekle Iletişim kutusunu kullanarak başvuru ekleme veya kaldırma](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).

- Sınıf Tasarımcısı bulmak için türün doğru kapsamda olduğundan emin olun. Kodda `using`, `imports`veya `#include` deyimlerinin eksik olmadığından emin olun. Ayrıca, türü (veya ilgili bir tür), başlangıçta bulunduğu ad alanından taşıdığınızdan emin olun.

### <a name="troubleshooting-other-error-messages"></a>Diğer hata Iletileri sorunlarını giderme
 Microsoft Developer Network (MSDN) ortak forumlarında sorun giderme hatalarıyla ve uyarılarla ilgili yardım bulabilirsiniz. Bkz. [Visual Studio Sınıf Tasarımcısı Forumu](https://go.microsoft.com/fwlink/?linkid=160754).

## <a name="limitations"></a>Kod öğeleri C++ için sınırlamalar

- Bir görsel C++ proje yüklendiğinde, sınıf Tasarımcısı işlevleri salt okunurdur. Sınıf diyagramını değiştirebilirsiniz, ancak sınıf diyagramından değişiklikleri kaynak koda geri kaydedemezsiniz.

- Sınıf Tasarımcısı yalnızca yerel C++ semantiğini destekler. Yönetilen koda C++ derlenen görsel projeler için sınıf Tasarımcısı yalnızca yerel türler olan kod öğelerini görselleştirilecek. Bu nedenle, bir projeye sınıf diyagramı ekleyebilirsiniz, ancak Sınıf Tasarımcısı `IsManaged` özelliğinin `true` (yani, değer türleri ve başvuru türleri) olarak ayarlandığı öğeleri görselleştirmenize izin vermez.

- Görsel C++ projeler için sınıf Tasarımcısı yalnızca türün tanımını okur. Örneğin, bir üstbilgi (. h) dosyasında bir tür tanımladığınızı ve üyelerini bir uygulama (. cpp) dosyasında tanımladığınızı varsayalım. Uygulama (. cpp) dosyasında "Görünüm sınıf diyagramını" çağırırsanız Sınıf Tasarımcısı hiçbir şey görüntülemez. Başka bir örnek olarak, diğer dosyaları dahil etmek için `#include` bir ifade kullanan ancak gerçek sınıf tanımları içermeyen bir. cpp dosyasında "Görünüm sınıf diyagramını" çağırırsanız, Sınıf Tasarımcısı hiçbir şey göstermez.

- COM arabirimlerini ve tür kitaplıklarını tanımlayan IDL (. IDL) dosyaları, yerel C++ koda derlenmedikleri takdirde diyagramlarda görüntülenmez.

- Sınıf Tasarımcısı, genel işlevleri ve değişkenleri desteklemez.

- Sınıf Tasarımcısı birleşimler desteklemez. Bu, ayrılan belleğin yalnızca birleşimin en büyük veri üyesi için gereken miktarı olduğu özel bir sınıf türüdür.

- Sınıf Tasarımcısı, `int` ve `char`gibi temel veri türlerini görüntülemez.

- Sınıf Tasarımcısı, projenin bu türlere doğru başvuruları yoksa, geçerli projenin dışında tanımlanan türleri görüntülemez.

- Sınıf Tasarımcısı, iç içe geçmiş türler ve diğer türler arasındaki ilişkileri değil, iç içe geçmiş türleri görüntüleyebilir.

- Sınıf Tasarımcısı void olan veya void bir türden türetilen türleri görüntüleyemez.

## <a name="see-also"></a>Ayrıca Bkz.
 Sınıfları ve türleri [tasarlama ve görüntüleme](../ide/designing-and-viewing-classes-and-types.md) [(sınıf Tasarımcısı)](../ide/working-with-classes-and-other-types-class-designer.md) [sınıf diyagramları ile çalışma (sınıf Tasarımcısı)](../ide/working-with-class-diagrams-class-designer.md) sınıflar ve [türler (sınıf Tasarımcısı)](../ide/designing-classes-and-types-class-designer.md) , sınıf Tasarımcısı görsel [ C++ numaralandırmalar](../ide/visual-cpp-enumerations-in-class-designer.md) [içindeki sınıf Tasarımcısı C++ ](../ide/visual-cpp-structures-in-class-designer.md) görsel numaralandırmalar [içindeki sınıf Tasarımcısı görsel C++ ](../ide/visual-cpp-classes-in-class-designer.md) Numaralandırmalarla [ C++ ](../ide/visual-cpp-typedefs-in-class-designer.md) [ilgili ek bilgileri sınıf Tasarımcısı](../ide/additional-information-about-class-designer-errors.md)
