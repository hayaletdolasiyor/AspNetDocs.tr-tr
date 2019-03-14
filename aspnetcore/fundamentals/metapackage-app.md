---
title: Microsoft.AspNetCore.App metapackage ASP.NET Core 2.1 ve üzeri
author: Rick-Anderson
description: Microsoft.AspNetCore.App metapackage desteklenen tüm ASP.NET Core ve Entity Framework Core paketleri içerir.
monikerRange: '>= aspnetcore-2.1'
ms.author: riande
ms.date: 09/20/2017
uid: fundamentals/metapackage-app
ms.openlocfilehash: 68b5aca60273a8c6ef03c0a29842e6a5305adeb3
ms.sourcegitcommit: 24b1f6decbb17bb22a45166e5fdb0845c65af498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57068952"
---
# <a name="microsoftaspnetcoreapp-metapackage-for-aspnet-core-21"></a><span data-ttu-id="9d610-103">ASP.NET Core 2.1 için Microsoft.AspNetCore.App metapackage</span><span class="sxs-lookup"><span data-stu-id="9d610-103">Microsoft.AspNetCore.App metapackage for ASP.NET Core 2.1</span></span>

<span data-ttu-id="9d610-104">Bu özellik, ASP.NET Core 2.1 ve üzeri hedefleyen .NET Core 2.1 ve üzeri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9d610-104">This feature requires ASP.NET Core 2.1 and later targeting .NET Core 2.1 and later.</span></span>

