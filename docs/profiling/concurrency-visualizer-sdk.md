---
title: Eşzamanlılık Görselleştiricisi SDK 'Sı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.sdk.about
ms.assetid: 4b22cdf9-59b1-4c88-a6d8-1644a4a11e08
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb48733f84dcf484d2c2d7ffb18e838faae07ab0
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911191"
---
# <a name="concurrency-visualizer-sdk"></a>Eşzamanlılık Görselleştiricisi SDK
Eşzamanlılık görselleştiricisi içinde ek bilgileri göstermek için Eşzamanlılık Görselleştiricisi SDK 'sını kullanarak kaynak kodunuzu gösterebilirsiniz. Ek verileri kodunuzda aşamalar ve olaylarla ilişkilendirebilirsiniz. Bu ek görselleştirmeler *işaretçiler*olarak bilinir.  Tanıtım amaçlı bir anlatım için bkz. [Eşzamanlılık Görselleştiricisi SDK 'Sını tanıtma](https://blogs.msdn.microsoft.com/visualizeparallel/2011/10/17/introducing-the-concurrency-visualizer-sdk/).

## <a name="properties"></a>Özellikler
 Bayraklar, yayılma ve mesajlar her biri iki özelliğe sahiptir: Kategori ve önem derecesi. [Gelişmiş ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusunda, görüntülenen işaretçiler kümesini filtrelemek için bu özellikleri kullanabilirsiniz. Ayrıca, bu özellikler işaretçiler görsel gösterimini etkiler. Örneğin, önemli olduğunu göstermek için bayrakların boyutu kullanılır. Ayrıca, kategori göstermek için renk kullanılır.

## <a name="basic-usage"></a>Temel kullanım
 Eşzamanlılık görselleştiricisi, işaretçiler oluşturmak için kullanabileceğiniz bir varsayılan sağlayıcı sunar. Sağlayıcı eşzamanlılık görselleştiricisi ile birlikte zaten kayıtlı ve işaretleyicileri Kullanıcı arabiriminde görünmesini sağlamak için başka bir şey yapmanız gerekmez.

### <a name="c-and-visual-basic"></a>C# ve Visual Basic
 İçinde C#, Visual Basic ve diğer yönetilen kodda, [işaretleyiciler](/previous-versions/hh694099(v=vs.140)) sınıfındaki yöntemleri çağırarak varsayılan sağlayıcıyı kullanın. İşaretleyiciler oluşturmak için dört yöntem sunar: [WriteFlag](/previous-versions/hh694185%28v%3dvs.140%29), [EnterSpan](/previous-versions/hh694205(v=vs.140)), [WriteMessage](/previous-versions/hh694161(v=vs.140))ve [WriteAlert](/previous-versions/hh694180(v=vs.140)). Özellikler için varsayılan değerleri kullanmak istediğinize bağlı olarak, bu işlevler için birden fazla aşırı yükleme vardır.  En basit aşırı yükleme yalnızca olayın açıklamasını belirten bir String parametresi alır. Açıklama eşzamanlılık görselleştiricisi raporlarında görüntülenir.

##### <a name="to-add-sdk-support-to-a-c-or-visual-basic-project"></a>Bir C# veya VISUAL BASIC projesine SDK desteği eklemek için

1. Menü çubuğunda **Çözümle**, **EŞZAMANLıLıK görselleştiricisi**, **SDK 'yı projeye Ekle**' yi seçin.

2. SDK 'ya erişmek istediğiniz projeyi seçin ve ardından **Seçili proje IÇIN SDK Ekle** düğmesini seçin.

3. Kodunuza içeri aktarmalar veya using deyimleri ekleyin.

    ```csharp
    using Microsoft.ConcurrencyVisualizer.Instrumentation;
    ```

    ```VB
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation
    ```

### <a name="c"></a>C++
 İçinde C++, bir [marker_series Class](../profiling/marker-series-class.md) nesnesi oluşturun ve işlevleri çağırmak için kullanın.  `marker_series` sınıfı, işaretçiler oluşturmak için üç işlev sunar, [marker_series:: Write_flag yöntemi](../profiling/marker-series-write-flag-method.md), [marker_series:: write_message yöntemi](../profiling/marker-series-write-message-method.md)ve [marker_series:: write_alert yöntemi](../profiling/marker-series-write-alert-method.md).

##### <a name="to-add-sdk-support-to-a-c-or-c-project"></a>Bir C++ veya C projesine SDK desteği eklemek için

1. Menü çubuğunda **Çözümle**, **EŞZAMANLıLıK görselleştiricisi**, **SDK 'yı projeye Ekle**' yi seçin.

2. SDK 'ya erişmek istediğiniz projeyi seçin ve ardından **Seçili proje IÇIN SDK Ekle** düğmesini seçin.

3. İçin C++`cvmarkersobj.h`ekleyin. C için `cvmarkers.h`ekleyin.

4. Kodunuza bir using deyimleri ekleyin.

    ```cpp
    using namespace Concurrency::diagnostic;
    ```

5. `marker_series` nesne oluşturun ve `span` oluşturucusuna geçirin.

    ```C++

    marker_series mySeries;
    span s(mySeries, _T("Span description"));

    ```

## <a name="custom-usage"></a>Özel kullanım
 Gelişmiş senaryolar için Eşzamanlılık Görselleştiricisi SDK 'Sı daha fazla denetim sunar.  İki ana kavram daha gelişmiş senaryolar ile ilişkilendirilmiştir: işaret sağlayıcıları ve işaretleyici serisi. İşaretleyici sağlayıcıları farklı ETW sağlayıcılarıdır (her biri farklı bir GUID 'e sahiptir). İşaretleyici serisi, bir sağlayıcı tarafından oluşturulan olayların seri kanallarıdır. Bunları, bir işaretleyici sağlayıcı tarafından oluşturulan olayları düzenlemek için kullanabilirsiniz.

#### <a name="to-use-a-new-marker-provider-in-a-c-or-visual-basic-project"></a>Bir C# veya Visual Basic projesinde yeni bir işaretleyici sağlayıcı kullanmak için

1. Bir [MarkerWriter](/previous-versions/hh694138(v=vs.140)) nesnesi oluşturun.  Oluşturucu bir GUID alır.

2. Sağlayıcıyı kaydetmek için eşzamanlılık görselleştiricisi [Gelişmiş ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusunu açın.  **İşaretleyiciler** sekmesini seçin ve ardından **Yeni Sağlayıcı Ekle** düğmesini seçin. [Gelişmiş ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusunda, sağlayıcıyı oluşturmak IÇIN kullanılan GUID 'yi ve sağlayıcının açıklamasını girin.

#### <a name="to-use-a-new-marker-provider-in-a-c-or-c-project"></a>Bir C++ veya C projesinde yeni bir işaretleyici sağlayıcı kullanmak için

1. Bir PCV_PROVIDER başlatmak için `CvInitProvider` işlevini kullanın.  Oluşturucu bir GUID * ve PCV_PROVIDER\*alır.

2. Sağlayıcıyı kaydetmek için [Gelişmiş ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusunu açın.  **İşaretleyiciler** sekmesini seçin ve ardından **Yeni Sağlayıcı Ekle** düğmesini seçin. Bu iletişim kutusunda, sağlayıcıyı oluşturmak için kullanılan GUID 'yi ve sağlayıcının açıklamasını girin.

#### <a name="to-use-a-marker-series-in-a-c-or-visual-basic-project"></a>Bir C# veya Visual Basic projesinde işaretleyici serisi kullanmak için

1. Yeni bir [MarkerSeries](/previous-versions/hh694127(v=vs.140))kullanmak için, önce bir [MarkerWriter](/previous-versions/hh694138(v=vs.140)) nesnesi kullanarak oluşturun ve sonra doğrudan yeni seriden işaret olayları oluşturun.

    ```csharp
    MarkerSeries series1 = myMarkerWriter.CreateMarkerSeries("Series 1");
    series1.WriteFlag("My flag");
    ```

    ```VB
    Dim series1 As New myMarkerWriter.CreateMarkerSeries("Series 1")
    series1.WriteFlag("My flag")
    ```

#### <a name="to-use-a-marker-series-in-a-c-project"></a>Bir C++ projede işaretleyici serisi kullanmak için

1. `marker_series` nesnesi oluşturun.  Bu yeni seriden olay oluşturabilirsiniz.

    ```scr
    marker_series series;
    series.write_flag(_T("Hello world!"));
    ```

#### <a name="to-use-a-marker-series-in-a-c-project"></a>Bir C projesinde işaretleyici serisini kullanmak için

1. Bir PCV_MARKERSERIES oluşturmak için `CvCreateMarkerSeries` işlevini kullanın.

    ```C++
    PCV_MARKERSERIES series;
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);
    CvWriteFlag(series, _T("Writing a flag"));
    ```

## <a name="see-also"></a>Ayrıca bkz.

|Başlık|Açıklama|
|-----------|-----------------|
|[C++kitaplık başvurusu](../profiling/cpp-library-reference.md)|İçin C++EŞZAMANLıLıK görselleştiricisi API 'sini açıklar.|
|[C Kitaplığı başvurusu](../profiling/c-library-reference.md)|C için eşzamanlılık görselleştiricisi API 'sini açıklar.|
|[Yapısı](/previous-versions/hh694104(v=vs.140))|Yönetilen kod için eşzamanlılık görselleştiricisi API 'sini açıklar.|
|[Eşzamanlılık görselleştiricisi](../profiling/concurrency-visualizer.md)|Eşzamanlılık yöntemi kullanılarak oluşturulan ve iş parçacığı yürütme verilerini içeren profil oluşturma veri dosyalarının görünümleri ve raporları için başvuru bilgileri.|