---
title: Evrensel Windows projelerini yönetme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e542d1cc53fbdfb287d004c15b2a9055d3a0cba1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647957"
---
# <a name="manage-universal-windows-projects"></a>Evrensel Windows projelerini yönetme

Evrensel Windows uygulamaları, geliştiricilerin her iki platformda de kod ve diğer varlıkları kullanmasına izin veren Windows 8.1 ve Windows Phone 8,1 ' i hedefleyen uygulamalardır. Paylaşılan kod ve kaynaklar paylaşılan bir projede tutulur, ancak platforma özgü kod ve kaynaklar bir diğeri Windows ve diğeri de Windows Phone ayrı projelerde tutulur. Evrensel Windows uygulamaları hakkında daha fazla bilgi için bkz. [Evrensel Windows uygulamaları](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx). Projeleri yöneten Visual Studio uzantıları, Evrensel Windows uygulama projelerinin tek platformlu uygulamalardan farklı bir yapıya sahip olduğunu bilmelidir. Bu izlenecek yol, paylaşılan projenin nasıl gezindiğini ve paylaşılan öğelerin nasıl yönetileceğini gösterir.

## <a name="prerequisites"></a>Prerequisites

Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="navigate-the-shared-project"></a>Paylaşılan projede gezin

1. C# **Testüniversalproject**adlı bir VSIX projesi oluşturun. (**Dosya**  > **Yeni**  > **projesi** ve **C#**  > **genişletilebilirlik**  > **Visual Studio paketi**). Özel bir **komut** projesi öğe şablonu ekleyin ( **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve  > **Yeni öğe** **Ekle** ' yi seçin ve ardından **genişletilebilirlik**' e gidin). **Testüniversalproject**dosyasını adlandırın.

2. *Microsoft. VisualStudio. Shell. Interop. 12,1. DesignTime. dll* ve *Microsoft. VisualStudio. Shell. Interop. 14.0. DesignTime. dll* ( **Uzantılar** bölümünde) için bir başvuru ekleyin.

3. *TestUniversalProject.cs* açın ve aşağıdaki `using` yönergeleri ekleyin:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.PlatformUI;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using System.Collections.Generic;
    using System.IO;
    using System.Windows.Forms;
    ```

4. @No__t_0 sınıfında, **Çıkış** penceresine işaret eden bir özel alan ekleyin.

    ```csharp
    public sealed class TestUniversalProject
    {
        IVsOutputWindowPane output;
    . . .
    }
    ```

5. Testüniversalproject oluşturucusunun içindeki çıkış bölmesine yönelik başvuruyu ayarlayın:

    ```csharp
    private TestUniversalProject(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);
            EventHandler eventHandler = this.ShowMessageBox;
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);
            commandService.AddCommand(menuItem);
        }
        // get a reference to the Output window
                    output = (IVsOutputWindowPane)ServiceProvider.GetService(typeof(SVsGeneralOutputWindowPane));
    }
    ```

6. @No__t_0 yönteminden mevcut kodu kaldırın:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
    }
    ```

