---
uid: web-api/overview/data/using-web-api-with-entity-framework/part-6
title: JavaScript istemcisini oluşturma | Microsoft Docs
author: MikeWasson
description: ''
ms.author: riande
ms.date: 06/16/2014
ms.assetid: 20360326-b123-4b1e-abae-1d350edf4ce4
msc.legacyurl: /web-api/overview/data/using-web-api-with-entity-framework/part-6
msc.type: authoredcontent
ms.openlocfilehash: b5cb4d93c30ef80a48da48ffc51dd51411b1d0d0
ms.sourcegitcommit: 24b1f6decbb17bb22a45166e5fdb0845c65af498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57075921"
---
<a name="create-the-javascript-client"></a><span data-ttu-id="81014-102">JavaScript İstemcisini Oluşturma</span><span class="sxs-lookup"><span data-stu-id="81014-102">Create the JavaScript Client</span></span>
====================
<span data-ttu-id="81014-103">tarafından [Mike Wasson](https://github.com/MikeWasson)</span><span class="sxs-lookup"><span data-stu-id="81014-103">by [Mike Wasson](https://github.com/MikeWasson)</span></span>

[<span data-ttu-id="81014-104">Projeyi yükle</span><span class="sxs-lookup"><span data-stu-id="81014-104">Download Completed Project</span></span>](https://github.com/MikeWasson/BookService)

<span data-ttu-id="81014-105">Bu bölümde, HTML, JavaScript kullanarak istemci uygulaması oluşturacak ve [Knockout.js](http://knockoutjs.com/) kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="81014-105">In this section, you will create the client for the application, using HTML, JavaScript, and the [Knockout.js](http://knockoutjs.com/) library.</span></span> <span data-ttu-id="81014-106">Aşamalar halinde istemci uygulaması oluşturacağız:</span><span class="sxs-lookup"><span data-stu-id="81014-106">We'll build the client app in stages:</span></span>

- <span data-ttu-id="81014-107">Kitap listesi gösteriliyor.</span><span class="sxs-lookup"><span data-stu-id="81014-107">Showing a list of books.</span></span>
- <span data-ttu-id="81014-108">Bir kitap ayrıntı gösteriliyor.</span><span class="sxs-lookup"><span data-stu-id="81014-108">Showing a book detail.</span></span>
- <span data-ttu-id="81014-109">Yeni bir kitap ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="81014-109">Adding a new book.</span></span>

<span data-ttu-id="81014-110">Knockout kitaplığı, Model-View-ViewModel (MVVM) desenini kullanır:</span><span class="sxs-lookup"><span data-stu-id="81014-110">The Knockout library uses the Model-View-ViewModel (MVVM) pattern:</span></span>

- <span data-ttu-id="81014-111">**Modeli** iş etki alanında (bizim çalışması, kitaplar ve yazarlar) verileri sunucu tarafı gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="81014-111">The **model** is the server-side representation of the data in the business domain (in our case, books and authors).</span></span>
- <span data-ttu-id="81014-112">**Görünümü** sunu katmanı (HTML).</span><span class="sxs-lookup"><span data-stu-id="81014-112">The **view** is the presentation layer (HTML).</span></span>
- <span data-ttu-id="81014-113">**Görünüm modeli** modelleri tutan bir JavaScript nesnesi.</span><span class="sxs-lookup"><span data-stu-id="81014-113">The **view model** is a JavaScript object that holds the models.</span></span> <span data-ttu-id="81014-114">Görünüm modeli, kullanıcı arabiriminin bir kod soyutlamadır.</span><span class="sxs-lookup"><span data-stu-id="81014-114">The view model is a code abstraction of the UI.</span></span> <span data-ttu-id="81014-115">HTML gösteriminin bilgisi var.</span><span class="sxs-lookup"><span data-stu-id="81014-115">It has no knowledge of the HTML representation.</span></span> <span data-ttu-id="81014-116">Bunun yerine, görünümün soyut özellikler gibi temsil ettiği &quot;kitap listesi&quot;.</span><span class="sxs-lookup"><span data-stu-id="81014-116">Instead, it represents abstract features of the view, such as &quot;a list of books&quot;.</span></span>

<span data-ttu-id="81014-117">Görünüm veri görünüm modeline bağlı.</span><span class="sxs-lookup"><span data-stu-id="81014-117">The view is data-bound to the view model.</span></span> <span data-ttu-id="81014-118">Görünüm modeli güncelleştirmeler Görünümü'nde otomatik olarak yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="81014-118">Updates to the view model are automatically reflected in the view.</span></span> <span data-ttu-id="81014-119">Düğmesine tıklar gibi görünüm modeli olayları da görünümden alır.</span><span class="sxs-lookup"><span data-stu-id="81014-119">The view model also gets events from the view, such as button clicks.</span></span>

![](part-6/_static/image1.png)

<span data-ttu-id="81014-120">Herhangi bir kodu yeniden yazma olmadan bağlamaları değiştirebilirsiniz çünkü bu yaklaşım, uygulamanızın kullanıcı Arabirimi ve düzeni değiştirmek kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="81014-120">This approach makes it easy to change the layout and UI of your app, because you can change the bindings, without rewriting any code.</span></span> <span data-ttu-id="81014-121">Örneğin, bir liste öğesi gösterebilir bir `<ul>`, daha sonra tabloya değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="81014-121">For example, you might show a list of items as a `<ul>`, then change it later to a table.</span></span>

## <a name="add-the-knockout-library"></a><span data-ttu-id="81014-122">Knockout kitaplığı Ekle</span><span class="sxs-lookup"><span data-stu-id="81014-122">Add the Knockout Library</span></span>

<span data-ttu-id="81014-123">Visual Studio'da gelen **Araçları** menüsünde **NuGet Paket Yöneticisi**.</span><span class="sxs-lookup"><span data-stu-id="81014-123">In Visual Studio, from the **Tools** menu, select **NuGet Package Manager**.</span></span> <span data-ttu-id="81014-124">Ardından **Paket Yöneticisi Konsolu**.</span><span class="sxs-lookup"><span data-stu-id="81014-124">Then select **Package Manager Console**.</span></span> <span data-ttu-id="81014-125">Paket Yöneticisi konsolu penceresinde, aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="81014-125">In the Package Manager Console window, enter the following command:</span></span>

[!code-console[Main](part-6/samples/sample1.cmd)]

<span data-ttu-id="81014-126">Bu komut, Knockout dosyaları Scripts klasörü olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="81014-126">This command adds the Knockout files to the Scripts folder.</span></span>

## <a name="create-the-view-model"></a><span data-ttu-id="81014-127">Görünüm modeli oluşturun</span><span class="sxs-lookup"><span data-stu-id="81014-127">Create the View Model</span></span>

<span data-ttu-id="81014-128">Betikler klasörüne App.js adlı bir JavaScript dosyası ekleyin.</span><span class="sxs-lookup"><span data-stu-id="81014-128">Add a JavaScript file named app.js to the Scripts folder.</span></span> <span data-ttu-id="81014-129">(Çözüm Gezgini'nde betikler klasörüne sağ tıklayın, **Ekle**, ardından **JavaScript dosyası**.) Aşağıdaki kodu yapıştırın:</span><span class="sxs-lookup"><span data-stu-id="81014-129">(In Solution Explorer, right-click the Scripts folder, select **Add**, then select **JavaScript File**.) Paste in the following code:</span></span>

[!code-javascript[Main](part-6/samples/sample2.js)]

<span data-ttu-id="81014-130">Knockout içinde `observable` sınıfı, veri bağlama sağlar.</span><span class="sxs-lookup"><span data-stu-id="81014-130">In Knockout, the `observable` class enables data-binding.</span></span> <span data-ttu-id="81014-131">Observable içeriğini değiştirdiğinizde, kendisini güncelleştirmek için gözlemlenebilir tüm verilere bağlı denetimleri bildirir.</span><span class="sxs-lookup"><span data-stu-id="81014-131">When the contents of an observable change, the observable notifies all of the data-bound controls, so they can update themselves.</span></span> <span data-ttu-id="81014-132">( `observableArray` Sınıfı, dizisi sürümü *observable*.) İle başlamak görünümü modelimizi, iki gözlemlenenler sahiptir:</span><span class="sxs-lookup"><span data-stu-id="81014-132">(The `observableArray` class is the array version of *observable*.) To start with, our view model has two observables:</span></span>

- <span data-ttu-id="81014-133">`books` kitap listesi içerir.</span><span class="sxs-lookup"><span data-stu-id="81014-133">`books` holds the list of books.</span></span>
- <span data-ttu-id="81014-134">`error` AJAX çağrısı başarısız olursa bir hata iletisi içerir.</span><span class="sxs-lookup"><span data-stu-id="81014-134">`error` contains an error message if an AJAX call fails.</span></span>

<span data-ttu-id="81014-135">`getAllBooks` Yöntemi books listesini almak için bir AJAX çağrısı yapar.</span><span class="sxs-lookup"><span data-stu-id="81014-135">The `getAllBooks` method makes an AJAX call to get the list of books.</span></span> <span data-ttu-id="81014-136">Sonucu üzerine gönderim sonra `books` dizisi.</span><span class="sxs-lookup"><span data-stu-id="81014-136">Then it pushes the result onto the `books` array.</span></span>

<span data-ttu-id="81014-137">`ko.applyBindings` Yöntemi Knockout Kitaplığı'nın bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="81014-137">The `ko.applyBindings` method is part of the Knockout library.</span></span> <span data-ttu-id="81014-138">Bu görünüm modeli parametre olarak alır ve veri bağlamasını ayarlamak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="81014-138">It takes the view model as a parameter and sets up the data binding.</span></span>

## <a name="add-a-script-bundle"></a><span data-ttu-id="81014-139">Betik paketi ekleme</span><span class="sxs-lookup"><span data-stu-id="81014-139">Add a Script Bundle</span></span>

<span data-ttu-id="81014-140">Paketleme, birleştirme veya birden çok dosyayı tek bir dosyada paket kolaylaştırır ASP.NET 4.5 özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="81014-140">Bundling is a feature in ASP.NET 4.5 that makes it easy to combine or bundle multiple files into a single file.</span></span> <span data-ttu-id="81014-141">Paketleme sayfa yükleme süresi iyileştirebilen sunucuya istek sayısını azaltır.</span><span class="sxs-lookup"><span data-stu-id="81014-141">Bundling reduces the number of requests to the server, which can improve page load time.</span></span>

<span data-ttu-id="81014-142">Uygulama dosyasını açın\_Start/BundleConfig.cs.</span><span class="sxs-lookup"><span data-stu-id="81014-142">Open the file App\_Start/BundleConfig.cs.</span></span> <span data-ttu-id="81014-143">RegisterBundles yöntemine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="81014-143">Add the following code to the RegisterBundles method.</span></span>

[!code-csharp[Main](part-6/samples/sample3.cs)]

> [!div class="step-by-step"]
> <span data-ttu-id="81014-144">[Önceki](part-5.md)
> [İleri](part-7.md)</span><span class="sxs-lookup"><span data-stu-id="81014-144">[Previous](part-5.md)
[Next](part-7.md)</span></span>