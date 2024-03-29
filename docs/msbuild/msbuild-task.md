---
title: MSBuild görevi | Microsoft Docs
ms.date: 07/30/2019
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#MSBuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild task [MSBuild]
- MSBuild, MSBuild task
ms.assetid: 76577f6c-7669-44ad-a840-363e37a04d34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d0b2b0c4cee2a372bccb8ad461ed195fc5519d7
ms.sourcegitcommit: 0554b59a2a251661e56824fb9cd6e9b1f326cef1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71831862"
---
# <a name="msbuild-task"></a>MSBuild görevi

Başka bir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projesinden projeler [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] oluşturur.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda `MSBuild` görevinin parametreleri açıklanmaktadır.

| Parametre | Açıklama |
|-----------------------------------| - |
| `BuildInParallel` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, `Projects` parametresinde belirtilen projeler mümkünse paralel olarak oluşturulur. Varsayılan değer `false`. |
| `Projects` | Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Oluşturulacak proje dosyalarını belirtir. |
| `Properties` | İsteğe bağlı `String` parametresi.<br /><br /> Alt projeye genel özellikler olarak uygulanacak Özellik adı/değer çiftleri için noktalı virgülle ayrılmış bir liste. Bu parametreyi belirttiğinizde, [*MSBuild. exe*](../msbuild/msbuild-command-line-reference.md)ile oluşturduğunuzda **-Property** anahtarına sahip özellikleri ayarlamaya işlevsel olarak eşdeğerdir. Örneğin:<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> Özellikleri projeye `Properties` parametresi aracılığıyla geçirdiğinizde, proje dosyası zaten yüklenmiş olsa bile [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projenin yeni bir örneğini oluşturabilir. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], belirli bir proje yolu ve özel bir genel özellikler kümesi için tek bir proje örneği oluşturur. Örneğin, bu davranış, Configuration = sürümü ile *MyProject. proj*' i çağıran birden çok MSBuild görevi oluşturmanıza olanak sağlar ve *MyProject. proj* ' in tek bir örneğini alırsınız (görevde benzersiz özellikler belirtilmemişse). Henüz [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]tarafından görülmemiş bir özellik belirtirseniz, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projenin diğer örneklerine paralel olarak oluşturulan yeni bir örneğini oluşturur. Örneğin, bir sürüm yapılandırması hata ayıklama yapılandırması ile aynı anda derleyebilir.|
| `RebaseOutputs` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, derleme projelerinin hedef çıkış öğelerinin göreli yollarının, çağıran projeye göreli olarak ayarlanmış yolları vardır. Varsayılan değer `false`. |
| `RemoveProperties` | İsteğe bağlı `String` parametresi.<br /><br /> Kaldırılacak genel özellikler kümesini belirtir. |
| `RunEachTargetSeparately` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] görevi her bir hedefi aynı anda değil, her seferinde bir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] bir kez çağırır. Bu parametrenin `true` olarak ayarlanması, daha önce çağrılan hedefler başarısız olsa bile sonraki hedeflerin çağrılmasını garanti eder. Aksi takdirde, bir yapı hatası sonraki tüm hedeflerin çağrılmasını durdurur. Varsayılan değer `false`. |
| `SkipNonexistentProjects` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, diskte bulunmayan proje dosyaları atlanır. Aksi takdirde, bu tür projeler hataya neden olur. |
| `StopOnFirstFailure` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, projelerden biri derlenmediğinde, daha fazla proje derlenmeyecektir. Şu anda paralel olarak (birden çok işlemciyle) oluşturulurken bu desteklenmez. |
| `TargetAndPropertyListSeparators` | İsteğe bağlı `String[]` parametresi.<br /><br /> `Project` öğesi meta verileri olarak hedeflerin ve özelliklerin listesini belirtir). Ayırıcıların işlenmeden önce önüne atlanacaktır. örn .% 3B (kaçan '; '), kaçışsız bir '; ' gibi değerlendirilir. |
| `TargetOutputs` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` salt okunurdur çıkış parametresi.<br /><br /> Tüm proje dosyalarından oluşturulan hedeflerin çıkışlarını döndürür. Yalnızca belirtilen hedeflerden gelen çıktılar döndürülür, bu hedeflerin bağımlı olduğu hedeflerde mevcut olabilecek hiçbir çıktı değildir.<br /><br /> `TargetOutputs` parametresi aşağıdaki meta verileri de içerir:<br /><br /> -   `MSBuildSourceProjectFile`: çıkışları belirten hedefi içeren [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje dosyası.<br />-   `MSBuildSourceTargetName`: çıkışları oluşturan hedef. **Note:**  Her bir proje dosyası veya hedefi için çıktıları ayrı ayrı tanımlamak istiyorsanız, `MSBuild` görevi her proje dosyası veya hedefi için ayrı olarak çalıştırın. Tüm proje dosyalarını derlemek için `MSBuild` görevi yalnızca bir kez çalıştırırsanız, tüm hedeflerin çıktıları tek bir dizide toplanır. |
| `Targets` | İsteğe bağlı `String` parametresi.<br /><br /> Proje dosyalarında oluşturulacak hedef veya hedefleri belirtir. Bir hedef adları listesini ayırmak için noktalı virgül kullanın. `MSBuild` görevde hiçbir hedef belirtilmemişse, proje dosyalarında belirtilen varsayılan hedefler oluşturulur. **Note:**  Hedefler tüm proje dosyalarında gerçekleşmelidir. Aksi takdirde, bir derleme hatası oluşur. |
| `ToolsVersion` | İsteğe bağlı `String` parametresi.<br /><br /> Bu göreve geçirilen projeler oluşturulurken kullanılacak `ToolsVersion` belirtir.<br /><br /> [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] görevin, projede belirtilenden farklı bir .NET Framework sürümünü hedefleyen bir proje oluşturmasını sağlar. Geçerli değerler `2.0`, `3.0` ve `3.5`. Varsayılan değer `3.5`. |

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

 *MSBuild. exe*' yi başlatmak için [Exec görevini](../msbuild/exec-task.md) kullanmaktan farklı olarak, bu görev alt projeleri oluşturmak için aynı [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] işlemini kullanır. Atlanmak üzere önceden oluşturulmuş hedeflerin listesi, üst ve alt derlemeler arasında paylaşılır. Yeni [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] işlem oluşturulmadığından bu görev da daha hızlıdır.

 Bu görev yalnızca proje dosyalarını değil, çözüm dosyalarını da işleyebilir.

 Bir yapılandırma, uzak altyapıyı (örneğin, bağlantı noktaları, protokoller, zaman aşımları, yeniden denemeler vb.) içerse de, projelerin aynı anda oluşturulmasını sağlamak için [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] tarafından gereken herhangi bir yapılandırma, bir yapılandırma dosyası kullanılarak yapılandırılabilir hale getirilmelidir. Mümkün olduğunda yapılandırma öğelerinin `MSBuild` görevde görev parametreleri olarak belirtibilmeleri gerekir.

 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3,5 ' den başlayarak, çözüm projeleri artık oluşturduğu tüm alt projelerdeki Targetoutkoyar.

## <a name="pass-properties-to-projects"></a>Özellikleri projelere geçir

 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3,5 ' den önceki sürümlerinde, farklı özellik kümelerinin [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] öğede listelenen farklı projelere geçirilmesi zor oldu. [MSBuild görevinin](../msbuild/msbuild-task.md)Properties özniteliğini kullandıysanız, bu ayar, [MSBuild görevini](../msbuild/msbuild-task.md) toplu olarak ve öğe listesindeki her proje için koşullu olarak farklı özellikler sağladıkça oluşturulan tüm projelere uygulandı.

 Ancak, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3,5, [MSBuild görevi](../msbuild/msbuild-task.md)kullanılarak oluşturulan farklı projelere yönelik farklı özellikleri geçirmek için esnek bir yol sağlayan iki yeni ayrılmış meta veri öğesi, özellik ve additionalproperties sağlar.

> [!NOTE]
> Bu yeni meta veri öğeleri yalnızca [MSBuild görevinin](../msbuild/msbuild-task.md)Projects özniteliğinde geçirilen öğeler için geçerlidir.

## <a name="multi-processor-build-benefits"></a>Çok işlemcili derleme avantajları

 Bu yeni meta verileri kullanmanın önemli avantajlarından biri, projelerinizi çok işlemcili bir sistemde paralel olarak oluşturduğunuzda oluşur. Meta veriler, tüm projeleri toplu işlem veya koşullu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] görevleri gerçekleştirmek zorunda kalmadan tek bir [MSBuild görev](../msbuild/msbuild-task.md) çağrısında birleştirmenize olanak tanır. Yalnızca tek bir [MSBuild görevini](../msbuild/msbuild-task.md)çağırdığınızda, projeler özniteliğinde listelenen tüm projeler paralel olarak oluşturulur. (Ancak, `BuildInParallel=true` özniteliği [MSBuild görevinde](../msbuild/msbuild-task.md)varsa.) Daha fazla bilgi için bkz. [paralel olarak birden çok proje oluşturma](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).

## <a name="properties-metadata"></a>Özellikler meta verileri

 Belirtildiğinde, Özellikler meta verileri görevin Özellikler parametresini geçersiz kılar, ancak [Additionalproperties](#additionalproperties-metadata) meta verileri parametrenin tanımlarına eklenir.

 Yaygın bir senaryo, [MSBuild görevini](../msbuild/msbuild-task.md)kullanarak yalnızca farklı derleme yapılandırması kullanarak birden çok çözüm dosyası derlerken olur. Hata ayıklama yapılandırması ve, sürüm yapılandırması kullanılarak a2 çözümünü kullanarak a1 çözümü oluşturmak isteyebilirsiniz. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2,0 ' de, bu proje dosyası aşağıdaki gibi görünür:

> [!NOTE]
> Aşağıdaki örnekte, "..." ek çözüm dosyalarını temsil eder.

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="Build">
        <MSBuild Projects="a1.sln..." Properties="Configuration=Debug"/>
        <MSBuild Projects="a2.sln" Properties="Configuration=Release"/>
    </Target>
</Project>
```

 Ancak, Özellikler meta verilerini kullanarak, aşağıdaki şekilde gösterildiği gibi tek bir [MSBuild görevi](../msbuild/msbuild-task.md)kullanmak için bunu basitleştirebilirsiniz:

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <ProjectToBuild Include="a1.sln...">
            <Properties>Configuration=Debug</Properties>
        </ProjectToBuild>
        <ProjectToBuild Include="a2.sln">
            <Properties>Configuration=Release</Properties>
        </ProjectToBuild>
    </ItemGroup>
    <Target Name="Build">
        <MSBuild Projects="@(ProjectToBuild)"/>
    </Target>
