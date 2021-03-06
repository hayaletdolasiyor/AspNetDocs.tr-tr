---
uid: web-forms/overview/ajax-control-toolkit/animation/animation-depending-on-a-condition-vb
title: Bir koşula bağlı animasyon (VB) | Microsoft Docs
author: wenz
description: ASP.NET AJAX denetim araç setinde animasyon denetimi yalnızca bir denetim değildir ancak bir denetime animasyon eklemek için bir bütün çerçevedir. Animasyonun olup olmadığı...
ms.author: riande
ms.date: 06/02/2008
ms.assetid: 1b87d8d6-b3f7-4126-b51c-d41442fbf947
msc.legacyurl: /web-forms/overview/ajax-control-toolkit/animation/animation-depending-on-a-condition-vb
msc.type: authoredcontent
ms.openlocfilehash: 583ebdbf109beb74b9a425020477183067bbb79a
ms.sourcegitcommit: e7e91932a6e91a63e2e46417626f39d6b244a3ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78614347"
---
# <a name="animation-depending-on-a-condition-vb"></a>Bir Koşula Bağlı Animasyon (VB)

[Hristia WENZ](https://github.com/wenz) tarafından

[Kodu indirin](https://download.microsoft.com/download/f/9/a/f9a26acd-8df4-4484-8a18-199e4598f411/Animation4.vb.zip) veya [PDF 'yi indirin](https://download.microsoft.com/download/6/7/1/6718d452-ff89-4d3f-a90e-c74ec2d636a3/animation4VB.pdf)

> ASP.NET AJAX denetim araç setinde animasyon denetimi yalnızca bir denetim değildir ancak bir denetime animasyon eklemek için bir bütün çerçevedir. Bir animasyonun çalıştırılıp çalıştırılmayacağı veya yüklenmediğini, bazı JavaScript kodu biçimindeki bir koşula de bağlı olabilir.

## <a name="overview"></a>Genel bakış

ASP.NET AJAX denetim araç setinde animasyon denetimi yalnızca bir denetim değildir ancak bir denetime animasyon eklemek için bir bütün çerçevedir. Bir animasyonun çalıştırılıp çalıştırılmayacağı veya yüklenmediğini, bazı JavaScript kodu biçimindeki bir koşula de bağlı olabilir.

## <a name="steps"></a>Adımlar

Birincisi, sayfaya `ScriptManager` ekleyin; ardından, ASP.NET AJAX kitaplığı yüklenir ve Denetim araç setini kullanmayı mümkün kılar:

[!code-aspx[Main](animation-depending-on-a-condition-vb/samples/sample1.aspx)]

Animasyon, şunun gibi görünen bir metin paneline uygulanır:

[!code-aspx[Main](animation-depending-on-a-condition-vb/samples/sample2.aspx)]

Panelin ilişkili CSS sınıfında, iyi bir arka plan rengi tanımlayın ve panel için sabit bir genişlik ayarlayın:

[!code-css[Main](animation-depending-on-a-condition-vb/samples/sample3.css)]

Daha sonra, bir `ID`, `TargetControlID` özniteliği ve obligatory sağlayarak sayfaya `AnimationExtender` ekleyin `runat="server":`

[!code-aspx[Main](animation-depending-on-a-condition-vb/samples/sample4.aspx)]

`<Animations>` düğümü içinde, sayfa tam olarak yüklendikten sonra animasyonları çalıştırmak için `<OnLoad>` kullanın. `<Condition>` öğesi, normal animasyonlardan biri yerine yürütmeye gelir. `ConditionScript` özniteliğinin değeri olarak belirtilen JavaScript kodu çalışma zamanında yürütülür. True olarak değerlendirilirse animasyon yürütülür, aksi takdirde değildir. Aşağıdaki biçimlendirme, her biri rastgele bir durum olan %50 ' de yürütülen iki animasyon sağlar. `<OnLoad>`içinde yalnızca bir animasyon olabileceğinden, iki `<Condition>` animasyonları `<Sequence>` öğesi kullanılarak birlikte birleştirilir:

[!code-aspx[Main](animation-depending-on-a-condition-vb/samples/sample5.aspx)]

`ConditionScript` özniteliğinde küçüktür işareti (`<`) kaçışın () olması gerektiğini unutmayın. Bu betiği çalıştırdığınızda, herhangi bir animasyon çalıştırması ya da iki ya da her ikisi de olamaz.

[![panel, yeniden boyutlandırmadan soluklaşmakta, bu nedenle ikinci animasyon çalışır, ilki](animation-depending-on-a-condition-vb/_static/image2.png)](animation-depending-on-a-condition-vb/_static/image1.png)

Panel, yeniden boyutlandırmadan soluklaşmakta, bu nedenle ikinci animasyon çalışır, ilki değil ([tam boyutlu görüntüyü görüntülemek Için tıklatın](animation-depending-on-a-condition-vb/_static/image3.png))

> [!div class="step-by-step"]
> [Önceki](executing-several-animations-after-each-other-vb.md)
> [İleri](picking-one-animation-out-of-a-list-vb.md)
