---
uid: mvc/overview/getting-started/introduction/examining-the-details-and-delete-methods
title: Ayrıntıları ve silme yöntemlerini İnceleme | Microsoft Docs
author: Rick-Anderson
description: ''
ms.author: riande
ms.date: 03/26/2015
ms.assetid: f1d2a916-626c-4a54-8df4-77e6b9fff355
msc.legacyurl: /mvc/overview/getting-started/introduction/examining-the-details-and-delete-methods
msc.type: authoredcontent
ms.openlocfilehash: 9c4e66454d6995bd750b62ef8b461bcfbdfb4b4f
ms.sourcegitcommit: 4e6d586faadbe4d9ef27122f86335ec9385134af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2020
ms.locfileid: "89045097"
---
# <a name="examining-the-details-and-delete-methods"></a>Details ve Delete Metotlarını inceleme

[Rick Anderson](https://twitter.com/RickAndMSFT) tarafından

[!INCLUDE [consider RP](~/includes/razor.md)]

Öğreticinin bu bölümünde otomatik olarak oluşturulan `Details` ve yöntemleri inceleyeceksiniz `Delete` .

## <a name="examining-the-details-and-delete-methods"></a>Details ve Delete Metotlarını inceleme

Denetleyiciyi açın `Movie` ve `Details` metodunu inceleyin.

![](examining-the-details-and-delete-methods/_static/image1.png)

[!code-csharp[Main](examining-the-details-and-delete-methods/samples/sample1.cs)]

Bu eylem yöntemini oluşturan MVC yapı iskelesi altyapısı, yöntemi çağıran bir HTTP isteğini gösteren bir açıklama ekler. Bu durumda `GET` , üç URL segmentine, `Movies` denetleyiciye, `Details` yönteme ve bir değere sahip bir istek vardır `ID` .

Code First yöntemi kullanarak verileri aramanızı kolaylaştırır `Find` . Yöntemi içinde yerleşik olarak bulunan önemli bir güvenlik özelliği, kodun, `Find` kod ile herhangi bir şey yapmayı denemeden önce yöntemin bir filmi buldığını doğruladığından emin değildir. Örneğin, bir korsan bağlantıları tarafından oluşturulan URL 'yi `http://localhost:xxxx/Movies/Details/1` `http://localhost:xxxx/Movies/Details/12345` (veya gerçek bir filmi temsil eden başka bir değer) gibi bir konuma değiştirerek siteye hata verebilir. Null bir filmi denetmediyseniz, null bir film bir veritabanı hatasına neden olur.

`Delete`Ve yöntemlerini inceleyin `DeleteConfirmed` .

[!code-csharp[Main](examining-the-details-and-delete-methods/samples/sample2.cs?highlight=17)]

HTTP GET `Delete` yönteminin belirtilen filmi silmediğini unutmayın. Bu, silme işlemini gönderebileceğiniz () filmin bir görünümünü döndürür `HttpPost` . Bir GET isteğine yanıt olarak silme işlemi gerçekleştirme (veya bu konuyla ilgili olarak, düzenleme işlemi gerçekleştirme, oluşturma işlemi yapma veya verileri değiştiren başka bir işlem) bir güvenlik deliği açılır. Bunun hakkında daha fazla bilgi için bkz. Stephen Walther Web günlüğü girdisi [ASP.NET MVC ipucu #46 — güvenlik delikleri oluşturdıklarından, silme bağlantılarını kullanmayın](http://stephenwalther.com/blog/archive/2009/01/21/asp.net-mvc-tip-46-ndash-donrsquot-use-delete-links-because.aspx).

`HttpPost`Verileri silen yöntemi, `DeleteConfirmed` http post yöntemine benzersiz bir imza veya ad vermek için olarak adlandırılır. İki yöntem imzası aşağıda gösterilmiştir:

[!code-csharp[Main](examining-the-details-and-delete-methods/samples/sample3.cs)]

Ortak dil çalışma zamanı (CLR), aşırı yüklenmiş yöntemlerin benzersiz bir parametre imzasına sahip olmasını gerektirir (aynı yöntem adı ancak farklı parametre listesi). Bununla birlikte, her ikisi de aynı parametre imzasına sahip olan--GET için bir tane olmak üzere iki silme yöntemine ihtiyacınız vardır. (Her ikisi de parametre olarak tek bir tamsayıyı kabul etmelidir.)

Bunu sıralamak için birkaç şey yapabilirsiniz. Bunlardan biri, yöntemlere farklı adlar vermektir. Bu, önceki örnekte bulunan yapı iskelesi mekanizmasına göre yapılır. Ancak, bu küçük bir sorun ortaya çıkarır: ASP.NET bir URL 'nin segmentlerini ada göre eylem yöntemlerine eşler ve bir yöntemi yeniden adlandırırsanız, yönlendirme normalde bu yöntemi bulamaz. Çözüm, örnekte gördüğünüz şeydir. Bu, `ActionName("Delete")` yöntemine özniteliği eklemektir `DeleteConfirmed` . Bu, bir POST isteği için */Delete/* IÇEREN bir URL 'nin yöntemini bulabilmesi için yönlendirme sistemi için eşlemeyi etkili bir şekilde gerçekleştirir `DeleteConfirmed` .

Özdeş adlara ve imzalara sahip Yöntemler ile ilgili bir sorunu önlemenin diğer yaygın bir yolu, yapay for the POST yönteminin imzasını kullanılmayan bir parametre içerecek şekilde değiştirmaktır. Örneğin, bazı geliştiriciler POST yöntemine geçirilen bir parametre türü ekler `FormCollection` ve sonra yalnızca parametresini kullanmayın:

[!code-csharp[Main](examining-the-details-and-delete-methods/samples/sample4.cs)]

## <a name="summary"></a>Özet

Artık yerel bir veritabanı veritabanında veri depolayan bir ASP.NET MVC uygulamanız var. Film oluşturabilir, okuyabilir, güncelleştirebilir, silebilir ve arayabilirsiniz.

![](examining-the-details-and-delete-methods/_static/image2.png)

## <a name="next-steps"></a>Sonraki Adımlar

Bir Web uygulaması oluşturup test ettikten sonra, bir sonraki adım, diğer kişilerin Internet üzerinden kullanması için kullanılabilir hale gelir. Bunu yapmak için, bir Web barındırma sağlayıcısına dağıtmanız gerekir. Microsoft, [ücretsiz bir Azure deneme hesabında](https://www.windowsazure.com/pricing/free-trial/?WT.mc_id=A443DD604)en fazla 10 Web sitesi için ücretsiz web barındırma hizmeti sunar. Bir sonraki öğreticimin [Azure 'A üyelik, OAuth ve SQL veritabanı Ile güvenli bir ASP.NET MVC uygulaması dağıtma](https://docs.microsoft.com/aspnet/core/security/authorization/secure-data)hakkında daha fazla önerdim. Harika bir öğretici, [bir ASP.NET MVC uygulaması için Entity Framework veri modeli oluşturma](../getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application.md)Tom Dykstra 'in ara düzeyindedir. [StackOverflow](http://stackoverflow.com/help) ve [ASP.NET MVC forumları](https://forums.asp.net/1146.aspx) , soru sormak için harika bir yerdir. En son öğreticilerimde güncelleştirmeleri alabilmeniz için Twitter 'da [beni](https://twitter.com/RickAndMSFT) izleyin.

Geribildirim hoş geldiniz.

— [Rick Anderson](https://blogs.msdn.com/rickAndy) Twitter: [@RickAndMSFT](https://twitter.com/RickAndMSFT)  
— [Scott Hanselman](http://www.hanselman.com/blog/) Twitter: [@shanselman](https://twitter.com/shanselman)

> [!div class="step-by-step"]
> [Önceki](adding-validation.md)
