---
title: ASP.NET core'da uygulama başlatma
author: tdykstra
description: ASP.NET core'da başlangıç sınıfı, hizmet ve uygulamaların istek işlem hattı nasıl yapılandırdığını öğrenmek.
monikerRange: '>= aspnetcore-2.1'
ms.author: tdykstra
ms.custom: mvc
ms.date: 01/17/2019
uid: fundamentals/startup
ms.openlocfilehash: cfd0a57d5d0b60862b017a170b6d5cbddf56f15a
ms.sourcegitcommit: 24b1f6decbb17bb22a45166e5fdb0845c65af498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57066222"
---
# <a name="app-startup-in-aspnet-core"></a><span data-ttu-id="49b4e-103">ASP.NET core'da uygulama başlatma</span><span class="sxs-lookup"><span data-stu-id="49b4e-103">App startup in ASP.NET Core</span></span>

<span data-ttu-id="49b4e-104">Tarafından [Tom Dykstra](https://github.com/tdykstra), [Luke Latham](https://github.com/guardrex), ve [Steve Smith](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="49b4e-104">By [Tom Dykstra](https://github.com/tdykstra), [Luke Latham](https://github.com/guardrex), and [Steve Smith](https://ardalis.com)</span></span>

<span data-ttu-id="49b4e-105">`Startup` Sınıfı, hizmetleri ve uygulamanın istek ardışık düzenini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="49b4e-105">The `Startup` class configures services and the app's request pipeline.</span></span>

## <a name="the-startup-class"></a><span data-ttu-id="49b4e-106">Başlangıç sınıfı</span><span class="sxs-lookup"><span data-stu-id="49b4e-106">The Startup class</span></span>

<span data-ttu-id="49b4e-107">ASP.NET Core uygulamaları kullanımı bir `Startup` adlı sınıfı `Startup` kural tarafından.</span><span class="sxs-lookup"><span data-stu-id="49b4e-107">ASP.NET Core apps use a `Startup` class, which is named `Startup` by convention.</span></span> <span data-ttu-id="49b4e-108">`Startup` Sınıfı:</span><span class="sxs-lookup"><span data-stu-id="49b4e-108">The `Startup` class:</span></span>

* <span data-ttu-id="49b4e-109">İsteğe bağlı olarak içeren bir <xref:Microsoft.AspNetCore.Hosting.StartupBase.ConfigureServices*> uygulamanın yapılandırmak için yöntem *Hizmetleri*.</span><span class="sxs-lookup"><span data-stu-id="49b4e-109">Optionally includes a <xref:Microsoft.AspNetCore.Hosting.StartupBase.ConfigureServices*> method to configure the app's *services*.</span></span> <span data-ttu-id="49b4e-110">Uygulama işlevselliği sağlayan bir yeniden kullanılabilir bileşen hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="49b4e-110">A service is a reusable component that provides app functionality.</span></span> <span data-ttu-id="49b4e-111">Hizmetleri yapılandırılmış&mdash;olarak da açıklanan *kayıtlı*&mdash;içinde `ConfigureServices` ve uygulama boyunca tüketilen [bağımlılık ekleme (dı)](xref:fundamentals/dependency-injection) veya <xref:Microsoft.AspNetCore.Builder.IApplicationBuilder.ApplicationServices*>.</span><span class="sxs-lookup"><span data-stu-id="49b4e-111">Services are configured&mdash;also described as *registered*&mdash;in `ConfigureServices` and consumed across the app via [dependency injection (DI)](xref:fundamentals/dependency-injection) or <xref:Microsoft.AspNetCore.Builder.IApplicationBuilder.ApplicationServices*>.</span></span>
* <span data-ttu-id="49b4e-112">İçeren bir <xref:Microsoft.AspNetCore.Hosting.StartupBase.Configure*> uygulamanın istek işleme ardışık düzenini oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="49b4e-112">Includes a <xref:Microsoft.AspNetCore.Hosting.StartupBase.Configure*> method to create the app's request processing pipeline.</span></span>

<span data-ttu-id="49b4e-113">`ConfigureServices` ve `Configure` uygulama başlatıldığında çalışma zamanı tarafından çağrılır:</span><span class="sxs-lookup"><span data-stu-id="49b4e-113">`ConfigureServices` and `Configure` are called by the runtime when the app starts:</span></span>

[!code-csharp[](startup/sample_snapshot/Startup1.cs?highlight=4,10)]

<span data-ttu-id="49b4e-114">`Startup` Sınıfı, uygulamaya belirtilirse, uygulamanın [konak](xref:fundamentals/index#host) oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="49b4e-114">The `Startup` class is specified to the app when the app's [host](xref:fundamentals/index#host) is built.</span></span> <span data-ttu-id="49b4e-115">Konak uygulamanın ne zaman oluşturulmuştur `Build` konak Oluşturucusu'nda üzerinde çağrılır `Program` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="49b4e-115">The app's host is built when `Build` is called on the host builder in the `Program` class.</span></span> <span data-ttu-id="49b4e-116">`Startup` Sınıf genellikle belirtilen çağırarak [WebHostBuilderExtensions.UseStartup\<TStartup >](xref:Microsoft.AspNetCore.Hosting.WebHostBuilderExtensions.UseStartup*) konak Oluşturucu yöntemi:</span><span class="sxs-lookup"><span data-stu-id="49b4e-116">The `Startup` class is usually specified by calling the [WebHostBuilderExtensions.UseStartup\<TStartup>](xref:Microsoft.AspNetCore.Hosting.WebHostBuilderExtensions.UseStartup*) method on the host builder:</span></span>

[!code-csharp[](startup/sample_snapshot/Program3.cs?name=snippet_Program&highlight=10)]

<span data-ttu-id="49b4e-117">Kullanılabilir hizmet ana bilgisayarının sağladığı `Startup` sınıf oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="49b4e-117">The host provides services that are available to the `Startup` class constructor.</span></span> <span data-ttu-id="49b4e-118">Ek hizmetler aracılığıyla uygulamanın eklediği `ConfigureServices`.</span><span class="sxs-lookup"><span data-stu-id="49b4e-118">The app adds additional services via `ConfigureServices`.</span></span> <span data-ttu-id="49b4e-119">Hem konak hem de uygulama hizmetleri ardından kullanılabilir `Configure` ve uygulama boyunca.</span><span class="sxs-lookup"><span data-stu-id="49b4e-119">Both the host and app services are then available in `Configure` and throughout the app.</span></span>

<span data-ttu-id="49b4e-120">Yaygın [bağımlılık ekleme](xref:fundamentals/dependency-injection) içine `Startup` sınıftır eklemesine:</span><span class="sxs-lookup"><span data-stu-id="49b4e-120">A common use of [dependency injection](xref:fundamentals/dependency-injection) into the `Startup` class is to inject:</span></span>

* <span data-ttu-id="49b4e-121"><xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment> ortamı tarafından hizmetleri yapılandırmak için.</span><span class="sxs-lookup"><span data-stu-id="49b4e-121"><xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment> to configure services by environment.</span></span>
* <span data-ttu-id="49b4e-122"><xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> yapılandırması okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="49b4e-122"><xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> to read configuration.</span></span>
* <span data-ttu-id="49b4e-123"><xref:Microsoft.Extensions.Logging.ILoggerFactory> içinde bir Günlükçü oluşturmak için `Startup.ConfigureServices`.</span><span class="sxs-lookup"><span data-stu-id="49b4e-123"><xref:Microsoft.Extensions.Logging.ILoggerFactory> to create a logger in `Startup.ConfigureServices`.</span></span>

[!code-csharp[](startup/sample_snapshot/Startup2.cs?highlight=7-8)]

<span data-ttu-id="49b4e-124">Ekleme alternatif `IHostingEnvironment` kurallarına dayalı bir yaklaşım kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="49b4e-124">An alternative to injecting `IHostingEnvironment` is to use a conventions-based approach.</span></span> <span data-ttu-id="49b4e-125">Ne zaman uygulama tanımlar ayrı `Startup` sınıflar farklı ortamlar için (örneğin, `StartupDevelopment`), uygun `Startup` sınıfı çalışma zamanında seçilen.</span><span class="sxs-lookup"><span data-stu-id="49b4e-125">When the app defines separate `Startup` classes for different environments (for example, `StartupDevelopment`), the appropriate `Startup` class is selected at runtime.</span></span> <span data-ttu-id="49b4e-126">Geçerli ortamı olan adı sonekiyle sınıfı kurtarılmasına öncelik verilir.</span><span class="sxs-lookup"><span data-stu-id="49b4e-126">The class whose name suffix matches the current environment is prioritized.</span></span> <span data-ttu-id="49b4e-127">Uygulama geliştirme ortamında çalıştırılır ve her ikisi de içeren bir `Startup` sınıfı ve `StartupDevelopment` sınıfı `StartupDevelopment` sınıfı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="49b4e-127">If the app is run in the Development environment and includes both a `Startup` class and a `StartupDevelopment` class, the `StartupDevelopment` class is used.</span></span> <span data-ttu-id="49b4e-128">Daha fazla bilgi için [birden fazla ortam kullanayım](xref:fundamentals/environments#environment-based-startup-class-and-methods).</span><span class="sxs-lookup"><span data-stu-id="49b4e-128">For more information, see [Use multiple environments](xref:fundamentals/environments#environment-based-startup-class-and-methods).</span></span>

<span data-ttu-id="49b4e-129">Konak hakkında daha fazla bilgi için bkz. [konak](xref:fundamentals/index#host).</span><span class="sxs-lookup"><span data-stu-id="49b4e-129">To learn more about the host, see [The host](xref:fundamentals/index#host).</span></span> <span data-ttu-id="49b4e-130">Başlatma sırasında hataları işleme hakkında daha fazla bilgi için bkz: [başlangıç özel durum işleme](xref:fundamentals/error-handling#startup-exception-handling).</span><span class="sxs-lookup"><span data-stu-id="49b4e-130">For information on handling errors during startup, see [Startup exception handling](xref:fundamentals/error-handling#startup-exception-handling).</span></span>

## <a name="the-configureservices-method"></a><span data-ttu-id="49b4e-131">Createservicereplicalisteners() yöntemi</span><span class="sxs-lookup"><span data-stu-id="49b4e-131">The ConfigureServices method</span></span>

<span data-ttu-id="49b4e-132"><xref:Microsoft.AspNetCore.Hosting.StartupBase.ConfigureServices*> Yöntemdir:</span><span class="sxs-lookup"><span data-stu-id="49b4e-132">The <xref:Microsoft.AspNetCore.Hosting.StartupBase.ConfigureServices*> method is:</span></span>

* <span data-ttu-id="49b4e-133">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="49b4e-133">Optional.</span></span>
* <span data-ttu-id="49b4e-134">Önce konak tarafından çağrılan `Configure` uygulamanın hizmetlerini yapılandırmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="49b4e-134">Called by the host before the `Configure` method to configure the app's services.</span></span>
* <span data-ttu-id="49b4e-135">Burada [yapılandırma seçenekleri](xref:fundamentals/configuration/index) kurala göre ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="49b4e-135">Where [configuration options](xref:fundamentals/configuration/index) are set by convention.</span></span>

<span data-ttu-id="49b4e-136">Tipik bir düzen tüm çağırmaktır `Add{Service}` yöntemleri ve tüm çağrı `services.Configure{Service}` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="49b4e-136">The typical pattern is to call all the `Add{Service}` methods and then call all of the `services.Configure{Service}` methods.</span></span> <span data-ttu-id="49b4e-137">Örneğin, [yapılandırma kimlik Hizmetleri](xref:security/authentication/identity#pw).</span><span class="sxs-lookup"><span data-stu-id="49b4e-137">For example, see [Configure Identity services](xref:security/authentication/identity#pw).</span></span>

<span data-ttu-id="49b4e-138">Bazı hizmetler önce konak yapılandırabilirsiniz `Startup` yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="49b4e-138">The host may configure some services before `Startup` methods are called.</span></span> <span data-ttu-id="49b4e-139">Daha fazla bilgi için [konak](xref:fundamentals/index#host).</span><span class="sxs-lookup"><span data-stu-id="49b4e-139">For more information, see [The host](xref:fundamentals/index#host).</span></span>

<span data-ttu-id="49b4e-140">Önemli kurulum gerektiren özellikler için vardır `Add{Service}` üzerinde genişletme yöntemleri <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span><span class="sxs-lookup"><span data-stu-id="49b4e-140">For features that require substantial setup, there are `Add{Service}` extension methods on <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="49b4e-141">Tipik bir ASP.NET Core uygulaması için Entity Framework, kimlik ve MVC Hizmetleri kaydeder:</span><span class="sxs-lookup"><span data-stu-id="49b4e-141">A typical ASP.NET Core app registers services for Entity Framework, Identity, and MVC:</span></span>

[!code-csharp[](startup/sample_snapshot/Startup3.cs?highlight=4,7,11)]

<span data-ttu-id="49b4e-142">Hizmet kapsayıcıya Hizmetleri ekleme kullanımınıza bunları uygulama içinde hem de `Configure` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="49b4e-142">Adding services to the service container makes them available within the app and in the `Configure` method.</span></span> <span data-ttu-id="49b4e-143">Hizmetleri aracılığıyla çözümlenir [bağımlılık ekleme](xref:fundamentals/dependency-injection) veya <xref:Microsoft.AspNetCore.Builder.IApplicationBuilder.ApplicationServices*>.</span><span class="sxs-lookup"><span data-stu-id="49b4e-143">The services are resolved via [dependency injection](xref:fundamentals/dependency-injection) or from <xref:Microsoft.AspNetCore.Builder.IApplicationBuilder.ApplicationServices*>.</span></span>

## <a name="the-configure-method"></a><span data-ttu-id="49b4e-144">Yapılandırma yöntemi</span><span class="sxs-lookup"><span data-stu-id="49b4e-144">The Configure method</span></span>

<span data-ttu-id="49b4e-145"><xref:Microsoft.AspNetCore.Hosting.StartupBase.Configure*> Yöntemi, uygulamanın HTTP isteklerine nasıl yanıt verdiğini belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="49b4e-145">The <xref:Microsoft.AspNetCore.Hosting.StartupBase.Configure*> method is used to specify how the app responds to HTTP requests.</span></span> <span data-ttu-id="49b4e-146">İstek ardışık düzenini ekleyerek yapılandırılır [ara yazılım](xref:fundamentals/middleware/index) bileşenleri bir <xref:Microsoft.AspNetCore.Builder.IApplicationBuilder> örneği.</span><span class="sxs-lookup"><span data-stu-id="49b4e-146">The request pipeline is configured by adding [middleware](xref:fundamentals/middleware/index) components to an <xref:Microsoft.AspNetCore.Builder.IApplicationBuilder> instance.</span></span> <span data-ttu-id="49b4e-147">`IApplicationBuilder` kullanılabilir `Configure` yöntemi, ancak service kapsayıcısında kayıtlı değil.</span><span class="sxs-lookup"><span data-stu-id="49b4e-147">`IApplicationBuilder` is available to the `Configure` method, but it isn't registered in the service container.</span></span> <span data-ttu-id="49b4e-148">Barındırma oluşturur bir `IApplicationBuilder` ve doğrudan geçirir `Configure`.</span><span class="sxs-lookup"><span data-stu-id="49b4e-148">Hosting creates an `IApplicationBuilder` and passes it directly to `Configure`.</span></span>

<span data-ttu-id="49b4e-149">[ASP.NET Core şablonları](/dotnet/core/tools/dotnet-new) desteği ile işlem hattı yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="49b4e-149">The [ASP.NET Core templates](/dotnet/core/tools/dotnet-new) configure the pipeline with support for:</span></span>

* [<span data-ttu-id="49b4e-150">Geliştirici özel durumu sayfası</span><span class="sxs-lookup"><span data-stu-id="49b4e-150">Developer exception page</span></span>](xref:fundamentals/error-handling#the-developer-exception-page)
* [<span data-ttu-id="49b4e-151">Özel durum işleyicisi</span><span class="sxs-lookup"><span data-stu-id="49b4e-151">Exception handler</span></span>](xref:fundamentals/error-handling#configure-a-custom-exception-handling-page)
* [<span data-ttu-id="49b4e-152">HTTP katı aktarım güvenliği (HSTS)</span><span class="sxs-lookup"><span data-stu-id="49b4e-152">HTTP Strict Transport Security (HSTS)</span></span>](xref:security/enforcing-ssl#http-strict-transport-security-protocol-hsts)
* [<span data-ttu-id="49b4e-153">HTTPS yeniden yönlendirmesi</span><span class="sxs-lookup"><span data-stu-id="49b4e-153">HTTPS redirection</span></span>](xref:security/enforcing-ssl)
* [<span data-ttu-id="49b4e-154">Statik dosyalar</span><span class="sxs-lookup"><span data-stu-id="49b4e-154">Static files</span></span>](xref:fundamentals/static-files)
* [<span data-ttu-id="49b4e-155">Genel veri koruma yönetmeliği (GDPR)</span><span class="sxs-lookup"><span data-stu-id="49b4e-155">General Data Protection Regulation (GDPR)</span></span>](xref:security/gdpr)
* <span data-ttu-id="49b4e-156">ASP.NET Core [MVC](xref:mvc/overview) ve [Razor sayfaları](xref:razor-pages/index)</span><span class="sxs-lookup"><span data-stu-id="49b4e-156">ASP.NET Core [MVC](xref:mvc/overview) and [Razor Pages](xref:razor-pages/index)</span></span>

[!code-csharp[](startup/sample_snapshot/Startup4.cs)]

<span data-ttu-id="49b4e-157">Her `Use` genişletme yöntemi, bir veya daha fazla ara yazılımı bileşenleri istek ardışık düzene ekler.</span><span class="sxs-lookup"><span data-stu-id="49b4e-157">Each `Use` extension method adds one or more middleware components to the request pipeline.</span></span> <span data-ttu-id="49b4e-158">Örneğin, `UseMvc` genişletme yöntemi ekler [yönlendirme ara yazılım](xref:fundamentals/routing) istek ardışık düzenine ve yapılandırır [MVC](xref:mvc/overview) varsayılan işleç olarak eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="49b4e-158">For instance, the `UseMvc` extension method adds [Routing Middleware](xref:fundamentals/routing) to the request pipeline and configures [MVC](xref:mvc/overview) as the default handler.</span></span>

<span data-ttu-id="49b4e-159">Her ara yazılım bileşeni istek ardışık düzende, ardışık düzende sonraki bileşene çağırma veya zincir uygunsa kısa devre sorumludur.</span><span class="sxs-lookup"><span data-stu-id="49b4e-159">Each middleware component in the request pipeline is responsible for invoking the next component in the pipeline or short-circuiting the chain, if appropriate.</span></span> <span data-ttu-id="49b4e-160">Kısa devre ara yazılım zincirinde oluşmuyorsa, her bir ara yazılım istemciye gönderilmeden önce isteği işlemek için ikinci bir şans sahiptir.</span><span class="sxs-lookup"><span data-stu-id="49b4e-160">If short-circuiting doesn't occur along the middleware chain, each middleware has a second chance to process the request before it's sent to the client.</span></span>

<span data-ttu-id="49b4e-161">Gibi ek hizmetleri `IHostingEnvironment` ve `ILoggerFactory`, içinde belirtilebilir `Configure` metodu imzası.</span><span class="sxs-lookup"><span data-stu-id="49b4e-161">Additional services, such as `IHostingEnvironment` and `ILoggerFactory`, may also be specified in the `Configure` method signature.</span></span> <span data-ttu-id="49b4e-162">Kullanılabilir iseler ek hizmetler belirtildiğinde, eklenmiş.</span><span class="sxs-lookup"><span data-stu-id="49b4e-162">When specified, additional services are injected if they're available.</span></span>

<span data-ttu-id="49b4e-163">Nasıl kullanılacağı hakkında daha fazla bilgi için `IApplicationBuilder` ve ara yazılım işlenme sırasını <xref:fundamentals/middleware/index>.</span><span class="sxs-lookup"><span data-stu-id="49b4e-163">For more information on how to use `IApplicationBuilder` and the order of middleware processing, see <xref:fundamentals/middleware/index>.</span></span>

## <a name="convenience-methods"></a><span data-ttu-id="49b4e-164">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="49b4e-164">Convenience methods</span></span>

<span data-ttu-id="49b4e-165">Kullanmadan, hizmetler ve istek işleme ardışık düzenini yapılandırmak için bir `Startup` sınıfı, çağrı `ConfigureServices` ve `Configure` konak oluşturucu üzerinde kullanışlı yöntemler.</span><span class="sxs-lookup"><span data-stu-id="49b4e-165">To configure services and the request processing pipeline without using a `Startup` class, call `ConfigureServices` and `Configure` convenience methods on the host builder.</span></span> <span data-ttu-id="49b4e-166">Birden çok çağrılar `ConfigureServices` birbirine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="49b4e-166">Multiple calls to `ConfigureServices` append to one another.</span></span> <span data-ttu-id="49b4e-167">Birden çok `Configure` yöntem çağrıları vardır, son `Configure` çağrısı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="49b4e-167">If multiple `Configure` method calls exist, the last `Configure` call is used.</span></span>

[!code-csharp[](startup/sample_snapshot/Program1.cs?highlight=18,22)]

## <a name="extend-startup-with-startup-filters"></a><span data-ttu-id="49b4e-168">Başlangıç başlangıç filtreleri ile genişletme</span><span class="sxs-lookup"><span data-stu-id="49b4e-168">Extend Startup with startup filters</span></span>

<span data-ttu-id="49b4e-169">Kullanım <xref:Microsoft.AspNetCore.Hosting.IStartupFilter> uygulamanın başında veya sonunda ara yazılımını yapılandırma [yapılandırma](#the-configure-method) ara yazılım ardışık düzenini.</span><span class="sxs-lookup"><span data-stu-id="49b4e-169">Use <xref:Microsoft.AspNetCore.Hosting.IStartupFilter> to configure middleware at the beginning or end of an app's [Configure](#the-configure-method) middleware pipeline.</span></span> <span data-ttu-id="49b4e-170">`IStartupFilter` bir ara yazılım önce veya sonra Ara yazılım tarafından kitaplıkları başında veya uygulamanın istek işleme ardışık sonuna eklenen çalıştığından emin olmak kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="49b4e-170">`IStartupFilter` is useful to ensure that a middleware runs before or after middleware added by libraries at the start or end of the app's request processing pipeline.</span></span>

<span data-ttu-id="49b4e-171">`IStartupFilter` tek bir yöntem uygular <xref:Microsoft.AspNetCore.Hosting.StartupBase.Configure*>, alır ve döndürür bir `Action<IApplicationBuilder>`.</span><span class="sxs-lookup"><span data-stu-id="49b4e-171">`IStartupFilter` implements a single method, <xref:Microsoft.AspNetCore.Hosting.StartupBase.Configure*>, which receives and returns an `Action<IApplicationBuilder>`.</span></span> <span data-ttu-id="49b4e-172">Bir <xref:Microsoft.AspNetCore.Builder.IApplicationBuilder> uygulamanın istek ardışık düzenini yapılandırmak için bir sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="49b4e-172">An <xref:Microsoft.AspNetCore.Builder.IApplicationBuilder> defines a class to configure an app's request pipeline.</span></span> <span data-ttu-id="49b4e-173">Daha fazla bilgi için [IApplicationBuilder ile bir ara yazılım ardışık düzenini oluşturma](xref:fundamentals/middleware/index#create-a-middleware-pipeline-with-iapplicationbuilder).</span><span class="sxs-lookup"><span data-stu-id="49b4e-173">For more information, see [Create a middleware pipeline with IApplicationBuilder](xref:fundamentals/middleware/index#create-a-middleware-pipeline-with-iapplicationbuilder).</span></span>

<span data-ttu-id="49b4e-174">Her `IStartupFilter` istek işlem hattı, bir veya daha fazla middlewares uygular.</span><span class="sxs-lookup"><span data-stu-id="49b4e-174">Each `IStartupFilter` implements one or more middlewares in the request pipeline.</span></span> <span data-ttu-id="49b4e-175">Filtreler, hizmet kapsayıcıya eklendikleri sırayla çağrılır.</span><span class="sxs-lookup"><span data-stu-id="49b4e-175">The filters are invoked in the order they were added to the service container.</span></span> <span data-ttu-id="49b4e-176">Ara yazılım önce filtreler ekleyebilir veya denetim sıradaki filtreye denetimini geçtikten sonra bu nedenle bunlar başına veya sonuna kadar uygulama ardışık ekleyin.</span><span class="sxs-lookup"><span data-stu-id="49b4e-176">Filters may add middleware before or after passing control to the next filter, thus they append to the beginning or end of the app pipeline.</span></span>

<span data-ttu-id="49b4e-177">Aşağıdaki örnek bir ara yazılımla kaydettirmek gösterilmektedir `IStartupFilter`.</span><span class="sxs-lookup"><span data-stu-id="49b4e-177">The following example demonstrates how to register a middleware with `IStartupFilter`.</span></span>

<span data-ttu-id="49b4e-178">`RequestSetOptionsMiddleware` Ara yazılım, bir sorgu dizesi parametresi bir seçenek değeri ayarlar:</span><span class="sxs-lookup"><span data-stu-id="49b4e-178">The `RequestSetOptionsMiddleware` middleware sets an options value from a query string parameter:</span></span>

[!code-csharp[](startup/sample_snapshot/RequestSetOptionsMiddleware.cs?name=snippet1&highlight=21)]

<span data-ttu-id="49b4e-179">`RequestSetOptionsMiddleware` Yapılandırılan `RequestSetOptionsStartupFilter` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="49b4e-179">The `RequestSetOptionsMiddleware` is configured in the `RequestSetOptionsStartupFilter` class:</span></span>

[!code-csharp[](startup/sample_snapshot/RequestSetOptionsStartupFilter.cs?name=snippet1&highlight=7)]

<span data-ttu-id="49b4e-180">`IStartupFilter` Service kapsayıcısında kayıtlı <xref:Microsoft.AspNetCore.Hosting.StartupBase.ConfigureServices*> ve artırmaktadır `Startup` gelen dışında `Startup` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="49b4e-180">The `IStartupFilter` is registered in the service container in <xref:Microsoft.AspNetCore.Hosting.StartupBase.ConfigureServices*> and augments `Startup` from outside of the `Startup` class:</span></span>

[!code-csharp[](startup/sample_snapshot/Program2.cs?name=snippet1&highlight=4-5)]

<span data-ttu-id="49b4e-181">Bir sorgu dizesi parametresi için zaman `option` MVC ara yazılımın yanıt işlemeden önce ara değer atama işlemleri sağlanır:</span><span class="sxs-lookup"><span data-stu-id="49b4e-181">When a query string parameter for `option` is provided, the middleware processes the value assignment before the MVC middleware renders the response:</span></span>

![İşlenen dizin sayfasını gösteren tarayıcı penceresi.](startup/_static/index.png)

<span data-ttu-id="49b4e-184">Yürütme sırası ara yazılım tarafından sırasına göre ayarlanmış `IStartupFilter` kayıtları:</span><span class="sxs-lookup"><span data-stu-id="49b4e-184">Middleware execution order is set by the order of `IStartupFilter` registrations:</span></span>

* <span data-ttu-id="49b4e-185">Birden çok `IStartupFilter` uygulamaları aynı nesnelerle etkileşim.</span><span class="sxs-lookup"><span data-stu-id="49b4e-185">Multiple `IStartupFilter` implementations may interact with the same objects.</span></span> <span data-ttu-id="49b4e-186">Sıralama önemlidir, sipariş kendi `IStartupFilter` hizmet kendi middlewares çalışması gereken sıraya uyacak şekilde kayıtları.</span><span class="sxs-lookup"><span data-stu-id="49b4e-186">If ordering is important, order their `IStartupFilter` service registrations to match the order that their middlewares should run.</span></span>
* <span data-ttu-id="49b4e-187">Kitaplıkları, bir veya daha fazla ile Ara yazılım ekleyebilir `IStartupFilter` önce veya sonra diğer uygulama ara yazılım kayıtlı çalışan uygulamaları `IStartupFilter`.</span><span class="sxs-lookup"><span data-stu-id="49b4e-187">Libraries may add middleware with one or more `IStartupFilter` implementations that run before or after other app middleware registered with `IStartupFilter`.</span></span> <span data-ttu-id="49b4e-188">Çağrılacak bir `IStartupFilter` ara yazılım bir kitaplık tarafından eklenen bir ara yazılım önce `IStartupFilter`, hizmet kaydı kitaplığı hizmet kapsayıcıya eklenmeden önce konumlandırın.</span><span class="sxs-lookup"><span data-stu-id="49b4e-188">To invoke an `IStartupFilter` middleware before a middleware added by a library's `IStartupFilter`, position the service registration before the library is added to the service container.</span></span> <span data-ttu-id="49b4e-189">Daha sonra çağırmak için kitaplık eklendikten sonra hizmet kaydı getirin.</span><span class="sxs-lookup"><span data-stu-id="49b4e-189">To invoke it afterward, position the service registration after the library is added.</span></span>

## <a name="add-configuration-at-startup-from-an-external-assembly"></a><span data-ttu-id="49b4e-190">Yapılandırma, başlatma sırasında dış bütünleştirilmiş koddan ekleyin.</span><span class="sxs-lookup"><span data-stu-id="49b4e-190">Add configuration at startup from an external assembly</span></span>

<span data-ttu-id="49b4e-191">Bir <xref:Microsoft.AspNetCore.Hosting.IHostingStartup> uygulama sağlayan uygulamanın dışındaki dış bütünleştirilmiş koddan başlatma sırasında bir uygulama için geliştirmeler ekleme `Startup` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="49b4e-191">An <xref:Microsoft.AspNetCore.Hosting.IHostingStartup> implementation allows adding enhancements to an app at startup from an external assembly outside of the app's `Startup` class.</span></span> <span data-ttu-id="49b4e-192">Daha fazla bilgi için bkz. <xref:fundamentals/configuration/platform-specific-configuration>.</span><span class="sxs-lookup"><span data-stu-id="49b4e-192">For more information, see <xref:fundamentals/configuration/platform-specific-configuration>.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="49b4e-193">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="49b4e-193">Additional resources</span></span>

* [<span data-ttu-id="49b4e-194">Ana bilgisayar</span><span class="sxs-lookup"><span data-stu-id="49b4e-194">The host</span></span>](xref:fundamentals/index#host)
* <xref:fundamentals/environments>
* <xref:fundamentals/middleware/index>
* <xref:fundamentals/logging/index>
* <xref:fundamentals/configuration/index>