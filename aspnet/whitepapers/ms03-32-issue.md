---
uid: whitepapers/ms03-32-issue
title: IE için güvenlik güncelleştirmesi uygulandıktan sonra 'Sunucu uygulaması kullanılamıyor' hatası için düzeltme | Microsoft Docs
author: rick-anderson
description: Bu incelemede, bir sorunu gideren MS03 32 güvenlik güncelleştirmesiyle Wi üzerinde çalışan ASP.NET 1.0 uygulamaları etkiler Internet Explorer için düzeltme eki anlatılmaktadır...
ms.author: riande
ms.date: 02/10/2010
ms.assetid: 1365eebb-bdf7-4a05-8d18-7f200531be55
msc.legacyurl: /whitepapers/ms03-32-issue
msc.type: content
ms.openlocfilehash: 9041f8d15a449a517594f8051c3d9f0ceb18a8a3
ms.sourcegitcommit: 24b1f6decbb17bb22a45166e5fdb0845c65af498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57070191"
---
<a name="fix-for-server-application-unavailable-error-after-applying-security-update-for-ie"></a><span data-ttu-id="10dda-103">IE için Güvenlik Güncelleştirmesi Uygulandıktan Sonra Oluşan 'Sunucu Uygulaması Kullanılamıyor' Hatasının Çözümü</span><span class="sxs-lookup"><span data-stu-id="10dda-103">Fix for 'Server Application Unavailable' Error after Applying Security Update for IE</span></span>
====================
> <span data-ttu-id="10dda-104">Bu yazıda, Internet Explorer, Windows XP Professional üzerinde çalışan ASP.NET 1.0 uygulamaları etkiler MS03 32 güvenlik güncelleştirmesiyle bir sorunu giderir düzeltme açıklar.</span><span class="sxs-lookup"><span data-stu-id="10dda-104">This paper describes the patch that fixes an issue with the MS03-32 Security Update for Internet Explorer that affects ASP.NET 1.0 applications running on Windows XP Professional.</span></span>
> 
> <span data-ttu-id="10dda-105">ASP.NET 1.0 ve Windows XP Professional için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="10dda-105">Applies to ASP.NET 1.0 and Windows XP Professional.</span></span>


<span data-ttu-id="10dda-106">Microsoft Internet Explorer güvenlik düzeltme ekini MS03 32 güvenlik güncelleştirmesi ve Windows XP'de çalışan ASP.NET 1.0 ile bir sorun belirledik.</span><span class="sxs-lookup"><span data-stu-id="10dda-106">Microsoft identified an issue with the MS03-32 Security Update for Internet Explorer security patch and ASP.NET 1.0 running on Windows XP.</span></span> <span data-ttu-id="10dda-107">Bu düzeltme ekini el ile veya Windows Update sitesinden yeni kritik güncelleştirmeler edinme yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="10dda-107">This patch can be installed manually or by obtaining recent critical updates from the Windows Update site.</span></span>

<span data-ttu-id="10dda-108">Bu sorunun belirtisi, Windows XP makine üzerinde düzeltme eki yükledikten sonra yerel IIS 5.1 web sunucusu üzerinde çalışan ASP.NET uygulamaları için tüm istekleri "Sunucu uygulaması kullanılamıyor" belirten bir hata iletisi neden olur.</span><span class="sxs-lookup"><span data-stu-id="10dda-108">The symptom of this issue is that after installing the patch on a Windows XP machine, all requests to ASP.NET applications running on the local IIS 5.1 web server result in an error message saying "Server Application Unavailable".</span></span> <span data-ttu-id="10dda-109">Uzak web sunucuları istekleri bundan etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="10dda-109">Requests to remote web servers are unaffected.</span></span>

<span data-ttu-id="10dda-110">Bu sorun, yalnızca ASP.NET 1.0 Windows XP'de çalışan yüklemeleri etkiler.</span><span class="sxs-lookup"><span data-stu-id="10dda-110">This issue only impacts installations running ASP.NET 1.0 on Windows XP.</span></span> <span data-ttu-id="10dda-111">Windows 2000 veya Windows Server 2003 çalıştıran makineleri etkilemez.</span><span class="sxs-lookup"><span data-stu-id="10dda-111">It does not impact machines running Windows 2000 or Windows Server 2003.</span></span> <span data-ttu-id="10dda-112">Aynı zamanda ASP.NET 1.1 ile Windows XP çalıştıran makineleri etkilemez.</span><span class="sxs-lookup"><span data-stu-id="10dda-112">It also does not impact machines running Windows XP with ASP.NET 1.1 installed.</span></span>

