---
uid: web-pages/overview/testing-and-debugging/introduction-to-debugging
title: Giriş hata ayıklama ASP.NET Web sayfaları (Razor) siteler | Microsoft Docs
author: Rick-Anderson
description: Hata ayıklama hataları bulma ve kod sayfalarınıza düzeltme işlemidir. Bu bölümde bazı araçlar ve hata ayıklamak için kullanabileceğiniz teknikleri gösterir ve analyz...
ms.author: riande
ms.date: 02/20/2014
ms.assetid: 68de4326-7611-4b9b-b5f6-79b7adc3069f
msc.legacyurl: /web-pages/overview/testing-and-debugging/introduction-to-debugging
msc.type: authoredcontent
ms.openlocfilehash: e5302492f01cbd507e0b0fd995f21621bf6f04c8
ms.sourcegitcommit: 24b1f6decbb17bb22a45166e5fdb0845c65af498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57068961"
---
<a name="introduction-to-debugging-aspnet-web-pages-razor-sites"></a><span data-ttu-id="96759-104">(Razor) giriş hata ayıklama ASP.NET Web sayfaları</span><span class="sxs-lookup"><span data-stu-id="96759-104">Introduction to Debugging ASP.NET Web Pages (Razor) Sites</span></span>
====================
<span data-ttu-id="96759-105">tarafından [Tom FitzMacken](https://github.com/tfitzmac)</span><span class="sxs-lookup"><span data-stu-id="96759-105">by [Tom FitzMacken](https://github.com/tfitzmac)</span></span>

> <span data-ttu-id="96759-106">Bu makalede, bir ASP.NET Web sayfaları (Razor) Web sayfalarında hata ayıklamak için çeşitli yollar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="96759-106">This article explains various ways to debug pages in an ASP.NET Web Pages (Razor) website.</span></span> <span data-ttu-id="96759-107">Hata ayıklama hataları bulma ve kod sayfalarınıza düzeltme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="96759-107">Debugging is the process of finding and fixing errors in your code pages.</span></span>
>
> <span data-ttu-id="96759-108">**Öğrenecekleriniz:**</span><span class="sxs-lookup"><span data-stu-id="96759-108">**What you'll learn:**</span></span>
>
> - <span data-ttu-id="96759-109">Yardımcı olacak bilgileri görüntülemek nasıl analiz edin ve hata ayıklama sayfaları.</span><span class="sxs-lookup"><span data-stu-id="96759-109">How to display information that helps analyze and debug pages.</span></span>
> - <span data-ttu-id="96759-110">Visual Studio'da hata ayıklama kullanmayı araçları.</span><span class="sxs-lookup"><span data-stu-id="96759-110">How to use debugging tools in Visual Studio.</span></span>
>
>
> <span data-ttu-id="96759-111">Bu makalede sunulan ASP.NET özellikleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="96759-111">These are the ASP.NET features introduced in the article:</span></span>
>
> - <span data-ttu-id="96759-112">`ServerInfo` Yardımcısı.</span><span class="sxs-lookup"><span data-stu-id="96759-112">The `ServerInfo` helper.</span></span>
> - <span data-ttu-id="96759-113">`ObjectInfo` Yardımcısı.</span><span class="sxs-lookup"><span data-stu-id="96759-113">`ObjectInfo` helper.</span></span>
>
>
> ## <a name="software-versions"></a><span data-ttu-id="96759-114">Yazılım sürümleri</span><span class="sxs-lookup"><span data-stu-id="96759-114">Software versions</span></span>
>
>
> - <span data-ttu-id="96759-115">ASP.NET Web sayfaları (Razor) 3</span><span class="sxs-lookup"><span data-stu-id="96759-115">ASP.NET Web Pages (Razor) 3</span></span>
> - <span data-ttu-id="96759-116">Visual Studio 2013</span><span class="sxs-lookup"><span data-stu-id="96759-116">Visual Studio 2013</span></span>
>
>
> <span data-ttu-id="96759-117">Bu öğreticide, ASP.NET Web Pages 2 ile de çalışır.</span><span class="sxs-lookup"><span data-stu-id="96759-117">This tutorial also works with ASP.NET Web Pages 2.</span></span> <span data-ttu-id="96759-118">WebMatrix 3'ü kullanabilirsiniz ancak tümleşik hata ayıklayıcı desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="96759-118">You can use WebMatrix 3 but the integrated debugger is not supported.</span></span>


<span data-ttu-id="96759-119">Hataları ve sorunları kodunuzda sorun giderme işlemlerinin önemli bir yönüdür bunları ilk başta önlemek içindir.</span><span class="sxs-lookup"><span data-stu-id="96759-119">An important aspect of troubleshooting errors and problems in your code is to avoid them in the first place.</span></span> <span data-ttu-id="96759-120">Hatalarla karşılaşırsanız neden olabilecek kod bölümlerini koyarak bunu yapabilirsiniz `try/catch` engeller.</span><span class="sxs-lookup"><span data-stu-id="96759-120">You can do that by putting sections of your code that are likely to cause errors into `try/catch` blocks.</span></span> <span data-ttu-id="96759-121">Hataları işleme hakkında daha fazla bilgi için bölüm bakın [giriş kullanımına ASP.NET Web programlama Razor söz dizimi](https://go.microsoft.com/fwlink/?LinkId=202890).</span><span class="sxs-lookup"><span data-stu-id="96759-121">For more information, see the section on handling errors in [Introduction to ASP.NET Web Programming Using the Razor Syntax](https://go.microsoft.com/fwlink/?LinkId=202890).</span></span>

<span data-ttu-id="96759-122">`ServerInfo` Yardımcı olan bir genel bakış sayfanız barındıran web sunucusu ortamı hakkındaki bilgileri sunan bir tanı aracıdır.</span><span class="sxs-lookup"><span data-stu-id="96759-122">The `ServerInfo` helper is a diagnostic tool that gives you an overview of information about the web server environment that hosts your page.</span></span> <span data-ttu-id="96759-123">Ayrıca, bir tarayıcı sayfa istediğinde gönderilen HTTP isteği bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="96759-123">It also shows you HTTP request information that's sent when a browser requests the page.</span></span> <span data-ttu-id="96759-124">`ServerInfo` Yardımcısı görüntüler geçerli bir kullanıcı kimliği, istekte tarayıcı türü ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="96759-124">The `ServerInfo` helper displays the current user identity, the type of browser that made the request, and so on.</span></span> <span data-ttu-id="96759-125">Bu tür bilgiler genel sorunları gidermenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="96759-125">This kind of information can help you troubleshoot common issues.</span></span>

1. <span data-ttu-id="96759-126">Adlı yeni bir web sayfası oluşturma *ServerInfo.cshtml*.</span><span class="sxs-lookup"><span data-stu-id="96759-126">Create a new web page named *ServerInfo.cshtml*.</span></span>
2. <span data-ttu-id="96759-127">Sayfasının sonunda, yeni kapatmadan önce `</body>` etiketinde, ekleyin `@ServerInfo.GetHtml()`:</span><span class="sxs-lookup"><span data-stu-id="96759-127">At the end of the page, just before the closing `</body>` tag, add `@ServerInfo.GetHtml()`:</span></span>

    [!code-cshtml[Main](introduction-to-debugging/samples/sample1.cshtml)]

    <span data-ttu-id="96759-128">Ekleyebileceğiniz `ServerInfo` kod sayfası herhangi bir yerindeki.</span><span class="sxs-lookup"><span data-stu-id="96759-128">You can add the `ServerInfo` code anywhere in the page.</span></span> <span data-ttu-id="96759-129">Ancak, sonunda ekleme çıktısını kolay okunur hale getiren, diğer sayfa içeriği, ayrı tutar.</span><span class="sxs-lookup"><span data-stu-id="96759-129">But adding it at the end will keep its output separate from your other page content, which makes it easier to read.</span></span>

    > [!NOTE]
    >
    > <span data-ttu-id="96759-130">**Önemli** bir üretim sunucusu için web sayfaları geçmeden önce web sayfalarınızdan herhangi bir tanılama kodu kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="96759-130">**Important** You should remove any diagnostic code from your web pages before you move web pages to a production server.</span></span> <span data-ttu-id="96759-131">Bu durum geçerlidir `ServerInfo` bir sayfaya kod ekleme, hatalı durumdaki diğer tanılama teknikler bu makaledeki yanı sıra Yardımcısı.</span><span class="sxs-lookup"><span data-stu-id="96759-131">This applies to the `ServerInfo` helper as well as the other diagnostic techniques in this article that involve adding code to a page.</span></span> <span data-ttu-id="96759-132">Bu tür bilgiler kötü amaçlı kişilerin yararlı olabileceği için sunucu ve benzer ayrıntıları, sunucu adı, kullanıcı adları, yollar hakkındaki bilgileri görmek için Web sitenizin ziyaretçileri istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="96759-132">You don't want your website visitors to see information about your server name, user names, paths on your server, and similar details, because this type of information might be useful to people with malicious intent.</span></span>
3. <span data-ttu-id="96759-133">Sayfayı kaydedin ve bir tarayıcıda çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="96759-133">Save the page and run it in a browser.</span></span>

    ![Hata ayıklama-1](introduction-to-debugging/_static/image1.jpg)

    <span data-ttu-id="96759-135">`ServerInfo` Yardımcısı sayfasında dört tablo bilgileri görüntüler:</span><span class="sxs-lookup"><span data-stu-id="96759-135">The `ServerInfo` helper displays four tables of information in the page:</span></span>

   - <span data-ttu-id="96759-136">Sunucu yapılandırması.</span><span class="sxs-lookup"><span data-stu-id="96759-136">Server Configuration.</span></span> <span data-ttu-id="96759-137">Bu bölümde, bilgisayar adı, çalıştırmakta olduğunuz ASP.NET, etki alanı adı ve sunucu sürümü dahil olmak üzere barındırma web sunucusu hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="96759-137">This section provides information about the hosting web server, including computer name, the version of ASP.NET you're running, the domain name, and server time.</span></span>
   - <span data-ttu-id="96759-138">ASP.NET sunucu değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="96759-138">ASP.NET Server Variables.</span></span> <span data-ttu-id="96759-139">Bu bölümde, birçok HTTP protokolü ayrıntıları (çağrılan HTTP değişkenler) hakkında ayrıntılı bilgi sağlar ve bu değerleri her web sayfa isteğinde bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="96759-139">This section provides details about the many HTTP protocol details (called HTTP variables) and values that are part of each web page request.</span></span>
   - <span data-ttu-id="96759-140">HTTP çalışma zamanı bilgileri.</span><span class="sxs-lookup"><span data-stu-id="96759-140">HTTP Runtime Information.</span></span> <span data-ttu-id="96759-141">Bu bölüm, ayrıntıları, sürümü, web sayfanızın altında çalışan Microsoft .NET Framework, yol, önbellek vb. hakkında ayrıntılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="96759-141">This section provides details about that the version of the Microsoft .NET Framework that your web page is running under, the path, details about the cache, and so on.</span></span> <span data-ttu-id="96759-142">(İçinde öğrenilen [kullanımına ASP.NET Web programlama Razor söz dizimi giriş](https://go.microsoft.com/fwlink/?LinkId=202890), Razor sözdizimi kendisini kapsamlı bir yazılım üzerinde oluşturulmuş olan Microsoft ASP.NET web sunucusu teknolojileri olanakları kullanan ASP.NET Web sayfaları .NET Framework adlı geliştirme kitaplığını.)</span><span class="sxs-lookup"><span data-stu-id="96759-142">(As you learned in [Introduction to ASP.NET Web Programming Using the Razor Syntax](https://go.microsoft.com/fwlink/?LinkId=202890), ASP.NET Web Pages using the Razor syntax are built on Microsoft's ASP.NET web server technology, which is itself built on an extensive software development library called the .NET Framework.)</span></span>
   - <span data-ttu-id="96759-143">Ortam değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="96759-143">Environment Variables.</span></span> <span data-ttu-id="96759-144">Bu bölümde web sunucusundaki tüm yerel ortam değişkenlerini ve değerleri listesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="96759-144">This section provides a list of all the local environment variables and their values on the web server.</span></span>

     <span data-ttu-id="96759-145">Tüm sunucu ve istek bilgileri tam açıklamasını bu makalenin kapsamı dışındadır, ancak gördüğünüz gibi `ServerInfo` Yardımcısı, çok miktarda tanılama bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="96759-145">A full description of all the server and request information is beyond the scope of this article, but you can see that the `ServerInfo` helper returns a lot of diagnostic information.</span></span> <span data-ttu-id="96759-146">Değerler hakkında daha fazla bilgi için `ServerInfo` döndürür, bkz: [tanınan ortam değişkenlerini](https://technet.microsoft.com/library/dd560744(WS.10).aspx) Microsoft TechNet Web sitesinde ve [IIS Sunucu değişkenleri](https://msdn.microsoft.com/library/ms524602(VS.90).aspx) MSDN Web sitesinde.</span><span class="sxs-lookup"><span data-stu-id="96759-146">For more information about the values that `ServerInfo` returns, see [Recognized Environment Variables](https://technet.microsoft.com/library/dd560744(WS.10).aspx) on the Microsoft TechNet website and [IIS Server Variables](https://msdn.microsoft.com/library/ms524602(VS.90).aspx) on the MSDN website.</span></span>

## <a name="embedding-output-expressions-to-display-page-values"></a><span data-ttu-id="96759-147">Sayfa değerleri görüntülemek için ekleme çıkış ifadeleri</span><span class="sxs-lookup"><span data-stu-id="96759-147">Embedding Output Expressions to Display Page Values</span></span>

<span data-ttu-id="96759-148">Kodunuzda neler olduğunu görmek için başka bir sayfaya çıkış ifade katıştırma yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="96759-148">Another way to see what's happening in your code is to embed output expressions in the page.</span></span> <span data-ttu-id="96759-149">Bildiğiniz gibi doğrudan bir değişkenin değerini aşağıdakine benzer ekleyerek çıkarabilirsiniz `@myVariable` veya `@(subTotal * 12)` sayfası.</span><span class="sxs-lookup"><span data-stu-id="96759-149">As you know, you can directly output the value of a variable by adding something like `@myVariable` or `@(subTotal * 12)` to the page.</span></span> <span data-ttu-id="96759-150">Hata ayıklama için kodunuzda bu çıkış ifadeler stratejik noktalarda yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96759-150">For debugging, you can place these output expressions at strategic points in your code.</span></span> <span data-ttu-id="96759-151">Bu, sayfa çalıştığında anahtar değişkenleri veya hesaplama sonucu değerini görmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="96759-151">This enables you to see the value of key variables or the result of calculations when your page runs.</span></span> <span data-ttu-id="96759-152">Bitirdiğinizde, hata ayıklama ifadeleri kaldırabilir veya yorum gönderin. Bu yordam, bir sayfa hataları ayıklamanıza yardımcı için katıştırılmış ifadeleri kullanma için tipik bir yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="96759-152">When you're done debugging, you can remove the expressions or comment them out. This procedure illustrates a typical way to use embedded expressions to help debug a page.</span></span>

1. <span data-ttu-id="96759-153">Adlı yeni bir WebMatrix sayfası oluşturma *OutputExpression.cshtml*.</span><span class="sxs-lookup"><span data-stu-id="96759-153">Create a new WebMatrix page that's named *OutputExpression.cshtml*.</span></span>
2. <span data-ttu-id="96759-154">Sayfa içeriği aşağıdakiyle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="96759-154">Replace the page content with the following:</span></span>

    [!code-html[Main](introduction-to-debugging/samples/sample2.html)]

    <span data-ttu-id="96759-155">Örnekte bir `switch` değerini denetlemek için bildirimi `weekday` değişkeni ve sonra görünen bir haftanın gününü bağlı olarak farklı çıkış iletisinin.</span><span class="sxs-lookup"><span data-stu-id="96759-155">The example uses a `switch` statement to check the value of the `weekday` variable and then display a different output message depending on which day of the week it is.</span></span> <span data-ttu-id="96759-156">Örnekte, `if` blok ilk kod bloğu içinde rastgele bir gün için geçerli haftanın gününü değeri ekleyerek haftanın günü değiştirir.</span><span class="sxs-lookup"><span data-stu-id="96759-156">In the example, the `if` block within the first code block arbitrarily changes the day of the week by adding one day to the current weekday value.</span></span> <span data-ttu-id="96759-157">Bu gösterim amacıyla sunulan bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="96759-157">This is an error introduced for illustration purposes.</span></span>
3. <span data-ttu-id="96759-158">Sayfayı kaydedin ve bir tarayıcıda çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="96759-158">Save the page and run it in a browser.</span></span>

    <span data-ttu-id="96759-159">Sayfa yanlış haftanın günü için iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="96759-159">The page displays the message for the wrong day of the week.</span></span> <span data-ttu-id="96759-160">Haftanın her günü gerçekten olduğundan, daha sonra bir günlük iletisi görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="96759-160">Whatever day of the week it actually is, you'll see the message for one day later.</span></span> <span data-ttu-id="96759-161">Bu durumda, (kod bilerek yanlış day değeri ayarlar nedeniyle) neden ileti kapalı olduğunu ancak, gerçekte, genellikle şeyleri burada kodda yanlış kalacaklarını bilmek zordur.</span><span class="sxs-lookup"><span data-stu-id="96759-161">Although in this case you know why the message is off (because the code deliberately sets the incorrect day value), in reality it's often hard to know where things are going wrong in the code.</span></span> <span data-ttu-id="96759-162">Hata ayıklamak için değeri olarak anahtar nesneler ve değişkenler gibi neler olup bittiğine bulmanız gereken `weekday`.</span><span class="sxs-lookup"><span data-stu-id="96759-162">To debug, you need to find out what's happening to the value of key objects and variables such as `weekday`.</span></span>
4. <span data-ttu-id="96759-163">Çıkış ifadeleri ekleyerek ekleyin `@weekday` kod açıklamaları tarafından gösterilen iki yerde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="96759-163">Add output expressions by inserting `@weekday` as shown in the two places indicated by comments in the code.</span></span> <span data-ttu-id="96759-164">Bu çıkış ifadeler değişkeni değerlerini o noktada kod yürütme görüntüler.</span><span class="sxs-lookup"><span data-stu-id="96759-164">These output expressions will display the values of the variable at that point in the code execution.</span></span>

    [!code-csharp[Main](introduction-to-debugging/samples/sample3.cs?highlight=2-3,15-16)]
5. <span data-ttu-id="96759-165">Kaydedin ve sayfanın tarayıcıda çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="96759-165">Save and run the page in a browser.</span></span>

    <span data-ttu-id="96759-166">Gerçek haftanın gününü, ilk sayfasını görüntüler ve ardından güncelleştirilmiş haftanın sonuçlarının bir gün ve sonuçta elde edilen iletiden eklemesini `switch` deyimi.</span><span class="sxs-lookup"><span data-stu-id="96759-166">The page displays the real day of the week first, then the updated day of the week that results from adding one day, and then the resulting message from the `switch` statement.</span></span> <span data-ttu-id="96759-167">İki değişken ifadeleri çıktısı (`@weekday`) gün arasında bir boşluk olmayan herhangi bir HTML eklemediğim sahip `<p>` ; çıkış etiketleri yalnızca test için ifadelerdir.</span><span class="sxs-lookup"><span data-stu-id="96759-167">The output from the two variable expressions (`@weekday`) has no spaces between the days because you didn't add any HTML `<p>` tags to the output; the expressions are just for testing.</span></span>

    ![Hata ayıklama-2](introduction-to-debugging/_static/image2.jpg)

    <span data-ttu-id="96759-169">Şimdi hatanın nerede görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96759-169">Now you can see where the error is.</span></span> <span data-ttu-id="96759-170">İlk kez görüntülediğinizde `weekday` değişken kodda, doğru günü gösterir.</span><span class="sxs-lookup"><span data-stu-id="96759-170">When you first display the `weekday` variable in the code, it shows the correct day.</span></span> <span data-ttu-id="96759-171">Görüntülediğinizde, ikincisinde ise, sonra `if` kodda engelleme, kapalı bir gündür.</span><span class="sxs-lookup"><span data-stu-id="96759-171">When you display it the second time, after the `if` block in the code, the day is off by one.</span></span> <span data-ttu-id="96759-172">Bu nedenle bir şey haftanın günü değişkeni birinci ve ikinci görünümünü arasında oluştuğunu bildirin.</span><span class="sxs-lookup"><span data-stu-id="96759-172">So you know that something has happened between the first and second appearance of the weekday variable.</span></span> <span data-ttu-id="96759-173">Bu tür bir yaklaşım, bu gerçek bir hata varsa, soruna neden olan kod konumunu sınırlandırmanıza yardımcı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="96759-173">If this were a real bug, this kind of approach would help you narrow down the location of the code that's causing the problem.</span></span>
6. <span data-ttu-id="96759-174">Kodu, eklediğiniz iki çıkış ifadeleri kaldırma ve haftanın günü değişiklikleri kod kaldırma sayfasında düzeltin.</span><span class="sxs-lookup"><span data-stu-id="96759-174">Fix the code in the page by removing the two output expressions you added, and removing the code that changes the day of the week.</span></span> <span data-ttu-id="96759-175">Kalan, tam kod bloğunu aşağıdaki örnekteki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="96759-175">The remaining, complete block of code looks like the following example:</span></span>

    [!code-cshtml[Main](introduction-to-debugging/samples/sample4.cshtml)]
7. <span data-ttu-id="96759-176">Sayfanın tarayıcıda çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="96759-176">Run the page in a browser.</span></span> <span data-ttu-id="96759-177">Bu süre, gerçek haftanın günü için görüntülenen doğru iletisini görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="96759-177">This time you see the correct message displayed for the actual day of the week.</span></span>

## <a name="using-the-objectinfo-helper-to-display-object-values"></a><span data-ttu-id="96759-178">Nesne değerleri görüntülemek için ObjectInfo Yardımcısını kullanma</span><span class="sxs-lookup"><span data-stu-id="96759-178">Using the ObjectInfo Helper to Display Object Values</span></span>

<span data-ttu-id="96759-179">`ObjectInfo` Yardımcısı, türü ve kendisine geçirdiğiniz her bir nesnenin değerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="96759-179">The `ObjectInfo` helper displays the type and the value of each object you pass to it.</span></span> <span data-ttu-id="96759-180">(Önceki örnekte çıkış ifadelerle yaptığınız gibi), kodunuzda değişkenler ve nesneler değerini görüntülemek için kullanın yanı sıra veri nesnesi hakkında bilgi türü görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96759-180">You can use it to view the value of variables and objects in your code (like you did with output expressions in the previous example), plus you can see data type information about the object.</span></span>

1. <span data-ttu-id="96759-181">Adlı dosyayı açın *OutputExpression.cshtml* daha önce oluşturduğunuz.</span><span class="sxs-lookup"><span data-stu-id="96759-181">Open the file named *OutputExpression.cshtml* that you created earlier.</span></span>
2. <span data-ttu-id="96759-182">Tüm kod sayfasında, aşağıdaki kod bloğunu ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="96759-182">Replace all code in the page with the following block of code:</span></span>

    [!code-html[Main](introduction-to-debugging/samples/sample5.html)]
3. <span data-ttu-id="96759-183">Kaydedin ve sayfanın tarayıcıda çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="96759-183">Save and run the page in a browser.</span></span>

    ![Hata ayıklama-4](introduction-to-debugging/_static/image3.jpg)

    <span data-ttu-id="96759-185">Bu örnekte, `ObjectInfo` Yardımcısı iki öğeleri görüntüler:</span><span class="sxs-lookup"><span data-stu-id="96759-185">In this example, the `ObjectInfo` helper displays two items:</span></span>

   - <span data-ttu-id="96759-186">Tür.</span><span class="sxs-lookup"><span data-stu-id="96759-186">The type.</span></span> <span data-ttu-id="96759-187">Birinci değişken için olan türdür `DayOfWeek`.</span><span class="sxs-lookup"><span data-stu-id="96759-187">For the first variable, the type is `DayOfWeek`.</span></span> <span data-ttu-id="96759-188">İkinci değişken için olan türdür `String`.</span><span class="sxs-lookup"><span data-stu-id="96759-188">For the second variable, the type is `String`.</span></span>
   - <span data-ttu-id="96759-189">Değer.</span><span class="sxs-lookup"><span data-stu-id="96759-189">The value.</span></span> <span data-ttu-id="96759-190">Sayfada zaten Karşılama değişkenin değerini görüntülemek için değişkenine geçirdiğinizde bu durumda, yeniden görüntülenmesi `ObjectInfo`.</span><span class="sxs-lookup"><span data-stu-id="96759-190">In this case, because you already display the value of the greeting variable in the page, the value is displayed again when you pass the variable to `ObjectInfo`.</span></span>

     <span data-ttu-id="96759-191">Daha karmaşık nesneler için `ObjectInfo` Yardımcısı, daha fazla bilgi görüntüleyebilir &#8212; temel olarak, bu türleri ve değerleri tüm bir nesnenin özelliklerini görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96759-191">For more complex objects, the `ObjectInfo` helper can display more information &#8212; basically, it can display the types and values of all of an object's properties.</span></span>

## <a name="using-debugging-tools-in-visual-studio"></a><span data-ttu-id="96759-192">Visual Studio'da hata ayıklama araçlarını kullanarak</span><span class="sxs-lookup"><span data-stu-id="96759-192">Using Debugging Tools in Visual Studio</span></span>

<span data-ttu-id="96759-193">Daha kapsamlı bir hata ayıklama deneyimi için kullanmak [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).</span><span class="sxs-lookup"><span data-stu-id="96759-193">For a more comprehensive debugging experience, use [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).</span></span> <span data-ttu-id="96759-194">Visual Studio ile incelemek istediğiniz satırı kodunuzda bir kesme noktası ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96759-194">With Visual Studio, you can set a breakpoint in your code at the line that you want to inspect.</span></span>

![kesme noktası Ayarla](introduction-to-debugging/_static/image1.png)

<span data-ttu-id="96759-196">Web sitesi test ettiğinizde, kodu yürütürken kesme noktasında durur.</span><span class="sxs-lookup"><span data-stu-id="96759-196">When you test the web site, the executing code halts at the breakpoint.</span></span>

![kesme noktası ulaşın](introduction-to-debugging/_static/image2.png)

<span data-ttu-id="96759-198">Değişkenler ve kod satırının satır adımlayın geçerli değerlerini inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96759-198">You can examine the current values of the variables, and step through the code line-by-line.</span></span>

![değerler bakın](introduction-to-debugging/_static/image3.png)

<span data-ttu-id="96759-200">ASP.NET Razor sayfaları hata ayıklamak için Visual Studio'da tümleşik hata ayıklayıcısı hakkında daha fazla bilgi için bkz. [programlama ASP.NET Web sayfaları (Razor) kullanarak Visual Studio](https://go.microsoft.com/fwlink/?LinkId=205854).</span><span class="sxs-lookup"><span data-stu-id="96759-200">For information about using the integrated debugger in Visual Studio to debug ASP.NET Razor pages, see [Programming ASP.NET Web Pages (Razor) Using Visual Studio](https://go.microsoft.com/fwlink/?LinkId=205854).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="96759-201">Ek Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="96759-201">Additional Resources</span></span>

- [<span data-ttu-id="96759-202">Visual Studio kullanarak ASP.NET Web sayfaları (Razor) programlama</span><span class="sxs-lookup"><span data-stu-id="96759-202">Programming ASP.NET Web Pages (Razor) Using Visual Studio</span></span>](https://go.microsoft.com/fwlink/?LinkId=205854)
- <span data-ttu-id="96759-203">[IIS Sunucu değişkenleri](https://msdn.microsoft.com/library/ms524602(VS.90).aspx) (MSDN)</span><span class="sxs-lookup"><span data-stu-id="96759-203">[IIS Server Variables](https://msdn.microsoft.com/library/ms524602(VS.90).aspx) (MSDN)</span></span>
- <span data-ttu-id="96759-204">[Ortam değişkenlerini tanınan](https://technet.microsoft.com/library/dd560744(WS.10).aspx) (TechNet)</span><span class="sxs-lookup"><span data-stu-id="96759-204">[Recognized Environment Variables](https://technet.microsoft.com/library/dd560744(WS.10).aspx) (TechNet)</span></span>