---
title: 'Nasıl yapılır: kodlama ile dosyaları kaydetme ve açma'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Unicode, bidirectional language support
- files, encoding
- bidirectional language support, encoded files
- file encoding, bidirectional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b02734af3efb24e1e3791246b0cea405b12d7b15
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645796"
---
# <a name="how-to-save-and-open-files-with-encoding"></a>Nasıl yapılır: kodlama ile dosyaları kaydetme ve açma

Çift yönlü dilleri desteklemek için belirli karakter kodlamasına sahip dosyaları kaydedebilirsiniz. Ayrıca, dosyayı açarken bir kodlama belirtebilirsiniz, böylece Visual Studio dosyayı doğru şekilde görüntüler.

## <a name="to-save-a-file-with-encoding"></a>Kodlamalı bir dosyayı kaydetmek için

1. **Dosya** menüsünde **dosyayı farklı kaydet**' i seçin ve ardından **Kaydet** düğmesinin yanındaki açılan düğmeye tıklayın.

     **Gelişmiş kaydetme seçenekleri** iletişim kutusu görüntülenir.

2. **Kodlama**bölümünde dosya için kullanılacak kodlamayı seçin.

3. İsteğe bağlı olarak **satır sonları**altında satır sonu karakterlerinin biçimini seçin.

     Bu seçenek, dosyayı farklı bir işletim sistemi kullanıcılarıyla değiş tokuş etmek istiyorsanız yararlıdır.

     Belirli bir şekilde kodlandığını bildiğiniz bir dosyayla çalışmak istiyorsanız, Visual Studio 'Yu dosyayı açarken bu kodlamayı kullanmasını söyleyebilirsiniz. Kullandığınız yöntem, dosyanın projenizin bir parçası olup olmamasına bağlıdır.

## <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>Projenin bir parçası olan kodlanmış bir dosyayı açmak için

1. **Çözüm Gezgini**, dosyaya sağ tıklayın ve **birlikte Aç**' ı seçin.

2. **Birlikte Aç** iletişim kutusunda dosyayı ile açmak için düzenleyiciyi seçin.

     Form Düzenleyicisi gibi birçok Visual Studio Düzenleyicisi, kodlamayı otomatik olarak algılayacak ve dosyayı uygun şekilde açacak. Bir kodlama seçmenize izin veren bir düzenleyici seçerseniz, **kodlama** iletişim kutusu görüntülenir.

3. **Kodlama** iletişim kutusunda düzenleyicinin kullanması gereken kodlamayı seçin.

## <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>Bir projenin parçası olmayan kodlanmış bir dosyayı açmak için

1. **Dosya** menüsünde **Aç**' ın üzerine gelin, Web 'den **Dosya** veya **Dosya**' yı seçin ve ardından açılacak dosyayı seçin.

2. **Aç** düğmesinin yanındaki açılan düğmeye tıklayın ve **birlikte Aç**' ı seçin.

3. Yukarıdaki yordamda 2. ve 3. adımları izleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kodlama ve satır sonları](encodings-and-line-breaks.md)
- [Kodlama ve Windows Forms Genelleştirme](/dotnet/framework/winforms/advanced/encoding-and-windows-forms-globalization)
- [Uygulamaları globalize ve yerelleştirme](../ide/globalizing-and-localizing-applications.md)