<span data-ttu-id="10dda-113">Unutmayın, bu sorunu **değil** ASP.NET bir güvenlik hatası.</span><span class="sxs-lookup"><span data-stu-id="10dda-113">Please note that this issue **is not** a security bug with ASP.NET.</span></span> <span data-ttu-id="10dda-114">Bunu **yok** açmanız veya herhangi bir ASP.NET uygulamasını veya server kötü amaçlı saldırıları izin verin.</span><span class="sxs-lookup"><span data-stu-id="10dda-114">It **does not** open up or allow any malicious attacks against an ASP.NET application or server.</span></span> <span data-ttu-id="10dda-115">Bunun yerine, bu düzeltme ekiyle neden yalnızca bir işlev hatadır.</span><span class="sxs-lookup"><span data-stu-id="10dda-115">Instead, it is purely a functional bug caused by the patch itself.</span></span>

<span data-ttu-id="10dda-116">Bu sorun için kalıcı bir çözüm üzerinde çalışıyoruz.</span><span class="sxs-lookup"><span data-stu-id="10dda-116">We are working hard on a permanent solution for this issue.</span></span> <span data-ttu-id="10dda-117">Bu sırada, sorun için geçici bir çözüm olarak şu toplu iş dosyasını çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10dda-117">In the meantime, you can execute the following batch file as a workaround for the issue.</span></span> <span data-ttu-id="10dda-118">Toplu iş dosyası şunları yapar:</span><span class="sxs-lookup"><span data-stu-id="10dda-118">The batch file does the following:</span></span>

1. <span data-ttu-id="10dda-119">IIS ve ASP.NET durum hizmetleri durdurur</span><span class="sxs-lookup"><span data-stu-id="10dda-119">Stops the IIS and ASP.NET state services</span></span>
2. <span data-ttu-id="10dda-120">Siler ve bilinen bir geçici parola ASPNET hesabıyla oluşturur</span><span class="sxs-lookup"><span data-stu-id="10dda-120">Deletes and recreates the ASPNET account with a known temporary password</span></span>
3. <span data-ttu-id="10dda-121">Windows kullanan `runas` bir ASP.NET kullanıcı profili oluşturan bir yürütülebilir dosyayı başlatmak için komut</span><span class="sxs-lookup"><span data-stu-id="10dda-121">Uses the Windows `runas` command to launch an executable that creates an ASPNET user profile</span></span>
4. <span data-ttu-id="10dda-122">ASP.NET yeniden kaydeder.</span><span class="sxs-lookup"><span data-stu-id="10dda-122">Re-registers ASP.NET.</span></span> <span data-ttu-id="10dda-123">Bu hesap için yeni rastgele bir parola oluşturur ve onu için varsayılan ASP.NET erişim denetimi ayarlarını uygular</span><span class="sxs-lookup"><span data-stu-id="10dda-123">This creates a new random password for the account and applies default ASP.NET access control settings for it</span></span>
5. <span data-ttu-id="10dda-124">IIS hizmetini yeniden başlatır</span><span class="sxs-lookup"><span data-stu-id="10dda-124">Restarts the IIS service</span></span>

<span data-ttu-id="10dda-125">Toplu iş dosyası, sabit kodlanmış geçici bir parola içeren "<strong>1pass\@word</strong>", olacağı için toplu iş dosyasını çalıştırdığınızda runas komutunu girmesi istenir.</span><span class="sxs-lookup"><span data-stu-id="10dda-125">The batch file contains a hardcoded temporary password of "<strong>1pass\@word</strong>" which you will be prompted to enter for the runas command when the batch file is run.</span></span> <span data-ttu-id="10dda-126">Runas komut tamamlandıktan sonra ASPNET hesap parolası ile rastgele bir güçlü değeri yeniden oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="10dda-126">After the runas command completes, the ASPNET account password is recreated with a strong random value.</span></span> <span data-ttu-id="10dda-127">Toplu iş dosyası kodlanmış parola ortamınızdaki parola karmaşıklık gereksinimlerini karşılamıyorsa başarısız olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="10dda-127">Note that the batch file may fail if the hardcoded password does not meet the password complexity requirements in your environment.</span></span> <span data-ttu-id="10dda-128">Bu durumda, ortamınız için uygun olan başka bir değerle değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10dda-128">If that's the case, you can change it to another value that is appropriate for your environment.</span></span>

