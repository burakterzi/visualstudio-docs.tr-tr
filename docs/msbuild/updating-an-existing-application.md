---
title: Mevcut bir uygulamayı MSBuild 15 ' e güncelleştirme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a891f6d18657bad65a1cf087da975849642b7aec
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72912043"
---
# <a name="update-an-existing-application-for-msbuild-15"></a>MSBuild 15 için mevcut bir uygulamayı güncelleştirme

15,0 ' dan önceki MSBuild sürümlerinde, MSBuild genel derleme önbelleğinden (GAC) yüklendi ve MSBuild uzantıları kayıt defterine yüklendi. Bu, tüm uygulamaların aynı MSBuild sürümünü kullandı ve aynı araç kümelerine erişimi vardı, ancak Visual Studio 'nun farklı sürümlerinin yan yana yüklemelerini engelledi.

Daha hızlı, daha küçük ve yan yana yüklemeyi desteklemek için, Visual Studio 2017 ve üzeri sürümler artık GAC 'de MSBuild 'e yerleştirmiyor veya kayıt defterini değiştirmiyor. Ne yazık ki bu şekilde, projeleri değerlendirmek veya oluşturmak için MSBuild API 'sini kullanmak isteyen uygulamalar, Visual Studio yüklemesinde örtülü olarak güvenemez.

## <a name="use-msbuild-from-visual-studio"></a>Visual Studio 'dan MSBuild 'i kullanma

Uygulamanıza ait program derlemelerinin Visual Studio veya *MSBuild. exe*içinde yapılan yapılarla eşleştiğinden emin olmak Için, Visual Studio 'dan MSBuild derlemelerini yükleyin ve Visual Studio 'Da bulunan SDK 'leri kullanın. Microsoft. Build. Locator NuGet paketi bu işlemi basitleştirir.

## <a name="use-microsoftbuildlocator"></a>Microsoft. Build. Locator kullanın

*Microsoft. Build. Locator. dll dosyasını* uygulamanızla yeniden dağıtırsanız, diğer MSBuild derlemelerini dağıtmanız gerekmez.

Bir projeyi MSBuild 15 kullanacak şekilde güncelleştirmek ve Konumlandırıcı API 'SI projenizde aşağıda açıklanan birkaç değişiklik yapılmasını gerektirir. Bir projeyi güncelleştirmek için gereken değişikliklere bir örnek görmek için bkz. [MSBuildLocator deposundaki örnek bir projeye yapılan işlemeler](https://github.com/Microsoft/MSBuildLocator/commits/example-updating-to-msbuild-15).

### <a name="change-msbuild-references"></a>MSBuild başvurularını değiştirme

MSBuild 'in merkezi bir konumdan yüklendiğinden emin olmak için derlemelerini uygulamanızla dağıtmamalıdır.

Merkezi bir konumdan MSBuild 'in yüklenmesini önlemek için projenizi değiştirme mekanizması, MSBuild 'e nasıl başvurdığınıza bağlıdır.

#### <a name="use-nuget-packages-preferred"></a>NuGet paketlerini kullan (tercih edilen)

Bu yönergelerde, [Packagereference stili NuGet başvurularını](/nuget/consume-packages/package-references-in-project-files)kullandığınız varsayılır.

Proje dosyanızı NuGet paketlerinden MSBuild derlemelerine başvuracak şekilde değiştirin. NuGet 'e derlemelerin yalnızca derleme zamanında gerekli olduğunu ve çıkış dizinine kopyalanmayacağını bildirmek için `ExcludeAssets=runtime` belirtin.

MSBuild paketlerinin büyük ve küçük sürümü, desteklemek istediğiniz Visual Studio 'nun en düşük sürümüne eşit veya ondan daha az olmalıdır. Örneğin, Visual Studio 2017 ve sonraki sürümlerini desteklemek istiyorsanız, başvuru paketi sürümüne `15.1.548`.

Örneğin, bu XML 'yi kullanabilirsiniz:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.Build" Version="15.1.548" ExcludeAssets="runtime" />
  <PackageReference Include="Microsoft.Build.Utilities.Core" Version="15.1.548" ExcludeAssets="runtime" />
</ItemGroup>
```

#### <a name="use-extension-assemblies"></a>Uzantı derlemelerini kullanma

NuGet paketlerini kullanamıyoruz, Visual Studio ile dağıtılan MSBuild derlemelerine başvurabilirsiniz. MSBuild 'e doğrudan başvurdıysanız, `Copy Local` `False`ayarlayarak çıkış dizininize kopyalanmadığından emin olun. Proje dosyasında, bu ayar aşağıdaki kodla aynı şekilde görünür:

```xml
    <Reference Include="Microsoft.Build, Version=15.1.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
      <Private>False</Private>
    </Reference>
```

#### <a name="binding-redirects"></a>Bağlama yeniden yönlendirmeleri

Uygulamanızın 15.1.0.0 sürümüne gereken bağlama yeniden yönlendirmelerini otomatik olarak kullandığından emin olmak için Microsoft. Build. Locator paketine başvurun. Bu sürüme yeniden yönlendirme, hem MSBuild 15 hem de MSBuild 16 desteği sağlar.

### <a name="ensure-output-is-clean"></a>Çıktının temiz olduğundan emin olun

Bir sonraki adımda eklenen Microsoft. Build. *Locator. dll*dışında *Microsoft. Build.\*. dll* derlemelerini içermediğinden emin olmak için projenizi derleyin ve çıkış dizinini inceleyin.

### <a name="add-package-reference-for-microsoftbuildlocator"></a>Microsoft. Build. Locator için paket başvurusu Ekle

[Microsoft. Build. Locator](https://www.nuget.org/packages/Microsoft.Build.Locator/)Için bir NuGet paketi başvurusu ekleyin.

```xml
    <PackageReference Include="Microsoft.Build.Locator">
      <Version>1.1.2</Version>
    </PackageReference>
```

Microsoft. Build. Locator paketi için `ExcludeAssets=runtime` belirtmeyin.

### <a name="register-instance-before-calling-msbuild"></a>MSBuild çağrılmadan önce örneği Kaydet

MSBuild kullanan herhangi bir yöntemi çağırmadan önce Locator API 'sine bir çağrı ekleyin.

Konumlandırıcı API 'sine çağrı eklemenin en kolay yolu,

```csharp
MSBuildLocator.RegisterDefaults();
```

uygulamanızın başlangıç kodunda.

MSBuild yüklemesi üzerinde daha ayrıntılı denetim isterseniz, `MSBuildLocator.RegisterInstance()` el ile geçirilecek `MSBuildLocator.QueryVisualStudioInstances()` sonucunu seçebilirsiniz, ancak bu genellikle gerekli değildir.
