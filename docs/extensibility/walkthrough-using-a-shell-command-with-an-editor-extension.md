---
title: 'İzlenecek yol: bir düzenleyici uzantısıyla kabuk komutu kullanma | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 08c3acb26fe6eed1918dd1f9bb9e84b260defa5e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72632495"
---
# <a name="walkthrough-use-a-shell-command-with-an-editor-extension"></a>İzlenecek yol: Düzenleyici uzantısı ile bir Shell komutu kullanma
VSPackage 'da, düzenleyiciye menü komutları gibi özellikler ekleyebilirsiniz. Bu izlenecek yol, bir menü komutunu çağırarak düzenleyicide bir metin görünümüne nasıl kenarlığı ekleneceğini gösterir.

 Bu izlenecek yol, bir VSPackage 'ın Managed Extensibility Framework (MEF) bileşeni bölümüyle birlikte kullanımını gösterir. Menü komutunu Visual Studio Kabuğu ile kaydetmek için VSPackage kullanmanız gerekir. Ve, MEF bileşeni bölümüne erişmek için komutunu da kullanabilirsiniz.

## <a name="prerequisites"></a>Prerequisites
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yükleyemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-menu-command"></a>Menü komutuyla uzantı oluşturma
 **Araçlar** menüsüne **Add kenarlığı** adlı bir menü komutu koyan VSPackage oluşturun.

1. @No__t_1 adlı C# bir VSIX projesi oluşturun ve özel bir komut öğesi şablon adı **AddAdornment**ekleyin. Daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).

2. MenuCommandTest adlı bir çözüm açılır. MenuCommandTestPackage dosyası, menü komutunu oluşturan ve **Araçlar** menüsüne yerleştiren koda sahiptir. Bu noktada, komut yalnızca bir ileti kutusunun görünmesine neden olur. Sonraki adımlarda, kenarlığı yorumunu görüntülemek için bunun nasıl değiştirileceği gösterilmektedir.

3. VSıX bildirim düzenleyicisinde *Source. Extension. valtmanifest* dosyasını açın. @No__t_0 sekmesi, MenuCommandTest adlı bir Microsoft. VisualStudio. VsPackage için bir satıra sahip olmalıdır.

4. *Source. Extension. valtmanifest* dosyasını kaydedin ve kapatın.

## <a name="add-a-mef-extension-to-the-command-extension"></a>Komut uzantısına bir MEF uzantısı ekleyin

1. **Çözüm Gezgini**, çözüm düğümüne sağ tıklayın, **Ekle**' ye tıklayın ve ardından **Yeni proje**' ye tıklayın. **Yeni Proje Ekle** iletişim kutusunda, **görsel C#** ' in altında **genişletilebilirlik** ' i ve **VSIX projesi**' ni tıklatın. Projeyi `CommentAdornmentTest` olarak adlandırın.

2. Bu proje, tanımlayıcı adlı VSPackage derlemesi ile etkileşime gireceğinden, derlemeyi imzalamanız gerekir. VSPackage derlemesi için önceden oluşturulmuş olan anahtar dosyasını yeniden kullanabilirsiniz.

    1. Proje özelliklerini açın ve **imzalama** sekmesini seçin.

    2. **Derlemeyi imzala**' yı seçin.

    3. **Tanımlayıcı ad anahtar dosyası seçin**altında, MenuCommandTest derlemesi Için oluşturulan *Key. snk* dosyasını seçin.

## <a name="refer-to-the-mef-extension-in-the-vspackage-project"></a>VSPackage projesindeki MEF uzantısına bakın
 VSPackage 'a bir MEF bileşeni ekliyorsanız, bildirimde her iki varlık türünü de belirtmeniz gerekir.

