---
uid: web-forms/overview/ajax-control-toolkit/animation/animating-in-response-to-user-interaction-vb
title: Kullanıcı etkileşimine yanıt olarak animasyon ekleme (VB) | Microsoft Docs
author: wenz
description: ASP.NET AJAX denetim araç setinde animasyon denetimi yalnızca bir denetim değildir ancak bir denetime animasyon eklemek için bir bütün çerçevedir. Animasyonlar yıldız alabilir...
ms.author: riande
ms.date: 06/02/2008
ms.assetid: c8204c05-ec27-40fe-933d-88e4e727a482
msc.legacyurl: /web-forms/overview/ajax-control-toolkit/animation/animating-in-response-to-user-interaction-vb
msc.type: authoredcontent
ms.openlocfilehash: 629d79505cebd49c2f05333bfbf78166f80fc6cb
ms.sourcegitcommit: e7e91932a6e91a63e2e46417626f39d6b244a3ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78614403"
---
# <a name="animating-in-response-to-user-interaction-vb"></a>Kullanıcı Etkileşimine Karşılık Olarak Animasyon Ekleme (VB)

[Hristia WENZ](https://github.com/wenz) tarafından

[Kodu indirin](https://download.microsoft.com/download/f/9/a/f9a26acd-8df4-4484-8a18-199e4598f411/Animation6.vb.zip) veya [PDF 'yi indirin](https://download.microsoft.com/download/6/7/1/6718d452-ff89-4d3f-a90e-c74ec2d636a3/animation6VB.pdf)

> ASP.NET AJAX denetim araç setinde animasyon denetimi yalnızca bir denetim değildir ancak bir denetime animasyon eklemek için bir bütün çerçevedir. Animasyonlar otomatik olarak başlayabilir veya Kullanıcı etkileşimi tarafından, ör. fareyle tıklanarak tetiklenebilir.

## <a name="overview"></a>Genel bakış

ASP.NET AJAX denetim araç setinde animasyon denetimi yalnızca bir denetim değildir ancak bir denetime animasyon eklemek için bir bütün çerçevedir. Animasyonlar otomatik olarak başlayabilir veya Kullanıcı etkileşimi tarafından, ör. fareyle tıklanarak tetiklenebilir.

## <a name="steps"></a>Adımlar

Birincisi, sayfaya `ScriptManager` ekleyin; ardından, ASP.NET AJAX kitaplığı yüklenir ve Denetim araç setini kullanmayı mümkün kılar:

[!code-aspx[Main](animating-in-response-to-user-interaction-vb/samples/sample1.aspx)]

Animasyon, şunun gibi görünen bir metin paneline uygulanır:

[!code-aspx[Main](animating-in-response-to-user-interaction-vb/samples/sample2.aspx)]

Panelin ilişkili CSS sınıfında, iyi bir arka plan rengi tanımlayın ve panel için sabit bir genişlik ayarlayın:

[!code-css[Main](animating-in-response-to-user-interaction-vb/samples/sample3.css)]

Daha sonra, bir `ID`, `TargetControlID` özniteliği ve obligatory `runat="server"`sağlayarak sayfaya `AnimationExtender` ekleyin:

[!code-aspx[Main](animating-in-response-to-user-interaction-vb/samples/sample4.aspx)]

`<Animations>` düğümü içinde, animasyonu Kullanıcı etkileşimi aracılığıyla başlatmaya yönelik beş yol vardır (eksik öğe, tüm sayfa tam olarak yüklendikten sonra yürütülür `<OnLoad>`):

- `<OnClick>` (denetime fare tıklaması)
- `<OnHoverOut>` (fare, denetimi bırakır)
- `<OnHoverOver>` (fare bir denetimin üzerine geldiğinde `<OnHoverOut>` animasyonunu durduruyor)
- `<OnMouseOut>` (fare bir denetimi bırakır)
- `<OnMouseOver>` (fare, bir denetimin üzerine geldiğinde `<OnMouseOut>` animasyonunu durdurmaz)

Bu senaryoda `<OnClick>` kullanılır. Kullanıcı panele tıkladığında, yeniden boyutlandırılır ve aynı anda silinir.

[!code-aspx[Main](animating-in-response-to-user-interaction-vb/samples/sample5.aspx)]

[fare tıklaması ![animasyonu başlatır](animating-in-response-to-user-interaction-vb/_static/image2.png)](animating-in-response-to-user-interaction-vb/_static/image1.png)

Fare tıklaması animasyonu başlatır ([tam boyutlu görüntüyü görüntülemek Için tıklatın](animating-in-response-to-user-interaction-vb/_static/image3.png))

> [!div class="step-by-step"]
> [Önceki](picking-one-animation-out-of-a-list-vb.md)
> [İleri](disabling-actions-during-animation-vb.md)