</Project>
```

 \- veya -

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <ProjectToBuild Include="a1.sln..."/>
        <ProjectToBuild Include="a2.sln">
            <Properties>Configuration=Release</Properties>
        </ProjectToBuild>
    </ItemGroup>
    <Target Name="Build">
        <MSBuild Projects="@(ProjectToBuild)"
          Properties="Configuration=Debug"/>
    </Target>
</Project>
```

## <a name="additionalproperties-metadata"></a>AdditionalProperties meta verileri

 Hem sürüm yapılandırması hem de x86 mimarisini ve diğerini ia64 mimarisini kullanarak bir [MSBuild görevini](../msbuild/msbuild-task.md)kullanarak iki çözüm dosyası oluşturduğunuz aşağıdaki senaryoyu göz önünde bulundurun. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2,0 ' de, farklı bir [MSBuild görevi](../msbuild/msbuild-task.md)örneği oluşturmanız gerekir: bir tane, sürüm yapılandırmasını kullanarak x86 mimarisi ile sürüm yapılandırması kullanarak projeyi derlemek için Proje dosyanız şu şekilde görünür:

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="Build">
        <MSBuild Projects="a1.sln..." Properties="Configuration=Release;
          Architecture=x86"/>
        <MSBuild Projects="a2.sln" Properties="Configuration=Release;
          Architecture=ia64"/>
    </Target>
