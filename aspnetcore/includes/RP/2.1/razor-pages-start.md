---
ms.openlocfilehash: 528dafa1ef39982fde2e11428a74c5c26f341554
ms.sourcegitcommit: 24b1f6decbb17bb22a45166e5fdb0845c65af498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57068718"
---
<span data-ttu-id="13f5e-101">Varsayılan şablon oluşturur **RazorPagesMovie**, **giriş**, **hakkında** ve **kişi** bağlantılar ve sayfalar.</span><span class="sxs-lookup"><span data-stu-id="13f5e-101">The default template creates **RazorPagesMovie**, **Home**, **About** and **Contact** links and pages.</span></span> <span data-ttu-id="13f5e-102">Tarayıcı pencerenizin boyutuna bağlı olarak, bağlantıları göstermek için Gezinti simgesi tıklamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="13f5e-102">Depending on the size of your browser window, you might need to click the navigation icon to show the links.</span></span>

![Giriş ya da dizin sayfası](~/tutorials/razor-pages/razor-pages-start/_static/home2.png)

<span data-ttu-id="13f5e-104">Bağlantıları test edin.</span><span class="sxs-lookup"><span data-stu-id="13f5e-104">Test the links.</span></span> <span data-ttu-id="13f5e-105">**RazorPagesMovie** ve **giriş** bağlantılar dizin sayfasına gider.</span><span class="sxs-lookup"><span data-stu-id="13f5e-105">The **RazorPagesMovie** and **Home** links go to the Index page.</span></span> <span data-ttu-id="13f5e-106">**Hakkında** ve **kişi** bağlantıları Git `About` ve `Contact` sayfaları, sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="13f5e-106">The **About** and **Contact** links go to the `About` and `Contact` pages, respectively.</span></span>

## <a name="project-files-and-folders"></a><span data-ttu-id="13f5e-107">Proje dosyaları ve klasörleri</span><span class="sxs-lookup"><span data-stu-id="13f5e-107">Project files and folders</span></span>

<span data-ttu-id="13f5e-108">Aşağıdaki tabloda, proje klasörleri ve dosyaları listeler.</span><span class="sxs-lookup"><span data-stu-id="13f5e-108">The following table lists the files and folders in the project.</span></span> <span data-ttu-id="13f5e-109">Bu öğretici için *Startup.cs* dosyasıdır anlamak en önemli.</span><span class="sxs-lookup"><span data-stu-id="13f5e-109">For this tutorial, the *Startup.cs* file is the most important to understand.</span></span> <span data-ttu-id="13f5e-110">Aşağıda sağlanan her bir bağlantısını incelemeniz gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="13f5e-110">You don't need to review each link provided below.</span></span> <span data-ttu-id="13f5e-111">Bir dosya veya klasör proje hakkında daha fazla bilgi gerektiğinde bağlantılar bir başvuru olarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="13f5e-111">The links are provided as a reference when you need more information on a file or folder in the project.</span></span>

