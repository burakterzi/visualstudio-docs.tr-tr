---
title: Menü öğelerine klavye kısayollarını bağlama | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98c0b6f5b26e7f423f2a89f680395ceaba7286bc
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72982266"
---
# <a name="bind-keyboard-shortcuts-to-menu-items"></a>Klavye kısayollarını menü öğelerine bağlama
Bir klavye kısayolunu özel bir menü komutuna bağlamak için, Package için *. vsct* dosyasına bir giriş eklemeniz yeterlidir. Bu konu başlığı altında, klavye kısayolunun özel düğme, menü öğesi veya araç çubuğu komutuna nasıl değiştirileceği ve varsayılan düzenleyicide klavye eşlemesinin nasıl uygulanacağı veya özel bir düzenleyici ile nasıl sınırlandırılacağını açıklanmaktadır.

 Mevcut Visual Studio menü öğelerine klavye kısayolları atamak için bkz. [klavye kısayollarını tanımlamak ve özelleştirmek](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

## <a name="choose-a-key-combination"></a>Bir anahtar birleşimi seçin
 Birçok klavye kısayolu, Visual Studio 'da zaten kullanılıyor. Yinelenen bağlamalar algılanabileceğinden ve ayrıca öngörülemeyen sonuçlara neden olabileceğinden, aynı kısayolu birden fazla komuta atamamalısınız. Bu nedenle, bir kısayolu atamadan önce kullanılabilirliğini doğrulamak iyi bir fikirdir.

### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Klavye kısayolunun kullanılabilirliğini doğrulamak için

1. **Araçlar** > **Seçenekler** > **ortam** penceresinde **klavye**' yi seçin.

2. **' De yeni kısayol kullan ' ın** **Global**olarak ayarlandığından emin olun.

3. **Kısayol tuşlarını bas** kutusunda, kullanmak istediğiniz klavye kısayolunu yazın.

    Kısayol zaten Visual Studio 'da kullanılıyorsa, Box **tarafından şu anda kullanılan kısayol** , kısayolun Şu anda çağırdığı komutu gösterir.

4. Eşlenmemiş bir tane bulana kadar anahtarların farklı birleşimlerini deneyin.

   > [!NOTE]
   > **Alt** kullanan klavye kısayolları, bir menü açabilir ve doğrudan bir komut yürütmez. Bu nedenle, **alt**içeren bir kısayol yazdığınızda, **Şu anda Box tarafından kullanılan kısayol** boş olabilir. Kısayolun, **Seçenekler** iletişim kutusunu kapatarak ve ardından tuşlara basarak bir menü açmadığından emin olabilirsiniz.

   Aşağıdaki yordamda, bir menü komutuyla mevcut bir VSPackage olduğunu varsaymaktadır. Bu işlemi gerçekleştirmek için yardıma ihtiyacınız varsa, bir [menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md)konusuna göz atın.

### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Bir komuta klavye kısayolu atamak için

1. Paketiniz için *. vsct* dosyasını açın.

2. Zaten mevcut değilse, `<Commands>` sonra boş bir `<KeyBindings>` bölümü oluşturun.

   > [!WARNING]
   > Anahtar bağlamaları hakkında daha fazla bilgi için bkz. [KeyBinding](../extensibility/keybinding-element.md).

    `<KeyBindings>` bölümünde, bir `<KeyBinding>` girişi oluşturun.

    `guid` ve `id` özniteliklerini çağırmak istediğiniz komuta ait olanlarla ayarlayın.

    `mod1` özniteliğini **Control**, **alt**veya **SHIFT**olarak ayarlayın.

    KeyBindings bölümü şuna benzemelidir:

   ```xml
   <KeyBindings>
       <KeyBinding guid="<name of command set>" id="<name of command id>"
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>
   </KeyBindings>

   ```

   Klavye kısayolunuz ikiden fazla anahtar gerektiriyorsa, `mod2` ve `key2` özniteliklerini ayarlayın.

   Çoğu durumda, **kaydırma** ikinci bir değiştirici olmadan kullanılmamalıdır çünkü bu, en fazla alfasayısal anahtarın büyük harf veya simge yazmasına neden olur.

   Sanal anahtar kodları, işlev anahtarları ve **geri al** tuşu gibi kendileriyle ilişkili bir karakter olmayan özel anahtarlara erişmenizi sağlar. Daha fazla bilgi için bkz. [sanal anahtar kodları](/windows/desktop/inputdev/virtual-key-codes).

   Komutu Visual Studio Düzenleyicisi 'nde kullanılabilir hale getirmek için `editor` özniteliğini `guidVSStd97`olarak ayarlayın.

   Komutu yalnızca özel bir düzenleyicide kullanılabilir hale getirmek için, `editor` özniteliğini, özel düzenleyiciyi içeren VSPackage oluşturduğunuzda [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] paket şablonu tarafından oluşturulan özel düzenleyicinin adına ayarlayın. Ad değerini bulmak için, `name` özniteliği "`editorfactory`" olan bir `<GuidSymbol>` düğümü için `<Symbols>` bölümüne bakın. Bu, özel düzenleyicinin adıdır.

## <a name="example"></a>Örnek
 Bu örnek, **Ctrl**+**alt**+**C** klavye kısayolunu `MyPackage`adlı bir pakette `cmdidMyCommand` adlı bir komuta bağlar.

```
<CommandTable>
. . .
<Commands>
. . .
</Commands>
<KeyBindings>
  <KeyBinding guid="guidMyPackageCmdSet" id="cmdidMyCommand"
      key1="C" mod1="CONTROL" mod2="ALT" editor="guidVSStd97" />
</KeyBindings>
. . .
</CommandTable>
```

## <a name="example"></a>Örnek
 Bu örnek, **Ctrl**+**B** klavye kısayolunu `TestEditor`adlı bir projede `cmdidBold` adında bir komuta bağlar. Komut, diğer düzenleyicilerde değil yalnızca özel düzenleyicide kullanılabilir.

```xml
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />
```

## <a name="see-also"></a>Ayrıca bkz.
- [Menüleri ve komutları genişletme](../extensibility/extending-menus-and-commands.md)