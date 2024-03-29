---
title: 'Öğretici: basit C# bir konsol uygulaması oluşturma'
description: Visual Studio 'da bir C# konsol uygulamasının nasıl oluşturulduğunu adım adım öğrenin.
ms.custom: seodec18, get-started
ms.date: 03/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 740968740306bed4c2cf52191c4ff661b6247bd0
ms.sourcegitcommit: 697f2ab875fd789685811687387e9e8e471a38c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74830003"
---
# <a name="tutorial-create-a-simple-c-console-app-in-visual-studio"></a>Öğretici: Visual Studio 'da C# basit bir konsol uygulaması oluşturma

İçin C#Bu öğreticide, Visual Studio 'yu kullanarak bir konsol uygulaması oluşturup çalıştırabilir ve bunu yaparken Visual Studio tümleşik geliştirme ORTAMıNıN (IDE) bazı özelliklerini keşfedebilirsiniz.

::: moniker range="vs-2017"

Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz yüklemek için sayfa.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) ücretsiz yüklemek için sayfa.

::: moniker-end

## <a name="create-a-project"></a>Proje oluştur

Başlamak için bir C# uygulama projesi oluşturacağız. Proje türü, ihtiyacınız olan tüm şablon dosyaları ile birlikte gelir, hatta herhangi bir şey eklemeden önce!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

2. Üstteki menü çubuğundan seçin **dosya** > **yeni** > **proje**.
   (Alternatif olarak, **Ctrl**+**SHIFT**+**N**) tuşuna basın.