<span data-ttu-id="9d610-105">[Microsoft.AspNetCore.App](https://www.nuget.org/packages/Microsoft.AspNetCore.App) [metapackage](/dotnet/core/packages#metapackages) ASP.NET Core için:</span><span class="sxs-lookup"><span data-stu-id="9d610-105">The [Microsoft.AspNetCore.App](https://www.nuget.org/packages/Microsoft.AspNetCore.App) [metapackage](/dotnet/core/packages#metapackages) for ASP.NET Core:</span></span>

* <span data-ttu-id="9d610-106">Üçüncü taraf bağımlılıklarının dışında içermez [Json.NET](https://www.nuget.org/packages/Newtonsoft.Json/), [Remotion.Linq](https://www.nuget.org/packages/Remotion.Linq/), ve [IX zaman uyumsuz](https://www.nuget.org/packages/System.Interactive.Async/).</span><span class="sxs-lookup"><span data-stu-id="9d610-106">Does not include third-party dependencies except for [Json.NET](https://www.nuget.org/packages/Newtonsoft.Json/), [Remotion.Linq](https://www.nuget.org/packages/Remotion.Linq/), and [IX-Async](https://www.nuget.org/packages/System.Interactive.Async/).</span></span> <span data-ttu-id="9d610-107">Bu 3. taraf bağımlılıkları, ana çerçeveler özellikleri işlevi sağlamak için gerekli sayılan.</span><span class="sxs-lookup"><span data-stu-id="9d610-107">These 3rd-party dependencies are deemed necessary to ensure the major frameworks features function.</span></span>
* <span data-ttu-id="9d610-108">Üçüncü taraf bağımlılıkları (dışında daha önce bahsedilenler) içeren hariç ASP.NET Core ekibi tarafından desteklenen tüm paketleri içerir.</span><span class="sxs-lookup"><span data-stu-id="9d610-108">Includes all supported packages by the ASP.NET Core team except those that contain third-party dependencies (other than those previously mentioned).</span></span>
* <span data-ttu-id="9d610-109">Üçüncü taraf bağımlılıkları (dışında daha önce bahsedilenler) içeren hariç Entity Framework Core ekibi tarafından desteklenen tüm paketleri içerir.</span><span class="sxs-lookup"><span data-stu-id="9d610-109">Includes all supported packages by the Entity Framework Core team except those that contain third-party dependencies (other than those previously mentioned).</span></span>

<span data-ttu-id="9d610-110">Tüm özellikleri ASP.NET Core 2.1 ve üzeri ve Entity Framework Core 2.1 ve üzeri dahil edilen `Microsoft.AspNetCore.App` paket.</span><span class="sxs-lookup"><span data-stu-id="9d610-110">All the features of ASP.NET Core 2.1 and later and Entity Framework Core 2.1 and later are included in the `Microsoft.AspNetCore.App` package.</span></span> <span data-ttu-id="9d610-111">Varsayılan proje şablonları ASP.NET Core 2.1 hedefleme ve daha sonra bu paketi kullanın.</span><span class="sxs-lookup"><span data-stu-id="9d610-111">The default project templates targeting ASP.NET Core 2.1 and later use this package.</span></span> <span data-ttu-id="9d610-112">ASP.NET Core 2.1 ve üzeri ve Entity Framework Core 2.1 hedefleyen uygulamalar önerilir ve daha sonra `Microsoft.AspNetCore.App` paket.</span><span class="sxs-lookup"><span data-stu-id="9d610-112">We recommend applications targeting ASP.NET Core 2.1 and later and Entity Framework Core 2.1 and later use the `Microsoft.AspNetCore.App` package.</span></span>

<span data-ttu-id="9d610-113">Sürüm numarasını `Microsoft.AspNetCore.App` metapackage sürümü Entity Framework Core ve ASP.NET Core sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9d610-113">The version number of the `Microsoft.AspNetCore.App` metapackage represents the ASP.NET Core version and Entity Framework Core version.</span></span>

<span data-ttu-id="9d610-114">Kullanarak `Microsoft.AspNetCore.App` metapackage uygulamanızı korumak sürüm kısıtlamaları sağlar:</span><span class="sxs-lookup"><span data-stu-id="9d610-114">Using the `Microsoft.AspNetCore.App` metapackage provides version restrictions that protect your app:</span></span>

* <span data-ttu-id="9d610-115">Bir paket eklenirse, bağımlıdır geçişli (doğrudan değil) bir paket içinde `Microsoft.AspNetCore.App`ve bu sürüm numaraları farklılık gösterir, NuGet bir hata üretir.</span><span class="sxs-lookup"><span data-stu-id="9d610-115">If a package is included that has a transitive (not direct) dependency on a package in `Microsoft.AspNetCore.App`, and those version numbers differ, NuGet will generate an error.</span></span>
* <span data-ttu-id="9d610-116">Uygulamanıza eklediğiniz diğer paketleri dahil paketleri sürümünü değiştiremezsiniz `Microsoft.AspNetCore.App`.</span><span class="sxs-lookup"><span data-stu-id="9d610-116">Other packages added to your app cannot change the version of packages included in `Microsoft.AspNetCore.App`.</span></span>
* <span data-ttu-id="9d610-117">Sürüm tutarlılık, güvenilir bir deneyim sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d610-117">Version consistency ensures a reliable experience.</span></span> <span data-ttu-id="9d610-118">`Microsoft.AspNetCore.App` ilgili BITS birlikte aynı uygulamada kullanılan test edilmemiş sürümü bileşimleri önlemek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9d610-118">`Microsoft.AspNetCore.App` was designed to prevent untested version combinations of related bits being used together in the same app.</span></span>

<span data-ttu-id="9d610-119">Kullanan uygulamalar `Microsoft.AspNetCore.App` metapackage otomatik olarak ASP.NET Core paylaşılan çerçeve avantajlarından yararlanın.</span><span class="sxs-lookup"><span data-stu-id="9d610-119">Applications that use the `Microsoft.AspNetCore.App` metapackage automatically take advantage of the ASP.NET Core shared framework.</span></span> <span data-ttu-id="9d610-120">Kullanırken `Microsoft.AspNetCore.App` metapackage, **hiçbir** başvurulan bir ASP.NET Core NuGet paket varlıklarından uygulamayla dağıtılan&mdash;ASP.NET Core paylaşılan çerçeve bu varlıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="9d610-120">When you use the `Microsoft.AspNetCore.App` metapackage, **no** assets from the referenced ASP.NET Core NuGet packages are deployed with the application&mdash;the ASP.NET Core shared framework contains these assets.</span></span> <span data-ttu-id="9d610-121">Uygulama başlatma süresini kısaltmak için paylaşılan çerçevesindeki varlıkları önceden derlenmiş.</span><span class="sxs-lookup"><span data-stu-id="9d610-121">The assets in the shared framework are precompiled to improve application startup time.</span></span> <span data-ttu-id="9d610-122">Daha fazla bilgi için bkz: "paylaşılan çerçeve" [.NET Core dağıtımı paketleme](/dotnet/core/build/distribution-packaging).</span><span class="sxs-lookup"><span data-stu-id="9d610-122">For more information, see "shared framework" in [.NET Core distribution packaging](/dotnet/core/build/distribution-packaging).</span></span>

<span data-ttu-id="9d610-123">Şu proje dosya başvuruları `Microsoft.AspNetCore.App` metapackage ASP.NET Core ve tipik bir ASP.NET Core 2.1 temsil şablonu için:</span><span class="sxs-lookup"><span data-stu-id="9d610-123">The following project file references the `Microsoft.AspNetCore.App` metapackage for ASP.NET Core and represents a typical ASP.NET Core 2.1 template:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.App" />
  </ItemGroup>

</Project>
```

<span data-ttu-id="9d610-124">Önceki biçimlendirme, normal ASP.NET Core 2.1 ve üzeri şablonu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9d610-124">The preceding markup represents a typical ASP.NET Core 2.1 and later template.</span></span> <span data-ttu-id="9d610-125">İçin bir sürüm numarası belirtmeyen `Microsoft.AspNetCore.App` paket başvurusu.</span><span class="sxs-lookup"><span data-stu-id="9d610-125">It doesn't specify a version number for the `Microsoft.AspNetCore.App` package reference.</span></span> <span data-ttu-id="9d610-126">Version belirtilmediğinde, bir [örtük](https://github.com/dotnet/core/blob/master/release-notes/1.0/sdk/1.0-rc3-implicit-package-refs.md) sürümü belirtildi SDK tarafından diğer bir deyişle, `Microsoft.NET.Sdk.Web`.</span><span class="sxs-lookup"><span data-stu-id="9d610-126">When the version is not specified, an [implicit](https://github.com/dotnet/core/blob/master/release-notes/1.0/sdk/1.0-rc3-implicit-package-refs.md) version is specified by the SDK, that is, `Microsoft.NET.Sdk.Web`.</span></span> <span data-ttu-id="9d610-127">SDK'sı tarafından belirtilen sürüm numarası paket başvurusu üzerinde açıkça ayarlamak örtük sürümü güvenmek öneririz.</span><span class="sxs-lookup"><span data-stu-id="9d610-127">We recommend relying on the implicit version specified by the SDK and not explicitly setting the version number on the package reference.</span></span> <span data-ttu-id="9d610-128">Bu yaklaşım hakkında sorularınız varsa, GitHub yorum [Microsoft.AspNetCore.App örtük sürümü için tartışma](https://github.com/aspnet/Docs/issues/6430).</span><span class="sxs-lookup"><span data-stu-id="9d610-128">If you have questions on this approach, leave a GitHub comment at the [Discussion for the Microsoft.AspNetCore.App implicit version](https://github.com/aspnet/Docs/issues/6430).</span></span>

<span data-ttu-id="9d610-129">Örtük sürüm kümesine `major.minor.0` taşınabilir uygulamalar için.</span><span class="sxs-lookup"><span data-stu-id="9d610-129">The implicit version is set to `major.minor.0` for portable apps.</span></span> <span data-ttu-id="9d610-130">Paylaşılan çerçeve sarma mekanizması, uygulama, en son uyumlu sürümü yüklü paylaşılan çerçeveleri arasında çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="9d610-130">The shared framework roll-forward mechanism will run the app on the latest compatible version among the installed shared frameworks.</span></span> <span data-ttu-id="9d610-131">Aynı sürüm, geliştirme, test ve üretim kullanılan sağlamak için paylaşılan framework sürümüyle aynı sürümü, tüm ortamlara yüklenen emin olun.</span><span class="sxs-lookup"><span data-stu-id="9d610-131">To guarantee the same version is used in development, test, and production, ensure the same version of the shared framework is installed in all environments.</span></span> <span data-ttu-id="9d610-132">Kendi uygulamaları'için örtük bir sürüm numarası ayarlanır `major.minor.patch` yüklü SDK'yı paketlenmiş paylaşılan framework'ün.</span><span class="sxs-lookup"><span data-stu-id="9d610-132">For self contained apps, the implicit version number is set to the `major.minor.patch` of the shared framework bundled in the installed SDK.</span></span>

<span data-ttu-id="9d610-133">Sürüm numarasını belirtme `Microsoft.AspNetCore.App` başvuru yapar **değil** paylaşılan sürümünün garanti framework seçilebilir.</span><span class="sxs-lookup"><span data-stu-id="9d610-133">Specifying a version number on the `Microsoft.AspNetCore.App` reference does **not** guarantee that version of the shared framework will be chosen.</span></span> <span data-ttu-id="9d610-134">Örneğin, sürümü "2.1.1" belirtildi, ancak "2.1.3" yüklü olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="9d610-134">For example, suppose version "2.1.1" is specified, but "2.1.3" is installed.</span></span> <span data-ttu-id="9d610-135">Bu durumda, uygulama "2.1.3" kullanır.</span><span class="sxs-lookup"><span data-stu-id="9d610-135">In that case, the app will use "2.1.3".</span></span> <span data-ttu-id="9d610-136">Önerilmemesine rağmen ileri sarma (düzeltme eki ve/veya ikincil) devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d610-136">Although not recommended, you can disable roll forward (patch and/or minor).</span></span> <span data-ttu-id="9d610-137">Dotnet konak sarma ve davranışını yapılandırma hakkında daha fazla bilgi için bkz. [dotnet konak ileri sarma](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/roll-forward-on-no-candidate-fx.md).</span><span class="sxs-lookup"><span data-stu-id="9d610-137">For more information regarding dotnet host roll-forward and how to configure its behavior, see [dotnet host roll forward](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/roll-forward-on-no-candidate-fx.md).</span></span>

<span data-ttu-id="9d610-138">`<Project Sdk` ayarlanmalıdır `Microsoft.NET.Sdk.Web` örtük sürümünü kullanacak şekilde `Microsoft.AspNetCore.App`.</span><span class="sxs-lookup"><span data-stu-id="9d610-138">`<Project Sdk` must be set to `Microsoft.NET.Sdk.Web` to use the implicit version `Microsoft.AspNetCore.App`.</span></span>  <span data-ttu-id="9d610-139">Zaman `<Project Sdk="Microsoft.NET.Sdk">` (sondaki olmadan `.Web`) kullanılır:</span><span class="sxs-lookup"><span data-stu-id="9d610-139">When `<Project Sdk="Microsoft.NET.Sdk">` (without the trailing `.Web`) is used:</span></span>

* <span data-ttu-id="9d610-140">Aşağıdaki uyarısı oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="9d610-140">The following warning is generated:</span></span>

     <span data-ttu-id="9d610-141">*Uyarı NU1604: Proje bağımlılığı Microsoft.AspNetCore.App kapsamlı bir alt sınırı içermiyor. Alt sınır tutarlı geri yükleme sonuçları emin olmak için bağımlılık sürümünü içerir.*</span><span class="sxs-lookup"><span data-stu-id="9d610-141">*Warning NU1604: Project dependency Microsoft.AspNetCore.App does not contain an inclusive lower bound. Include a lower bound in the dependency version to ensure consistent restore results.*</span></span>
* <span data-ttu-id="9d610-142">Bu, .NET Core 2.1 SDK'sı ile bilinen bir sorundur ve .NET Core 2.2 SDK düzeltilecektir.</span><span class="sxs-lookup"><span data-stu-id="9d610-142">This is a known issue with the .NET Core 2.1 SDK and will be fixed in the .NET Core 2.2 SDK.</span></span>

<a name="update"></a>

## <a name="update-aspnet-core"></a><span data-ttu-id="9d610-143">ASP.NET Core güncelleştir</span><span class="sxs-lookup"><span data-stu-id="9d610-143">Update ASP.NET Core</span></span>

<span data-ttu-id="9d610-144">`Microsoft.AspNetCore.App` [Metapackage](/dotnet/core/packages#metapackages) Nuget'ten güncelleştirilir geleneksel bir paket değil.</span><span class="sxs-lookup"><span data-stu-id="9d610-144">The `Microsoft.AspNetCore.App` [metapackage](/dotnet/core/packages#metapackages) isn't a traditional package that's updated from NuGet.</span></span> <span data-ttu-id="9d610-145">Benzer şekilde `Microsoft.NETCore.App`, `Microsoft.AspNetCore.App` NuGet dışında işlenmiş özel sürüm semantiğe sahip bir paylaşılan çalışma zamanı, temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9d610-145">Similar to `Microsoft.NETCore.App`, `Microsoft.AspNetCore.App` represents a shared runtime, which has special versioning semantics handled outside of NuGet.</span></span> <span data-ttu-id="9d610-146">Daha fazla bilgi için [paketler, meta paketler ve çerçeveler](/dotnet/core/packages).</span><span class="sxs-lookup"><span data-stu-id="9d610-146">For more information, see [Packages, metapackages and frameworks](/dotnet/core/packages).</span></span>

<span data-ttu-id="9d610-147">ASP.NET Core güncelleştirmek için:</span><span class="sxs-lookup"><span data-stu-id="9d610-147">To update ASP.NET Core:</span></span>

* <span data-ttu-id="9d610-148">Makineleri geliştirme ve derleme sunucuları: İndirme ve yükleme [.NET Core SDK'sı](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="9d610-148">On development machines and build servers: Download and install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>
* <span data-ttu-id="9d610-149">Dağıtım sunucularında: İndirme ve yükleme [.NET Core çalışma zamanı](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="9d610-149">On deployment servers: Download and install the [.NET Core runtime](https://www.microsoft.com/net/download).</span></span>

 <span data-ttu-id="9d610-150">Uygulamalar için en son yüklenen sürüm uygulama başlatmada İleri dökümünü yapar.</span><span class="sxs-lookup"><span data-stu-id="9d610-150">Applications will roll forward to the latest installed version on application restart.</span></span> <span data-ttu-id="9d610-151">Güncelleştirme gerekli değil `Microsoft.AspNetCore.App` proje dosyasındaki sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="9d610-151">It's not necessary to update the `Microsoft.AspNetCore.App` version number in the project file.</span></span> <span data-ttu-id="9d610-152">Daha fazla bilgi için [Framework bağımlı uygulamaları alma İleri](/dotnet/core/versions/selection#framework-dependent-apps-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="9d610-152">For more information, see [Framework-dependent apps roll forward](/dotnet/core/versions/selection#framework-dependent-apps-roll-forward).</span></span>

<span data-ttu-id="9d610-153">Uygulamanızı daha önce kullandıysanız `Microsoft.AspNetCore.All`, bkz: [Microsoft.AspNetCore.App için Microsoft.AspNetCore.All geçirme](xref:fundamentals/metapackage#migrate).</span><span class="sxs-lookup"><span data-stu-id="9d610-153">If your application previously used `Microsoft.AspNetCore.All`, see [Migrating from Microsoft.AspNetCore.All to Microsoft.AspNetCore.App](xref:fundamentals/metapackage#migrate).</span></span>