7. Bu kılavuzda birkaç farklı amaçla kullanacağınız DTE nesnesini Al. Ayrıca, menü düğmesine tıklandığında bir çözümün yüklendiğinden emin olun.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (EnvDTE.DTE)this.ServiceProvider.GetService(typeof(EnvDTE.DTE));
        if (dte.Solution != null)
        {
            . . .
        }
        else
        {
            MessageBox.Show("No solution is open");
            return;
        }
    }
    ```

8. Paylaşılan projeyi bulun. Paylaşılan proje, saf bir kapsayıcıdır; çıkış oluşturmaz veya üretmez. Aşağıdaki yöntem, paylaşılan proje özelliğine sahip <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> nesnesini arayarak çözümdeki ilk paylaşılan projeyi bulur.

    ```csharp
    private IVsHierarchy FindSharedProject()
    {
        var sln = (IVsSolution)this.ServiceProvider.GetService(typeof(SVsSolution));
        Guid empty = Guid.Empty;
        IEnumHierarchies enumHiers;

        //get all the projects in the solution
        ErrorHandler.ThrowOnFailure(sln.GetProjectEnum((uint)__VSENUMPROJFLAGS.EPF_LOADEDINSOLUTION, ref empty, out enumHiers));
        foreach (IVsHierarchy hier in ComUtilities.EnumerableFrom(enumHiers))
        {
            if (PackageUtilities.IsCapabilityMatch(hier, "SharedAssetsProject"))
            {
                return hier;
            }
        }
        return null;
    }
    ```

9. @No__t_0 yönteminde, paylaşılan projenin yazı başlığını ( **Çözüm Gezgini**görüntülenen proje adı) çıkış.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));

        if (dte.Solution != null)
        {
            var sharedHier = this.FindSharedProject();
            if (sharedHier != null)
            {
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,
                     (int)__VSHPROPID.VSHPROPID_Caption);
                output.OutputStringThreadSafe(string.Format("Found shared project: {0}\n", sharedCaption));
            }
            else
            {
                MessageBox.Show("Solution has no shared project");
                return;
            }
                }
        else
        {
            MessageBox.Show("No solution is open");
            return;
        }
    }
    ```

10. Etkin platform projesini alın. Platform projeleri, platforma özgü kod ve kaynakları içeren projelerdir. Aşağıdaki yöntem, etkin platform projesini almak için <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy> yeni alanını kullanır.

    ```csharp
    private IVsHierarchy GetActiveProjectContext(IVsHierarchy hierarchy)
    {
        IVsHierarchy activeProjectContext;
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,
             (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, out activeProjectContext))
        {
            return activeProjectContext;
        }
        else
        {
            return null;
        }
    }
    ```

11. @No__t_0 yönteminde, etkin platform projesinin resim yazısını çıkış.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));

        if (dte.Solution != null)
        {
            var sharedHier = this.FindSharedProject();
            if (sharedHier != null)
            {
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,
                     (int)__VSHPROPID.VSHPROPID_Caption);
                output.OutputStringThreadSafe(string.Format("Shared project: {0}\n", sharedCaption));

                var activePlatformHier = this.GetActiveProjectContext(sharedHier);
                if (activePlatformHier != null)
                {
                    string activeCaption = HierarchyUtilities.GetHierarchyProperty<string>(activePlatformHier,
                         (uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_Caption);
                    output.OutputStringThreadSafe(string.Format("Active platform project: {0}\n", activeCaption));
                }
                else
                {
                MessageBox.Show("Shared project has no active platform project");
                }
            }
            else
            {
                MessageBox.Show("Solution has no shared project");
                return;
            }
        }
        else
            {
                MessageBox.Show("No solution is open");
                return;
            }
        }
    }
    ```

12. Platform projeleri aracılığıyla yineleyin. Aşağıdaki yöntem, paylaşılan projeden tüm içeri aktarma (Platform) projelerini alır.

    ```csharp
    private IEnumerable<IVsHierarchy> EnumImportingProjects(IVsHierarchy hierarchy)
    {
        IVsSharedAssetsProject sharedAssetsProject;
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,
            (int)__VSHPROPID7.VSHPROPID_SharedAssetsProject, out sharedAssetsProject)
            && sharedAssetsProject != null)
        {
            foreach (IVsHierarchy importingProject in sharedAssetsProject.EnumImportingProjects())
            {
                yield return importingProject;
            }
        }
    }
    ```

    > [!IMPORTANT]
    > Kullanıcı deneysel örnekte bir C++ Evrensel Windows uygulaması projesi açarsa, yukarıdaki kod bir özel durum oluşturur. Bu bilinen bir sorundur. Özel durumdan kaçınmak için yukarıdaki `foreach` bloğunu aşağıdaki kodla değiştirin:

    ```csharp
    var importingProjects = sharedAssetsProject.EnumImportingProjects();
    for (int i = 0; i < importingProjects.Count; ++i)
    {
        yield return importingProjects[i];
    }
    ```

13. @No__t_0 yönteminde, her platform projesinin resim yazısını çıkış. Etkin platform projesinin açıklamalı alt yazısının çıkışını çıkaran satırdan sonra aşağıdaki kodu ekleyin. Yalnızca yüklenen platform projeleri bu listede görüntülenir.

    ```csharp
    output.OutputStringThreadSafe("Platform projects:\n");

    IEnumerable<IVsHierarchy> projects = this.EnumImportingProjects(sharedHier);

    bool isActiveProjectSet = false;
    foreach (IVsHierarchy platformHier in projects)
    {
        string platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,
            (int)__VSHPROPID.VSHPROPID_Caption);
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));
    }
    ```

14. Etkin platform projesini değiştirin. Aşağıdaki yöntem <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A> kullanarak etkin projeyi ayarlar.

    ```csharp
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)
    {
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);
    }
    ```

15. @No__t_0 yönteminde, etkin platform projesini değiştirin. Bu kodu `foreach` bloğunun içine ekleyin.

    ```csharp
    bool isActiveProjectSet = false;
    string platformCaption = null;
    foreach (IVsHierarchy platformHier in projects)
    {
        platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,
             (int)__VSHPROPID.VSHPROPID_Caption);
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));

        // if this project is neither the shared project nor the current active platform project,
        // set it to be the active project
        if (!isActiveProjectSet && platformHier != activePlatformHier)
        {
            this.SetActiveProjectContext(sharedHier, platformHier);
            activePlatformHier = platformHier;
            isActiveProjectSet = true;
        }
    }
    output.OutputStringThreadSafe("set active project: " + platformCaption +'\n');
    ```

16. Şimdi deneyin. Deneysel örneği başlatmak için F5 tuşuna basın. Deneysel örnekte C# bir evrensel Hub uygulaması projesi oluşturun ( **Yeni proje** iletişim kutusunda, **Visual C#**   > **Windows**  > **Windows 8**  > **Universal** 0**hub app**). Çözüm yüklendikten sonra, **Araçlar** menüsüne gidin ve **Testüniversalproject komutunu çağır**' a tıklayın ve ardından **Çıkış** bölmesinde metni kontrol edin. Aşağıdakine benzer bir şey görmeniz gerekir:

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    ```

