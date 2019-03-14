---
uid: web-forms/overview/ajax-control-toolkit/dynamicpopulate/using-dynamicpopulate-with-a-user-control-and-javascript-vb
title: Kullanıcı denetimi ve JavaScript (VB) ile dynamicpopulate kullanma | Microsoft Docs
author: wenz
description: ASP.NET AJAX Denetim Araç Seti DynamicPopulate denetimi web hizmetini (veya sayfa yöntemi) çağırır ve t hedef denetime sonuç değerini doldurur...
ms.author: riande
ms.date: 06/02/2008
ms.assetid: 778b9009-76f2-4665-940e-afc0e35bc917
msc.legacyurl: /web-forms/overview/ajax-control-toolkit/dynamicpopulate/using-dynamicpopulate-with-a-user-control-and-javascript-vb
msc.type: authoredcontent
ms.openlocfilehash: a275eed17552d26b63f98762c6c870bd53dd455d
ms.sourcegitcommit: 24b1f6decbb17bb22a45166e5fdb0845c65af498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57069765"
---
<a name="using-dynamicpopulate-with-a-user-control-and-javascript-vb"></a><span data-ttu-id="c0b87-103">Kullanıcı Denetimi ve JavaScript ile DynamicPopulate Kullanma (VB)</span><span class="sxs-lookup"><span data-stu-id="c0b87-103">Using DynamicPopulate with a User Control And JavaScript (VB)</span></span>
====================
<span data-ttu-id="c0b87-104">tarafından [Christian Wenz](https://github.com/wenz)</span><span class="sxs-lookup"><span data-stu-id="c0b87-104">by [Christian Wenz](https://github.com/wenz)</span></span>

<span data-ttu-id="c0b87-105">[Kodu indir](http://download.microsoft.com/download/d/8/f/d8f2f6f9-1b7c-46ad-9252-e1fc81bdea3e/dynamicpopulate2.vb.zip) veya [PDF olarak indirin](http://download.microsoft.com/download/b/6/a/b6ae89ee-df69-4c87-9bfb-ad1eb2b23373/dynamicpopulate2VB.pdf)</span><span class="sxs-lookup"><span data-stu-id="c0b87-105">[Download Code](http://download.microsoft.com/download/d/8/f/d8f2f6f9-1b7c-46ad-9252-e1fc81bdea3e/dynamicpopulate2.vb.zip) or [Download PDF](http://download.microsoft.com/download/b/6/a/b6ae89ee-df69-4c87-9bfb-ad1eb2b23373/dynamicpopulate2VB.pdf)</span></span>

> <span data-ttu-id="c0b87-106">ASP.NET AJAX Denetim Araç Seti DynamicPopulate denetimi, bir web hizmeti (veya sayfa yöntemi) çağırır ve bir hedef denetimine sayfasında, bir sayfa yenileme olmadan sonuç değerini doldurur.</span><span class="sxs-lookup"><span data-stu-id="c0b87-106">The DynamicPopulate control in the ASP.NET AJAX Control Toolkit calls a web service (or page method) and fills the resulting value into a target control on the page, without a page refresh.</span></span> <span data-ttu-id="c0b87-107">Özel istemci tarafı JavaScript kodu kullanarak popülasyon tetiklemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="c0b87-107">It is also possible to trigger the population using custom client-side JavaScript code.</span></span> <span data-ttu-id="c0b87-108">Ancak özel dikkat genişletici bir kullanıcı denetiminde bulunduğunda alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c0b87-108">However special care has to be taken when the extender resides in a user control.</span></span>


## <a name="overview"></a><span data-ttu-id="c0b87-109">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c0b87-109">Overview</span></span>

<span data-ttu-id="c0b87-110">`DynamicPopulate` ASP.NET AJAX Denetim Araç Seti denetiminde bir web hizmeti (veya sayfa yöntemi) çağırır ve bir hedef denetimine sayfasında, bir sayfa yenileme olmadan sonuç değerini doldurur.</span><span class="sxs-lookup"><span data-stu-id="c0b87-110">The `DynamicPopulate` control in the ASP.NET AJAX Control Toolkit calls a web service (or page method) and fills the resulting value into a target control on the page, without a page refresh.</span></span> <span data-ttu-id="c0b87-111">Özel istemci tarafı JavaScript kodu kullanarak popülasyon tetiklemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="c0b87-111">It is also possible to trigger the population using custom client-side JavaScript code.</span></span> <span data-ttu-id="c0b87-112">Ancak özel dikkat genişletici bir kullanıcı denetiminde bulunduğunda alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c0b87-112">However special care has to be taken when the extender resides in a user control.</span></span>

## <a name="steps"></a><span data-ttu-id="c0b87-113">Adımlar</span><span class="sxs-lookup"><span data-stu-id="c0b87-113">Steps</span></span>

<span data-ttu-id="c0b87-114">İlk olarak bir ASP.NET Web hizmeti çağrılacak yöntemin uygulayan ihtiyacınız `DynamicPopulateExtender` denetimi.</span><span class="sxs-lookup"><span data-stu-id="c0b87-114">First of all, you need an ASP.NET Web Service which implements the method to be called by the `DynamicPopulateExtender` control.</span></span> <span data-ttu-id="c0b87-115">Web hizmeti yöntemini uygulayan `getDate()` adlı dize türündeki bir bağımsız değişken bekliyor `contextKey`, bu yana `DynamicPopulate` denetim bağlam bilgilerini tek bir parçası olan her web hizmeti çağrısı gönderir.</span><span class="sxs-lookup"><span data-stu-id="c0b87-115">The web service implements the method `getDate()` that expects one argument of type string, called `contextKey`, since the `DynamicPopulate` control sends one piece of context information with each web service call.</span></span> <span data-ttu-id="c0b87-116">Kodu (dosyaları `DynamicPopulate.vb.asmx`) geçerli tarihi kullanılan üç biçimlerden birini alır:</span><span class="sxs-lookup"><span data-stu-id="c0b87-116">Here is the code (files `DynamicPopulate.vb.asmx`) which retrieves the current date in one of three formats:</span></span>

[!code-aspx[Main](using-dynamicpopulate-with-a-user-control-and-javascript-vb/samples/sample1.aspx)]

<span data-ttu-id="c0b87-117">Sonraki adımda, yeni bir kullanıcı denetimi oluşturma (`.ascx` dosyası), ilk satırında, aşağıdaki bildirimi tarafından başlar:</span><span class="sxs-lookup"><span data-stu-id="c0b87-117">In the next step, create a new user control (`.ascx` file), denoted by the following declaration in its first line:</span></span>

[!code-aspx[Main](using-dynamicpopulate-with-a-user-control-and-javascript-vb/samples/sample2.aspx)]

<span data-ttu-id="c0b87-118">A &lt; `label` &gt; öğesi, sunucudan gelen verileri görüntülemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c0b87-118">A &lt;`label`&gt; element will be used to display the data coming from the server.</span></span>

[!code-aspx[Main](using-dynamicpopulate-with-a-user-control-and-javascript-vb/samples/sample3.aspx)]

<span data-ttu-id="c0b87-119">Ayrıca kullanıcı denetimi dosyasında kullanacağız üç radyo düğmeleri, web hizmeti tarafından desteklenen üç olası tarih biçimlerinden birini temsil eden her biri.</span><span class="sxs-lookup"><span data-stu-id="c0b87-119">Also in the user control file, we will use three radio buttons, each one representing one of the three possible date formats supported by the web service.</span></span> <span data-ttu-id="c0b87-120">Kullanıcı için bir radyo düğmeleri tıkladığında tarayıcı, şuna benzer bir JavaScript kodu yürütür:</span><span class="sxs-lookup"><span data-stu-id="c0b87-120">When the user clicks on one of the radio buttons, the browser will execute JavaScript code which looks like this:</span></span>

[!code-powershell[Main](using-dynamicpopulate-with-a-user-control-and-javascript-vb/samples/sample4.ps1)]

<span data-ttu-id="c0b87-121">Bu kod erişen `DynamicPopulateExtender` (garip kimliği hakkında endişe duymamanızı henüz, bunu daha sonra ele alınacak) ve dinamik nüfus verileri tetikler.</span><span class="sxs-lookup"><span data-stu-id="c0b87-121">This code accesses the `DynamicPopulateExtender` (do not worry about the strange ID yet, this will be covered later on) and triggers the dynamic population with data.</span></span> <span data-ttu-id="c0b87-122">Geçerli bir radyo düğmesi bağlamında `this.value` olan değerine başvuran `format1`, `format2` veya `format3` tam olarak hangi web yöntemini bekliyor.</span><span class="sxs-lookup"><span data-stu-id="c0b87-122">In the context of the current radio button, `this.value` refers to its value which is `format1`, `format2` or `format3` exactly what the web method expects.</span></span>

<span data-ttu-id="c0b87-123">Kullanıcı denetiminde henüz eksik gereken tek şey `DynamicPopulateExtender` radyo düğmeleri web hizmetine bağlayan denetimi.</span><span class="sxs-lookup"><span data-stu-id="c0b87-123">The only thing missing in the user control yet is the `DynamicPopulateExtender` control which links the radio buttons to the web service.</span></span>

[!code-aspx[Main](using-dynamicpopulate-with-a-user-control-and-javascript-vb/samples/sample5.aspx)]

<span data-ttu-id="c0b87-124">Denetimde kullanılan garip kimliği yeniden fark edebilir: `mcd1$myDate` yerine `myDate`.</span><span class="sxs-lookup"><span data-stu-id="c0b87-124">Again you may note the strange ID used in the control: `mcd1$myDate` instead of `myDate`.</span></span> <span data-ttu-id="c0b87-125">Daha önce kullanılan JavaScript kodu `mcd1_dpe1` erişimi `DynamicPopulateExtender` yerine `dpe1`. Bu adlandırma stratejisi kullanılırken özel bir gereksinim olan `DynamicPopulateExtender` içinde bir kullanıcı denetimi.</span><span class="sxs-lookup"><span data-stu-id="c0b87-125">Previously, the JavaScript code used `mcd1_dpe1` to access the `DynamicPopulateExtender` instead of `dpe1`.This naming strategy is a special requirement when using `DynamicPopulateExtender` within a user control.</span></span> <span data-ttu-id="c0b87-126">Ayrıca, tüm çalışması için belirli bir şekilde kullanıcı öne katıştırmak vardır.</span><span class="sxs-lookup"><span data-stu-id="c0b87-126">Furthermore, you have to embed the user contol in a specific way to make it all work.</span></span> <span data-ttu-id="c0b87-127">Yeni bir ASP.NET sayfası oluşturmak ve bir etiket öneki yalnızca uyguladıysanız kullanıcı denetimi kaydedin:</span><span class="sxs-lookup"><span data-stu-id="c0b87-127">Create a new ASP.NET page and register a tag prefix for the user control you have just implemented:</span></span>

[!code-aspx[Main](using-dynamicpopulate-with-a-user-control-and-javascript-vb/samples/sample6.aspx)]

<span data-ttu-id="c0b87-128">Ardından, ASP.NET AJAX dahil `ScriptManager` yeni sayfada denetimi:</span><span class="sxs-lookup"><span data-stu-id="c0b87-128">Then, include the ASP.NET AJAX `ScriptManager` control on the new page:</span></span>

[!code-aspx[Main](using-dynamicpopulate-with-a-user-control-and-javascript-vb/samples/sample7.aspx)]

<span data-ttu-id="c0b87-129">Son olarak, kullanıcı denetimi sayfasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c0b87-129">Finally, add the user control to the page.</span></span> <span data-ttu-id="c0b87-130">Yalnızca ayarlamak zorunda kendi `ID` özniteliği (ve `runat="server"`, Elbette), ancak belirli bir adına ayarlamak de: `mcd1` olduğundan bu kullanıcı denetimi içinde JavaScript kullanarak erişmek için kullanılan önek.</span><span class="sxs-lookup"><span data-stu-id="c0b87-130">You only have to set its `ID` attribute (and `runat="server"`, of course), but you also have to set it to a specific name: `mcd1` since this is the prefix used within the user control to access it using JavaScript.</span></span>

[!code-aspx[Main](using-dynamicpopulate-with-a-user-control-and-javascript-vb/samples/sample8.aspx)]

<span data-ttu-id="c0b87-131">Ve İşte bu kadar!</span><span class="sxs-lookup"><span data-stu-id="c0b87-131">And that's it!</span></span> <span data-ttu-id="c0b87-132">Sayfa beklendiği gibi davranır: Radyo düğmelerinden birini kullanıcı tıkladığında, araç setindeki denetim web hizmetini çağıran ve istenen biçiminde geçerli tarihi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c0b87-132">The page behaves as expected: A user clicks on one of the radio buttons, the control in the Toolkit calls the web service and displays the current date in the desired format.</span></span>


<span data-ttu-id="c0b87-133">[![Radyo düğmelerinin kullanıcı denetiminde yer alır.](using-dynamicpopulate-with-a-user-control-and-javascript-vb/_static/image2.png)](using-dynamicpopulate-with-a-user-control-and-javascript-vb/_static/image1.png)</span><span class="sxs-lookup"><span data-stu-id="c0b87-133">[![The radio buttons reside in a user control](using-dynamicpopulate-with-a-user-control-and-javascript-vb/_static/image2.png)](using-dynamicpopulate-with-a-user-control-and-javascript-vb/_static/image1.png)</span></span>

<span data-ttu-id="c0b87-134">Radyo düğmelerinin kullanıcı denetiminde bulunan ([tam boyutlu görüntüyü görmek için tıklatın](using-dynamicpopulate-with-a-user-control-and-javascript-vb/_static/image3.png))</span><span class="sxs-lookup"><span data-stu-id="c0b87-134">The radio buttons reside in a user control ([Click to view full-size image](using-dynamicpopulate-with-a-user-control-and-javascript-vb/_static/image3.png))</span></span>

> [!div class="step-by-step"]
> [<span data-ttu-id="c0b87-135">Önceki</span><span class="sxs-lookup"><span data-stu-id="c0b87-135">Previous</span></span>](dynamically-populating-a-control-using-javascript-code-vb.md)