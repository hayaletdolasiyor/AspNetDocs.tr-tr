---
uid: web-forms/overview/deployment/configuring-server-environments-for-web-deployment/scenario-configuring-a-test-environment-for-web-deployment
title: 'Senaryo: Web dağıtımı için bir Test Ortamı yapılandırma | Microsoft Docs'
author: jrjlee
description: Bu konu, bir geliştiricinin normal web dağıtım senaryosu açıklanmaktadır veya test ortamları ve bir sı ayarlamak için tamamlamanız gereken görevleri açıklar...
ms.author: riande
ms.date: 05/04/2012
ms.assetid: 44a22ac7-1fc7-4174-b946-c6129fb6a19b
msc.legacyurl: /web-forms/overview/deployment/configuring-server-environments-for-web-deployment/scenario-configuring-a-test-environment-for-web-deployment
msc.type: authoredcontent
ms.openlocfilehash: 3c6c8850e77f4a3cbb71db4353487c8a5e9c097d
ms.sourcegitcommit: 24b1f6decbb17bb22a45166e5fdb0845c65af498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57076167"
---
<a name="scenario-configuring-a-test-environment-for-web-deployment"></a><span data-ttu-id="82525-103">Senaryo: Web Dağıtımı için Test Ortamı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="82525-103">Scenario: Configuring a Test Environment for Web Deployment</span></span>
====================
<span data-ttu-id="82525-104">tarafından [Jason Lee](https://github.com/jrjlee)</span><span class="sxs-lookup"><span data-stu-id="82525-104">by [Jason Lee](https://github.com/jrjlee)</span></span>

[<span data-ttu-id="82525-105">PDF'yi indirin</span><span class="sxs-lookup"><span data-stu-id="82525-105">Download PDF</span></span>](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/63/56/8130.DeployingWebAppsInEnterpriseScenarios.pdf)

> <span data-ttu-id="82525-106">Bu konuda tipik web dağıtım senaryosu için geliştirici veya test ortamları ve benzer bir ortamı ayarlamak için tamamlanması gereken görevleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="82525-106">This topic describes a typical web deployment scenario for developer or test environments and explains the tasks you need to complete in order to set up a similar environment.</span></span>


<span data-ttu-id="82525-107">Geliştiricilere web uygulamaları üzerinde çalışırken, bunlar genellikle erişim gerçekçi bir ayarda uygulamalarına değişiklikleri test etmek için kullanabileceğiniz bir sunucu ortamınıza verilir.</span><span class="sxs-lookup"><span data-stu-id="82525-107">When developers work on web applications, they're often given access to a server environment that they can use to test changes to their applications in a realistic setting.</span></span> <span data-ttu-id="82525-108">Bu tür bir geliştirme veya test ortamı genellikle şu özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="82525-108">This kind of development or test environment typically has these characteristics:</span></span>

- <span data-ttu-id="82525-109">Ortamı, tek bir web sunucusu ve tek veritabanı sunucusu oluşur.</span><span class="sxs-lookup"><span data-stu-id="82525-109">The environment consists of a single web server and a single database server.</span></span>
- <span data-ttu-id="82525-110">Geliştiriciler genellikle uygulamalarını gereksinimler için ortamı yapılandırmak bildirmek için bu sunucularda yönetici ayrıcalıklarına sahip.</span><span class="sxs-lookup"><span data-stu-id="82525-110">The developers usually have administrator privileges on the servers, to let them configure the environment to the requirements of their applications.</span></span>
- <span data-ttu-id="82525-111">Değişiklikleri uygulamalara ortamı tek adımlı desteklemek gereken şekilde sık olarak dağıtılan veya otomatik dağıtım.</span><span class="sxs-lookup"><span data-stu-id="82525-111">Changes to applications are deployed on a frequent basis, so the environment needs to support single-step or automated deployment.</span></span>

<span data-ttu-id="82525-112">Örneğin, bizim [öğretici senaryo](../deploying-web-applications-in-enterprise-scenarios/enterprise-web-deployment-scenario-overview.md), Matt Hink Fabrikam, Inc. şirketinde bir geliştirici olan Matt Kişi Yöneticisi çözümü çalıştığından ve değişiklikleri bir test ortamına dağıtmak düzenli olarak gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="82525-112">For example, in our [tutorial scenario](../deploying-web-applications-in-enterprise-scenarios/enterprise-web-deployment-scenario-overview.md), Matt Hink is a developer at Fabrikam, Inc. Matt is working on the Contact Manager solution and regularly needs to deploy changes to a test environment.</span></span> <span data-ttu-id="82525-113">Matt, test web sunucusu ve test veritabanı sunucusunda bir yöneticidir.</span><span class="sxs-lookup"><span data-stu-id="82525-113">Matt is an administrator on the test web server and the test database server.</span></span> <span data-ttu-id="82525-114">Başlangıçta, çözüm doğrudan test ortamına dağıtın edebilmek Matt gerekir.</span><span class="sxs-lookup"><span data-stu-id="82525-114">Initially, Matt needs to be able to deploy the solution to the test environment directly.</span></span>

![](scenario-configuring-a-test-environment-for-web-deployment/_static/image1.png)

<span data-ttu-id="82525-115">İş ilerler ve geliştiricilerin takım, kişi yöneticisi çözümü sürekli tümleştirme (CI) Team Foundation Server (TFS) için yapılandırılmış katılın.</span><span class="sxs-lookup"><span data-stu-id="82525-115">As work progresses and more developers join the team, the Contact Manager solution is configured for continuous integration (CI) in Team Foundation Server (TFS).</span></span> <span data-ttu-id="82525-116">Bir geliştirici içeriği denetimi gerçekleştirildiğinde, ekip Çözümü derleyin, herhangi bir birim testlerini çalıştırmak ve otomatik olarak bir çözümü test ortamına dağıtın.</span><span class="sxs-lookup"><span data-stu-id="82525-116">Whenever a developer checks in content, Team Build should build the solution, run any unit tests, and automatically deploy the solution to the test environment.</span></span>

![](scenario-configuring-a-test-environment-for-web-deployment/_static/image2.png)

## <a name="solution-overview"></a><span data-ttu-id="82525-117">Çözüme genel bakış</span><span class="sxs-lookup"><span data-stu-id="82525-117">Solution Overview</span></span>

<span data-ttu-id="82525-118">Test ortamı tek adımlı desteklemesi gerekir veya uzak bir bilgisayardan dağıtım için iki ana yaklaşım seçeneğiniz otomatik.</span><span class="sxs-lookup"><span data-stu-id="82525-118">The test environment needs to support single-step or automated deployment from a remote computer, so you have a choice of two main approaches.</span></span> <span data-ttu-id="82525-119">Şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="82525-119">You can:</span></span>

- <span data-ttu-id="82525-120">Test web sunucusunu Web dağıtımı Aracı hizmeti ("Uzak Aracı") dağıtımı desteklemek üzere yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="82525-120">Configure the test web server to support deployment using the Web Deployment Agent Service (the "remote agent").</span></span>
- <span data-ttu-id="82525-121">Test web sunucusunu Web dağıtımı işleyicisi kullanarak dağıtımı desteklemek üzere yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="82525-121">Configure the test web server to support deployment using the Web Deploy handler.</span></span>

> [!NOTE]
> <span data-ttu-id="82525-122">Ayrıca kullanabileceğinizi [Web dağıtımı isteğe bağlı](https://technet.microsoft.com/library/ee517345(WS.10).aspx) ("geçici agent").</span><span class="sxs-lookup"><span data-stu-id="82525-122">You could also use [Web Deploy On Demand](https://technet.microsoft.com/library/ee517345(WS.10).aspx) (the "temp agent").</span></span> <span data-ttu-id="82525-123">Bu gereksinimleri ve kısıtlamaları açısından uzak aracı yaklaşımı benzer.</span><span class="sxs-lookup"><span data-stu-id="82525-123">This is similar to the remote agent approach in terms of requirements and constraints.</span></span>


<span data-ttu-id="82525-124">Bu durumda, geliştiriciler hedef sunuculara yönetici ayrıcalıklarına sahip ve mantıksal seçimi, uzak aracı kullanarak dağıtımı desteklemek üzere test web sunucusunu yapılandırmak için bu nedenle test ortamı katı güvenlik kısıtlamalarına tabi değildir.</span><span class="sxs-lookup"><span data-stu-id="82525-124">In this case, the developers have administrator privileges on the destination servers, and the test environment is not subject to strict security constraints, so the logical choice is to configure the test web server to support deployment using the remote agent.</span></span> <span data-ttu-id="82525-125">Bu daha az karmaşık olan ve Web dağıtımı işleyicisi yaklaşım daha az başlangıç yapılandırmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="82525-125">This is less complex and requires less initial configuration than the Web Deploy Handler approach.</span></span> <span data-ttu-id="82525-126">Uzaktan erişim ve dağıtımını desteklemek için veritabanı sunucunuzu yapılandırmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="82525-126">You'll also need to configure your database server to support remote access and deployment.</span></span>

<span data-ttu-id="82525-127">Bu konular bu görevleri tamamlamak için gereken tüm bilgileri sağlar:</span><span class="sxs-lookup"><span data-stu-id="82525-127">These topics provide all the information you need in order to complete these tasks:</span></span>

- <span data-ttu-id="82525-128">[Bir Web sunucusunu Web dağıtımı yayımlama (Uzak Aracı) için yapılandırma](configuring-a-web-server-for-web-deploy-publishing-remote-agent.md).</span><span class="sxs-lookup"><span data-stu-id="82525-128">[Configure a Web Server for Web Deploy Publishing (Remote Agent)](configuring-a-web-server-for-web-deploy-publishing-remote-agent.md).</span></span> <span data-ttu-id="82525-129">Bu konuda, temiz bir Windows Server 2008 R2 derleme başlatma yayımlama, uzak aracı yaklaşımı kullanarak Web dağıtımını destekleyen bir web sunucusu nasıl oluşturulduğu açıklanır.</span><span class="sxs-lookup"><span data-stu-id="82525-129">This topic describes how to build a web server that supports Web Deploy publishing, using the remote agent approach, starting from a clean Windows Server 2008 R2 build.</span></span>
- <span data-ttu-id="82525-130">[Bir veritabanı sunucusunu Web dağıtımı yayımlama için yapılandırma](configuring-a-database-server-for-web-deploy-publishing.md).</span><span class="sxs-lookup"><span data-stu-id="82525-130">[Configure a Database Server for Web Deploy Publishing](configuring-a-database-server-for-web-deploy-publishing.md).</span></span> <span data-ttu-id="82525-131">Bu konuda, uzaktan erişim ve dağıtımını, bir SQL Server 2008 R2'in varsayılan yüklemesinden başlatma desteklemek için bir veritabanı sunucusunun nasıl yapılandırılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="82525-131">This topic describes how to configure a database server to support remote access and deployment, starting from a default installation of SQL Server 2008 R2.</span></span>

## <a name="further-reading"></a><span data-ttu-id="82525-132">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="82525-132">Further Reading</span></span>

<span data-ttu-id="82525-133">Tipik bir hazırlık ortamı yapılandırma hakkında yönergeler için bkz. [senaryosu: Web dağıtımı için hazırlama ortamı yapılandırma](scenario-configuring-a-staging-environment-for-web-deployment.md).</span><span class="sxs-lookup"><span data-stu-id="82525-133">For guidance on configuring a typical staging environment, see [Scenario: Configuring a Staging Environment for Web Deployment](scenario-configuring-a-staging-environment-for-web-deployment.md).</span></span> <span data-ttu-id="82525-134">Tipik bir üretim ortamı yapılandırma hakkında yönergeler için bkz. [senaryosu: Web dağıtımı için bir üretim ortamı yapılandırma](scenario-configuring-a-production-environment-for-web-deployment.md).</span><span class="sxs-lookup"><span data-stu-id="82525-134">For guidance on configuring a typical production environment, see [Scenario: Configuring a Production Environment for Web Deployment](scenario-configuring-a-production-environment-for-web-deployment.md).</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="82525-135">[Önceki](choosing-the-right-approach-to-web-deployment.md)
> [İleri](scenario-configuring-a-staging-environment-for-web-deployment.md)</span><span class="sxs-lookup"><span data-stu-id="82525-135">[Previous](choosing-the-right-approach-to-web-deployment.md)
[Next](scenario-configuring-a-staging-environment-for-web-deployment.md)</span></span>