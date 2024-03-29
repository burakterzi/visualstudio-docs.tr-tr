---
title: Diğer Visual Studio sürümlerindeki modelleri ve diyagramları okuma
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29c190115836972f86590233e331f172422efbd6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747429"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Diğer Visual Studio sürümlerindeki modelleri ve diyagramları okuma

Model oluşturmayı desteklemeyen bir Visual Studio sürümünde model açtığınızda, model salt okuma modunda açılır. Bu modda, diyagramların yerleşimini değiştirebilirsiniz, ancak modeli değiştiremezsiniz.

Hangi Visual Studio sürümünün model oluşturmayı desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="obtaining-access-to-a-model-and-diagrams"></a>Model ve diyagramlara erişim sağlama

Bir bağımlılık diyagramını okumak için öncelikle Visual Studio 'Yu kullanarak modelleme projesini açın ve sonra diyagramı içinde açın.

Bu nedenle, bir bağımlılık diyagramını okumak istiyorsanız, oluşturulduğu modelleme projesine de erişiminizin olması gerekir. Bunu, projeye kaynak denetiminden erişerek ya da proje dosyalarının bir kopyasını alarak yapabilirsiniz.

> [!NOTE]
> Bu, koddan oluşturulan kod haritaları ve .NET sınıf diyagramları için geçerlidir. Bu diyagramlar, modelleme projesinden bağımsız olarak görüntülenebilir.

Bir bağımlılık diyagramını okumak için, ihtiyacınız olan minimum dosya kümesi aşağıdaki gibidir:

- Okumak istediğiniz diyagram için iki Diyagram dosyası; örneğin, **MyDiagram. classdiagram ve MyDiagram. classdiagram. Layout**.

    > [!NOTE]
    > Bağımlılık diyagramlarında, _MyDiagram_ **. layerdiagram. suppressions**adlı dosyaya da sahip olmanız gerekir.

- Modelleme proje dosyası (**MyModel. modelproj**)

- Kök model dosyası (**Modeldefinition\mymodel.exe**)

- Diyagramda başvurulan herhangi bir paket için paket dosyaları (**Modeldefinition\mypackage.exe**)

## <a name="changes-that-you-can-make-in-read-only-mode"></a>Salt okuma modunda yapabileceğiniz değişiklikler

Model oluşturmayı desteklemeyen bir Visual Studio sürümünde model ve diyagramlarını açarsanız modeli değiştiremezsiniz. Diğer bir deyişle, diyagramlarda veya model Gezgininde görüntülenen öğeleri ve ilişkileri değiştiremezsiniz. Ancak, diyagramların düzeninde bazı değişiklikler yapabilirsiniz:

- Diyagramdaki şekilleri ve bağlayıcıları yeniden düzenleyin.

- Şekilleri Genişlet ve daralt.

Bu değişiklikleri kaydedebilirsiniz. Değişikliklerinizi diğer kullanıcılara görünür yapmak istiyorsanız, en azından güncelleştirilmiş **. Layout** dosyalarını göndermeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)
- [Uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)