| <span data-ttu-id="13f5e-112">Dosya veya klasör</span><span class="sxs-lookup"><span data-stu-id="13f5e-112">File or folder</span></span> | <span data-ttu-id="13f5e-113">Amaç</span><span class="sxs-lookup"><span data-stu-id="13f5e-113">Purpose</span></span> |
| -------------- | ------- |
| <span data-ttu-id="13f5e-114">*wwwroot*</span><span class="sxs-lookup"><span data-stu-id="13f5e-114">*wwwroot*</span></span> | <span data-ttu-id="13f5e-115">Statik varlıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="13f5e-115">Contains static assets.</span></span> <span data-ttu-id="13f5e-116">Bkz: [statik dosyalar](xref:fundamentals/static-files).</span><span class="sxs-lookup"><span data-stu-id="13f5e-116">See [Static files](xref:fundamentals/static-files).</span></span> |
| <span data-ttu-id="13f5e-117">*Sayfalar*</span><span class="sxs-lookup"><span data-stu-id="13f5e-117">*Pages*</span></span> | <span data-ttu-id="13f5e-118">Klasör [Razor sayfaları](xref:razor-pages/index).</span><span class="sxs-lookup"><span data-stu-id="13f5e-118">Folder for [Razor Pages](xref:razor-pages/index).</span></span> |
| <span data-ttu-id="13f5e-119">*appsettings.json*</span><span class="sxs-lookup"><span data-stu-id="13f5e-119">*appsettings.json*</span></span> | [<span data-ttu-id="13f5e-120">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="13f5e-120">Configuration</span></span>](xref:fundamentals/configuration/index) |
| <span data-ttu-id="13f5e-121">*Program.cs*</span><span class="sxs-lookup"><span data-stu-id="13f5e-121">*Program.cs*</span></span> | <span data-ttu-id="13f5e-122">Yapılandırır [konak](xref:fundamentals/index#host) ASP.NET Core uygulaması.</span><span class="sxs-lookup"><span data-stu-id="13f5e-122">Configures the [host](xref:fundamentals/index#host) of the ASP.NET Core app.</span></span> |
| <span data-ttu-id="13f5e-123">*Startup.cs*</span><span class="sxs-lookup"><span data-stu-id="13f5e-123">*Startup.cs*</span></span> | <span data-ttu-id="13f5e-124">Hizmetler ve istek ardışık düzenini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="13f5e-124">Configures services and the request pipeline.</span></span> <span data-ttu-id="13f5e-125">Bkz: [başlangıç](xref:fundamentals/startup).</span><span class="sxs-lookup"><span data-stu-id="13f5e-125">See [Startup](xref:fundamentals/startup).</span></span> |

### <a name="the-pagesshared-folder"></a><span data-ttu-id="13f5e-126">Sayfa/paylaşılan klasör</span><span class="sxs-lookup"><span data-stu-id="13f5e-126">The Pages/Shared folder</span></span>

<span data-ttu-id="13f5e-127">*_Layout.cshtml* dosya ortak HTML öğeleri (komut dosyası ve stil sayfası bağlantılar) içerir ve uygulama düzenini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="13f5e-127">The *_Layout.cshtml* file contains common HTML elements (script and stylesheet links) and sets the layout for the app.</span></span> <span data-ttu-id="13f5e-128">Örneğin seçtiğinizde **RazorPagesMovie**, **giriş**, **hakkında** veya **kişi**, öğeler ortak bir dizi Web sayfasında görünür.</span><span class="sxs-lookup"><span data-stu-id="13f5e-128">For example when you select **RazorPagesMovie**, **Home**, **About** or **Contact**, a common set of elements appears in the webpage.</span></span> <span data-ttu-id="13f5e-129">Sık kullanılan öğeleri üstte ve pencerenin alt kısmındaki üst gezinti menüsünde içerir.</span><span class="sxs-lookup"><span data-stu-id="13f5e-129">The common elements include the navigation menu at the top and the header at the bottom of the window.</span></span> <span data-ttu-id="13f5e-130">Daha fazla bilgi için [Düzen](xref:mvc/views/layout).</span><span class="sxs-lookup"><span data-stu-id="13f5e-130">For more information, see [Layout](xref:mvc/views/layout).</span></span>

<span data-ttu-id="13f5e-131">*_ValidationScriptsPartial.cshtml* dosyası bir başvuru sağlar [jQuery](https://jquery.com/) doğrulama komut.</span><span class="sxs-lookup"><span data-stu-id="13f5e-131">The *_ValidationScriptsPartial.cshtml* file provides a reference to [jQuery](https://jquery.com/) validation scripts.</span></span> <span data-ttu-id="13f5e-132">Zaman `Create` ve `Edit` sayfaları öğreticide daha sonra eklenen *_ValidationScriptsPartial.cshtml* dosyası kullanılır.</span><span class="sxs-lookup"><span data-stu-id="13f5e-132">When the `Create` and `Edit` pages are added later in the tutorial, the *_ValidationScriptsPartial.cshtml* file is used.</span></span>

<span data-ttu-id="13f5e-133">*_CookieConsentPartial.cshtml* dosyası bir gezinti çubuğu sağlar ve içerik özetlemek gizlilik ve tanımlama bilgisi İlkesi'ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="13f5e-133">The *_CookieConsentPartial.cshtml* file provides a navigation bar and content to summarize the privacy and cookie use policy.</span></span> <span data-ttu-id="13f5e-134">Projeye dahil GDPR varlıkları hakkında daha fazla bilgi için bkz. [ASP.NET Core AB genel veri koruma yönetmeliği (GDPR) desteği)](xref:security/gdpr).</span><span class="sxs-lookup"><span data-stu-id="13f5e-134">For more information on the GDPR assets included in the project, see [EU General Data Protection Regulation (GDPR) support in ASP.NET Core)](xref:security/gdpr).</span></span>

### <a name="the-pages-folder"></a><span data-ttu-id="13f5e-135">Sayfalar klasöründe</span><span class="sxs-lookup"><span data-stu-id="13f5e-135">The Pages folder</span></span>

<span data-ttu-id="13f5e-136">*_ViewStart.cshtml* Razor sayfaları ayarlar `Layout` kullanılacak özellik *_Layout.cshtml* dosya.</span><span class="sxs-lookup"><span data-stu-id="13f5e-136">The *_ViewStart.cshtml* sets the Razor Pages `Layout` property to use the *_Layout.cshtml* file.</span></span> <span data-ttu-id="13f5e-137">Bkz: [Düzen](xref:mvc/views/layout) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="13f5e-137">See [Layout](xref:mvc/views/layout) for more information.</span></span>

<span data-ttu-id="13f5e-138">*_Viewımports.cshtml* dosyası her bir Razor sayfası alınan Razor yönergeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="13f5e-138">The *_ViewImports.cshtml* file contains Razor directives that are imported into each Razor Page.</span></span> <span data-ttu-id="13f5e-139">Bkz: [paylaşılan yönergeleri alma](xref:mvc/views/layout#importing-shared-directives) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="13f5e-139">See [Importing Shared Directives](xref:mvc/views/layout#importing-shared-directives) for more information.</span></span>

<span data-ttu-id="13f5e-140">`About`, `Contact` Ve `Index` sayfalarıdır temel sayfaları bir uygulamayı başlatmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13f5e-140">The `About`, `Contact` and `Index` pages are basic pages you can use to start an app.</span></span> <span data-ttu-id="13f5e-141">`Error` Sayfası, hata bilgilerini görüntülemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="13f5e-141">The `Error` page is used to display error information.</span></span>