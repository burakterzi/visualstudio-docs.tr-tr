---
title: Çağrı yığınının görsel haritasını oluşturun | Microsoft Docs
ms.date: 11/26/2018
ms.topic: conceptual
f1_keywords:
- vs.progression.debugwithcodemaps
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- call stacks, code maps
- Call Stack window, mapping calls
- debugging [Visual Studio], diagramming the call stack
- call stacks, mapping
- Call Stack window, visualizing
- debugging code visually
- debugging [Visual Studio], mapping the call stack
- call stacks, visualizing
- debugging, code maps
- Call Stack window, tracing calls visually
- Call Stack window, show on code map
- debugging [Visual Studio], tracing the call stack visually
- debugging [Visual Studio], visualizing the call stack
ms.assetid: d6a72e5e-f88d-46fc-94a3-1789d34805ef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 135c7c66c9c6602f8c2e32bbdc1ba6e2fd28f548
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911515"
---
# <a name="create-a-visual-map-of-the-call-stack-while-debugging-c-visual-basic-c-javascript"></a>Hata ayıklarken çağrı yığınının görsel haritasını oluşturma (C#, Visual Basic, C++JavaScript)

Hata ayıklarken çağrı yığınını görsel olarak izlemek için bir kod haritası oluşturun. Kodun ne yaptığını izlemek için haritada Not oluşturabilir, böylece hataları bulmaya odaklanırsınız.

İzlenecek yol için şu videoyu izleyin: [video: kod Haritası hata ayıklayıcısı tümleştirmesiyle görsel hata ayıkla (Channel 9)](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012Debug-visually-with-Code-Map-debugger-integration)

Kod haritaları ile kullanabileceğiniz komutların ve eylemlerin ayrıntıları için bkz. [kod haritalarını inceleyin ve yeniden düzenleyin](../modeling/browse-and-rearrange-code-maps.md).

