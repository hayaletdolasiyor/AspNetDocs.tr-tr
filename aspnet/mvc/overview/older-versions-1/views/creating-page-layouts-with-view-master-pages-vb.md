---
uid: mvc/overview/older-versions-1/views/creating-page-layouts-with-view-master-pages-vb
title: (VB) görünüm ana sayfalarıyla sayfa düzenleri oluşturma | Microsoft Docs
author: microsoft
description: Bu öğreticide, görünüm ana sayfalarına yararlanarak uygulamanızda ortak bir sayfa düzeni için birden çok sayfa oluşturma konusunda bilgi edinin. Kullanabileceğiniz bir...
ms.author: riande
ms.date: 10/16/2008
ms.assetid: d34f90a1-6de3-482a-a326-f87fdcbaaaff
msc.legacyurl: /mvc/overview/older-versions-1/views/creating-page-layouts-with-view-master-pages-vb
msc.type: authoredcontent
ms.openlocfilehash: 4ff74b1dc1d83b7ec1c8ecf6eca341a5cd14403f
ms.sourcegitcommit: 24b1f6decbb17bb22a45166e5fdb0845c65af498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57066663"
---
<a name="creating-page-layouts-with-view-master-pages-vb"></a><span data-ttu-id="6ecf6-104">Görünüm Ana Sayfalarıyla Sayfa Düzenleri Oluşturma (VB)</span><span class="sxs-lookup"><span data-stu-id="6ecf6-104">Creating Page Layouts with View Master Pages (VB)</span></span>
====================
<span data-ttu-id="6ecf6-105">tarafından [Microsoft](https://github.com/microsoft)</span><span class="sxs-lookup"><span data-stu-id="6ecf6-105">by [Microsoft](https://github.com/microsoft)</span></span>

[<span data-ttu-id="6ecf6-106">PDF'yi indirin</span><span class="sxs-lookup"><span data-stu-id="6ecf6-106">Download PDF</span></span>](http://download.microsoft.com/download/e/f/3/ef3f2ff6-7424-48f7-bdaa-180ef64c3490/ASPNET_MVC_Tutorial_12_VB.pdf)

> <span data-ttu-id="6ecf6-107">Bu öğreticide, görünüm ana sayfalarına yararlanarak uygulamanızda ortak bir sayfa düzeni için birden çok sayfa oluşturma konusunda bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-107">In this tutorial, you learn how to create a common page layout for multiple pages in your application by taking advantage of view master pages.</span></span> <span data-ttu-id="6ecf6-108">Örneğin, iki sütunlu sayfa düzeni tanımlamak ve web uygulamanızda tüm sayfalar için iki sütunlu düzeni kullanmak için ana görünüm sayfası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-108">You can use a view master page, for example, to define a two-column page layout and use the two-column layout for all of the pages in your web application.</span></span>


## <a name="creating-page-layouts-with-view-master-pages"></a><span data-ttu-id="6ecf6-109">Görünüm ana sayfalarıyla sayfa düzenleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="6ecf6-109">Creating Page Layouts with View Master Pages</span></span>

<span data-ttu-id="6ecf6-110">Bu öğreticide, görünüm ana sayfalarına yararlanarak uygulamanızda ortak bir sayfa düzeni için birden çok sayfa oluşturma konusunda bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-110">In this tutorial, you learn how to create a common page layout for multiple pages in your application by taking advantage of view master pages.</span></span> <span data-ttu-id="6ecf6-111">Örneğin, iki sütunlu sayfa düzeni tanımlamak ve web uygulamanızda tüm sayfalar için iki sütunlu düzeni kullanmak için ana görünüm sayfası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-111">You can use a view master page, for example, to define a two-column page layout and use the two-column layout for all of the pages in your web application.</span></span>

<span data-ttu-id="6ecf6-112">Ayrıca görünümün birden çok sayfada uygulamanızda ortak içerik paylaşmak için ana sayfalar yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-112">You also can take advantage of view master pages to share common content across multiple pages in your application.</span></span> <span data-ttu-id="6ecf6-113">Örneğin, bir görünüm ana sayfaya, Web sitesi logosu, gezinti bağlantılarının ve başlık reklamları yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-113">For example, you can place your website logo, navigation links, and banner advertisements in a view master page.</span></span> <span data-ttu-id="6ecf6-114">Bu şekilde, uygulamanızdaki her sayfada bu içerik otomatik olarak görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-114">That way, every page in your application would display this content automatically.</span></span>

<span data-ttu-id="6ecf6-115">Bu öğreticide, yeni bir görünüm ana sayfası oluşturun ve ana sayfasını temel alan yeni bir görünüm içerik sayfası oluşturmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-115">In this tutorial, you learn how to create a new view master page and create a new view content page based on the master page.</span></span>

### <a name="creating-a-view-master-page"></a><span data-ttu-id="6ecf6-116">Görünüm ana sayfası oluşturma</span><span class="sxs-lookup"><span data-stu-id="6ecf6-116">Creating a View Master Page</span></span>

<span data-ttu-id="6ecf6-117">İki sütunlu düzeni tanımlayan bir görünümü ana sayfası oluşturarak başlayalım.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-117">Let's start by creating a view master page that defines a two-column layout.</span></span> <span data-ttu-id="6ecf6-118">Yeni bir görünüm ana sayfası bir MVC projesi için görünümler/paylaşılan klasörünü sağ tıklayarak menü seçeneğini belirleyerek eklediğiniz **Ekle, yeni öğe**, MVC görünüm ana sayfası şablonu seçip (bkz. Şekil 1).</span><span class="sxs-lookup"><span data-stu-id="6ecf6-118">You add a new view master page to an MVC project by right-clicking the Views\Shared folder, selecting the menu option **Add, New Item**, and selecting the  MVC View Master Page template (see Figure 1).</span></span>


<span data-ttu-id="6ecf6-119">[![Görünüm ana sayfası ekleme](creating-page-layouts-with-view-master-pages-vb/_static/image2.png)](creating-page-layouts-with-view-master-pages-vb/_static/image1.png)</span><span class="sxs-lookup"><span data-stu-id="6ecf6-119">[![Adding a view master page](creating-page-layouts-with-view-master-pages-vb/_static/image2.png)](creating-page-layouts-with-view-master-pages-vb/_static/image1.png)</span></span>

<span data-ttu-id="6ecf6-120">**Şekil 01**: Görünüm ana sayfası ekleme ([tam boyutlu görüntüyü görmek için tıklatın](creating-page-layouts-with-view-master-pages-vb/_static/image3.png))</span><span class="sxs-lookup"><span data-stu-id="6ecf6-120">**Figure 01**: Adding a view master page ([Click to view full-size image](creating-page-layouts-with-view-master-pages-vb/_static/image3.png))</span></span>


<span data-ttu-id="6ecf6-121">Bir uygulamada birden fazla ana görünüm sayfası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-121">You can create more than one view master page in an application.</span></span> <span data-ttu-id="6ecf6-122">Her görünüm ana sayfası farklı sayfa düzeni tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-122">Each view master page can define a different page layout.</span></span> <span data-ttu-id="6ecf6-123">Örneğin, iki sütunlu düzeni için belirli sayfaları ve diğer sayfalara üç sütunlu düzeni isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-123">For example, you might want certain pages to have a two-column layout and other pages to have a three-column layout.</span></span>

<span data-ttu-id="6ecf6-124">Görünüm ana sayfası gibi standart bir ASP.NET MVC görünüm çok arar.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-124">A view master page looks very much like a standard ASP.NET MVC view.</span></span> <span data-ttu-id="6ecf6-125">Ancak, normal görünümünden farklı olarak, bir veya daha fazla görünüm ana sayfası içeren `<asp:ContentPlaceHolder>` etiketler.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-125">However, unlike a normal view, a view master page contains one or more `<asp:ContentPlaceHolder>` tags.</span></span> <span data-ttu-id="6ecf6-126">`<contentplaceholder>` Etiketler tek tek bir içerik sayfasındaki geçersiz kılınabilir ana sayfa alanlarının işaretlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-126">The `<contentplaceholder>` tags are used to mark the areas of the master page that can be overridden in an individual content page.</span></span>

<span data-ttu-id="6ecf6-127">Örneğin, iki sütunlu düzeni listeleme 1 görünüm ana sayfasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-127">For example, the view master page in Listing 1 defines a two-column layout.</span></span> <span data-ttu-id="6ecf6-128">İki tane `<contentplaceholder>` etiketler.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-128">It contains two `<contentplaceholder>` tags.</span></span> <span data-ttu-id="6ecf6-129">Bir `<ContentPlaceHolder>` her sütun için.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-129">One `<ContentPlaceHolder>` for each column.</span></span>

<span data-ttu-id="6ecf6-130">**Kod 1 – `Views\Shared\Site.master`**</span><span class="sxs-lookup"><span data-stu-id="6ecf6-130">**Listing 1 – `Views\Shared\Site.master`**</span></span>

[!code-aspx[Main](creating-page-layouts-with-view-master-pages-vb/samples/sample1.aspx)]

<span data-ttu-id="6ecf6-131">Ana sayfa 1 listeleme içeren iki görünüm gövdesi `<div>` iki sütunlara karşılık gelen etiketleri.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-131">The body of the view master page in Listing 1 contains two `<div>` tags that correspond to the two columns.</span></span> <span data-ttu-id="6ecf6-132">Geçişli stil sayfası sütun sınıf her ikisi de uygulanır `<div>` etiketler.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-132">The Cascading Style Sheet column class is applied to both `<div>` tags.</span></span> <span data-ttu-id="6ecf6-133">Bu sınıf ana sayfanın en üstündeki bildirilen stil sayfası içinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-133">This class is defined in the style sheet declared at the top of the master page.</span></span> <span data-ttu-id="6ecf6-134">Tasarım görünümüne geçerek görünüm ana sayfasını nasıl işlenir önizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-134">You can preview how the view master page will be rendered by switching to Design view.</span></span> <span data-ttu-id="6ecf6-135">Kaynak kod düzenleyicisinin alt sol tasarım sekmesine tıklayın (bkz: Şekil 2).</span><span class="sxs-lookup"><span data-stu-id="6ecf6-135">Click the Design tab at the bottom-left of the source code editor (see Figure 2).</span></span>


<span data-ttu-id="6ecf6-136">[![Bir ana sayfa tasarımcıyı Önizleme](creating-page-layouts-with-view-master-pages-vb/_static/image5.png)](creating-page-layouts-with-view-master-pages-vb/_static/image4.png)</span><span class="sxs-lookup"><span data-stu-id="6ecf6-136">[![Previewing a master page in the designer](creating-page-layouts-with-view-master-pages-vb/_static/image5.png)](creating-page-layouts-with-view-master-pages-vb/_static/image4.png)</span></span>

<span data-ttu-id="6ecf6-137">**Şekil 02**: Bir ana sayfa tasarımcıyı Önizleme ([tam boyutlu görüntüyü görmek için tıklatın](creating-page-layouts-with-view-master-pages-vb/_static/image6.png))</span><span class="sxs-lookup"><span data-stu-id="6ecf6-137">**Figure 02**: Previewing a master page in the designer ([Click to view full-size image](creating-page-layouts-with-view-master-pages-vb/_static/image6.png))</span></span>


### <a name="creating-a-view-content-page"></a><span data-ttu-id="6ecf6-138">Bir görünüm içerik sayfası oluşturma</span><span class="sxs-lookup"><span data-stu-id="6ecf6-138">Creating a View Content Page</span></span>

<span data-ttu-id="6ecf6-139">Görünüm ana sayfası oluşturduktan sonra içerik sayfalarının görünüm ana sayfasını temel alan bir veya daha fazla görünüm oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-139">After you create a view master page, you can create one or more view content pages based on the view master page.</span></span> <span data-ttu-id="6ecf6-140">Görünümler/giriş klasörünü sağ tıklayarak dizini bir görünüm içerik sayfası için giriş denetleyicisine gibi oluşturabilirsiniz seçerek **Ekle, yeni öğe**u seçerek **MVC görünüm içerik sayfası** girme şablonu ' % s'adı Index.aspx ve Ekle düğmesine (bkz: Şekil 3) düğmesi.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-140">For example, you can create an Index view content page for the Home controller by right-clicking the Views\Home folder, selecting **Add, New Item**, selecting the **MVC View Content Page** template, entering the name Index.aspx, and clicking the Add button (see Figure 3).</span></span>


<span data-ttu-id="6ecf6-141">[![Bir görünüm içerik sayfası ekleme](creating-page-layouts-with-view-master-pages-vb/_static/image8.png)](creating-page-layouts-with-view-master-pages-vb/_static/image7.png)</span><span class="sxs-lookup"><span data-stu-id="6ecf6-141">[![Adding a view content page](creating-page-layouts-with-view-master-pages-vb/_static/image8.png)](creating-page-layouts-with-view-master-pages-vb/_static/image7.png)</span></span>

<span data-ttu-id="6ecf6-142">**Şekil 03**: Bir görünüm içerik sayfası ekleme ([tam boyutlu görüntüyü görmek için tıklatın](creating-page-layouts-with-view-master-pages-vb/_static/image9.png))</span><span class="sxs-lookup"><span data-stu-id="6ecf6-142">**Figure 03**: Adding a view content page ([Click to view full-size image](creating-page-layouts-with-view-master-pages-vb/_static/image9.png))</span></span>


<span data-ttu-id="6ecf6-143">Ekle düğmesine tıkladıktan sonra Görünüm içerik sayfası ile ilişkilendirmek için bir ana görünüm sayfası seçmenize olanak sağlayan yeni bir iletişim kutusu görünür (bkz: Şekil 4).</span><span class="sxs-lookup"><span data-stu-id="6ecf6-143">After you click the Add button, a new dialog appears that enables you to select a view master page to associate with the view content page (see Figure 4).</span></span> <span data-ttu-id="6ecf6-144">Önceki bölümde oluşturduğumuz Site.master görünüm ana sayfasına gidebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-144">You can navigate to the Site.master view master page that we created in the previous section.</span></span>


<span data-ttu-id="6ecf6-145">[![Ana sayfa seçme](creating-page-layouts-with-view-master-pages-vb/_static/image11.png)](creating-page-layouts-with-view-master-pages-vb/_static/image10.png)</span><span class="sxs-lookup"><span data-stu-id="6ecf6-145">[![Selecting a master page](creating-page-layouts-with-view-master-pages-vb/_static/image11.png)](creating-page-layouts-with-view-master-pages-vb/_static/image10.png)</span></span>

<span data-ttu-id="6ecf6-146">**Şekil 04**: Ana sayfa seçme ([tam boyutlu görüntüyü görmek için tıklatın](creating-page-layouts-with-view-master-pages-vb/_static/image12.png))</span><span class="sxs-lookup"><span data-stu-id="6ecf6-146">**Figure 04**: Selecting a master page ([Click to view full-size image](creating-page-layouts-with-view-master-pages-vb/_static/image12.png))</span></span>


<span data-ttu-id="6ecf6-147">Site.master ana sayfasını temel alan yeni bir görünüm içerik sayfası oluşturduktan sonra 2 listeleme dosyasında alın.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-147">After you create a new view content page based on the Site.master master page, you get the file in Listing 2.</span></span>

<span data-ttu-id="6ecf6-148">**Kod 2 – `Views\Home\Index.aspx`**</span><span class="sxs-lookup"><span data-stu-id="6ecf6-148">**Listing 2 – `Views\Home\Index.aspx`**</span></span>

[!code-aspx[Main](creating-page-layouts-with-view-master-pages-vb/samples/sample2.aspx)]

<span data-ttu-id="6ecf6-149">Bu görünüm içeren bildirimi bir `<asp:Content>` her biri için karşılık gelen etiket `<asp:ContentPlaceHolder>` görünüm ana sayfasındaki etiketler.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-149">Notice that this view contains a `<asp:Content>` tag that corresponds to each of the `<asp:ContentPlaceHolder>` tags in the view master page.</span></span> <span data-ttu-id="6ecf6-150">Her `<asp:Content>` etiketi içeren belirli işaret eden bir ContentPlaceHolderID özniteliği `<asp:ContentPlaceHolder>` , onu geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-150">Each `<asp:Content>` tag includes a ContentPlaceHolderID attribute that points to the particular `<asp:ContentPlaceHolder>` that it overrides.</span></span>

<span data-ttu-id="6ecf6-151">Ayrıca, içerik görünümü sayfası listeleme 2 normal açılış ve kapanış HTML etiketleri herhangi birini içermediğinden emin dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-151">Notice, furthermore, that the content view page in Listing 2 does not contain any of the normal opening and closing HTML tags.</span></span> <span data-ttu-id="6ecf6-152">Örneğin, bu açılış ve kapanış içermiyor `<html>` veya `<head>` etiketler.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-152">For example, it does not contain the opening and closing `<html>` or `<head>` tags.</span></span> <span data-ttu-id="6ecf6-153">Normal açılış ve kapanış etiketlerinin tümünün görünüm ana sayfada yer alır.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-153">All of the normal opening and closing tags are contained in the view master page.</span></span>

<span data-ttu-id="6ecf6-154">Bir görünüm içerik sayfası görüntülemek istediğiniz herhangi bir içerik içinde yerleştirilmelidir bir `<asp:Content>` etiketi.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-154">Any content that you want to display in a view content page must be placed within a `<asp:Content>` tag.</span></span> <span data-ttu-id="6ecf6-155">Herhangi bir HTML veya bu etiketleri dışında diğer içerik yerleştirirseniz, sayfayı görüntülemeye çalıştığınızda bir hata alırsınız.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-155">If you place any HTML or other content outside of these tags, then you will get an error when you attempt to view the page.</span></span>

<span data-ttu-id="6ecf6-156">Geçersiz kılma gerekmez her `<asp:ContentPlaceHolder>` bir ana sayfa içerik görünümü sayfasında etiketi.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-156">You don't need to override every `<asp:ContentPlaceHolder>` tag from a master page in a content view page.</span></span> <span data-ttu-id="6ecf6-157">Yalnızca geçersiz kılmak gereken bir `<asp:ContentPlaceHolder>` etiketi ile belirli bir içeriğe etiket değiştirmek istediğinizde.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-157">You only need to override a `<asp:ContentPlaceHolder>` tag when you want to replace the tag with particular content.</span></span>

<span data-ttu-id="6ecf6-158">Örneğin, yalnızca iki listeleme 3'te değiştirilmiş Index görünümünü içerir `<asp:Content>` etiketler.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-158">For example, the modified Index view in Listing 3 contains only two `<asp:Content>` tags.</span></span> <span data-ttu-id="6ecf6-159">Her biri `<asp:Content>` etiketleri, bazı metinleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-159">Each of the `<asp:Content>` tags includes some text.</span></span>

<span data-ttu-id="6ecf6-160">**Kod 3 – `Views\Home\Index.aspx (modified)`**</span><span class="sxs-lookup"><span data-stu-id="6ecf6-160">**Listing 3 – `Views\Home\Index.aspx (modified)`**</span></span>

[!code-aspx[Main](creating-page-layouts-with-view-master-pages-vb/samples/sample3.aspx)]

<span data-ttu-id="6ecf6-161">3 liste görünümünde istendiğinde, Şekil 5'te sayfasını işler.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-161">When the view in Listing 3 is requested, it renders the page in Figure 5.</span></span> <span data-ttu-id="6ecf6-162">Görünüm iki sütuna sahip bir sayfa işler dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-162">Notice that the view renders a page with two columns.</span></span> <span data-ttu-id="6ecf6-163">Ayrıca, içerik görünümü içerik sayfasından ana görünüm sayfası içerikle birleştirilir dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-163">Notice, furthermore, that the content from the view content page is merged with the content from the view master page.</span></span>


<span data-ttu-id="6ecf6-164">[![Dizin görünüm içerik sayfası](creating-page-layouts-with-view-master-pages-vb/_static/image14.png)](creating-page-layouts-with-view-master-pages-vb/_static/image13.png)</span><span class="sxs-lookup"><span data-stu-id="6ecf6-164">[![The Index view content page](creating-page-layouts-with-view-master-pages-vb/_static/image14.png)](creating-page-layouts-with-view-master-pages-vb/_static/image13.png)</span></span>

<span data-ttu-id="6ecf6-165">**Şekil 05**: Dizin görünüm içerik sayfası ([tam boyutlu görüntüyü görmek için tıklatın](creating-page-layouts-with-view-master-pages-vb/_static/image15.png))</span><span class="sxs-lookup"><span data-stu-id="6ecf6-165">**Figure 05**: The Index view content page ([Click to view full-size image](creating-page-layouts-with-view-master-pages-vb/_static/image15.png))</span></span>


### <a name="modifying-view-master-page-content"></a><span data-ttu-id="6ecf6-166">Görünüm ana sayfa içeriğini değiştirme</span><span class="sxs-lookup"><span data-stu-id="6ecf6-166">Modifying View Master Page Content</span></span>

<span data-ttu-id="6ecf6-167">Neredeyse karşılaştığınız bir sorun, farklı bir görünüm içerik sayfalarını istendiğinde görünüm ana sayfa içeriği değiştirme sorununu hemen görünüm ana sayfalarıyla çalışırken.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-167">One issue that you encounter almost immediately when working with view master pages is the problem of modifying view master page content when different view content pages are requested.</span></span> <span data-ttu-id="6ecf6-168">Örneğin, her sayfada web uygulamanıza benzersiz bir başlık olmasını istersiniz.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-168">For example, you want each page in your web application to have a unique title.</span></span> <span data-ttu-id="6ecf6-169">Ancak, ana sayfa görünümü ve görünüm içerik sayfası başlığı bildirilir.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-169">However, the title is declared in the view master page and not in the view content page.</span></span> <span data-ttu-id="6ecf6-170">Bu nedenle, nasıl sayfa başlığının her görünüm içerik sayfası için özelleştirdiğiniz?</span><span class="sxs-lookup"><span data-stu-id="6ecf6-170">So, how do you customize the page title for each view content page?</span></span>

<span data-ttu-id="6ecf6-171">Görünüm içerik sayfası tarafından gördüğü başlık değiştirebileceğiniz iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-171">There are two ways that you can modify the title displayed by a view content page.</span></span> <span data-ttu-id="6ecf6-172">İlk olarak, bir sayfa başlığı başlık özniteliğiyle atayabilirsiniz `<%@ page %>` yönergesi bildirilen bir görünüm içerik sayfası üstünde.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-172">First, you can assign a page title to the title attribute of the `<%@ page %>` directive declared at the top of a view content page.</span></span> <span data-ttu-id="6ecf6-173">Örneğin, dizin görünümü sayfa başlığı "Süper harika Web sitesi" atamak istiyorsanız, aşağıdaki yönerge Index görünümünü üst kısmındaki şunları içerebilir:</span><span class="sxs-lookup"><span data-stu-id="6ecf6-173">For example, if you want to assign the page title "Super Great Website" to the Index view, then you can include the following directive at the top of the Index view:</span></span>

[!code-aspx[Main](creating-page-layouts-with-view-master-pages-vb/samples/sample4.aspx)]

<span data-ttu-id="6ecf6-174">Dizin görünümünün tarayıcıya işlendiğinde, istenen başlık tarayıcının başlık çubuğunda görünür:</span><span class="sxs-lookup"><span data-stu-id="6ecf6-174">When the Index view is rendered to the browser, the desired title appears in the browser title bar:</span></span>


<span data-ttu-id="6ecf6-175">[![Tarayıcının başlık çubuğu](creating-page-layouts-with-view-master-pages-vb/_static/image17.png)](creating-page-layouts-with-view-master-pages-vb/_static/image16.png)</span><span class="sxs-lookup"><span data-stu-id="6ecf6-175">[![Browser title bar](creating-page-layouts-with-view-master-pages-vb/_static/image17.png)](creating-page-layouts-with-view-master-pages-vb/_static/image16.png)</span></span>


<span data-ttu-id="6ecf6-176">Bir ana görünüm sayfası, sırayla çalışmak üzere title özniteliği için karşılaması gereken önemli bir gereksinim yoktur.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-176">There is one important requirement that a master view page must satisfy in order for the title attribute to work.</span></span> <span data-ttu-id="6ecf6-177">Görünüm ana sayfası içermelidir bir `<head runat="server">` yerine normal bir etiket `<head>` üstbilgisi etiketi.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-177">The view master page must contain a `<head runat="server">` tag instead of a normal `<head>` tag for its header.</span></span> <span data-ttu-id="6ecf6-178">Varsa `<head>` etiketi runat içermez başlığı görünmez sonra = "server" özniteliği.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-178">If the `<head>` tag does not include the runat="server" attribute then the title won't appear.</span></span> <span data-ttu-id="6ecf6-179">Ana sayfa içerir gerekli varsayılan görünüm `<head runat="server">` etiketi.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-179">The default view master page includes the required `<head runat="server">` tag.</span></span>

<span data-ttu-id="6ecf6-180">Tek görünüm içerik sayfasından ana sayfa içeriği değiştirme için alternatif bir yaklaşım sarmaktır değiştirmek için istediğiniz bölgede bir `<asp:ContentPlaceHolder>` etiketi.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-180">An alternative approach to modifying master page content from an individual view content page is to wrap the region that you want to modify in a `<asp:ContentPlaceHolder>` tag.</span></span> <span data-ttu-id="6ecf6-181">Örneğin, yalnızca başlığı, aynı zamanda bir ana görünüm sayfası tarafından oluşturulan meta etiketleri değiştirmek istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-181">For example, imagine that you want to change not only the title, but also the meta tags, rendered by a master view page.</span></span> <span data-ttu-id="6ecf6-182">Ana görünüm sayfası 4 listesi içeren bir `<asp:ContentPlaceHolder>` içinde etiketi kendi `<head>` etiketi.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-182">The master view page in Listing 4 contains a `<asp:ContentPlaceHolder>` tag within its `<head>` tag.</span></span>

<span data-ttu-id="6ecf6-183">**4 listeleme – `Views\Shared\Site2.master`**</span><span class="sxs-lookup"><span data-stu-id="6ecf6-183">**Listing 4 – `Views\Shared\Site2.master`**</span></span>

[!code-aspx[Main](creating-page-layouts-with-view-master-pages-vb/samples/sample5.aspx)]

<span data-ttu-id="6ecf6-184">Dikkat `<asp:ContentPlaceHolder>` listeleme 4'te etiketi varsayılan içerik içerir: varsayılan başlık ve varsayılan meta etiketler.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-184">Notice that the `<asp:ContentPlaceHolder>` tag in Listing 4 includes default content: a default title and default meta tags.</span></span> <span data-ttu-id="6ecf6-185">Bu geçersiz kılmazsanız `<asp:ContentPlaceHolder>` varsayılan içerik görüntülenecek sonra tek tek görünüm içerik sayfası etiketleyin.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-185">If you don't override this `<asp:ContentPlaceHolder>` tag in an individual view content page, then the default content will be displayed.</span></span>

<span data-ttu-id="6ecf6-186">Geçersiz kılmaları listeleme 5'teki içerik görünümü sayfası `<asp:ContentPlaceHolder>` özel bir başlık ve özel meta etiketler görüntülemek için etiket.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-186">The content view page in Listing 5 overrides the `<asp:ContentPlaceHolder>` tag in order to display a custom title and custom meta tags.</span></span>

<span data-ttu-id="6ecf6-187">**5 listeleme – `Views\Home\Index2.aspx`**</span><span class="sxs-lookup"><span data-stu-id="6ecf6-187">**Listing 5 – `Views\Home\Index2.aspx`**</span></span>

[!code-aspx[Main](creating-page-layouts-with-view-master-pages-vb/samples/sample6.aspx)]

### <a name="summary"></a><span data-ttu-id="6ecf6-188">Özet</span><span class="sxs-lookup"><span data-stu-id="6ecf6-188">Summary</span></span>

<span data-ttu-id="6ecf6-189">Bu öğreticide, ana sayfalar ve içerik sayfalarını görüntülemek için temel bir giriş sağlanan.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-189">This tutorial provided you with a basic introduction to view master pages and view content pages.</span></span> <span data-ttu-id="6ecf6-190">Ana sayfalar yeni görünüm oluşturma ve bunları temel alan içerik sayfalarını görüntüleme oluşturmayı öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-190">You learned how to create new view master pages and create view content pages based on them.</span></span> <span data-ttu-id="6ecf6-191">Ayrıca belirli görünüm içerik sayfası görünüm ana sayfadan içerik nasıl değiştirebileceğiniz incelenir.</span><span class="sxs-lookup"><span data-stu-id="6ecf6-191">We also examined how you can modify the content of a view master page from a particular view content page.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="6ecf6-192">[Önceki](using-the-tagbuilder-class-to-build-html-helpers-vb.md)
> [İleri](passing-data-to-view-master-pages-vb.md)</span><span class="sxs-lookup"><span data-stu-id="6ecf6-192">[Previous](using-the-tagbuilder-class-to-build-html-helpers-vb.md)
[Next](passing-data-to-view-master-pages-vb.md)</span></span>