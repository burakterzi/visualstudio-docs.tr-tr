---
title: Yüklemeden sonra çalıştırılması gereken komutlar | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e85a03c71064687fdfbacf24b7aa59cd2a47f1a
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72982030"
---
# <a name="commands-that-must-be-run-after-installation"></a>Yüklemeden sonra çalıştırılması gereken komutlar
Uzantınızı bir *. msi* dosyası aracılığıyla dağıtırsanız, Visual Studio 'nun uzantılarınızı bulması için **devenv/setup** ' ı yüklemenizin bir parçası olarak çalıştırmanız gerekir.

> [!NOTE]
> Bu konudaki bilgiler, *devenv. exe dosyasını* Visual Studio 2008 ve öncesiyle bulmaya yöneliktir. *Devenv. exe dosyasını* Visual Studio 'nun sonraki sürümleriyle bulma hakkında bilgi için bkz. [sistem gereksinimlerini algılama](../../extensibility/internals/detecting-system-requirements.md).

## <a name="find-devenvexe"></a>Devenv. exe dosyasını bulun
 Her bir sürümün *devenv. exe* ' yi, kayıt defteri değerlerini özellikler olarak depolamak Için RegLocator tablosu ve AppSearch tablolarını kullanarak, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yükleyiciler tarafından yazılan kayıt defteri değerlerinden bulabilirsiniz. Daha fazla bilgi için bkz. [sistem gereksinimlerini algılama](../../extensibility/internals/detecting-system-requirements.md).

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>Visual Studio 'nun farklı sürümlerindeki devenv. exe ' yi bulmak için RegLocator tablo satırları

|İmza|Asıl|Anahtar|Name|Tür|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2003|2|Software\microsoft\visualstudio\7,1\setup\vs|EnvironmentPath|2|
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Karşılık gelen RegLocator tablo satırları için AppSearch Tablo satırları

|Özellik|İmza|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 Örneğin, Visual Studio yükleyicisi **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** kayıt defteri değerini *C:\VS2008\Common7\IDE\devenv.exe*olarak yazar, yürütülebilir dosyanın tüm yolu yükleyicinin çalışması gerekir.

> [!NOTE]
> RegLocator tablosunun Type sütunu 2 olduğundan, Imza tablosunda ek sürüm bilgisi belirtilmesi gerekli değildir.

## <a name="run-devenvexe"></a>Devenv. exe dosyasını çalıştır
 AppSearch standart eylemi yükleyicide çalıştıktan sonra, AppSearch tablosundaki her bir özellik, ilgili Visual Studio sürümü için *devenv. exe* dosyasını işaret eden bir değere sahiptir. Belirtilen kayıt defteri değerlerinden herhangi biri mevcut değilse — Visual Studio 'nun bu sürümü yüklü olmadığından, belirtilen özellik null olarak ayarlanır.

 Windows Installer, özelliğin özel eylem türü 50 aracılığıyla işaret ettiği yürütülebilir dosyayı çalıştırmayı destekler. Özel eylem, VSPackage 'ın [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ile tümleştirmadan önce başarılı bir şekilde yüklendiğinden emin olmak için komut dosyası yürütme seçeneklerini `msidbCustomActionTypeInScript` (1024) ve `msidbCustomActionTypeCommit` (512) içermelidir. Daha fazla bilgi için bkz. [komut dosyası yürütme seçeneklerinde](/windows/desktop/msi/custom-action-in-script-execution-options) [CustomAction tablosu](/windows/desktop/msi/customaction-table) ve özel eylem.

 50 türündeki özel eylemler, kaynak sütunun değeri olarak yürütülebilir dosyayı içeren özelliği ve hedef sütununda komut satırı bağımsız değişkenlerini belirtir.

### <a name="customaction-table-rows-to-run-devenvexe"></a>Devenv. exe dosyasını çalıştırmak için CustomAction tablosu satırları

|Eylem|Tür|Kaynak|Hedef|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/Setup|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/Setup|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/Setup|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/Setup|

 Yükleme sırasında yürütülmek üzere zamanlamak için, özel eylemler InstallExecuteSequence tablosuna yazılmalıdır. Bu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sürümü sistemde yüklü değilse özel eylemin çalıştırılmasını engellemek için koşul sütununun her satırında karşılık gelen özelliğini kullanın.

> [!NOTE]
> Koşullarda kullanıldığında null değerli özellikler `False` değerlendirilir.

 Her bir özel eylem için dizi sütununun değeri, Windows Installer paketinizin diğer sıra değerlerine bağlıdır. Sıra değerleri, InstallFinalize standart eyleminden hemen önce, *devenv. exe* özel eylemlerinin mümkün olduğunca yakın şekilde çalışmasını sağlamak için olmalıdır.

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Devenv. exe özel eylemlerini zamanlamak için InstallExecuteSequence tablosu

|Eylem|Koşul|Sequence|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>Ayrıca bkz.
- [Windows Installer ile VSPackages 'i yükler](../../extensibility/internals/installing-vspackages-with-windows-installer.md)