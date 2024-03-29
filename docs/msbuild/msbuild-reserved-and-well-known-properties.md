---
title: MSBuild ayrılmış ve Iyi bilinen Özellikler | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, reserved properties
ms.assetid: 99333e61-83c9-4804-84e3-eda297c2478d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9bd54e97535c281d50119fdc7aa759d0704fa9e1
ms.sourcegitcommit: b5cb0eb09369677514ee1f44d5d7050d34c7fbc1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491553"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>MSBuild ayrılmış ve iyi bilinen Özellikler
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], proje dosyası ve [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ikilileri hakkında bilgi depolayan önceden tanımlanmış özellikler kümesi sağlar. Bu özellikler diğer [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] özellikleriyle aynı şekilde değerlendirilir. Örneğin, `MSBuildProjectFile` özelliğini kullanmak için `$(MSBuildProjectFile)`yazın.

 MSBuild, ayrılmış ve iyi bilinen özellikleri önceden tanımlamak için aşağıdaki tablodaki değerleri kullanır. Ayrılmış Özellikler geçersiz kılınamaz, ancak aynı adlı ortam özellikleri, genel özellikler veya proje dosyasında belirtilen özellikler kullanılarak iyi bilinen özellikler geçersiz kılınabilir.

## <a name="reserved-and-well-known-properties"></a>Ayrılmış ve iyi bilinen Özellikler
 Aşağıdaki tabloda [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] önceden tanımlanmış özellikler açıklanmaktadır.

| Özellik | Ayrılmış veya iyi bilinen | Açıklama |
|----------------------------------|------------------------| - |
| `MSBuildBinPath` | Ayrılamadı | Kullanılmakta olan [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ikililerin bulunduğu klasörün mutlak yolu (örneğin, *C:\Windows\Microsoft.NET\Framework\\\<versionNumber >* ). [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] dizinindeki dosyalara başvurmanız gerekirse bu özellik faydalıdır.<br /><br /> Bu özelliğe son ters eğik çizgiyi eklemeyin. |
| `MSBuildExtensionsPath` | İyi bilinen | .NET Framework 4 ' te tanıtılan: varsayılan `MSBuildExtensionsPath` ve `MSBuildExtensionsPath32`değerleri arasında fark yoktur. Daha önceki sürümlerde `MSBuildExtensionsPath` varsayılan değerinin davranışını etkinleştirmek için ortam değişkenini `MSBUILDLEGACYEXTENSIONSPATH` null olmayan bir değere ayarlayabilirsiniz.<br /><br /> .NET Framework 3,5 ve önceki sürümlerde varsayılan `MSBuildExtensionsPath` değeri, geçerli işlemin bitliğine bağlı olarak *\program files\\* veya *\Program Files (x86)* klasörü altındaki MSBuild alt klasörünün yolunu işaret eder. Örneğin, 64 bit bir makinedeki 32 bitlik bir işlem için bu özellik, *\Program Files (x86)* klasörünü işaret eder. 64 bit makinede 64 bitlik bir işlem için bu özellik *\Program Files* klasörünü işaret eder.<br /><br /> Bu özelliğe son ters eğik çizgiyi eklemeyin.<br /><br /> Bu konum, özel hedef dosyaları yerleştirmek için kullanışlı bir yerdir. Örneğin, hedef dosyalarınız *\Program Files\msbuild\myfiles\northwind.exe dizinine* yüklenip daha sonra bu XML kodu kullanılarak proje dosyalarına aktarılabilir:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>` |
| `MSBuildExtensionsPath32` | İyi bilinen | *\Program Files* veya *\Program Files (x86)* klasörü altındaki [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] alt klasörünün yolu. Yol her zaman 32 bit makinedeki 32-bit *\Program Files (x86)* klasörünü ve 64-bit makinesindeki *\Program dosyalarını* işaret eder. ". Ayrıca bkz. `MSBuildExtensionsPath` ve `MSBuildExtensionsPath64`.<br /><br /> Bu özelliğe son ters eğik çizgiyi eklemeyin. |
| `MSBuildExtensionsPath64` | İyi bilinen | *\Program Files* klasörü altındaki [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] alt klasörünün yolu. 64 bitlik bir makine için bu yol her zaman *\Program Files* klasörünü işaret eder. 32 bitlik bir makine için bu yol boştur. Ayrıca bkz. `MSBuildExtensionsPath` ve `MSBuildExtensionsPath32`.<br /><br /> Bu özelliğe son ters eğik çizgiyi eklemeyin. |
| `MSBuildLastTaskResult` | Ayrılamadı | önceki görev herhangi bir hata olmadan (Uyarılar olsa bile) veya önceki görevde hata varsa `false` `true`. Genellikle, bir görevde bir hata oluştuğunda, hata bu projede gerçekleşen son şeydir. Bu nedenle, bu özelliğin değeri hiçbir şekilde `false`, bu senaryolar haricinde:<br /><br /> - [Görev öğesinin (MSBuild)](../msbuild/task-element-msbuild.md) `ContinueOnError` özniteliği `WarnAndContinue` (veya `true`) ya da `ErrorAndContinue`olarak ayarlandığında.<br /><br /> -`Target` bir alt öğe olarak bir [HATADÜZEYİ (MSBuild) öğesi](../msbuild/onerror-element-msbuild.md) olduğunda. |
| `MSBuildNodeCount` | Ayrılamadı | Oluşturulurken kullanılan eşzamanlı işlem sayısı üst sınırı. Bu, komut satırında **-maxcpucount** için belirttiğiniz değerdir. Değer belirtmeden **-maxcpucount** belirttiyseniz, `MSBuildNodeCount` bilgisayardaki işlemcilerin sayısını belirtir. Daha fazla bilgi için bkz. [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md) ve [paralel olarak birden çok proje oluşturma](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md). |
| `MSBuildProgramFiles32` | Ayrılamadı | 32 bit program klasörünün konumu; Örneğin, *C:\Program Files (x86)* .<br /><br /> Bu özelliğe son ters eğik çizgiyi eklemeyin. |
| `MSBuildProjectDefaultTargets` | Ayrılamadı | `Project` öğesinin `DefaultTargets` özniteliğinde belirtilen hedeflerin tamamı listesi. Örneğin, aşağıdaki `Project` öğesi `A;B;C``MSBuildDefaultTargets` özellik değerine sahip olacaktır:<br /><br /> `<Project DefaultTargets="A;B;C" >` |
| `MSBuildProjectDirectory` | Ayrılamadı | Proje dosyasının bulunduğu dizinin mutlak yolu, örneğin *C:\company\myproduct*.<br /><br /> Bu özelliğe son ters eğik çizgiyi eklemeyin. |
| `MSBuildProjectDirectoryNoRoot` | Ayrılamadı | Kök sürücü hariç `MSBuildProjectDirectory` özelliğinin değeri.<br /><br /> Bu özelliğe son ters eğik çizgiyi eklemeyin. |
| `MSBuildProjectExtension` | Ayrılamadı | Proje dosyasının süresi de dahil olmak üzere dosya adı uzantısı; Örneğin, *. proj*. |
| `MSBuildProjectFile` | Ayrılamadı | Proje dosyasının dosya adı uzantısı da dahil olmak üzere dosyanın tamamı. Örneğin, *MyApp. proj*. |
| `MSBuildProjectFullPath` | Ayrılamadı | Dosya adı uzantısı da dahil olmak üzere, proje dosyasının mutlak yolu ve tam dosya adı. Örneğin, *C:\mycompany\myproduct\myapp.exe*. |
| `MSBuildProjectName` | Ayrılamadı | Dosya adı uzantısı olmadan proje dosyasının dosya adı; Örneğin, *MyApp*. |
| `MSBuildRuntimeType` | Ayrılamadı | Şu anda yürütülmekte olan çalışma zamanının türü. MSBuild 15 ' te tanıtılmıştır. Değer tanımsız olabilir (MSBuild 15 ' ten önce), MSBuild 'in masaüstü .NET Framework üzerinde çalıştığını belirten `Full`, `Core` .NET Core üzerinde (örneğin `dotnet build`) veya MSBuild 'in mono üzerinde çalıştığını belirten `Mono`. |
| `MSBuildStartupDirectory` | Ayrılamadı | [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] çağrıldığı klasörün mutlak yolu. Bu özelliği kullanarak, her dizinde *\<dizin >. proj* dosyası oluşturmadan bir proje ağacındaki belirli bir noktanın altındaki her şeyi oluşturabilirsiniz. Bunun yerine, burada gösterildiği gibi yalnızca bir projeniz vardır — örneğin, *c:\traversal.proj*.<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Ağaçta herhangi bir noktada derlemek için şunu yazın:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> Bu özelliğe son ters eğik çizgiyi eklemeyin. |
| `MSBuildThisFile` | Ayrılamadı | `MSBuildThisFileFullPath`dosya adı ve dosya uzantısı kısmı. |
| `MSBuildThisFileDirectory` | Ayrılamadı | `MSBuildThisFileFullPath`Dizin kısmı.<br /><br /> Yola son ters eğik çizgiyi ekleyin. |
| `MSBuildThisFileDirectoryNoRoot` | Ayrılamadı | Kök sürücü hariç `MSBuildThisFileFullPath`Dizin kısmı.<br /><br /> Yola son ters eğik çizgiyi ekleyin. |
| `MSBuildThisFileExtension` | Ayrılamadı | `MSBuildThisFileFullPath`dosya adı uzantısı kısmı. |
| `MSBuildThisFileFullPath` | Ayrılamadı | Çalıştıran hedefi içeren projenin veya hedef dosyanın mutlak yolu.<br /><br /> İpucu: asıl proje dosyasına göre değil, hedef dosya ile ilişkili olan bir hedefler dosyasında göreli bir yol belirtebilirsiniz. |
| `MSBuildThisFileName` | Ayrılamadı | Dosya adı uzantısı olmadan `MSBuildThisFileFullPath`dosya adı kısmı. |
| `MSBuildToolsPath` | Ayrılamadı | `MSBuildToolsVersion`değeri ile ilişkili [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] sürümünün yükleme yolu.<br /><br /> Yola son ters eğik çizgiyi eklemeyin.<br /><br /> Bu özellik geçersiz kılınamaz. |
| `MSBuildToolsVersion` | Ayrılamadı | Projeyi derlemek için kullanılan [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] araç takımının sürümü.<br /><br /> Note: bir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] araç takımı, bir uygulama oluşturmak için kullanılan görevlerden, hedeflerin ve araçlardan oluşur. Araçlar, *CSC. exe* ve *Vbc. exe*gibi derleyiciler içerir. Daha fazla bilgi için bkz. [araç takımı (araçları sürümü)](../msbuild/msbuild-toolset-toolsversion.md)ve [Standart ve özel araç takımı yapılandırması](../msbuild/standard-and-custom-toolset-configurations.md). |
| `MSBuildVersion` | Ayrılamadı | Projeyi derlemek için kullanılan [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] sürümü. <br /><br/> Bu özellik geçersiz kılınamıyor, aksi takdirde `MSB4004 - The 'MSBuildVersion' property is reserved, and can not be modified.` hata iletisi döndürülür. |

## <a name="names-that-conflict-with-msbuild-elements"></a>MSBuild öğeleriyle çakışan adlar

Yukarıdaki ' a ek olarak, MSBuild dil öğelerine karşılık gelen adlar Kullanıcı tanımlı özellikler, öğeler veya öğe meta verileri için kullanılamaz:

* VisualStudioProject
* Hedef
* PropertyGroup
* Çıkış
* ItemGroup
* UsingTask
* ProjectExtensions
* OnError
* ImportGroup
* Yerel koruma uygulamak isterseniz
* Oluşturulurken
* güvenmiyorsanız

## <a name="see-also"></a>Ayrıca bkz.
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)

- [MSBuild özellikleri](../msbuild/msbuild-properties.md)