> [!NOTE]
> MEF hakkında daha fazla bilgi için bkz. [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>VSPackage projesindeki MEF bileşenine başvurmak için

1. MenuCommandTest projesinde, VSıX bildirim düzenleyicisinde *Source. Extension. valtmanifest* dosyasını açın.

2. **Varlıklar** sekmesinde **Yeni**' ye tıklayın.

3. **Tür** listesinde, **Microsoft. VisualStudio. MefComponent**öğesini seçin.

4. **Kaynak** listesinde, **Geçerli çözümde bir proje**seçin.

5. **Proje** listesinde **Yorumtadornmenttest**' i seçin.

6. *Source. Extension. valtmanifest* dosyasını kaydedin ve kapatın.

7. MenuCommandTest projesinin Yorumtadornmenttest projesine bir başvurusu olduğundan emin olun.

8. Yorumtadornmenttest projesinde, projeyi derleme oluşturacak şekilde ayarlayın. **Çözüm Gezgini**, projeyi seçin ve **derleme çıkışını OutputDirectory 'ye Kopyala** özelliğinin **Özellikler** penceresine bakın ve bunu **true**olarak ayarlayın.

## <a name="define-a-comment-adornment"></a>Yorum kenarlığı tanımlama
 Kenarlığı yorumu, seçilen metni izleyen bir <xref:Microsoft.VisualStudio.Text.ITrackingSpan> ve yazarı temsil eden bazı dizeleri ve metin açıklamasını içerir.

#### <a name="to-define-a-comment-adornment"></a>Bir yorum kenarlığı tanımlamak için

1. Yorumtadornmenttest projesinde, yeni bir sınıf dosyası ekleyin ve `CommentAdornment` adlandırın.

2. Aşağıdaki başvuruları ekleyin:

    1. Microsoft. VisualStudio. CoreUtility

    2. Microsoft. VisualStudio. Text. Data

    3. Microsoft. VisualStudio. Text. Logic

    4. Microsoft. VisualStudio. Text. UI

    5. Microsoft. VisualStudio. Text. UI. WPF

    6. System. ComponentModel. Composition

    7. PresentationCore

    8. PresentationFramework

    9. WindowsBase

3. Aşağıdaki `using` yönergesini ekleyin.

    ```csharp
    using Microsoft.VisualStudio.Text;
    ```

4. Dosya `CommentAdornment` adlı bir sınıf içermelidir.

    ```csharp
    internal class CommentAdornment
    ```

5. @No__t_1, yazar ve açıklama için `CommentAdornment` sınıfına üç alan ekleyin.

    ```csharp
    public readonly ITrackingSpan Span;
    public readonly string Author;
    public readonly string Text;
    ```

6. Alanları Başlatan bir Oluşturucu ekleyin.

    ```csharp
    public CommentAdornment(SnapshotSpan span, string author, string text)
    {
        this.Span = span.Snapshot.CreateTrackingSpan(span, SpanTrackingMode.EdgeExclusive);
        this.Author = author;
        this.Text = text;
    }
    ```

## <a name="create-a-visual-element-for-the-adornment"></a>Kenarlığı için görsel öğe oluşturma
 Kenarlığı için görsel bir öğe tanımlayın. Bu izlenecek yol için, Windows Presentation Foundation (WPF) sınıfından <xref:System.Windows.Controls.Canvas> devralan bir denetim tanımlayın.

1. Yorumtadornmenttest projesinde bir sınıf oluşturun ve `CommentBlock` adlandırın.

2. Aşağıdaki `using` yönergelerini ekleyin.

    ```csharp
    using Microsoft.VisualStudio.Text;
    using System;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Media;
    using System.Windows.Shapes;
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. @No__t_0 sınıfın <xref:System.Windows.Controls.Canvas> devralmasını sağlayın.

    ```csharp
    internal class CommentBlock : Canvas
    { }
    ```

4. Kenarlığı görsel yönlerini tanımlamak için bazı özel alanlar ekleyin.

    ```csharp
    private Geometry textGeometry;
    private Grid commentGrid;
    private static Brush brush;
    private static Pen solidPen;
    private static Pen dashPen;
    ```

5. Kenarlığı yorumunu tanımlayan ve ilgili metni ekleyen bir Oluşturucu ekleyin.

    ```csharp
    public CommentBlock(double textRightEdge, double viewRightEdge,
            Geometry newTextGeometry, string author, string body)
    {
        if (brush == null)
        {
            brush = new SolidColorBrush(Color.FromArgb(0x20, 0x00, 0xff, 0x00));
            brush.Freeze();
            Brush penBrush = new SolidColorBrush(Colors.Green);
            penBrush.Freeze();
            solidPen = new Pen(penBrush, 0.5);
            solidPen.Freeze();
            dashPen = new Pen(penBrush, 0.5);
            dashPen.DashStyle = DashStyles.Dash;
            dashPen.Freeze();
        }

        this.textGeometry = newTextGeometry;

        TextBlock tb1 = new TextBlock();
        tb1.Text = author;
        TextBlock tb2 = new TextBlock();
        tb2.Text = body;

        const int MarginWidth = 8;
        this.commentGrid = new Grid();
        this.commentGrid.RowDefinitions.Add(new RowDefinition());
        this.commentGrid.RowDefinitions.Add(new RowDefinition());
        ColumnDefinition cEdge = new ColumnDefinition();
        cEdge.Width = new GridLength(MarginWidth);
        ColumnDefinition cEdge2 = new ColumnDefinition();
        cEdge2.Width = new GridLength(MarginWidth);
        this.commentGrid.ColumnDefinitions.Add(cEdge);
        this.commentGrid.ColumnDefinitions.Add(new ColumnDefinition());
        this.commentGrid.ColumnDefinitions.Add(cEdge2);

        System.Windows.Shapes.Rectangle rect = new System.Windows.Shapes.Rectangle();
        rect.RadiusX = 6;
        rect.RadiusY = 3;
        rect.Fill = brush;
        rect.Stroke = Brushes.Green;

            Size inf = new Size(double.PositiveInfinity, double.PositiveInfinity);
            tb1.Measure(inf);
            tb2.Measure(inf);
            double middleWidth = Math.Max(tb1.DesiredSize.Width, tb2.DesiredSize.Width);
            this.commentGrid.Width = middleWidth + 2 * MarginWidth;

        Grid.SetColumn(rect, 0);
        Grid.SetRow(rect, 0);
        Grid.SetRowSpan(rect, 2);
        Grid.SetColumnSpan(rect, 3);
        Grid.SetRow(tb1, 0);
        Grid.SetColumn(tb1, 1);
        Grid.SetRow(tb2, 1);
        Grid.SetColumn(tb2, 1);
        this.commentGrid.Children.Add(rect);
        this.commentGrid.Children.Add(tb1);
        this.commentGrid.Children.Add(tb2);

        Canvas.SetLeft(this.commentGrid, Math.Max(viewRightEdge - this.commentGrid.Width - 20.0, textRightEdge + 20.0));
        Canvas.SetTop(this.commentGrid, textGeometry.GetRenderBounds(solidPen).Top);

        this.Children.Add(this.commentGrid);
    }
    ```

6. Ayrıca, kenarlığı çizen bir <xref:System.Windows.Controls.Panel.OnRender%2A> olay işleyicisi uygulayın.

    ```csharp
    protected override void OnRender(DrawingContext dc)
    {
        base.OnRender(dc);
        if (this.textGeometry != null)
        {
            dc.DrawGeometry(brush, solidPen, this.textGeometry);
            Rect textBounds = this.textGeometry.GetRenderBounds(solidPen);
            Point p1 = new Point(textBounds.Right, textBounds.Bottom);
            Point p2 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid) - 20.0, p1.X), p1.Y);
            Point p3 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid), p1.X), (Canvas.GetTop(this.commentGrid) + p1.Y) * 0.5);
            dc.DrawLine(dashPen, p1, p2);
            dc.DrawLine(dashPen, p2, p3);
        }
    }
    ```

## <a name="add-an-iwpftextviewcreationlistener"></a>IWpfTextViewCreationListener ekleme
 @No__t_0, oluşturma olaylarını görüntülemeyi dinlemek için kullanabileceğiniz bir MEF bileşeni bölümüdür.

1. Yorumtadornmenttest projesine bir sınıf dosyası ekleyin ve `Connector` adlandırın.

2. Aşağıdaki `using` yönergelerini ekleyin.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. @No__t_0 uygulayan bir sınıf bildirin ve bunu "metin" <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> ve <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> dışarı aktarın. İçerik türü özniteliği, bileşenin uygulandığı içerik türünü belirtir. Metin türü, ikili olmayan tüm dosya türlerinin temel türüdür. Bu nedenle, neredeyse her metin görünümü bu türden olacaktır. Metin görünümü rolü özniteliği, bileşenin geçerli olduğu metin görünümü türünü belirtir. Belge metni görünümü rolleri genellikle satırlardan oluşan ve bir dosyada depolanan metni gösterir.

     [!code-vb[VSSDKMenuCommandTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)]
     [!code-csharp[VSSDKMenuCommandTest#11](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]

4. @No__t_0 yöntemini, `CommentAdornmentManager` statik `Create()` olayını çağıracak şekilde uygulayın.

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        CommentAdornmentManager.Create(textView);
    }
    ```

