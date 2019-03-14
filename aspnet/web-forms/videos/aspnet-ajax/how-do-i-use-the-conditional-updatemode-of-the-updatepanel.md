---
uid: web-forms/videos/aspnet-ajax/how-do-i-use-the-conditional-updatemode-of-the-updatepanel
title: "[Bunu nasıl yaparım:] Koşullu Updatemode'unu kullanma? | Microsoft Docs"
author: JoeStagner
description: ASP.NET AJAX UpdatePanel 'Always' veya 'Koşullu' için ayarlanmış bir UpdateMode özelliğini içerir. Her zaman UpdatePan durumda varsayılandır...
ms.author: riande
ms.date: 08/01/2007
ms.assetid: 10b5bad3-4c18-464f-9454-0b3e60b7b8be
msc.legacyurl: /web-forms/videos/aspnet-ajax/how-do-i-use-the-conditional-updatemode-of-the-updatepanel
msc.type: video
ms.openlocfilehash: 96d7bc95fd80e410feb332264695835e68793ae2
ms.sourcegitcommit: 24b1f6decbb17bb22a45166e5fdb0845c65af498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57073920"
---
<a name="how-do-i-use-the-conditional-updatemode-of-the-updatepanel"></a><span data-ttu-id="37e49-105">[Bunu nasıl yaparım:] Koşullu Updatemode'unu kullanma?</span><span class="sxs-lookup"><span data-stu-id="37e49-105">[How Do I:] Use the Conditional UpdateMode of the UpdatePanel?</span></span>
====================
<span data-ttu-id="37e49-106">tarafından [ALi Stagner](https://github.com/JoeStagner)</span><span class="sxs-lookup"><span data-stu-id="37e49-106">by [Joe Stagner](https://github.com/JoeStagner)</span></span>

<span data-ttu-id="37e49-107">ASP.NET AJAX UpdatePanel 'Always' veya 'Koşullu' için ayarlanmış bir UpdateMode özelliğini içerir.</span><span class="sxs-lookup"><span data-stu-id="37e49-107">The ASP.NET AJAX UpdatePanel includes an UpdateMode property that may be set to 'Always' or 'Conditional'.</span></span> <span data-ttu-id="37e49-108">Her zaman, bu durumda UpdatePanel her zaman içeriğini bir Aracıdan geri gönderme sırasında güncelleştirilir varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="37e49-108">The default is Always, in which case the UpdatePanel will always update its content during an asychronous postback.</span></span> <span data-ttu-id="37e49-109">Bu videoda, biz sunucu tarafı kodumuz kendi güncelleştirme yöntemini çağırdığında, servis talebi UpdatePanel yalnızca içeriği güncelleştirir koşullu UpdateMode nasıl ayarlayabileceğinizi öğrenin.</span><span class="sxs-lookup"><span data-stu-id="37e49-109">In this video we learn how we can set the UpdateMode to Conditional, in which case the UpdatePanel will only update its content when our server-side code calls its Update method.</span></span> <span data-ttu-id="37e49-110">UpdatePanel içeriğini geçerli zaman uyumsuz geri gönderme sırasında güncelleştirme olup olmadığını belirlemek için C# veya Visual Basic kodunu koşullu mantık kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="37e49-110">This allows you to use conditional logic in your C# or Visual Basic code to determine whether the UpdatePanel will update its content during the current asynchronous postback.</span></span>

[<span data-ttu-id="37e49-111">&#9654;Videoyu (13 dakika)</span><span class="sxs-lookup"><span data-stu-id="37e49-111">&#9654; Watch video (13 minutes)</span></span>](https://channel9.msdn.com/Blogs/ASP-NET-Site-Videos/how-do-i-use-the-conditional-updatemode-of-the-updatepanel)

> [!div class="step-by-step"]
> <span data-ttu-id="37e49-112">[Önceki](how-do-i-determine-whether-an-asynchronous-postback-has-occurred.md)
> [İleri](how-do-i-implement-the-persistent-communications-pattern-with-the-updatepanel.md)</span><span class="sxs-lookup"><span data-stu-id="37e49-112">[Previous](how-do-i-determine-whether-an-asynchronous-postback-has-occurred.md)
[Next](how-do-i-implement-the-persistent-communications-pattern-with-the-updatepanel.md)</span></span>