>[!IMPORTANT]
>Yalnızca [Visual Studio Enterprise sürümünde](https://visualstudio.microsoft.com/downloads)kod haritaları oluşturabilirsiniz.

İşte bir kod haritasına hızlı bakış:

 ![Kod Eşlemlerde çağrı yığınları ile hata ayıklama](../debugger/media/debuggermap_overview.png "DebuggerMap_Overview")

## <a name="MapStack"></a>Çağrı yığınını eşleme

1. Visual Studio Enterprise C#, Visual Basic, C++veya JavaScript **projesinde hata ayıklama > hata** **ayıklamayı Başlat** ' ı seçerek veya **F5**tuşuna basarak hata ayıklamayı başlatın.

1. Uygulamanız kesme moduna girdiğinde veya bir işleve adımladıktan sonra, **hata ayıkla** > **kod Haritası**' nı seçin veya **CTRL**+**SHIFT**+ **`** ' a basın.

   Geçerli çağrı yığını yeni bir kod haritası üzerinde turuncu renkte görüntülenir:

   ![Bkz. kod eşlemesinde çağrı yığını](../debugger/media/debuggermap_seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

Kod eşleme, hata ayıklamaya devam ederken otomatik olarak güncelleştirilir. Harita öğelerini veya yerleşimini değiştirmek kodu herhangi bir şekilde etkilemez. Haritadaki herhangi bir şeyi rahatça yeniden adlandırabilir, taşıyabilir veya kaldırabilirsiniz.

Bir öğe hakkında daha fazla bilgi edinmek için, üzerine gelin ve öğenin araç ipucuna bakın. Her simgenin ne anlama geldiğini öğrenmek için araç çubuğunda **gösterge** ' ı da seçebilirsiniz.

![Kod Haritası göstergesi](../debugger/media/debuggermap_showlegend.png "Kod Haritası göstergesi")

>[!NOTE]
>Diyagramda, kod eşlemesinin en üstündeki **kodun eski bir sürümünü temel alan bir** ileti, Haritayı son güncelleştirdikten sonra kodun değişmiş olabileceği anlamına gelir. Örneğin, harita üzerindeki bir çağrı artık kodda bulunmayabilir. İletiyi kapatın ve haritayı yeniden güncelleştirmeden önce çözümü yeniden oluşturmayı deneyin.

## <a name="map-external-code"></a>Dış kod eşleme

Varsayılan olarak, haritada yalnızca kendi kodunuz görüntülenir. Haritada dış kodu görmek için:

- **Çağrı yığını** penceresine sağ tıklayın ve **dış kodu göster**' i seçin:

  ![Çağrı yığını penceresini kullanarak dış kodu görüntüle](../debugger/media/debuggermap_callstackmenu.png "DebuggerMap_CallStackMenu")
- Ya da Visual Studio **araçlarında** **yalnızca kendi kodum etkinleştir** seçimini kaldırın (veya **hata ayıklama**) > **Seçenekler** > **hata ayıklama**:

  ![Seçenekler iletişim kutusunu kullanarak dış kodu göster](../debugger/media/debuggermap_debugoptions.png "DebuggerMap_DebugOptions")

## <a name="control-the-maps-layout"></a>Haritanın yerleşimini denetleme

Haritanın düzeninin değiştirilmesi, kodu herhangi bir şekilde etkilemez.

Haritanın yerleşimini denetlemek için harita araç çubuğunda **Düzen** menüsünü seçin.

**Düzen** menüsünde şunları yapabilirsiniz:

- Ekran düzenini değiştirin.
- **Hata ayıklama sırasında otomatik olarak düzen**seçimini kaldırarak Haritayı otomatik olarak yeniden düzenlemeyi durdurun.
- **Artımlı düzenin**seçimini kaldırarak eşlemeyi öğe eklediğinizde mümkün olduğunca az yeniden düzenleyin.

## <a name="MakeNotes"></a>Kodla ilgili notlar alın

Kodda neler olduğunu izlemek için yorum ekleyebilirsiniz.

Bir açıklama eklemek için, kod haritasına sağ tıklayın ve > **Yeni açıklama** **Düzenle** ' yi seçin ve ardından yorumu yazın.

Açıklamaya yeni bir satır eklemek için **shıft**+**ENTER**tuşlarına basın.

 ![Kod eşlemesinde çağrı yığınına Açıklama Ekle](../debugger/media/debuggermap_addcomment.png "DebuggerMap_AddComment")

## <a name="UpdateMap"></a>Sonraki çağrı yığını ile Haritayı güncelleştirme

Uygulamanızı sonraki kesme noktasında çalıştırdığınız veya bir işleve adımla, eşleme otomatik olarak yeni çağrı yığınları ekler.

![Sonraki çağrı yığını ile kod haritasını Güncelleştir](../debugger/media/debuggermap_addclearcallstack.png "DebuggerMap_AddClearCallStack")

Haritanın otomatik olarak yeni çağrı yığınları eklemesini durdurmak için kod Haritası araç çubuğunda ![kod haritasında çağrı yığınını göster](../debugger/media/debuggermap_automaticupdateicon.gif "Çağrı yığınını kod eşlemesinde otomatik olarak göster") ' i seçin. Eşleme, varolan çağrı yığınlarını vurgulamaya devam eder. Geçerli çağrı yığınını haritaya el ile eklemek için, **Ctrl**+**SHIFT**+ **`** tuşlarına basın.

## <a name="AddRelatedCode"></a>Haritaya ilgili kod ekleme

C# Ya da Visual Basic bir haritanız olduğuna göre, kodda neler olduğunu izlemek için alanlar, Özellikler ve diğer yöntemler gibi öğeleri de ekleyebilirsiniz.

Koddaki yöntemin tanımına gitmek için haritadaki yönteme çift tıklayın veya seçin, **F12**tuşuna basın veya sağ tıklayın ve **Tanıma Git**' i seçin.

![Kod eşlemesindeki bir yöntem için kod tanımına git](../debugger/media/debuggermap_gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

Haritaya izlemek istediğiniz öğeleri eklemek için bir yönteme sağ tıklayın ve izlemek istediğiniz öğeleri seçin. En son eklenen öğeler yeşil görünür.

![Çağrı yığını kod eşlemesindeki bir metotla ilgili alanlar](../debugger/media/debuggermap_showedfields.png "DebuggerMap_ShowedFields")

>[!NOTE]
>Varsayılan olarak, haritaya öğe eklemek sınıf, ad alanı ve derleme gibi üst grup düğümlerini da ekler. Kod Haritası araç çubuğunda **üst öğeleri dahil et** düğmesini seçerek veya öğe eklerken **CTRL** tuşuna basarak bu özelliği devre dışı bırakabilirsiniz.

![Çağrı yığını kod eşlemesinde bir yöntemde alanları gösterme](../debugger/media/debuggermap_showfields.png "DebuggerMap_ShowFields")

Daha fazla kod görmek için haritayı oluşturmaya devam edin.

 ![Bir alan kullanan yöntemlere bakın: çağrı yığını kod eşlemesi](../debugger/media/debuggermap_findallreferences.png "DebuggerMap_FindAllReferences")

 ![Çağrı yığını kod eşlemesinde bir alan kullanan Yöntemler](../debugger/media/debuggermap_foundallreferences.png "DebuggerMap_FoundAllReferences")

## <a name="FindBugs"></a>Haritayı kullanarak hataları bulma
 Kodunuzu görselleştirmeniz, hataları daha hızlı şekilde bulmanıza yardımcı olabilir. Örneğin, bir çizim uygulamasında bir hatayı araştırdığınızı varsayalım. Bir çizgi çizip geri almayı denediğinizde, başka bir çizgi çizinceye kadar hiçbir şey olmaz.

 `clear`, `undo`ve `Repaint` yöntemlerinde kesme noktaları ayarlayın, hata ayıklamayı başlatın ve bunun gibi bir eşleme oluşturun:

 ![Kod eşlemesine başka bir çağrı yığını ekleyin](../debugger/media/debuggermap_addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 Eşleme çağrısındaki tüm Kullanıcı hareketlerine `undo` hariç `Repaint` fark edersiniz. Bu, `undo` neden hemen çalışmadığına ilişkin bir açıklama verebilir.

 Hatayı düzelttikten ve uygulamayı çalıştırmaya devam ettikten sonra, eşleme `undo` yeni çağrıyı `Repaint`öğesine ekler:

 ![Kod eşlemesinde çağrı yığınına yeni yöntem çağrısı Ekle](../debugger/media/debuggermap_addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="share-the-map-with-others"></a>Haritayı başkalarıyla paylaşma

Bir Haritayı dışarı aktarabilir, Microsoft Outlook ile başka bir kişiye gönderebilir, çözümünüze kaydedebilir ve sürüm denetimine iade edebilirsiniz.

Haritayı paylaştırmak veya kaydetmek için, kod Haritası araç çubuğunda **paylaşma** ' yı kullanın.

![Çağrı yığını kod haritasını başkalarıyla paylaşma](../debugger/media/debuggermap_sharewithothers.png "Çağrı yığını kod haritasını başkalarıyla paylaşma")

## <a name="see-also"></a>Ayrıca bkz.
[Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)

[Uygulamalarınızda hata ayıklamak için kod haritalarını kullanma](../modeling/use-code-maps-to-debug-your-applications.md)

[Kod haritası çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)

[Kod haritalarına göz atma ve bunları yeniden düzenleme](../modeling/browse-and-rearrange-code-maps.md)