5. Komutu yürütmek için kullanabileceğiniz bir yöntem ekleyin.

    ```csharp
    static public void Execute(IWpfTextViewHost host)
    {
        IWpfTextView view = host.TextView;
        //Add a comment on the selected text. 
        if (!view.Selection.IsEmpty)
        {
            //Get the provider for the comment adornments in the property bag of the view.
            CommentAdornmentProvider provider = view.Properties.GetProperty<CommentAdornmentProvider>(typeof(CommentAdornmentProvider));

            //Add some arbitrary author and comment text. 
            string author = System.Security.Principal.WindowsIdentity.GetCurrent().Name;
            string comment = "Four score....";

            //Add the comment adornment using the provider.
            provider.Add(view.Selection.SelectedSpans[0], author, comment);
        }
    }
    ```

## <a name="define-an-adornment-layer"></a>Bir kenarlığı katmanı tanımlama
 Yeni bir kenarlığı eklemek için bir kenarlığı katmanı tanımlamanız gerekir.

### <a name="to-define-an-adornment-layer"></a>Bir kenarlığı katmanını tanımlamak için

1. @No__t_0 sınıfında, <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition> türünde bir ortak alan bildirin ve bunu kenarlığı katmanı için benzersiz bir ad belirten bir <xref:Microsoft.VisualStudio.Utilities.NameAttribute> ve bu kenarlığı katmanının diğer metin görünümü katmanlarında Z-Order ilişkisini tanımlayan bir <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> dışarı aktarın (metin , şapka ve seçim).

    ```csharp
    [Export(typeof(AdornmentLayerDefinition))]
    [Name("CommentAdornmentLayer")]
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
    public AdornmentLayerDefinition commentLayerDefinition;

    ```

