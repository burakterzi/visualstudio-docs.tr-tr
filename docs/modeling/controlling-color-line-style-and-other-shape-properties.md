---
title: Renk, Çizgi Stili ve Diğer Şekil Özelliklerini Denetleme
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bcc7e3a80650edff411506b9e651885b3852383
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654154"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Renk, Çizgi Stili ve Diğer Şekil Özelliklerini Denetleme

Renk gibi bazı şekil özellikleri ' açığa çıkabilir ' olabilir. Diğer bir deyişle, Özellikler şeklin bir etki alanı özelliğine bağlanabilir. Diğerlerinin doğrudan denetlenmesi gerekir.

## <a name="exposing-a-property"></a>Bir özelliği gösterme
 Color gibi bazı şekil özellikleri, bir etki alanı özelliğinin değeri ile bağlantılı olabilir.

 DSL tanımında bir şekil, bağlayıcı veya Diyagram sınıfı seçin. Sağ tıklama menüsünde, **gösterilen Ekle**' yi seçin ve ardından istediğiniz özelliği (örneğin, Fill Color) seçin.

 Artık şekil, program kodunda veya Kullanıcı olarak ayarlayabileceğiniz bir etki alanı özelliğine sahiptir.

## <a name="dynamically-updating-an-exposed-property"></a>Sunulan bir özelliği dinamik olarak güncelleştirme
 Genellikle, ortaya çıkan özelliği başka bir özelliğe bağımlı hale getirmek istersiniz. Örneğin, belirli bir etki alanı özelliği sıfırdan küçük olduğunda bir şeklin kırmızı olmasını isteyebilirsiniz. Bu bağımlılığı yapmak için bir [kural](../modeling/rules-propagate-changes-within-the-model.md)oluşturun. Örneğin:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
namespace ExampleNamespace
{
 // Attribute associates the rule with class:
 [RuleOn(typeof(CarShape), FireTime = TimeToFire.TopLevelCommit)]
 // The rule is a class derived from one of the abstract rules:
 class CarShapeAddRule : AddRule
 {
 // Override the abstract method:
 public override void ElementAdded(ElementAddedEventArgs e)
 {
 base.ElementAdded(e);
 CarShape shape = e.ModelElement as CarShape;
 Store store = shape.Store;
 // Ignore this call if we're currently loading a model:
 if (store.TransactionManager.CurrentTransaction.IsSerializing)
  return;
 Car car = shape.ModelElement as Car;
 // Code here propagates change as required - for example:
 shape.FillColor = car.Somebool ? System.Drawing.Color.Red : System.Drawing.Color.Green;
 }
}
 // The rule must be registered:
 public partial class ExampleDomainModel
 {
 protected override Type[] GetCustomDomainModelTypes()
 {
  List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
  types.Add(typeof(CarShapeAddRule));
  // If you add more rules, list them here.
  return types.ToArray();
 }
 }
}
```