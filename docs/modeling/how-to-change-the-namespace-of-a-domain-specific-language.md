---
title: 'Nasıl yapılır: etki alanına özgü dilin ad alanını değiştirme'
ms.date: 10/31/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b64a61c02f44db0ce70b758331d0d70f7bb8014d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653759"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Nasıl yapılır: etki alanına özgü dilin ad alanını değiştirme

Etki alanına özgü dilin ad alanını değiştirebilirsiniz. DSL **Gezgini**' nde, DSL paketi projesinin özelliklerinde ve derleme bilgilerinde değişiklik yapın.

## <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Etki alanına özgü dilin ad alanını değiştirmek için

1. **DSL Gezgini**' nde **DSL** düğümünü seçin.

2. **Özellikler** penceresinde **ad alanı** özelliğini değiştirin.

3. Çözümü kaydedin ve şablonları dönüştürün.

4. **Proje** menüsünde **DSL özellikleri**' ni seçin.

   Projenizin özellikleri görüntülenir.

5. **Uygulama** sekmesini seçin.

6. **Varsayılan ad alanı** özelliğini yeni ad alanı adı olarak değiştirin.

7. Derlemenin adını da değiştirmek istiyorsanız, **derleme adı özelliğini değiştirin.**

8. Derleme adını değiştirdiyseniz Dslpackage\package.exe ' i açın ve bu satırı güncelleştirin:

   `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Herhangi bir özel kod yazdıysanız, kod dosyalarındaki ad alanını ve sınıf başvurularını değiştirdiğinizden emin olun.

10. Visual Studio Deneysel örneğini sıfırlayın.

    1. **\Users \\** _{Name}_ **\appdata\local\microsoft\visualstudio \\ \*Exp**silin.

    2. Windows **Başlat** menüsünde **tüm programlar**  > **Microsoft Visual Studio 2010 SDK**  > **Araçlar**  > **deneysel örneği sıfırlayın**.

11. **Derle** menüsünde **çözümü yeniden derle**' yi seçin.

## <a name="see-also"></a>Ayrıca bkz.

[Etki alanına özgü dil Araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)