## <a name="provide-comment-adornments"></a>Açıklama donbesleri sağla
 Bir kenarlığı tanımladığınızda, bir Comment kenarlığı sağlayıcısı ve bir Comment kenarlığı Manager da uygular. Comment kenarlığı sağlayıcısı, açıklama donatılarının bir listesini tutar, temel alınan metin arabelleğindeki <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> olayları dinler ve temel alınan metin silindiğinde, açıklama donatılarımı siler.

1. Yorumtadornmenttest projesine yeni bir sınıf dosyası ekleyin ve `CommentAdornmentProvider` adlandırın.

2. Aşağıdaki `using` yönergelerini ekleyin.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Collections.ObjectModel;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    ```

3. @No__t_0 adlı bir sınıf ekleyin.

    ```csharp
    internal class CommentAdornmentProvider
    {
    }
    ```

4. Metin arabelleği için özel alanlar ve arabelleğin ilişkili olduğu açıklama listesini ekleyin.

    ```csharp
    private ITextBuffer buffer;
    private IList<CommentAdornment> comments = new List<CommentAdornment>();

    ```

5. @No__t_0 için bir Oluşturucu ekleyin. Sağlayıcı `Create()` yöntemi tarafından örneklendiği için bu oluşturucunun özel erişimi olmalıdır. Oluşturucu, <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> olayına `OnBufferChanged` olay işleyicisini ekler.

    ```csharp
    private CommentAdornmentProvider(ITextBuffer buffer)
    {
        this.buffer = buffer;
        //listen to the Changed event so we can react to deletions. 
        this.buffer.Changed += OnBufferChanged;
    }

    ```

6. @No__t_0 yöntemi ekleyin.

    ```csharp
    public static CommentAdornmentProvider Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentProvider>(delegate { return new CommentAdornmentProvider(view.TextBuffer); });
    }

    ```

7. @No__t_0 yöntemi ekleyin.

    ```csharp
    public void Detach()
    {
        if (this.buffer != null)
        {
            //remove the Changed listener 
            this.buffer.Changed -= OnBufferChanged;
            this.buffer = null;
        }
    }
    ```

8. @No__t_0 olay işleyicisini ekleyin.

     [!code-csharp[VSSDKMenuCommandTest#21](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs)]
     [!code-vb[VSSDKMenuCommandTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]

9. @No__t_0 olayı için bildirim ekleyin.

    ```csharp
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;
    ```

10. Kenarlığı eklemek için bir `Add()` yöntemi oluşturun.

    ```csharp
    public void Add(SnapshotSpan span, string author, string text)
    {
        if (span.Length == 0)
            throw new ArgumentOutOfRangeException("span");
        if (author == null)
            throw new ArgumentNullException("author");
        if (text == null)
            throw new ArgumentNullException("text");

        //Create a comment adornment given the span, author and text.
        CommentAdornment comment = new CommentAdornment(span, author, text);

        //Add it to the list of comments. 
        this.comments.Add(comment);

        //Raise the changed event.
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;
        if (commentsChanged != null)
            commentsChanged(this, new CommentsChangedEventArgs(comment, null));
    }

    ```

11. @No__t_0 yöntemi ekleyin.

    ```csharp
    public void RemoveComments(SnapshotSpan span)
    {
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;

        //Get a list of all the comments that are being kept
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);

        foreach (CommentAdornment comment in this.comments)
        {
            //find out if the given span overlaps with the comment text span. If two spans are adjacent, they do not overlap. To consider adjacent spans, use IntersectsWith. 
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))
            {
                //Raise the change event to delete this comment. 
                if (commentsChanged != null)
                    commentsChanged(this, new CommentsChangedEventArgs(null, comment));
            }
            else
                keptComments.Add(comment);
        }

        this.comments = keptComments;
    }
    ```

12. Belirli bir anlık görüntü yayılma alanındaki tüm açıklamaları döndüren bir `GetComments()` yöntemi ekleyin.

    ```csharp
    public Collection<CommentAdornment> GetComments(SnapshotSpan span)
    {
        IList<CommentAdornment> overlappingComments = new List<CommentAdornment>();
        foreach (CommentAdornment comment in this.comments)
        {
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))
                overlappingComments.Add(comment);
        }

        return new Collection<CommentAdornment>(overlappingComments);
    }
    ```

13. Aşağıdaki gibi `CommentsChangedEventArgs` adlı bir sınıf ekleyin.

    ```csharp
    internal class CommentsChangedEventArgs : EventArgs
    {
        public readonly CommentAdornment CommentAdded;

        public readonly CommentAdornment CommentRemoved;

        public CommentsChangedEventArgs(CommentAdornment added, CommentAdornment removed)
        {
            this.CommentAdded = added;
            this.CommentRemoved = removed;
        }
    }
    ```

## <a name="manage-comment-adornments"></a>Açıklama donbeslerinizi Yönet
 Comment kenarlığı Manager, kenarlığı öğesini oluşturur ve kenarlığı katmanına ekler. Kenarlığı taşıyabilmesi veya silebilmesi için <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> ve <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> olaylarını dinler. Ayrıca, açıklamalar eklendiğinde veya kaldırıldığında Comment kenarlığı sağlayıcısı tarafından tetiklenen `CommentsChanged` olayını dinler.

1. Yorumtadornmenttest projesine bir sınıf dosyası ekleyin ve `CommentAdornmentManager` adlandırın.

2. Aşağıdaki `using` yönergelerini ekleyin.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Windows.Media;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Formatting;
    ```