### <a name="manage-the-shared-items-in-the-platform-project"></a>Platform projesindeki paylaşılan öğeleri yönetme

1. Platform projesinde paylaşılan öğeleri bulun. Paylaşılan projedeki öğeler, platform projesinde paylaşılan öğeler olarak görüntülenir. Bunları **Çözüm Gezgini**göremez, ancak proje hiyerarşisine onları bulmak için bu adımları izleyebilirsiniz. Aşağıdaki yöntem hiyerarşiyi açıklar ve tüm paylaşılan öğeleri toplar. Bu, isteğe bağlı olarak her öğenin başlığını verir. Paylaşılan öğeler yeni özellik <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_IsSharedItem> tarafından tanımlanır.

    ```csharp
    private void InspectHierarchyItems(IVsHierarchy hier, uint itemid, int level, List<uint> itemIds, bool getSharedItems, bool printItems)
    {
        string caption = HierarchyUtilities.GetHierarchyProperty<string>(hier, itemid, (int)__VSHPROPID.VSHPROPID_Caption);
        if (printItems)
            output.OutputStringThreadSafe(string.Format("{0}{1}\n", new string('\t', level), caption));

        // if getSharedItems is true, inspect only shared items; if it's false, inspect only unshared items
        bool isSharedItem;
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID7.VSHPROPID_IsSharedItem, out isSharedItem)
            && (isSharedItem == getSharedItems))
        {
            itemIds.Add(itemid);
        }

        uint child;
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID.VSHPROPID_FirstChild, Unbox.AsUInt32, out child)
            && child != (uint)VSConstants.VSITEMID.Nil)
        {
            this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);

            while (HierarchyUtilities.TryGetHierarchyProperty(hier, child, (int)__VSHPROPID.VSHPROPID_NextSibling, Unbox.AsUInt32, out child)
                && child != (uint)VSConstants.VSITEMID.Nil)
            {
                this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);
            }
                    }
    }
    ```