3. **Yeni proje** iletişim kutusunun sol bölmesinde, öğesini genişletin **C#** ve ardından **.NET Core**' u seçin. Orta bölmede **konsol uygulaması (.NET Core)** öğesini seçin. Ardından dosya ***Hesaplayıcı***adını adlandırın.

   ![Visual Studio IDE 'de yeni proje iletişim kutusundaki konsol uygulaması (.NET Core) proje şablonu](./media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workload-optional"></a>İş yükü ekleme (isteğe bağlı)

**Konsol uygulaması (.NET Core)** proje şablonunu görmüyorsanız, **.NET Core platformlar arası geliştirme** iş yükünü ekleyerek buna ulaşabilirsiniz. İşte nasıl.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Seçenek 1: yeni proje iletişim kutusunu kullanma

1. **Yeni proje** iletişim kutusunun sol bölmesindeki **Visual Studio yükleyicisi aç** bağlantısını seçin.

   ![Yeni proje iletişim kutusundan Visual Studio Yükleyicisi Aç bağlantısını seçin](./media/csharp-open-visual-studio-installer-generic-dark.png)

1. Visual Studio Yükleyicisi'ni başlatır. **.NET Core platformlar arası geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

   ![Visual Studio Yükleyicisi .NET Core platformlar arası geliştirme iş yükü](./media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>2\. seçenek: Araçlar menü çubuğunu kullanma

1. **Yeni proje** iletişim kutusunu iptal edin ve üst menü çubuğundan Araçlar **ve Özellikler al**> **Araçlar** ' ı seçin.

1. Visual Studio Yükleyicisi'ni başlatır. **.NET Core platformlar arası geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio 2019 ' i açın.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   ![' Yeni proje oluştur ' penceresini görüntüleyin](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. **Yeni proje oluştur** penceresinde, arama kutusuna *konsol* girin veya yazın. Ardından, dil **C#** listesinden seçin ve ardından platform listesinden **Windows** ' u seçin. 

   Dil ve platform filtrelerini uyguladıktan sonra **konsol uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin.

   ![Konsol uygulaması C# için şablonu seçin (.NET Framework)](./media/vs-2019/csharp-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > **Konsol uygulaması (.NET Core)** şablonunu görmüyorsanız, **Yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın.
   >
   > ![' Yeni proje oluştur ' penceresindeki ' daha fazla araç ve özellik yüklemesi ' ' ne aradığınızı bulma ' iletisi bağlantısı](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Sonra, Visual Studio Yükleyicisi **.NET Core platformlar arası geliştirme** iş yükünü seçin.
   >
   > ![Visual Studio Yükleyicisi .NET Core platformlar arası geliştirme iş yükü](./media/dot-net-core-xplat-dev-workload.png)
   >
   > Bundan sonra Visual Studio Yükleyicisi **Değiştir** düğmesini seçin. İşinizi kaydetmeniz istenebilir; Öyleyse, bunu yapın. Sonra, iş yükünü yüklemek için **devam** ' ı seçin. Ardından, bu "[Proje oluşturma](#create-a-project)" yordamında 2. adıma geri dönün.

1. **Yeni projeyi yapılandırın** penceresinde, **Proje adı** kutusuna *Hesaplayıcı* yazın veya girin. Ardından **Oluştur**' u seçin.

   ![' yeni projenizi yapılandırın ' penceresinde, projenizi ' Hesaplayıcı ' olarak adlandırın](./media/vs-2019/csharp-name-your-calculator-project.png)

   Visual Studio, varsayılan "Merhaba Dünya" kodunu içeren yeni projenizi açar.
   
::: moniker-end

## <a name="create-the-app"></a>Uygulama oluşturma

İlk olarak, içinde C#bazı temel tamsayı matematiğini araştıracağız. Daha sonra, temel bir Hesaplayıcı oluşturmak için kod ekleyeceğiz. Bundan sonra, hataları bulmak ve gidermek için uygulamada hata ayıklaması yapacağız. Son olarak, kodu daha verimli hale getirmek için belirginleştireceğiz.

### <a name="explore-integer-math"></a>Tamsayı matematiğini inceleme

' De C#bazı temel tamsayı matematiği ile başlayalım.

1. Kod Düzenleyicisi 'nde varsayılan "Merhaba Dünya" kodunu silin.

    ![Yeni Hesaplayıcı uygulamanızdan varsayılan Merhaba Dünya kodunu silme](./media/csharp-console-calculator-deletehelloworld.png)

   Özellikle, `Console.WriteLine("Hello World!");`belirten satırı silin.

1. Onun yerine, aşağıdaki kodu yazın:

    ```csharp
            int a = 42;
            int b = 119;
            int c = a + b;
            Console.WriteLine(c);
            Console.ReadKey();
    ```

    Bunu yaptığınızda, Visual Studio 'daki IntelliSense özelliğinin girişi otomatik tamamlama seçeneğini sunduğunu unutmayın.

    ![Visual Studio IDE 'de IntelliSense otomatik tamamlama özelliğini gösteren tamsayı matematik kodu animasyonu](./media/integer-math-intellisense.gif)

1. Çalışma **Hesaplayıcı** ' ın yanındaki yeşil **Başlat** düğmesini seçerek programınızı derleyip çalıştırın veya **F5**tuşuna basın.

   ![Uygulamayı araç çubuğundan çalıştırmak için hesaplayıcı düğmesini seçin](./media/csharp-console-calculator-button.png)

   42 + 119 toplamını gösteren bir konsol penceresi açılır ve bu da **161**.

    ![Tamsayı matematiğinin sonuçlarını gösteren konsol penceresi](./media/csharp-console-integer-math.png)

1. **(Isteğe bağlı)** Sonucu değiştirmek için işlecini değiştirebilirsiniz. Örneğin, kod `int c = a + b;` satırındaki `+` işlecini çıkarma için `-`, çarpma için `*` veya bölme için `/` değiştirebilirsiniz. Ardından, programı çalıştırdığınızda, sonuç de değişir.

1. Konsol penceresini kapatın.

### <a name="add-code-to-create-a-calculator"></a>Hesaplayıcı oluşturmak için kod ekleme

Projenize daha karmaşık bir hesap makinesi kodu kümesi ekleyerek devam edelim.

1. Kod düzenleyicisinde gördüğünüz tüm kodu silin.

1. Aşağıdaki yeni kodu kod düzenleyicisine girin veya yapıştırın:

    ```csharp
    using System;

    namespace Calculator
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Declare variables and then initialize to zero.
                int num1 = 0; int num2 = 0;

                // Display title as the C# console calculator app.
                Console.WriteLine("Console Calculator in C#\r");
                Console.WriteLine("------------------------\n");

                // Ask the user to type the first number.
                Console.WriteLine("Type a number, and then press Enter");
                num1 = Convert.ToInt32(Console.ReadLine());

                // Ask the user to type the second number.
                Console.WriteLine("Type another number, and then press Enter");
                num2 = Convert.ToInt32(Console.ReadLine());

                // Ask the user to choose an option.
                Console.WriteLine("Choose an option from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                // Use a switch statement to do the math.
                switch (Console.ReadLine())
                {
                    case "a":
                        Console.WriteLine($"Your result: {num1} + {num2} = " + (num1 + num2));
                        break;
                    case "s":
                        Console.WriteLine($"Your result: {num1} - {num2} = " + (num1 - num2));
                        break;
                    case "m":
                        Console.WriteLine($"Your result: {num1} * {num2} = " + (num1 * num2));
                        break;
                    case "d":
                        Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                        break;
                }
                // Wait for the user to respond before closing.
                Console.Write("Press any key to close the Calculator console app...");
                Console.ReadKey();
            }
        }
    }
    ```

1. Programınızı çalıştırmak için **Hesaplayıcı** ' ı seçin veya **F5**tuşuna basın.

   ![Uygulamayı araç çubuğundan çalıştırmak için hesaplayıcı düğmesini seçin](./media/csharp-console-calculator-button.png)

   Bir konsol penceresi açılır.

1. Konsol penceresinde uygulamanızı görüntüleyin ve sonra **42** ve **119**sayılarını eklemek için istemleri izleyin.

   Uygulamanız aşağıdaki ekran görüntüsüne benzer görünmelidir:

    ![Hesap makinesi uygulamasını gösteren konsol penceresi ve hangi eylemlerin alınacağı hakkında komut istemleri içerir](./media/csharp-console-calculator.png)

### <a name="add-functionality-to-the-calculator"></a>Hesap makinesine işlevsellik ekleme

Daha fazla işlevsellik eklemek için kodu ince ayar.

### <a name="add-decimals"></a>Ondalık sayı Ekle

Hesaplayıcı uygulaması şu anda kabul ediyor ve tüm sayıları döndürüyor. Ancak, ondalıkla izin veren kodu eklediğimiz takdirde daha kesin olacaktır.

Aşağıdaki ekran görüntüsünde olduğu gibi, uygulamayı çalıştırırsanız ve 42 sayısını 119 olarak bölebiliyorsanız, sonucu 0 (sıfır) olur ve bu da tam değildir.

![Sonuç olarak ondalık sayı döndürmeyen Hesaplayıcı uygulamasını gösteren konsol penceresi](./media/csharp-console-calculator-nodecimal.png)

Onlukları işleyecek şekilde kodu düzeldelim.

1. **Bul ve Değiştir** denetimini açmak için **CTRL** + **F** tuşlarına basın.

1. `int` değişkenin her örneğini `float`olacak şekilde değiştirin.

   **Bul ve Değiştir** denetiminde **eşleşme büyük/küçük harf** (**alt**+**C**) ve **tüm kelimeyi** (**alt**+**W**) ile eşleştiğinden emin olun.

    ![Int değişkeninin float olarak nasıl değiştirileceğini gösteren bul ve Değiştir denetiminin animasyonu](./media/find-replace-control-animation.gif)

1. Hesaplayıcı uygulamanızı yeniden çalıştırın ve **42** sayısını **119**sayısına bölün.

   Uygulamanın artık sıfır yerine ondalık sayı döndürdüğünden emin olun.

    ![Artık sonuç olarak ondalık sayı döndüren Hesaplayıcı uygulamasını gösteren konsol penceresi](./media/csharp-console-calculator-decimal.png)

Ancak, uygulama yalnızca bir ondalık sonuç üretir. Uygulamanın Onlukları da hesaplayabilmesi için daha fazla sayıda kod verelim.

1. `float` değişkeninin her bir örneğini `double`olarak değiştirmek ve `Convert.ToInt32` yönteminin her örneğini `Convert.ToDouble`olarak değiştirmek için **Bul ve Değiştir** denetimini (**CTRL** + **F**) kullanın.

1. Hesaplayıcı uygulamanızı çalıştırın ve **42,5** sayısını **119,75**sayısına bölün.

   Uygulamanın artık ondalık değerleri kabul ettiğini ve sonuç olarak daha uzun bir ondalık sayı döndürdüğünden emin olun.

    ![Artık ondalık sayıları kabul eden ve sonuç olarak daha uzun bir ondalık sayı döndüren Hesaplayıcı uygulamasını gösteren konsol penceresi](./media/csharp-console-calculator-usedecimals.png)

    ( [Kodu gözden geçirme](#revise-the-code) bölümünde ondalık basamak sayısını düzeltireceğiz.)

## <a name="debug-the-app"></a>Uygulamada hata ayıklama

Temel Hesaplayıcı uygulamamız geliştirdik, ancak kullanıcı giriş hataları gibi özel durumları işlemek için henüz başarısız oldu.

Örneğin, bir sayıyı sıfıra bölmeye çalışırsanız veya uygulama sayısal bir karakter (veya tersi) beklerken bir Alfa karakteri girerseniz, uygulama çalışmayı durduruyor ve bir hata döndürür.

Birkaç ortak kullanıcı girişi hatasını gözden geçirelim, bunları hata ayıklayıcıda bulalım ve kodda çözeceğiz.

>[!TIP]
>Hata ayıklayıcı ve nasıl çalıştığı hakkında daha fazla bilgi için [Visual Studio hata ayıklayıcısı sayfasına ilk göz](../../debugger/debugger-feature-tour.md) atın.

### <a name="fix-the-divide-by-zero-error"></a>"Sıfıra bölme" hatasını çözme

Bir sayıyı sıfıra bölmeye çalıştığınızda konsol uygulaması donuyor. Daha sonra Visual Studio, kod düzenleyicisinde neyin yanlış olduğunu gösterir.

   ![Visual Studio kod Düzenleyicisi, sıfıra bölme hatasını gösterir](./media/csharp-console-calculator-dividebyzero-error.png)

Bu hatayı işlemek için kodu değiştirelim.

1. `case "d":` ile doğrudan görüntülenen kodu ve `// Wait for the user to respond before closing`belirten açıklamayı silin.

1. Aşağıdaki kodla değiştirin:

   ```csharp
            // Ask the user to enter a non-zero divisor until they do so.
                while (num2 == 0)
                {
                    Console.WriteLine("Enter a non-zero divisor: ");
                    num2 = Convert.ToInt32(Console.ReadLine());
                }
                Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                break;
        }
    ```

   Kodu ekledikten sonra, `switch` ifadesiyle olan bölüm aşağıdaki ekran görüntüsüne benzer şekilde görünmelidir:

   ![Visual Studio kod Düzenleyicisi 'ndeki düzeltilen "anahtar" bölümü](./media/csharp-console-calculator-switch-code.png)

Böylece, herhangi bir sayıyı sıfıra böldüğünüzde, uygulama başka bir sayı ister. Daha da iyisi: sıfır dışında bir sayı sağlamadan önce sorma ' ı durdurmaz.

   ![Visual Studio kod Düzenleyicisi, sıfıra bölme hatasını gösterir](./media/csharp-console-calculator-dividebyzero.png)

### <a name="fix-the-format-error"></a>"Biçim" hatasını çözme

Uygulama sayısal bir karakter beklediği zaman bir Alfa karakteri girerseniz (veya tersi), konsol uygulaması donuyor. Daha sonra Visual Studio, kod düzenleyicisinde neyin yanlış olduğunu gösterir.

   ![Visual Studio kod Düzenleyicisi bir biçim hatası gösterir](./media/csharp-console-calculator-format-error.png)

Bu hatayı onarmak için, daha önce girmiş olduğumuz kodu yeniden düzenlemeniz gerekir.

#### <a name="revise-the-code"></a>Kodu gözden geçirin

Tüm kodu işlemek için `program` sınıfa güventense, uygulamamızı iki sınıfa böleceğiz: `Calculator` ve `Program`.

`Calculator` sınıfı hesaplama işinin toplu işini işleymeyecektir ve `Program` sınıfı kullanıcı arabirimini ve hata yakalama işini işleymeyecektir.

Haydi başlayalım.

1. Aşağıdaki kod bloğundan *sonra* her şeyi sil:

    ```csharp

    using System;

    namespace Calculator
    {

    ```

1. Ardından, yeni bir `Calculator` sınıfını aşağıdaki gibi ekleyin:

    ```csharp
    class Calculator
    {
        public static double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    break;
                case "s":
                    result = num1 - num2;
                    break;
                case "m":
                    result = num1 * num2;
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            return result;
        }
    }

    ```

1. Ardından, aşağıdaki gibi yeni bir `Program` sınıfı ekleyin:

    ```csharp
    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            while (!endApp)
            {
                // Declare variables and set to empty.
                string numInput1 = "";
                string numInput2 = "";
                double result = 0;

                // Ask the user to type the first number.
                Console.Write("Type a number, and then press Enter: ");
                numInput1 = Console.ReadLine();

                double cleanNum1 = 0;
                while (!double.TryParse(numInput1, out cleanNum1))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput1 = Console.ReadLine();
                }

                // Ask the user to type the second number.
                Console.Write("Type another number, and then press Enter: ");
                numInput2 = Console.ReadLine();

                double cleanNum2 = 0;
                while (!double.TryParse(numInput2, out cleanNum2))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput2 = Console.ReadLine();
                }

                // Ask the user to choose an operator.
                Console.WriteLine("Choose an operator from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                string op = Console.ReadLine();

                try
                {
                    result = Calculator.DoOperation(cleanNum1, cleanNum2, op);
                    if (double.IsNaN(result))
                    {
                        Console.WriteLine("This operation will result in a mathematical error.\n");
                    }
                    else Console.WriteLine("Your result: {0:0.##}\n", result);
                }
                catch (Exception e)
                {
                    Console.WriteLine("Oh no! An exception occurred trying to do the math.\n - Details: " + e.Message);
                }

                Console.WriteLine("------------------------\n");

                // Wait for the user to respond before closing.
                Console.Write("Press 'n' and Enter to close the app, or press any other key and Enter to continue: ");
                if (Console.ReadLine() == "n") endApp = true;

                Console.WriteLine("\n"); // Friendly linespacing.
            }
            return;
        }
    }
    ```

1. Programınızı çalıştırmak için **Hesaplayıcı** ' ı seçin veya **F5**tuşuna basın.

1. İstemleri izleyin ve **42** sayısını **119**sayısına bölün. Uygulamanız aşağıdaki ekran görüntüsüne benzer görünmelidir:

    ![Yeniden düzenlenmiş Hesaplayıcı uygulamasını gösteren ve hatalı girişler için hata işlemeye yönelik komut istemlerini içeren konsol penceresi](./media/csharp-console-calculator-refactored.png)

    Konsol uygulamasını kapatmayı seçinceye kadar daha fazla denklem girme seçeneğiniz olduğuna dikkat edin. Ayrıca, sonucun ondalık basamak sayısını da azalttık.

## <a name="close-the-app"></a>Uygulamayı kapat

1. Daha önce yapmadıysanız, hesaplayıcı uygulamasını kapatın.

1. Visual Studio 'da **Çıkış** bölmesini kapatın.

   ![Visual Studio 'da çıkış bölmesini kapatma](./media/csharp-calculator-close-output-pane.png)

1. Visual Studio 'da uygulamanızı kaydetmek için **Ctrl**+**S** tuşlarına basın.

1. Visual Studio’yu kapatın.

## <a name="code-complete"></a>Kod Tamam

Bu öğreticide, hesaplayıcı uygulamasında çok fazla değişiklik yaptık. Uygulama, işlem kaynaklarını daha verimli bir şekilde işler ve çoğu kullanıcı giriş hatasını işler.

Hepsi tek bir yerde olmak üzere kodun tamamı aşağıda verilmiştir:

```csharp

using System;

namespace Calculator
{
    class Calculator
    {
        public static double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    break;
                case "s":
                    result = num1 - num2;
                    break;
                case "m":
                    result = num1 * num2;
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            return result;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            while (!endApp)
            {
                // Declare variables and set to empty.
                string numInput1 = "";
                string numInput2 = "";
                double result = 0;

                // Ask the user to type the first number.
                Console.Write("Type a number, and then press Enter: ");
                numInput1 = Console.ReadLine();

                double cleanNum1 = 0;
                while (!double.TryParse(numInput1, out cleanNum1))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput1 = Console.ReadLine();
                }

                // Ask the user to type the second number.
                Console.Write("Type another number, and then press Enter: ");
                numInput2 = Console.ReadLine();

                double cleanNum2 = 0;
                while (!double.TryParse(numInput2, out cleanNum2))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput2 = Console.ReadLine();
                }

                // Ask the user to choose an operator.
                Console.WriteLine("Choose an operator from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                string op = Console.ReadLine();

                try
                {
                    result = Calculator.DoOperation(cleanNum1, cleanNum2, op);
                    if (double.IsNaN(result))
                    {
                        Console.WriteLine("This operation will result in a mathematical error.\n");
                    }
                    else Console.WriteLine("Your result: {0:0.##}\n", result);
                }
                catch (Exception e)
                {
                    Console.WriteLine("Oh no! An exception occurred trying to do the math.\n - Details: " + e.Message);
                }

                Console.WriteLine("------------------------\n");

                // Wait for the user to respond before closing.
                Console.Write("Press 'n' and Enter to close the app, or press any other key and Enter to continue: ");
                if (Console.ReadLine() == "n") endApp = true;

                Console.WriteLine("\n"); // Friendly linespacing.
            }
            return;
        }
    }
}

```

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticiyi tamamlamak Tebrikler! Daha da fazla bilgi edinmek için aşağıdaki öğreticilerle devam edin.

> [!div class="nextstepaction"]
> [Daha fazla C# öğreticiyle devam edin](/dotnet/csharp/tutorials/)

## <a name="see-also"></a>Ayrıca bkz.

* [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
* [Visual Studio 'da C# kod hata ayıklamayı öğrenin](tutorial-debugger.md)