3. @No__t_0 adlı bir sınıf ekleyin.

    ```csharp
    internal class CommentAdornmentManager
        {
        }
    ```

4. Bazı özel alanlar ekleyin.

    ```csharp
    private readonly IWpfTextView view;
    private readonly IAdornmentLayer layer;
    private readonly CommentAdornmentProvider provider;
    ```

5. Yöneticiyi <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> ve <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> olaylarına ve ayrıca `CommentsChanged` olayına abone eden bir Oluşturucu ekleyin. Yönetici statik `Create()` yöntemi tarafından örneklendiği için Oluşturucu özeldir.

    ```csharp
    private CommentAdornmentManager(IWpfTextView view)
    {
        this.view = view;
        this.view.LayoutChanged += OnLayoutChanged;
        this.view.Closed += OnClosed;

        this.layer = view.GetAdornmentLayer("CommentAdornmentLayer");

        this.provider = CommentAdornmentProvider.Create(view);
        this.provider.CommentsChanged += OnCommentsChanged;
    }
    ```

6. Sağlayıcıyı alan `Create()` yöntemini ekleyin veya gerekirse bir tane oluşturur.

    ```csharp
    public static CommentAdornmentManager Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });
    }
    ```

7. @No__t_0 işleyicisini ekleyin.

    ```csharp
    private void OnCommentsChanged(object sender, CommentsChangedEventArgs e)
    {
        //Remove the comment (when the adornment was added, the comment adornment was used as the tag). 
        if (e.CommentRemoved != null)
            this.layer.RemoveAdornmentsByTag(e.CommentRemoved);

        //Draw the newly added comment (this will appear immediately: the view does not need to do a layout). 
        if (e.CommentAdded != null)
            this.DrawComment(e.CommentAdded);
    }
    ```

8. @No__t_0 işleyicisini ekleyin.

    ```csharp
    private void OnClosed(object sender, EventArgs e)
    {
        this.provider.Detach();
        this.view.LayoutChanged -= OnLayoutChanged;
        this.view.Closed -= OnClosed;
    }
    ```