<span data-ttu-id="10dda-129">*> [!IMPORTANT]* Özel erişim denetimi ayarları veya veritabanı hesap izinlerini hesabından eklediyseniz, bu toplu iş dosyası tamamlandıktan sonra yeniden oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="10dda-129">*> [!IMPORTANT]* If you have added custom access control settings or database account permissions for the ASPNET account, they will need to be recreated after this batch file completes.</span></span> <span data-ttu-id="10dda-130">Hesabı yeniden oluşturulduğunda, yeni bir güvenlik tanımlayıcısı (SID) alırsınız olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="10dda-130">This is because when the account is recreated, it will get a new security identifier (SID).</span></span>

<span data-ttu-id="10dda-131">*> [!IMPORTANT]* Ardından ASP.NET hesabı dışında özel bir hesap ile ASP.NET işçi işlemine çalıştırıyorsanız, bu toplu iş dosyası çalıştırmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="10dda-131">*> [!IMPORTANT]* If you are running the ASP.NET worker process with a custom account other than the ASPNET account, then you should not run this batch file.</span></span> <span data-ttu-id="10dda-132">Bunun yerine etkileşimli olarak oturum açın veya bu hesap için kullanıcı profili oluşturacak bu hesapla runas komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="10dda-132">Instead, you should log in interactively or use the runas command with that account which will create a user profile for that account.</span></span>

<span data-ttu-id="10dda-133">Toplu iş dosyası, aşağıdaki kendiliğinden arşive eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="10dda-133">The batch file is included in the self-extracting archive below.</span></span> <span data-ttu-id="10dda-134">Bunu kullanmak için:</span><span class="sxs-lookup"><span data-stu-id="10dda-134">To use it:</span></span>

1. <span data-ttu-id="10dda-135">Yönetici ayrıcalıklarına sahip bir hesap olarak çalıştırıyor olmalısınız</span><span class="sxs-lookup"><span data-stu-id="10dda-135">You must be running as an account with Administrator privileges</span></span>
2. [<span data-ttu-id="10dda-136">İndirin ve kendiliğinden yürütülebilir dosyasını açın</span><span class="sxs-lookup"><span data-stu-id="10dda-136">Download and open the self-extracting executable file</span></span>](ms03-32-issue/_static/fixup1.exe)
3. <span data-ttu-id="10dda-137">C:\ içeriği Ayıkla</span><span class="sxs-lookup"><span data-stu-id="10dda-137">Extract the contents to c:\\</span></span>
4. <span data-ttu-id="10dda-138">Select... Başlat menüsünden çalıştırın ve girin `cmd.exe`</span><span class="sxs-lookup"><span data-stu-id="10dda-138">Select Run... from the start menu, and enter `cmd.exe`</span></span>
5. <span data-ttu-id="10dda-139">Açık komut windows yazın `c:\fixup.cmd`.</span><span class="sxs-lookup"><span data-stu-id="10dda-139">In the open command windows, type `c:\fixup.cmd`.</span></span>
6. <span data-ttu-id="10dda-140">İstendiğinde girin <strong>1pass\@word</strong> parolası.</span><span class="sxs-lookup"><span data-stu-id="10dda-140">When prompted, enter <strong>1pass\@word</strong> as the password.</span></span>
7. <span data-ttu-id="10dda-141">Daha önce özel erişim denetimi ayarları ya da ASP.NET hesabından veritabanı hesabı izinleri varsa, bu ayarlar artık yeniden uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="10dda-141">If you have previously custom access control settings or database account permissions for the ASPNET account, you'll need to re-apply these settings now.</span></span>

<span data-ttu-id="10dda-142">Birçok neden bu sorundan dolayı özür.</span><span class="sxs-lookup"><span data-stu-id="10dda-142">Many apologies for the inconvenience that this has caused.</span></span> <span data-ttu-id="10dda-143">Kullanıma sunulduğunda size ek bilgi gönderecektir.</span><span class="sxs-lookup"><span data-stu-id="10dda-143">We'll post additional information as it becomes available.</span></span>

<span data-ttu-id="10dda-144">Matris aşağıdaki platformlara ve sürümlere bu sorundan etkilenen ayrıntılı olarak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="10dda-144">The matrix below details platforms and versions impacted by this issue.</span></span>

