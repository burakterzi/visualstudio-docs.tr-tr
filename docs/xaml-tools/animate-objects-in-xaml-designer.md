---
title: XAML Tasarımcısı’nda nesnelere animasyon ekleme
titleSuffix: Blend for Visual Studio
ms.date: 07/31/2019
ms.topic: conceptual
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23ddc7379e35fb060e34754f4188c04f91910ad0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649741"
---
# <a name="animate-objects-in-xaml-designer"></a>XAML Tasarımcısı’nda nesnelere animasyon ekleme

Visual Studio için Blend, nesneleri taşımak veya onları aşağı veya dışarı bir şekilde soluklaştırmak için kolayca bir kısa animasyon oluşturmanızı sağlar.

Animasyon oluşturmak için bir *görsel taslağa*ihtiyacınız vardır. Film şeridi bir veya daha fazla *zaman çizelgesi*içerir. Özellik değişikliklerini işaretlemek için zaman çizelgesinde *ana kareleri* ayarlayın. Daha sonra, animasyonu çalıştırdığınızda Visual Studio için Blend, belirlenen süre içinde özellik değişikliklerini enterpolasyonlar. Sonuç kesintisiz bir geçiştir. Nesneye ait olan herhangi bir özelliğe, hatta görsel olmayan özelliklere animasyon uygulayabilirsiniz.

Aşağıdaki resimlerde **Storyboard1**adlı bir görsel taslak gösterilmektedir. Zaman çizelgesi, bir dikdörtgenin X ve Y konumunu işaretleyen ana kareleri içerir. Bu animasyon çalıştırıldığında, dikdörtgen bir konumdan diğerine doğru gider.

![Visual Studio için Blend animasyon için görsel taslak](media/storyboard-timeline.png)

## <a name="create-an-animation"></a>Animasyon oluşturma

1. Görsel taslak oluşturmak için **nesneler ve zaman çizelgesi** penceresinde **görsel taslak seçenekleri** düğmesini seçin ve ardından **Yeni**' yi seçin.

   ![Visual Studio için Blend film şeridi ekleme](media/new-storyboard.png)

2. **Görsel taslak kaynağı oluştur** iletişim kutusunda, film şeridi için bir ad girin.

3. Tasarım görünümü ' deki **varlıklar** panelinden sayfanın sol alt tarafına bir dikdörtgen ekleyin.

   ![XAML Tasarımcısı Varlıklar panelinde dikdörtgen](media/add-rectangle.PNG)

4. **Nesneler ve zaman çizelgesi** penceresinde, sarı zaman işaretçisini **3** saniyeye taşıyın.

   ![Zaman çizelgesindeki zaman göstergesi](media/timeline-indicator.PNG)

5. Sayfanın Tasarım görünümü, dikdörtgeni sayfanın sağ tarafına sürükleyin.

6. Sol taraftan sayfanın sağ tarafına doğru olan dikdörtgeni izlemek için **oynat** ' a basın.

Dikdörtgenin farklı noktalarında diğer değişikliklerle dolaşma yapın. Örneğin, Özellikler penceresi, dolguyu veya yönü ters çevirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio için Blend’i kullanarak kullanıcı arabirimi oluşturma](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md)