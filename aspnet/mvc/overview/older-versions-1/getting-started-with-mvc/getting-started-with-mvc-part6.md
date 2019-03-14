---
uid: mvc/overview/older-versions-1/getting-started-with-mvc/getting-started-with-mvc-part6
title: Ekleme bir yöntem oluşturma ve oluşturma görünümü | Microsoft Docs
author: shanselman
description: ASP.NET MVC ile ilgili temel bilgileri tanıtan bir başlangıç Öğreticisi budur. Okuyan ve yazan bir veritabanından basit bir web uygulaması oluşturun.
ms.author: riande
ms.date: 08/14/2010
ms.assetid: a3a90963-0286-4fa0-9b3d-c230cc18b0a3
msc.legacyurl: /mvc/overview/older-versions-1/getting-started-with-mvc/getting-started-with-mvc-part6
msc.type: authoredcontent
ms.openlocfilehash: 546c3e0a24ecd0d916c79e9ad12f62b926c760c5
ms.sourcegitcommit: 24b1f6decbb17bb22a45166e5fdb0845c65af498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57072201"
---
<a name="adding-a-create-method-and-create-view"></a><span data-ttu-id="0e428-104">Oluşturma Metodu ve Oluşturma Görünümü Ekleme</span><span class="sxs-lookup"><span data-stu-id="0e428-104">Adding a Create Method and Create View</span></span>
====================
<span data-ttu-id="0e428-105">tarafından [Scott Hanselman](https://github.com/shanselman)</span><span class="sxs-lookup"><span data-stu-id="0e428-105">by [Scott Hanselman](https://github.com/shanselman)</span></span>

> <span data-ttu-id="0e428-106">ASP.NET MVC ile ilgili temel bilgileri tanıtan bir başlangıç Öğreticisi budur.</span><span class="sxs-lookup"><span data-stu-id="0e428-106">This is a beginner tutorial that introduces the basics of ASP.NET MVC.</span></span> <span data-ttu-id="0e428-107">Okuyan ve yazan bir veritabanından basit bir web uygulaması oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="0e428-107">You'll create a simple web application that reads and writes from a database.</span></span> <span data-ttu-id="0e428-108">Ziyaret [ASP.NET MVC eğitim Merkezi](../../../index.md) diğer ASP.NET MVC, öğreticilerimiz ve örneklerimizden bulunacak.</span><span class="sxs-lookup"><span data-stu-id="0e428-108">Visit the [ASP.NET MVC learning center](../../../index.md) to find other ASP.NET MVC tutorials and samples.</span></span>


<span data-ttu-id="0e428-109">Bu bölümde yeni filmler veritabanımızda yer oluşturmak için kullanıcıları etkinleştirmek için gereken destek uygulamak için kullanacağız.</span><span class="sxs-lookup"><span data-stu-id="0e428-109">In this section we are going to implement the support necessary to enable users to create new movies in our database.</span></span> <span data-ttu-id="0e428-110">Biz, filmler/Create URL eylemi uygulayarak yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="0e428-110">We'll do this by implementing the /Movies/Create URL action.</span></span>

<span data-ttu-id="0e428-111">Filmler/Create URL'sini uygulama iki adımlı bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="0e428-111">Implementing the /Movies/Create URL is a two step process.</span></span> <span data-ttu-id="0e428-112">Bir kullanıcı ilk filmler/Create URL'sini ziyaret ettiğinde, yeni bir film girmek için doldurun bir HTML formuna göstermek istiyoruz.</span><span class="sxs-lookup"><span data-stu-id="0e428-112">When a user first visits the /Movies/Create URL we want to show them an HTML form that they can fill out to enter a new movie.</span></span> <span data-ttu-id="0e428-113">Kullanıcı gönderileri sunucuya verileri yedekleyin ve formu gönderdiğinde, ardından, gönderilen içeriği almak ve bizim veritabanına kaydetmek istiyoruz.</span><span class="sxs-lookup"><span data-stu-id="0e428-113">Then, when the user submits the form and posts the data back to the server, we want to retrieve the posted contents and save it into our database.</span></span>

<span data-ttu-id="0e428-114">Biz bizim MoviesController sınıfı içinde iki Create() yöntemler içindeki iki adımları uygulayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="0e428-114">We'll implement these two steps within two Create() methods within our MoviesController class.</span></span> <span data-ttu-id="0e428-115">Bir yöntemi gösterir &lt;form&gt; kullanıcı yeni bir film oluşturmak için doldurun.</span><span class="sxs-lookup"><span data-stu-id="0e428-115">One method will show the &lt;form&gt; that the user should fill out to create a new movie.</span></span> <span data-ttu-id="0e428-116">İkinci yöntem, kullanıcı gönderdiğinde gönderilen verilerin işlenmesi işleyecek &lt;form&gt; tekrar sunucuya ve yeni bir film veritabanımızdaki içinde kaydedin.</span><span class="sxs-lookup"><span data-stu-id="0e428-116">The second method will handle processing the posted data when the user submits the &lt;form&gt; back to the server, and save a new Movie within our database.</span></span>

<span data-ttu-id="0e428-117">Aşağıdaki kodu Bunu uygulamak için sunduğumuz MoviesController sınıf ekleyeceğiz:</span><span class="sxs-lookup"><span data-stu-id="0e428-117">Below is the code we'll add to our MoviesController class to implement this:</span></span>

[!code-csharp[Main](getting-started-with-mvc-part6/samples/sample1.cs)]

<span data-ttu-id="0e428-118">Yukarıdaki kod içinde Denetleyicimizin yapmamız gereken kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="0e428-118">The above code contains all of the code that we'll need within our Controller.</span></span>

<span data-ttu-id="0e428-119">Şimdi bir form kullanıcıya görüntülenecek kullanacağız Görünüm Oluştur şablonu hemen uygulayın.</span><span class="sxs-lookup"><span data-stu-id="0e428-119">Let's now implement the Create View template that we'll use to display a form to the user.</span></span> <span data-ttu-id="0e428-120">Biz ilk oluşturma yönteminde sağ tıklayın ve film formumuzu görünüm şablonu oluşturmak için "Görünüm Ekle"'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="0e428-120">We'll right click in the first Create method and select "Add View" to create the view template for our Movie form.</span></span>

<span data-ttu-id="0e428-121">Biz şablonu görüntüle "Film" geçirmek için Görünüm veri sınıfı gitme ve "Şablon"Oluştur"iskelesini" istediğimizi belirten seçeneğini belirleyeceğiz.</span><span class="sxs-lookup"><span data-stu-id="0e428-121">We'll select that we are going to pass the view template a "Movie" as its view data class, and indicate that we want to "scaffold" a "Create" template.</span></span>

<span data-ttu-id="0e428-122">[![Görünüm Ekle](getting-started-with-mvc-part6/_static/image2.png)](getting-started-with-mvc-part6/_static/image1.png)</span><span class="sxs-lookup"><span data-stu-id="0e428-122">[![Add View](getting-started-with-mvc-part6/_static/image2.png)](getting-started-with-mvc-part6/_static/image1.png)</span></span>

<span data-ttu-id="0e428-123">Ekle düğmesine tıkladıktan sonra \Movies\Create.aspx görünümü şablon sizin için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0e428-123">After you click the Add button, \Movies\Create.aspx View template will be created for you.</span></span> <span data-ttu-id="0e428-124">"Oluştur" "içeriği görüntüleme" açılan listeden seçilmediğinden Görünüm Ekle iletişim kutusu otomatik olarak "bazı varsayılan içerik bizim için iskele kurulmuş".</span><span class="sxs-lookup"><span data-stu-id="0e428-124">Because we selected "Create" from the "view content" dropdown, the Add View dialog automatically "scaffolded" some default content for us.</span></span> <span data-ttu-id="0e428-125">Bir HTML yapı iskelesi oluşturulmuş &lt;form&gt;gitmek için bir alan doğrulama hatası iletileri ve yapı iskelesi filmler hakkında bilmesi olduğundan, etiket ve alanları bizim sınıfın her bir özellik için oluşturulan.</span><span class="sxs-lookup"><span data-stu-id="0e428-125">The scaffolding created an HTML &lt;form&gt;, a place for validation error messages to go, and since scaffolding knows about Movies, it created Label and Fields for each property of our class.</span></span>

[!code-aspx[Main](getting-started-with-mvc-part6/samples/sample2.aspx)]

<span data-ttu-id="0e428-126">Şimdi veritabanımızdaki bir kimliği otomatik olarak bir filmi sağlandığından, bu alanlar, başvuru modeli kaldırın. Bizim Oluştur görünümünün kimliği.</span><span class="sxs-lookup"><span data-stu-id="0e428-126">Since our database automatically gives a Movie an ID, let's remove those fields that reference model.Id from our Create View.</span></span> <span data-ttu-id="0e428-127">Sonra 7 satırları kaldırmak &lt;gösterge&gt;alanları&lt;/legend&gt; biz istemiyorsanız, kimlik alanının gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="0e428-127">Remove the 7 lines after &lt;legend&gt;Fields&lt;/legend&gt; as they show the ID field that we don't want.</span></span>

<span data-ttu-id="0e428-128">Şimdi artık yeni bir film oluşturabilir ve veritabanına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0e428-128">Let's now create a new movie and add it to the database.</span></span> <span data-ttu-id="0e428-129">Biz bunu uygulamayı yeniden çalıştırarak ve ziyaret edin "/ filmler" URL'si ve tıklayın "Oluştur" bağlantısını yeni bir film eklemek için.</span><span class="sxs-lookup"><span data-stu-id="0e428-129">We'll do this by running the application again and visit the "/Movies" URL and click the "Create" link to add a new Movie.</span></span>

<span data-ttu-id="0e428-130">[![Oluştur - Windows Internet Explorer](getting-started-with-mvc-part6/_static/image4.png)](getting-started-with-mvc-part6/_static/image3.png)</span><span class="sxs-lookup"><span data-stu-id="0e428-130">[![Create - Windows Internet Explorer](getting-started-with-mvc-part6/_static/image4.png)](getting-started-with-mvc-part6/_static/image3.png)</span></span>

<span data-ttu-id="0e428-131">Biz Oluştur düğmesine tıkladığınızda, size geri (HTTP POST) oluşturduğumuz /Movies/Create yöntemi için bu formdaki verileri gönderme.</span><span class="sxs-lookup"><span data-stu-id="0e428-131">When we click the Create button, we'll be posting back (via HTTP POST) the data on this form to the /Movies/Create method that we just created.</span></span> <span data-ttu-id="0e428-132">Yalnızca zaman sistem otomatik olarak URL dışında "numTimes" ve "name" parametresi sürdü ve daha önce bir yöntem parametreleri eşlenen gibi sistem otomatik olarak Form alanlarını bir YAYININDAN alın ve bunları bir nesneye eşleyin.</span><span class="sxs-lookup"><span data-stu-id="0e428-132">Just like when the system automatically took the "numTimes" and "name " parameter out of the URL and mapped them to parameters on a method earlier, the system will automatically take the Form Fields from a POST and map them to an object.</span></span> <span data-ttu-id="0e428-133">Bu durumda, "ReleaseDate" ve "Title" gibi HTML alanlarındaki değerleri otomatik olarak bir filmi yeni bir örneğini doğru özelliklerine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0e428-133">In this case, values from fields in HTML like "ReleaseDate" and "Title" will automatically be put into the correct properties of a new instance of a Movie.</span></span>

<span data-ttu-id="0e428-134">İkinci oluşturma yöntemi bizim MoviesController yeniden göz atalım.</span><span class="sxs-lookup"><span data-stu-id="0e428-134">Let's look at the second Create method from our MoviesController again.</span></span> <span data-ttu-id="0e428-135">Bağımsız değişken olarak bir "Film" nesnesini nasıl sürdüğünü dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="0e428-135">Notice how it takes a "Movie" object as an argument:</span></span>

[!code-csharp[Main](getting-started-with-mvc-part6/samples/sample3.cs)]

<span data-ttu-id="0e428-136">Bu film nesne ardından bizim oluşturma eylem yöntemi [HttpPost] sürümüne geçirildi ve veritabanına kaydedilir ve kullanıcı kaydedilen sonuç film listesinde gösteren geri İNDİS() eylem yöntemine yeniden yönlendirildi:</span><span class="sxs-lookup"><span data-stu-id="0e428-136">This Movie object was then passed to the [HttpPost] version of our Create action method, and we saved it in the database and then redirected the user back to the Index() action method which will show the saved result in the movie list:</span></span>

<span data-ttu-id="0e428-137">[![Film listesi - Windows Internet Explorer](getting-started-with-mvc-part6/_static/image6.png)](getting-started-with-mvc-part6/_static/image5.png)</span><span class="sxs-lookup"><span data-stu-id="0e428-137">[![Movie List - Windows Internet Explorer](getting-started-with-mvc-part6/_static/image6.png)](getting-started-with-mvc-part6/_static/image5.png)</span></span>

<span data-ttu-id="0e428-138">Bizim filmler ancak doğru olduğundan ve veritabanının bir filmi başlığı ile kaydetmek bize izin vermiyor denetimi değildir.</span><span class="sxs-lookup"><span data-stu-id="0e428-138">We aren't checking if our movies are correct, though, and the database won't allow us to save a movie with no Title.</span></span> <span data-ttu-id="0e428-139">Biz bir hata oluşturdu, veritabanı önce kullanıcı söyleyebilirsiniz iyi olurdu.</span><span class="sxs-lookup"><span data-stu-id="0e428-139">It'd be nice if we could tell the user that before the database threw an error.</span></span> <span data-ttu-id="0e428-140">Biz bu İleri uygulamamıza doğrulama desteği ekleyerek yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="0e428-140">We'll do this next by adding validation support to our application.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="0e428-141">[Önceki](getting-started-with-mvc-part5.md)
> [İleri](getting-started-with-mvc-part7.md)</span><span class="sxs-lookup"><span data-stu-id="0e428-141">[Previous](getting-started-with-mvc-part5.md)
[Next](getting-started-with-mvc-part7.md)</span></span>