9. @No__t_0 işleyicisini ekleyin.

    ```csharp
    private void OnLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
    {
        //Get all of the comments that intersect any of the new or reformatted lines of text.
        List<CommentAdornment> newComments = new List<CommentAdornment>();

        //The event args contain a list of modified lines and a NormalizedSpanCollection of the spans of the modified lines.  
        //Use the latter to find the comments that intersect the new or reformatted lines of text. 
        foreach (Span span in e.NewOrReformattedSpans)
        {
            newComments.AddRange(this.provider.GetComments(new SnapshotSpan(this.view.TextSnapshot, span)));
        }

        //It is possible to get duplicates in this list if a comment spanned 3 lines, and the first and last lines were modified but the middle line was not. 
        //Sort the list and skip duplicates.
        newComments.Sort(delegate(CommentAdornment a, CommentAdornment b) { return a.GetHashCode().CompareTo(b.GetHashCode()); });

        CommentAdornment lastComment = null;
        foreach (CommentAdornment comment in newComments)
        {
            if (comment != lastComment)
            {
                lastComment = comment;
                this.DrawComment(comment);
            }
        }
    }
    ```

10. Yorumu çizen özel yöntemi ekleyin.

     [!code-csharp[VSSDKMenuCommandTest#35](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_3.cs)]
     [!code-vb[VSSDKMenuCommandTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_3.vb)]

## <a name="use-the-menu-command-to-add-the-comment-adornment"></a>Kenarlığı açıklamasını eklemek için menü komutunu kullanın
 VSPackage 'ın `MenuItemCallback` yöntemini uygulayarak bir açıklama kenarlığı oluşturmak için menü komutunu kullanabilirsiniz.

1. Aşağıdaki başvuruları MenuCommandTest projesine ekleyin:

    - Microsoft. VisualStudio. TextManager. Interop

    - Microsoft. VisualStudio. Editor

    - Microsoft. VisualStudio. Text. UI. WPF

2. *AddAdornment.cs* dosyasını açın ve aşağıdaki `using` yönergelerini ekleyin.

    ```csharp
    using Microsoft.VisualStudio.TextManager.Interop;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Editor;
    using CommentAdornmentTest;
    ```

3. @No__t_0 yöntemini silin ve aşağıdaki komut işleyicisini ekleyin.

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
    }
    ```

4. Etkin görünümü almak için kod ekleyin. Etkin `IVsTextView` almak için Visual Studio Kabuğu `SVsTextManager` almalısınız.

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
    }
    ```

5. Bu metin görünümü bir düzenleyici metin görünümünün bir örneği ise, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> arabirimine çevirebilirsiniz ve sonra <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> ve onunla ilişkili <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> sağlayabilirsiniz. Kenarlığı yöntemini `Connector.Execute()` çağırmak için <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> kullanın. Bu, Comment sağlayıcısını alır ve kenarlığı ekler. Komut işleyicisi şu kod gibi görünmelidir:

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
        IVsUserData userData = vTextView as IVsUserData;
         if (userData == null)
        {
            Console.WriteLine("No text view is currently open");
            return;
        }
        IWpfTextViewHost viewHost;
        object holder;
        Guid guidViewHost = DefGuidList.guidIWpfTextViewHost;
        userData.GetData(ref guidViewHost, out holder);
        viewHost = (IWpfTextViewHost)holder;
        Connector.Execute(viewHost);
    }
    ```

6. Addaddornmenthandler yöntemini AddAdornment oluşturucusunda AddAdornment komutu için işleyici olarak ayarlayın.

    ```csharp
    private AddAdornment(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));

        var menuCommandID = new CommandID(CommandSet, CommandId);
        var menuItem = new MenuCommand(this.AddAdornmentHandler, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

## <a name="build-and-test-the-code"></a>Kodu derleyin ve test edin

1. Çözümü oluşturun ve hata ayıklamayı başlatın. Deneysel örnek görünmelidir.

2. Bir metin dosyası oluşturun. Biraz metin yazın ve ardından seçin.

3. **Araçlar** menüsünde, **kenarlığı Ekle öğesini çağır**' a tıklayın. Bir balon, metin penceresinin sağ tarafında görüntülenmelidir ve aşağıdaki metne benzer bir metin içermelidir.

     Adınız

     On puan...

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: bir içerik türünü bir dosya adı uzantısına bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