| <span data-ttu-id="10dda-145">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="10dda-145">.NET Framework</span></span> | <span data-ttu-id="10dda-146">Platform</span><span class="sxs-lookup"><span data-stu-id="10dda-146">Platform</span></span> | <span data-ttu-id="10dda-147">Etkilenen</span><span class="sxs-lookup"><span data-stu-id="10dda-147">Affected</span></span> |
| --- | --- | --- |
| <span data-ttu-id="10dda-148">Sürüm 1.0</span><span class="sxs-lookup"><span data-stu-id="10dda-148">Version 1.0</span></span> | <span data-ttu-id="10dda-149">Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="10dda-149">Windows 2000 Professional</span></span> | <span data-ttu-id="10dda-150">Hayır</span><span class="sxs-lookup"><span data-stu-id="10dda-150">No</span></span> |
| <span data-ttu-id="10dda-151">Sürüm 1.0</span><span class="sxs-lookup"><span data-stu-id="10dda-151">Version 1.0</span></span> | <span data-ttu-id="10dda-152">Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="10dda-152">Windows 2000 Server</span></span> | <span data-ttu-id="10dda-153">Hayır</span><span class="sxs-lookup"><span data-stu-id="10dda-153">No</span></span> |
| <span data-ttu-id="10dda-154">Sürüm 1.0</span><span class="sxs-lookup"><span data-stu-id="10dda-154">Version 1.0</span></span> | <span data-ttu-id="10dda-155">Windows XP Professional</span><span class="sxs-lookup"><span data-stu-id="10dda-155">Windows XP Professional</span></span> | <span data-ttu-id="10dda-156">Evet</span><span class="sxs-lookup"><span data-stu-id="10dda-156">Yes</span></span> |
| <span data-ttu-id="10dda-157">Sürüm 1.0</span><span class="sxs-lookup"><span data-stu-id="10dda-157">Version 1.0</span></span> | <span data-ttu-id="10dda-158">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="10dda-158">Windows Server 2003</span></span> | <span data-ttu-id="10dda-159">Hayır</span><span class="sxs-lookup"><span data-stu-id="10dda-159">No</span></span> |
| <span data-ttu-id="10dda-160">Sürüm 1.0</span><span class="sxs-lookup"><span data-stu-id="10dda-160">Version 1.0</span></span> | <span data-ttu-id="10dda-161">Windows XP Home Cassini'ye ile</span><span class="sxs-lookup"><span data-stu-id="10dda-161">Windows XP Home with Cassini</span></span> | <span data-ttu-id="10dda-162">Hayır</span><span class="sxs-lookup"><span data-stu-id="10dda-162">No</span></span> |
| <span data-ttu-id="10dda-163">Sürüm 1.1</span><span class="sxs-lookup"><span data-stu-id="10dda-163">Version 1.1</span></span> | <span data-ttu-id="10dda-164">Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="10dda-164">Windows 2000 Professional</span></span> | <span data-ttu-id="10dda-165">Hayır</span><span class="sxs-lookup"><span data-stu-id="10dda-165">No</span></span> |
| <span data-ttu-id="10dda-166">Sürüm 1.1</span><span class="sxs-lookup"><span data-stu-id="10dda-166">Version 1.1</span></span> | <span data-ttu-id="10dda-167">Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="10dda-167">Windows 2000 Server</span></span> | <span data-ttu-id="10dda-168">Hayır</span><span class="sxs-lookup"><span data-stu-id="10dda-168">No</span></span> |
| <span data-ttu-id="10dda-169">Sürüm 1.1</span><span class="sxs-lookup"><span data-stu-id="10dda-169">Version 1.1</span></span> | <span data-ttu-id="10dda-170">Windows XP Professional</span><span class="sxs-lookup"><span data-stu-id="10dda-170">Windows XP Professional</span></span> | <span data-ttu-id="10dda-171">Hayır</span><span class="sxs-lookup"><span data-stu-id="10dda-171">No</span></span> |
| <span data-ttu-id="10dda-172">Sürüm 1.1</span><span class="sxs-lookup"><span data-stu-id="10dda-172">Version 1.1</span></span> | <span data-ttu-id="10dda-173">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="10dda-173">Windows Server 2003</span></span> | <span data-ttu-id="10dda-174">Hayır</span><span class="sxs-lookup"><span data-stu-id="10dda-174">No</span></span> |
| <span data-ttu-id="10dda-175">Sürüm 1.1</span><span class="sxs-lookup"><span data-stu-id="10dda-175">Version 1.1</span></span> | <span data-ttu-id="10dda-176">Windows XP Home Cassini'ye ile</span><span class="sxs-lookup"><span data-stu-id="10dda-176">Windows XP Home with Cassini</span></span> | <span data-ttu-id="10dda-177">Hayır</span><span class="sxs-lookup"><span data-stu-id="10dda-177">No</span></span> |

<span data-ttu-id="10dda-178">teşekkürler</span><span class="sxs-lookup"><span data-stu-id="10dda-178">Thanks,</span></span>   
 <span data-ttu-id="10dda-179">ASP.NET takımı</span><span class="sxs-lookup"><span data-stu-id="10dda-179">The ASP.NET Team</span></span>