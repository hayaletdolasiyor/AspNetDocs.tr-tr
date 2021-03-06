---
uid: web-forms/overview/ajax-control-toolkit/animation/picking-one-animation-out-of-a-list-cs
title: Listeden bir animasyon seçme (C#) | Microsoft Docs
author: wenz
description: ASP.NET AJAX denetim araç setinde animasyon denetimi yalnızca bir denetim değildir ancak bir denetime animasyon eklemek için bir bütün çerçevedir. Çerçeve ayrıca allo...
ms.author: riande
ms.date: 06/02/2008
ms.assetid: 06a776fe-7c73-4ca7-8e02-5260a86edc03
msc.legacyurl: /web-forms/overview/ajax-control-toolkit/animation/picking-one-animation-out-of-a-list-cs
msc.type: authoredcontent
ms.openlocfilehash: 2bc203d694792716bbf4f7d7b8d152c589bf99b1
ms.sourcegitcommit: e7e91932a6e91a63e2e46417626f39d6b244a3ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78597974"
---
# <a name="picking-one-animation-out-of-a-list-c"></a>Bir Listeden Animasyon Seçme (C#)

[Hristia WENZ](https://github.com/wenz) tarafından

[Kodu indirin](https://download.microsoft.com/download/f/9/a/f9a26acd-8df4-4484-8a18-199e4598f411/Animation5.cs.zip) veya [PDF 'yi indirin](https://download.microsoft.com/download/6/7/1/6718d452-ff89-4d3f-a90e-c74ec2d636a3/animation5CS.pdf)

> ASP.NET AJAX denetim araç setinde animasyon denetimi yalnızca bir denetim değildir ancak bir denetime animasyon eklemek için bir bütün çerçevedir. Framework Ayrıca programcı 'nin bazı JavaScript kodunun değerlendirmesine bağlı olarak bir animasyon listesinden bir animasyon seçmesine olanak sağlar.

## <a name="overview"></a>Genel bakış

ASP.NET AJAX denetim araç setinde animasyon denetimi yalnızca bir denetim değildir ancak bir denetime animasyon eklemek için bir bütün çerçevedir. Framework Ayrıca programcı 'nin bazı JavaScript kodunun değerlendirmesine bağlı olarak bir animasyon listesinden bir animasyon seçmesine olanak sağlar.

## <a name="steps"></a>Adımlar

Birincisi, sayfaya `ScriptManager` ekleyin; ardından, ASP.NET AJAX kitaplığı yüklenir ve Denetim araç setini kullanmayı mümkün kılar:

[!code-aspx[Main](picking-one-animation-out-of-a-list-cs/samples/sample1.aspx)]

Animasyon, şunun gibi görünen bir metin paneline uygulanır:

[!code-aspx[Main](picking-one-animation-out-of-a-list-cs/samples/sample2.aspx)]

Panelin ilişkili CSS sınıfında, iyi bir arka plan rengi tanımlayın ve panel için sabit bir genişlik ayarlayın:

[!code-css[Main](picking-one-animation-out-of-a-list-cs/samples/sample3.css)]

Daha sonra, bir `ID`, `TargetControlID` özniteliği ve obligatory sağlayarak sayfaya `AnimationExtender` ekleyin `runat="server":`

[!code-aspx[Main](picking-one-animation-out-of-a-list-cs/samples/sample4.aspx)]

`<Animations>` düğümü içinde, sayfa tam olarak yüklendikten sonra animasyonları çalıştırmak için `<OnLoad>` kullanın. `<Case>` öğesi, normal animasyonlardan biri yerine yürütmeye gelir. SelectScript özniteliğinin değeri değerlendirilir; dönüş değeri sayısal olmalıdır. Bu sayıya bağlı olarak, &lt;Case&gt; içindeki alt animasyonlardan biri yürütülür. Örneğin, Selectscrıpt 2 olarak değerlendirilirse, Denetim araç seti &lt;Case&gt; içinde üçüncü animasyonu çalıştırır (sayım 0 ' dan başlar).

Aşağıdaki biçimlendirme üç alt animasyonu tanımlar: genişliği yeniden boyutlandırma, yüksekliği yeniden boyutlandırma ve genişleme. JavaScript kodu (`Math.floor(3 * Math.random())`), üç animasyondan birinin çalışması için 0 ile 2 arasında bir sayı seçer:

[!code-aspx[Main](picking-one-animation-out-of-a-list-cs/samples/sample5.aspx)]

[mümkün olan üç animasyondan birini ![: panel daha geniştir](picking-one-animation-out-of-a-list-cs/_static/image2.png)](picking-one-animation-out-of-a-list-cs/_static/image1.png)

Olası üç animasyondan biri: panel daha geniştir ([tam boyutlu görüntüyü görüntülemek Için tıklatın](picking-one-animation-out-of-a-list-cs/_static/image3.png))

> [!div class="step-by-step"]
> [Önceki](animation-depending-on-a-condition-cs.md)
> [İleri](animating-in-response-to-user-interaction-cs.md)
