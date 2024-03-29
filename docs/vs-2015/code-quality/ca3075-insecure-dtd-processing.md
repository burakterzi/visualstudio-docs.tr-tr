---
title: 'CA3075: güvenli olmayan DTD Işleme | Microsoft Docs'
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 65798d66-7a30-4359-b064-61a8660c1eed
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2ce5390ce8d649ab2c57eccde34506d6831b8193
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300970"
---
# <a name="ca3075-insecure-dtd-processing"></a>CA3075: Güvensiz DTD İşleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|Insecuredtdprocessing|
|CheckId|CA3075|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Güvenli olmayan <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> örnekleri kullanırsanız veya dış varlık kaynaklarına başvuru yaparsanız, ayrıştırıcı güvenilmeyen girişi kabul edebilir ve duyarlı bilgileri saldırganlar 'e açığa çıkarabilir.

## <a name="rule-description"></a>Kural Tanımı
 Bir [belge türü tanımı (DTD)](https://msdn.microsoft.com/library/aa468547.aspx) , bir XML ayrıştırıcısının, [World Wide Web Konsorsiyumu (W3C) Genişletilebilir Biçimlendirme Dili (XML) 1,0](https://www.w3.org/TR/2008/REC-xml-20081126/)tarafından tanımlanan bir belgenin geçerliliğini belirleyebilmesi için iki yönden biridir. Bu kural, geliştiricilerin [hizmet reddi (DOS)](https://msdn.microsoft.com/library/dfb150f3-d598-4697-a5e6-6779e4f9b600) saldırılarına yol açabilecek olası [bilgi açığa çıkması](https://msdn.microsoft.com/library/4064c89f-afa6-444a-aa7e-807ef072131c) tehditleri hakkında geliştiricilere uyarı vermek için güvenilmeyen verilerin kabul edildiği özellikleri ve örnekleri arar. Bu kural şu durumlarda tetiklenir:

- DtdProcessing, <xref:System.Xml.XmlUrlResolver>kullanarak dış XML varlıklarını çözen <xref:System.Xml.XmlReader> örneğinde etkinleştirilir.

- XML 'deki <xref:System.Xml.XmlNode.InnerXml%2A> özelliği ayarlanır.

- <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> özelliği Parse olarak ayarlandı.

- Güvenilmeyen giriş, <xref:System.Xml.XmlSecureResolver> yerine <xref:System.Xml.XmlResolver> kullanılarak işlenir.

- XmlReader.<xref:System.Xml.XmlReader.Create%2A> Yöntem, güvenli olmayan bir <xref:System.Xml.XmlReaderSettings> örneğiyle veya hiç örnek olmadan çağrıldı.

- <xref:System.Xml.XmlReader>, güvenli olmayan varsayılan ayarlarla veya değerlerle oluşturulur.

  Bu durumların her birinde, sonuç aynıdır: XML 'nin işlendiği makinedeki dosya sistemi veya ağ paylaşımlarından içerik saldırgana sunulacaktır ve bu da bir DoS vektörü olarak kullanılabilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?

- Yol bilgilerinin açığa çıkmasını önlemek için tüm XmlTextReader özel durumlarını doğru bir şekilde yakalayın ve işleyin.

- XmlTextReader 'ın erişebileceği kaynakları kısıtlamak için <xref:System.Xml.XmlSecureResolver> kullanın.

- <xref:System.Xml.XmlResolver> özelliğini **null**olarak ayarlayarak <xref:System.Xml.XmlReader> dış kaynakları açmasına izin vermeyin.

- <xref:System.Data.DataViewManager> <xref:System.Data.DataViewManager.DataViewSettingCollectionString%2A> özelliğinin güvenilen bir kaynaktan atandığından emin olun.

  .NET 3,5 ve öncesi

-  <xref:System.Xml.XmlReaderSettings.ProhibitDtd%2A> özelliğini **true** olarak ayarlayarak güvenilmeyen kaynaklarla UĞRAŞıYORSANıZ DTD işlemesini devre dışı bırakın.

- XmlTextReader sınıfı tam güven devralma talebine sahiptir. Daha fazla bilgi için bkz. [Devralma talepleri](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) .

  .NET 4 ve üzeri

- DtdProcessing özelliğini [yasakla veya Yoksay](https://msdn.microsoft.com/library/system.xml.dtdprocessing.aspx) olarak ayarlayarak güvenilmeyen kaynaklarla uğraşıyorsanız DtdProcessing 'ı etkinleştirmemeye özen gösterin

- Load () yönteminin tüm InnerXml durumlarında bir XmlReader örneği aldığından emin olun.

> [!NOTE]
> Bu kural, bazı geçerli XmlSecureResolver örneklerinde hatalı pozitif sonuçlar bildirebilir. Bu sorunu çözmek için 2016 ' ye kadar çalışıyoruz.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Girişin güvenilen bir kaynaktan geldiğinden emin olmadığınız için, bu uyarıdan bir kuralı engellemez.

## <a name="pseudo-code-examples"></a>Sözde kod örnekleri

### <a name="violation"></a>Edildiği

```csharp
using System.IO;
using System.Xml.Schema;

class TestClass
{
    public XmlSchema Test
    {
        get
        {
            var src = "";
            TextReader tr = new StreamReader(src);
            XmlSchema schema = XmlSchema.Read(tr, null); // warn
            return schema;
        }
    }
}
```

### <a name="solution"></a>Çözüm

```csharp
using System.IO;
using System.Xml;
using System.Xml.Schema;

class TestClass
{
    public XmlSchema Test
    {
        get
        {
            var src = "";
            TextReader tr = new StreamReader(src);
            XmlTextReader reader = new XmlTextReader(tr) { DtdProcessing = DtdProcessing.Prohibit };
            XmlSchema schema = XmlSchema.Read(reader , null);
            return schema;
        }
    }
}
```

### <a name="violation"></a>Edildiği

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public XmlReaderSettings settings = new XmlReaderSettings();
        public void TestMethod(string path)
        {
            var reader = XmlReader.Create(path, settings);  // warn
        }
    }
}
```

### <a name="solution"></a>Çözüm

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public XmlReaderSettings settings = new XmlReaderSettings()
        {
            DtdProcessing = DtdProcessing.Prohibit
        };

        public void TestMethod(string path)
        {
            var reader = XmlReader.Create(path, settings);
        }
    }
}
```