2. @No__t_0 yönteminde, Platform proje hiyerarşisi öğelerine yol göstermek için aşağıdaki kodu ekleyin. @No__t_0 bloğunun içine ekleyin.

    ```csharp
    output.OutputStringThreadSafe("Walk the active platform project:\n");
    var sharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ```

3. Paylaşılan öğeleri okuyun. Paylaşılan öğeler, platform projesinde gizli bağlantılı dosyalar olarak görünür ve tüm özellikleri sıradan bağlantılı dosyalar olarak okuyabilirsiniz. Aşağıdaki kod, ilk paylaşılan öğenin tam yolunu okur.

    ```csharp
    var sharedItemId = sharedItemIds[0];
    string fullPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));
    ```

4. Şimdi deneyin. Deneysel örneği başlatmak için **F5** tuşuna basın. Deneysel örnekte C# bir evrensel Hub uygulaması projesi oluşturun ( **Yeni proje** iletişim kutusunda, **Visual C#**   > **Windows**  > **Windows 8**  > **Universal** 0**Hub uygulaması**) **Araçlar** menüsüne gidin ve **Testüniversalproject komutunu çağır**' a tıklayın ve ardından **Çıkış** bölmesinde metni kontrol edin. Aşağıdakine benzer bir şey görmeniz gerekir:

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    Walk the active platform project:
        HubApp.WindowsPhone
            <HubApp.Shared>
                App.xaml
                    App.xaml.cs
                Assets
                    DarkGray.png
                    LightGray.png
                    MediumGray.png
                Common
                    NavigationHelper.cs
                    ObservableDictionary.cs
                    RelayCommand.cs
                    SuspensionManager.cs
                DataModel
                    SampleData.json
                    SampleDataSource.cs
                HubApp.Shared.projitems
                Strings
                    en-US
                        Resources.resw
            Assets
                HubBackground.theme-dark.png
                HubBackground.theme-light.png
                Logo.scale-240.png
                SmallLogo.scale-240.png
                SplashScreen.scale-240.png
                Square71x71Logo.scale-240.png
                StoreLogo.scale-240.png
                WideLogo.scale-240.png
            HubPage.xaml
                HubPage.xaml.cs
            ItemPage.xaml
                ItemPage.xaml.cs
            Package.appxmanifest
            Properties
                AssemblyInfo.cs
            References
                .NET for Windows Store apps
                HubApp.Shared
                Windows Phone 8.1
            SectionPage.xaml
                SectionPage.xaml.cs
    ```

### <a name="detect-changes-in-platform-projects-and-shared-projects"></a>Platform projelerindeki ve paylaşılan projelerdeki değişiklikleri Algıla

1. Platform projeleri için olduğu gibi, paylaşılan projelerdeki değişiklikleri algılamak için hiyerarşi ve proje olaylarını kullanabilirsiniz. Ancak, Paylaşılan projedeki proje öğeleri görünür değildir, bu da paylaşılan proje öğeleri değiştirildiğinde belirli olayların tetiklememesinin anlamına gelir.

    Projedeki bir dosya yeniden adlandırıldığında olay sırasını göz önünde bulundurun:

   1. Dosya adı diskte değiştirilir.

   2. Proje dosyası, dosyanın yeni adını içerecek şekilde güncelleştirilir.

      Hiyerarşi olayları (örneğin, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>) genellikle kullanıcı arabiriminde gösterilecek değişiklikleri **Çözüm Gezgini**gibi izler. Hiyerarşi olayları, dosya silmeyi ve sonra dosya eklemeyi bir dosya yeniden adlandırma işlemini ele alalım. Ancak, görünmeyen öğeler değiştirildiğinde, hiyerarşi olay sistemi bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> olayı tetikler, ancak <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> bir olay vermez. Bu nedenle, bir platform projesindeki bir dosyayı yeniden adlandırırsanız, hem <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> hem de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> alırsınız, ancak paylaşılan bir projede bir dosyayı yeniden adlandırırsanız yalnızca <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> alırsınız.

      Proje öğelerindeki değişiklikleri izlemek için, DTE proje öğesi olaylarını (<xref:EnvDTE.ProjectItemsEventsClass> bulunan) işleyebilirsiniz. Ancak, çok sayıda olayı işliyorsa, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> olayları daha iyi bir şekilde işlemeyi sağlayabilirsiniz. Bu kılavuzda yalnızca hiyerarşi olayları ve DTE olayları gösterilmektedir. Bu yordamda paylaşılan bir projeye ve bir platform projesine bir olay dinleyicisi eklersiniz. Ardından, paylaşılan bir projedeki bir dosyayı ve bir platform projesindeki başka bir dosyayı yeniden adlandırdığınızda, her yeniden adlandırma işlemi için tetiklenen olayları görebilirsiniz.

      Bu yordamda paylaşılan bir projeye ve bir platform projesine bir olay dinleyicisi eklersiniz. Ardından, paylaşılan bir projedeki bir dosyayı ve bir platform projesindeki başka bir dosyayı yeniden adlandırdığınızda, her yeniden adlandırma işlemi için tetiklenen olayları görebilirsiniz.

2. Olay dinleyicisi ekleyin. Projeye yeni bir sınıf dosyası ekleyin ve *HierarchyEventListener.cs*çağırın.

3. *HierarchyEventListener.cs* dosyasını açın ve aşağıdaki using yönergelerini ekleyin:

   ```csharp
   using Microsoft.VisualStudio.Shell.Interop;
   using Microsoft.VisualStudio;
   using System.IO;
   ```

4. @No__t_0 sınıfı <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents> uygular:

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   { }
   ```