</Project>
```

 AdditionalProperties meta verilerini kullanarak, aşağıdakileri kullanarak tek bir [MSBuild görevi](../msbuild/msbuild-task.md) kullanmak için bunu basitleştirebilirsiniz:

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <ProjectToBuild Include="a1.sln...">
            <AdditionalProperties>Architecture=x86
              </AdditionalProperties>
        </ProjectToBuild>
        <ProjectToBuild Include="a2.sln">
            <AdditionalProperties>Architecture=ia64
              </AdditionalProperties>
        </ProjectToBuild>
    </ItemGroup>
    <Target Name="Build">
        <MSBuild Projects="@(ProjectToBuild)"
          Properties="Configuration=Release"/>
    </Target>
</Project>
```

## <a name="example"></a>Örnek

 Aşağıdaki örnek, `ProjectReferences` öğesi koleksiyonu tarafından belirtilen projeleri oluşturmak için `MSBuild` görevini kullanır. Elde edilen hedef çıktıları `AssembliesBuiltByChildProjects` öğesi koleksiyonu 'nda depolanır.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <ProjectReferences Include="*.*proj" />
    </ItemGroup>

    <Target Name="BuildOtherProjects">
        <MSBuild
            Projects="@(ProjectReferences)"
            Targets="Build">
            <Output
                TaskParameter="TargetOutputs"
                ItemName="AssembliesBuiltByChildProjects" />
        </MSBuild>
    </Target>

</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
