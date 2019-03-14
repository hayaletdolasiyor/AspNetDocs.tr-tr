---
uid: web-forms/overview/ajax-control-toolkit/popup/handling-postbacks-from-a-popup-control-with-an-updatepanel-vb
title: UpdatePanel (VB) ile bir açılan denetimden gelen geri göndermeleri işleme | Microsoft Docs
author: wenz
description: AJAX Denetim Araç Seti, PopupControl genişletici herhangi bir denetimi etkinleştirildiğinde, popup tetiklemek için kolay bir yolunu sunar. Özel dikkat edilmelidir...
ms.author: riande
ms.date: 06/02/2008
ms.assetid: ec9db57c-9f68-402a-bf4c-0d63d5f6908e
msc.legacyurl: /web-forms/overview/ajax-control-toolkit/popup/handling-postbacks-from-a-popup-control-with-an-updatepanel-vb
msc.type: authoredcontent
ms.openlocfilehash: e2b4c7c7920cc67daa3c234d397cbf8c7f00bd37
ms.sourcegitcommit: 24b1f6decbb17bb22a45166e5fdb0845c65af498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57066486"
---
<a name="handling-postbacks-from-a-popup-control-with-an-updatepanel-vb"></a><span data-ttu-id="77c37-104">UpdatePanel ile Bir Açılan Denetimden Gelen Geri Göndermeleri İşleme (VB)</span><span class="sxs-lookup"><span data-stu-id="77c37-104">Handling Postbacks from A Popup Control With an UpdatePanel (VB)</span></span>
====================
<span data-ttu-id="77c37-105">tarafından [Christian Wenz](https://github.com/wenz)</span><span class="sxs-lookup"><span data-stu-id="77c37-105">by [Christian Wenz](https://github.com/wenz)</span></span>

<span data-ttu-id="77c37-106">[Kodu indir](http://download.microsoft.com/download/9/3/f/93f8daea-bebd-4821-833b-95205389c7d0/PopupControl2.vb.zip) veya [PDF olarak indirin](http://download.microsoft.com/download/2/d/c/2dc10e34-6983-41d4-9c08-f78f5387d32b/popupcontrol2VB.pdf)</span><span class="sxs-lookup"><span data-stu-id="77c37-106">[Download Code](http://download.microsoft.com/download/9/3/f/93f8daea-bebd-4821-833b-95205389c7d0/PopupControl2.vb.zip) or [Download PDF](http://download.microsoft.com/download/2/d/c/2dc10e34-6983-41d4-9c08-f78f5387d32b/popupcontrol2VB.pdf)</span></span>

> <span data-ttu-id="77c37-107">AJAX Denetim Araç Seti, PopupControl genişletici herhangi bir denetimi etkinleştirildiğinde, popup tetiklemek için kolay bir yolunu sunar.</span><span class="sxs-lookup"><span data-stu-id="77c37-107">The PopupControl extender in the AJAX Control Toolkit offers an easy way to trigger a popup when any other control is activated.</span></span> <span data-ttu-id="77c37-108">Böyle bir açılan pencere içinde bir geri gönderme gerçekleştiğinde yapılacak önemi sahiptir.</span><span class="sxs-lookup"><span data-stu-id="77c37-108">Special care has to be taken when a postback occurs within such a popup.</span></span>


## <a name="overview"></a><span data-ttu-id="77c37-109">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="77c37-109">Overview</span></span>

<span data-ttu-id="77c37-110">AJAX Denetim Araç Seti, PopupControl genişletici herhangi bir denetimi etkinleştirildiğinde, popup tetiklemek için kolay bir yolunu sunar.</span><span class="sxs-lookup"><span data-stu-id="77c37-110">The PopupControl extender in the AJAX Control Toolkit offers an easy way to trigger a popup when any other control is activated.</span></span> <span data-ttu-id="77c37-111">Böyle bir açılan pencere içinde bir geri gönderme gerçekleştiğinde yapılacak önemi sahiptir.</span><span class="sxs-lookup"><span data-stu-id="77c37-111">Special care has to be taken when a postback occurs within such a popup.</span></span>

## <a name="steps"></a><span data-ttu-id="77c37-112">Adımlar</span><span class="sxs-lookup"><span data-stu-id="77c37-112">Steps</span></span>

<span data-ttu-id="77c37-113">Kullanırken bir `PopupControl` bir geri gönderme bir `UpdatePanel` göndermenin neden sayfa yenileme engelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="77c37-113">When using a `PopupControl` with a postback, an `UpdatePanel` can prevent the page refresh caused by the postback.</span></span> <span data-ttu-id="77c37-114">Aşağıdaki biçimlendirmede birkaç önemli öğe tanımlar:</span><span class="sxs-lookup"><span data-stu-id="77c37-114">The following markup defines a couple of important elements:</span></span>

- <span data-ttu-id="77c37-115">A `ScriptManager` ASP.NET AJAX Denetim Araç Seti çalışmasını kontrol</span><span class="sxs-lookup"><span data-stu-id="77c37-115">A `ScriptManager` control so that the ASP.NET AJAX Control Toolkit works</span></span>
- <span data-ttu-id="77c37-116">İki `TextBox` hem popup tetikleyecek denetimleri</span><span class="sxs-lookup"><span data-stu-id="77c37-116">Two `TextBox` controls which will both trigger a popup</span></span>
- <span data-ttu-id="77c37-117">A `Panel` açılan menüsü hizmet verecek denetimi</span><span class="sxs-lookup"><span data-stu-id="77c37-117">A `Panel` control that will serve as the popup</span></span>
- <span data-ttu-id="77c37-118">Panel içinde bir `Calendar` denetimi içine gömüldüğü bir `UpdatePanel` denetimi</span><span class="sxs-lookup"><span data-stu-id="77c37-118">Within the panel, a `Calendar` control is embedded within an `UpdatePanel` control</span></span>
- <span data-ttu-id="77c37-119">İki `PopupControlExtender` metin kutuları paneli atama denetimleri</span><span class="sxs-lookup"><span data-stu-id="77c37-119">Two `PopupControlExtender` controls that assign the panel to the text boxes</span></span>

[!code-aspx[Main](handling-postbacks-from-a-popup-control-with-an-updatepanel-vb/samples/sample1.aspx)]

<span data-ttu-id="77c37-120">Unutmayın `OnSelectionChanged` özniteliği `Calendar` denetim ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="77c37-120">Note that the `OnSelectionChanged` attribute of the `Calendar` control is set.</span></span> <span data-ttu-id="77c37-121">Kullanıcının Takvim içinde bir tarih seçtiğinde, bir geri gönderme oluşmaz ve sunucu tarafı yöntemi `c1_SelectionChanged()` yürütülür.</span><span class="sxs-lookup"><span data-stu-id="77c37-121">So when the user selects a date within the calendar, a postback occurs and the server-side method `c1_SelectionChanged()` is executed.</span></span> <span data-ttu-id="77c37-122">Bu yöntem içinde geçerli tarihi alınır ve TextBox'a geri yazılır.</span><span class="sxs-lookup"><span data-stu-id="77c37-122">Within that method, the current date must be retrieved and written back to the textbox.</span></span>

<span data-ttu-id="77c37-123">Bu sözdizimi aşağıdaki gibidir: İlk olarak bir proxy nesnesi `PopupControlExtender` sayfada oluşturulmuş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="77c37-123">The syntax for that is as follows: First of all, a proxy object for the `PopupControlExtender` on the page must be generated.</span></span> <span data-ttu-id="77c37-124">ASP.NET AJAX Denetim Araç Seti sunar `GetProxyForCurrentPopup()` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="77c37-124">The ASP.NET AJAX Control Toolkit offers the `GetProxyForCurrentPopup()` method.</span></span> <span data-ttu-id="77c37-125">Bu yöntem döndürür nesne destekleyen `Commit()` yöntemi bir değer (yöntem çağrısı tetikleyen denetimi değil!) açılan tetiklenen denetim geri gönderir.</span><span class="sxs-lookup"><span data-stu-id="77c37-125">The object this method returns supports the `Commit()` method which sends a value back to the control that triggered the popup (not the control that triggered the method call!).</span></span> <span data-ttu-id="77c37-126">Aşağıdaki kod, seçilen tarihten bağımsız değişkeni olarak sağlar `Commit()` yöntemi, seçilen tarihten metin kutusuna geri yazmak için kodu neden:</span><span class="sxs-lookup"><span data-stu-id="77c37-126">The following code provides the selected date as the argument for the `Commit()` method, causing the code to write the selected date back to the text box:</span></span>

[!code-aspx[Main](handling-postbacks-from-a-popup-control-with-an-updatepanel-vb/samples/sample2.aspx)]

<span data-ttu-id="77c37-127">Bir takvim tarihi, ilişkili metin kutusuna, seçilen tarihten görünür tıklattığınızda artık bir tarih seçici denetimi oluşturma şu anda birçok Web sitesi üzerinde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="77c37-127">Now whenever you click on a calendar date, the selected date appears in the associated text box, creating a date picker control that can currently be found on many websites.</span></span>


<span data-ttu-id="77c37-128">[![Takvim kullanıcı TextBox'a tıkladığında görünür](handling-postbacks-from-a-popup-control-with-an-updatepanel-vb/_static/image2.png)](handling-postbacks-from-a-popup-control-with-an-updatepanel-vb/_static/image1.png)</span><span class="sxs-lookup"><span data-stu-id="77c37-128">[![The Calendar appears when the user clicks into the textbox](handling-postbacks-from-a-popup-control-with-an-updatepanel-vb/_static/image2.png)](handling-postbacks-from-a-popup-control-with-an-updatepanel-vb/_static/image1.png)</span></span>

<span data-ttu-id="77c37-129">Takvim kullanıcı TextBox'a tıkladığında görünür ([tam boyutlu görüntüyü görmek için tıklatın](handling-postbacks-from-a-popup-control-with-an-updatepanel-vb/_static/image3.png))</span><span class="sxs-lookup"><span data-stu-id="77c37-129">The Calendar appears when the user clicks into the textbox ([Click to view full-size image](handling-postbacks-from-a-popup-control-with-an-updatepanel-vb/_static/image3.png))</span></span>


<span data-ttu-id="77c37-130">[![Bir tarihte tıklayarak metin kutusunda yerleştirir](handling-postbacks-from-a-popup-control-with-an-updatepanel-vb/_static/image5.png)](handling-postbacks-from-a-popup-control-with-an-updatepanel-vb/_static/image4.png)</span><span class="sxs-lookup"><span data-stu-id="77c37-130">[![Clicking on a date puts it in the textbox](handling-postbacks-from-a-popup-control-with-an-updatepanel-vb/_static/image5.png)](handling-postbacks-from-a-popup-control-with-an-updatepanel-vb/_static/image4.png)</span></span>

<span data-ttu-id="77c37-131">Bir tarihte tıklayarak onu koyar metin kutusu içinde ([tam boyutlu görüntüyü görmek için tıklatın](handling-postbacks-from-a-popup-control-with-an-updatepanel-vb/_static/image6.png))</span><span class="sxs-lookup"><span data-stu-id="77c37-131">Clicking on a date puts it in the textbox ([Click to view full-size image](handling-postbacks-from-a-popup-control-with-an-updatepanel-vb/_static/image6.png))</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="77c37-132">[Önceki](using-multiple-popup-controls-vb.md)
> [İleri](handling-postbacks-from-a-popup-control-without-an-updatepanel-vb.md)</span><span class="sxs-lookup"><span data-stu-id="77c37-132">[Previous](using-multiple-popup-controls-vb.md)
[Next](handling-postbacks-from-a-popup-control-without-an-updatepanel-vb.md)</span></span>