### <a name="violations"></a>Lerinden

```csharp
using System.Xml;

namespace TestNamespace
{
    public class DoNotUseSetInnerXml
    {
        public void TestMethod(string xml)
        {
            XmlDocument doc = new XmlDocument() { XmlResolver = null };
            doc.InnerXml = xml; // warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    public class DoNotUseLoadXml
    {
        public void TestMethod(string xml)
        {
            XmlDocument doc = new XmlDocument(){ XmlResolver = null };
            doc.LoadXml(xml); // warn
        }
    }
}
```

### <a name="solution"></a>Çözüm

```csharp
using System.Xml;

public static void TestMethod(string xml)
{
    XmlDocument doc = new XmlDocument() { XmlResolver = null };
    System.IO.StringReader sreader = new System.IO.StringReader(xml);
    XmlTextReader reader = new XmlTextReader(sreader) { DtdProcessing = DtdProcessing.Prohibit };
    doc.Load(reader);
}
```

### <a name="violation"></a>Edildiği

```csharp
using System.IO;
using System.Xml;
using System.Xml.Serialization;

namespace TestNamespace
{
    public class UseXmlReaderForDeserialize
    {
        public void TestMethod(Stream stream)
        {
            XmlSerializer serializer = new XmlSerializer(typeof(UseXmlReaderForDeserialize));
            serializer.Deserialize(stream); // warn
        }
    }
}
```

### <a name="solution"></a>Çözüm

```csharp
using System.IO;
using System.Xml;
using System.Xml.Serialization;

namespace TestNamespace
{
    public class UseXmlReaderForDeserialize
    {
        public void TestMethod(Stream stream)
        {
            XmlSerializer serializer = new XmlSerializer(typeof(UseXmlReaderForDeserialize));
            XmlTextReader reader = new XmlTextReader(stream) { DtdProcessing = DtdProcessing.Prohibit } ;
            serializer.Deserialize(reader );
        }
    }
}
```

### <a name="violation"></a>Edildiği

```csharp
using System.Xml;
using System.Xml.XPath;

namespace TestNamespace
{
    public class UseXmlReaderForXPathDocument
    {
        public void TestMethod(string path)
        {
            XPathDocument doc = new XPathDocument(path); // warn
        }
    }
}
```

### <a name="solution"></a>Çözüm

```csharp
using System.Xml;
using System.Xml.XPath;

namespace TestNamespace
{
    public class UseXmlReaderForXPathDocument
    {
        public void TestMethod(string path)
        {
            XmlTextReader reader = new XmlTextReader(path) { DtdProcessing = DtdProcessing.Prohibit };
            XPathDocument doc = new XPathDocument(reader);
        }
    }
}
```

### <a name="violation"></a>Edildiği

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        public XmlDocument doc = new XmlDocument() { XmlResolver = new XmlUrlResolver() };
    }
}
```

### <a name="solution"></a>Çözüm

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        public XmlDocument doc = new XmlDocument() { XmlResolver = null }; // or set to a XmlSecureResolver instance
    }
}
```

### <a name="violations"></a>Lerinden

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            XmlReaderSettings settings = new XmlReaderSettings(){ DtdProcessing = DtdProcessing.Parse };
            XmlReader reader = XmlReader.Create(path, settings); // warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod()
        {
            var reader = XmlTextReader.Create(""doc.xml""); //warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            try {
                XmlTextReader reader = new XmlTextReader(path); // warn
            }
            catch { throw ; }
            finally {}
        }
    }
}
```

### <a name="solution"></a>Çözüm

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            XmlReaderSettings settings = new XmlReaderSettings(){ DtdProcessing = DtdProcessing.Prohibit };
            XmlReader reader = XmlReader.Create(path, settings);
        }
    }
}
```