5. @No__t_0 üyelerini aşağıdaki kodda olduğu gibi uygulayın.

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   {
       private IVsHierarchy hierarchy;
       IVsOutputWindowPane output;

       internal HierarchyEventListener(IVsHierarchy hierarchy, IVsOutputWindowPane outputWindow) {
            this.hierarchy = hierarchy;
            this.output = outputWindow;
       }

       int IVsHierarchyEvents.OnInvalidateIcon(IntPtr hIcon) {
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnInvalidateItems(uint itemIDParent) {
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemAdded(uint itemIDParent, uint itemIDSiblingPrev, uint itemIDAdded) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemAdded: " + itemIDAdded + "\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemDeleted(uint itemID) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemDeleted: " + itemID + "\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemsAppended(uint itemIDParent) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemsAppended\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnPropertyChanged(uint itemID, int propID, uint flags) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnPropertyChanged: item ID " + itemID + "\n");
           return VSConstants.S_OK;
       }
   }
   ```

6. Aynı sınıfta, bir proje öğesi yeniden adlandırıldığında gerçekleşen DTE Event <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> için başka bir olay işleyicisi ekleyin.

   ```csharp
   public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)
   {
       output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",
            oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));
   }
   ```

7. Hiyerarşi olayları için kaydolun. İzlemekte olduğunuz her proje için ayrı ayrı kaydolmanız gerekir. Aşağıdaki kodu, biri paylaşılan proje için ve diğeri de platform projelerinden biri için `ShowMessageBox` ekleyin.

   ```csharp
   // hook up the event listener for hierarchy events on the shared project
   HierarchyEventListener listener1 = new HierarchyEventListener(sharedHier, output);
   uint cookie1;
   sharedHier.AdviseHierarchyEvents(listener1, out cookie1);

   // hook up the event listener for hierarchy events on the
   active project
   HierarchyEventListener listener2 = new HierarchyEventListener(activePlatformHier, output);
   uint cookie2;
   activePlatformHier.AdviseHierarchyEvents(listener2, out cookie2);
   ```

8. DTE proje öğesi olay <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> için kaydolun. İkinci dinleyiciyi geçirdikten sonra aşağıdaki kodu ekleyin.

   ```csharp
   // hook up DTE events for project items
   Events2 dteEvents = (Events2)dte.Events;
   dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;
   ```

9. Paylaşılan öğeyi değiştirin. Bir platform projesindeki paylaşılan öğeleri değiştiremezsiniz; Bunun yerine, bunları, bu öğelerin gerçek sahibi olan paylaşılan projede değiştirmeniz gerekir. @No__t_0 Paylaşılan projedeki karşılık gelen öğe KIMLIĞINI, paylaşılan öğenin tam yolunu vererek alabilirsiniz. Ardından paylaşılan öğeyi değiştirebilirsiniz. Değişiklik platform projelerine dağıtılır.

    > [!IMPORTANT]
    > Projeyi değiştirmeden önce bir proje öğesinin paylaşılan öğe olup olmadığını fark etmelisiniz.

     Aşağıdaki yöntem bir proje öğesi dosyasının adını değiştirir.

    ```csharp
    private void ModifyFileNameInProject(IVsHierarchy project, string path)
    {
        int found;
        uint projectItemID;
        VSDOCUMENTPRIORITY[] priority = new VSDOCUMENTPRIORITY[1];
        if (ErrorHandler.Succeeded(((IVsProject)project).IsDocumentInProject(path, out found, priority, out projectItemID))
            && found != 0)
        {
            var name = DateTime.Now.Ticks.ToString() + Path.GetExtension(path);
            project.SetProperty(projectItemID, (int)__VSHPROPID.VSHPROPID_EditLabel, name);
            output.OutputStringThreadSafe(string.Format("Renamed {0} to {1}\n", path,name));
        }
    }
    ```

10. Dosya adını Paylaşılan projedeki öğe olarak değiştirmek için `ShowMessageBox` tüm diğer koddan sonra bu yöntemi çağırın. Paylaşılan projedeki öğenin tam yolunu alan koddan sonra bunu ekleyin.

    ```csharp
    // change the file name of an item in a shared project
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));
    this.ModifyFileNameInProject(sharedHier, fullPath);
    ```

11. Projeyi derleyin ve çalıştırın. Deneysel örnekte C# bir evrensel Hub uygulaması oluşturun, **Araçlar** menüsüne gidin ve **Testuniversal salproject komutunu çağır**' a tıklayın ve genel çıkış bölmesindeki metni denetleyin. Paylaşılan projedeki ilk öğenin adı ( *app. xaml* dosyası olması beklenir) değiştirilmelidir ve <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> olayının tetiklendiğini görmeniz gerekir. Bu durumda, *app. xaml* 'in yeniden adlandırılması, *app.xaml.cs* 'in de yeniden adlandırılmasına neden olduğundan, dört olay görmeniz gerekir (her platform projesi için iki adet). (DTE olayları Paylaşılan projedeki öğeleri izlemez.) İki <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> olayı (Platform projelerinin her biri için bir tane) görmeniz gerekir, ancak hiçbir <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> olay görmezsiniz.

12. Şimdi bir platform projesindeki bir dosyayı yeniden adlandırmayı deneyin ve tetiklenen olaylardaki farkı görebilirsiniz. @No__t_1 çağrısından sonra `ShowMessageBox` aşağıdaki kodu ekleyin.

    ```csharp
    // change the file name of an item in a platform project
    var unsharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, unsharedItemIds, false, false);

    var unsharedItemId = unsharedItemIds[0];
    string unsharedPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(unsharedItemId, out unsharedPath));
    output.OutputStringThreadSafe(string.Format("Platform project item ID = {0}, full path = {1}\n", unsharedItemId, unsharedPath));

    this.ModifyFileNameInProject(activePlatformHier, unsharedPath);
    ```

13. Projeyi derleyin ve çalıştırın. Deneysel örnekte C# bir evrensel proje oluşturun, **Araçlar** menüsüne gidin ve **Testuniversal salproject komutunu çağır**' a tıklayın ve genel çıkış bölmesindeki metni denetleyin. Platform projesindeki dosya yeniden adlandırıldıktan sonra, hem <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> hem de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> bir olay görmeniz gerekir. Dosyanın değiştirilmesi başka hiçbir dosyanın değiştirilmesine neden olduğundan ve bir platform projesindeki öğelerde yapılan değişiklikler her yerde yayılmadığı için, bu olayların yalnızca bir tane vardır.
