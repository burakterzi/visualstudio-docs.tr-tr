---
title: Sembol türlerinin sözcük hiyerarşisi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ad782ddb9a88b492d03e2338f17d95fb7bfa4f79
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738666"
---
# <a name="lexical-hierarchy-of-symbol-types"></a>Simge Türlerinin Sözcük Hiyerarşisi
Aşağıdaki tabloda, sözcük temelli hiyerarşide sembol türleri gösterilmektedir.

## <a name="symbol-types"></a>Sembol türleri

|Sembol türü|Açıklama|
|-----------------|-----------------|
|[Ek Açıklama](../../debugger/debug-interface-access/annotation.md)|Program kodunda açıklamalı bir konum belirtir.|
|[Block](../../debugger/debug-interface-access/block.md)|İşlevlerde iç içe kapsamları belirtir.|
|`Compiland`|. Exe dosyasına bağlı bir `compiland` belirtir.|
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|Ek compiland ayrıntılarının yüklenmesi gereken compiland verilerini belirtir ve bu nedenle alınacak çalışma zamanı ek yüküne neden olur.|
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Compiland derlemesi için önemli olan ek ortam değişkenlerini belirtir.|
|[Özel (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|Kullanıcı tanımlı bir simge belirtir.|
|[Veriler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|Bu tür değişkenleri parametreler, yerel değişkenler, genel değişkenler ve sınıf üyeleri olarak belirtir.|
|[Exe](../../debugger/debug-interface-access/exe.md)|Verilerin genel kapsamını belirtir; bir. exe veya. dll dosyasının tamamına karşılık gelir.|
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|Hata ayıklamanın sona erdirmek için tanımlı bir noktaya sahip bir işlevi belirtir.|
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|Hata ayıklamanın başlayacağı tanımlı bir noktaya sahip bir işlevi belirtir.|
|[İşlev (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|Bir işlevi belirtir.|
|[Etiket (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|Program kodundaki bir konumu belirtir.|
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|Yürütülebilir program oluşturulurken görüntülenen bir dış simgeyi belirtir.|
|[Dönüştürücü](../../debugger/debug-interface-access/thunk.md)|Bir `thunk`belirtir.|
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|Bir `namespace`tanımlayıcıyı belirtir.|

> [!NOTE]
> Sembol türüne bağlı olarak ek sembol özellikleri kullanılabilir olabilir. Bu özellikler, tek sembol konularında listelenmiştir.

## <a name="see-also"></a>Ayrıca bkz.
- [Simge Türlerinin Sınıf Hiyerarşisi](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
- [Simgeler ve Simge Etiketleri](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)
- [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)