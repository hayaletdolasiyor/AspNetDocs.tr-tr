---
uid: web-forms/overview/data-access/enhancing-the-gridview/adding-a-gridview-column-of-checkboxes-cs
title: Onay kutularından (C#) oluşan GridView sütunu ekleme | Microsoft Docs
author: rick-anderson
description: Bu öğretici, kullanıcı G. birden çok satır seçme kullanımı kolay bir yol sağlamak üzere bir GridView denetimi için onay kutuları içeren bir sütun ekleme bakan...
ms.author: riande
ms.date: 03/06/2007
ms.assetid: f63a9443-2db0-4f80-8246-840d3e86c2a3
msc.legacyurl: /web-forms/overview/data-access/enhancing-the-gridview/adding-a-gridview-column-of-checkboxes-cs
msc.type: authoredcontent
ms.openlocfilehash: 1921ceeb33197299f3cedb0eef082af0fd8fa960
ms.sourcegitcommit: 24b1f6decbb17bb22a45166e5fdb0845c65af498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57077769"
---
<a name="adding-a-gridview-column-of-checkboxes-c"></a><span data-ttu-id="fe471-103">Onay Kutularından Oluşan GridView Sütunu Ekleme (C#)</span><span class="sxs-lookup"><span data-stu-id="fe471-103">Adding a GridView Column of Checkboxes (C#)</span></span>
====================
<span data-ttu-id="fe471-104">tarafından [Scott Mitchell](https://twitter.com/ScottOnWriting)</span><span class="sxs-lookup"><span data-stu-id="fe471-104">by [Scott Mitchell](https://twitter.com/ScottOnWriting)</span></span>

<span data-ttu-id="fe471-105">[Örnek uygulamayı indirin](http://download.microsoft.com/download/4/a/7/4a7a3b18-d80e-4014-8e53-a6a2427f0d93/ASPNET_Data_Tutorial_52_CS.exe) veya [PDF olarak indirin](adding-a-gridview-column-of-checkboxes-cs/_static/datatutorial52cs1.pdf)</span><span class="sxs-lookup"><span data-stu-id="fe471-105">[Download Sample App](http://download.microsoft.com/download/4/a/7/4a7a3b18-d80e-4014-8e53-a6a2427f0d93/ASPNET_Data_Tutorial_52_CS.exe) or [Download PDF](adding-a-gridview-column-of-checkboxes-cs/_static/datatutorial52cs1.pdf)</span></span>

> <span data-ttu-id="fe471-106">Bu öğretici, kullanıcı birden çok satır GridView'ın seçilmesi, kullanımı kolay bir yol sağlamak üzere bir GridView denetimi için onay kutuları içeren bir sütun ekleme bakar.</span><span class="sxs-lookup"><span data-stu-id="fe471-106">This tutorial looks at how to add a column of check boxes to a GridView control to provide the user with an intuitive way of selecting multiple rows of the GridView.</span></span>


## <a name="introduction"></a><span data-ttu-id="fe471-107">Giriş</span><span class="sxs-lookup"><span data-stu-id="fe471-107">Introduction</span></span>

<span data-ttu-id="fe471-108">Önceki öğreticide size belirli bir kayıt seçmek amacıyla GridView radyo düğmelerinden oluşan bir sütun eklemek nasıl incelenir.</span><span class="sxs-lookup"><span data-stu-id="fe471-108">In the preceding tutorial we examined how to add a column of radio buttons to the GridView for the purpose of selecting a particular record.</span></span> <span data-ttu-id="fe471-109">Kullanıcı kılavuzundan en fazla bir öğe seçmek için sınırlı olduğunda radyo düğmelerinden oluşan bir sütunu uygun kullanıcı arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="fe471-109">A column of radio buttons is a suitable user interface when the user is limited to choosing at most one item from the grid.</span></span> <span data-ttu-id="fe471-110">Bazen, ancak biz kılavuzdan öğeleri tercihe bağlı sayıda kullanıcının izin vermek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe471-110">At times, however, we may want to allow the user to pick an arbitrary number of items from the grid.</span></span> <span data-ttu-id="fe471-111">Web tabanlı e-posta istemcileri, örneğin, genellikle onay kutularından oluşan bir sütun ile iletilerinin listesini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="fe471-111">Web-based email clients, for example, typically display the list of messages with a column of checkboxes.</span></span> <span data-ttu-id="fe471-112">Kullanıcı, iletileri rastgele bir sayıdan seçin ve ardından başka bir klasöre e-postaları taşıma veya silme gibi bazı eylemleri gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="fe471-112">The user can select an arbitrary number of messages and then perform some action, such as moving the emails to another folder or deleting them.</span></span>

<span data-ttu-id="fe471-113">Bu öğreticide onay kutularından oluşan bir sütun eklemek nasıl ve hangi onay kutularını geri göndermede denetlenen belirleme göreceğiz.</span><span class="sxs-lookup"><span data-stu-id="fe471-113">In this tutorial we will see how to add a column of checkboxes and how to determine what checkboxes were checked on postback.</span></span> <span data-ttu-id="fe471-114">Özellikle, web tabanlı e-posta istemcisi kullanıcı arabirimi yakından taklit eden bir örnek oluşturacağız.</span><span class="sxs-lookup"><span data-stu-id="fe471-114">In particular, we'll build an example that closely mimics the web-based email client user interface.</span></span> <span data-ttu-id="fe471-115">Bizim örneğimizde ürünleri listeleme disk belleğine alınan GridView içerecektir `Products` bir onay kutusu her veritabanı tablosu satır (bkz. Şekil 1).</span><span class="sxs-lookup"><span data-stu-id="fe471-115">Our example will include a paged GridView listing the products in the `Products` database table with a checkbox in each row (see Figure 1).</span></span> <span data-ttu-id="fe471-116">Tıklandığında, seçili ürünlerin Sil düğmesini seçili bu ürünlerin silinmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="fe471-116">A Delete Selected Products button, when clicked, will delete those products selected.</span></span>


<span data-ttu-id="fe471-117">[![Bir onay kutusu her bir ürün satır içerir](adding-a-gridview-column-of-checkboxes-cs/_static/image1.gif)](adding-a-gridview-column-of-checkboxes-cs/_static/image1.png)</span><span class="sxs-lookup"><span data-stu-id="fe471-117">[![Each Product Row Includes a Checkbox](adding-a-gridview-column-of-checkboxes-cs/_static/image1.gif)](adding-a-gridview-column-of-checkboxes-cs/_static/image1.png)</span></span>

<span data-ttu-id="fe471-118">**Şekil 1**: Bir onay kutusu her bir ürün satır içerir ([tam boyutlu görüntüyü görmek için tıklatın](adding-a-gridview-column-of-checkboxes-cs/_static/image2.png))</span><span class="sxs-lookup"><span data-stu-id="fe471-118">**Figure 1**: Each Product Row Includes a Checkbox ([Click to view full-size image](adding-a-gridview-column-of-checkboxes-cs/_static/image2.png))</span></span>


## <a name="step-1-adding-a-paged-gridview-that-lists-product-information"></a><span data-ttu-id="fe471-119">1. Adım: Ürün bilgileri listeleyen bir disk belleğine alınan GridView ekleme</span><span class="sxs-lookup"><span data-stu-id="fe471-119">Step 1: Adding a Paged GridView that Lists Product Information</span></span>

<span data-ttu-id="fe471-120">Onay kutularından oluşan bir sütun ekleme hakkında endişe önce disk belleği destekleyen GridView ürünleri listeleme s ilk odaklanmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="fe471-120">Before we worry about adding a column of checkboxes, let s first focus on listing the products in a GridView that supports paging.</span></span> <span data-ttu-id="fe471-121">Başlangıç açarak `CheckBoxField.aspx` sayfasını `EnhancedGridView` klasörü ve ayar Tasarımcısı araç kutusundan sürükleyip GridView kendi `ID` için `Products`.</span><span class="sxs-lookup"><span data-stu-id="fe471-121">Start by opening the `CheckBoxField.aspx` page in the `EnhancedGridView` folder and drag a GridView from the Toolbox onto the Designer, setting its `ID` to `Products`.</span></span> <span data-ttu-id="fe471-122">Ardından, GridView adlı yeni bir ObjectDataSource bağlamak seçin `ProductsDataSource`.</span><span class="sxs-lookup"><span data-stu-id="fe471-122">Next, choose to bind the GridView to a new ObjectDataSource named `ProductsDataSource`.</span></span> <span data-ttu-id="fe471-123">ObjectDataSource kullanmak için yapılandırma `ProductsBLL` çağırma, sınıf `GetProducts()` verileri döndürmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fe471-123">Configure the ObjectDataSource to use the `ProductsBLL` class, calling the `GetProducts()` method to return the data.</span></span> <span data-ttu-id="fe471-124">Bu GridView salt okunur olacağından, güncelleştirme, ekleme, açılan listeler ayarlayın ve sekme (hiçbiri) SİLİN.</span><span class="sxs-lookup"><span data-stu-id="fe471-124">Since this GridView will be read-only, set the drop-down lists in the UPDATE, INSERT, and DELETE tabs to (None) .</span></span>


<span data-ttu-id="fe471-125">[![ProductsDataSource adlı yeni bir ObjectDataSource oluşturma](adding-a-gridview-column-of-checkboxes-cs/_static/image2.gif)](adding-a-gridview-column-of-checkboxes-cs/_static/image3.png)</span><span class="sxs-lookup"><span data-stu-id="fe471-125">[![Create a New ObjectDataSource Named ProductsDataSource](adding-a-gridview-column-of-checkboxes-cs/_static/image2.gif)](adding-a-gridview-column-of-checkboxes-cs/_static/image3.png)</span></span>

<span data-ttu-id="fe471-126">**Şekil 2**: Adlı yeni bir ObjectDataSource oluşturma `ProductsDataSource` ([tam boyutlu görüntüyü görmek için tıklatın](adding-a-gridview-column-of-checkboxes-cs/_static/image4.png))</span><span class="sxs-lookup"><span data-stu-id="fe471-126">**Figure 2**: Create a New ObjectDataSource Named `ProductsDataSource` ([Click to view full-size image](adding-a-gridview-column-of-checkboxes-cs/_static/image4.png))</span></span>


<span data-ttu-id="fe471-127">[![ObjectDataSource GetProducts() yöntemi kullanarak verileri almak için yapılandırma](adding-a-gridview-column-of-checkboxes-cs/_static/image3.gif)](adding-a-gridview-column-of-checkboxes-cs/_static/image5.png)</span><span class="sxs-lookup"><span data-stu-id="fe471-127">[![Configure the ObjectDataSource to Retrieve Data Using the GetProducts() Method](adding-a-gridview-column-of-checkboxes-cs/_static/image3.gif)](adding-a-gridview-column-of-checkboxes-cs/_static/image5.png)</span></span>

<span data-ttu-id="fe471-128">**Şekil 3**: ObjectDataSource kullanarak verileri almak için yapılandırma `GetProducts()` yöntemi ([tam boyutlu görüntüyü görmek için tıklatın](adding-a-gridview-column-of-checkboxes-cs/_static/image6.png))</span><span class="sxs-lookup"><span data-stu-id="fe471-128">**Figure 3**: Configure the ObjectDataSource to Retrieve Data Using the `GetProducts()` Method ([Click to view full-size image](adding-a-gridview-column-of-checkboxes-cs/_static/image6.png))</span></span>


<span data-ttu-id="fe471-129">[![Güncelleştirme, ekleme, açılan listeler ayarlayın ve sekmeleri (hiçbiri) silme](adding-a-gridview-column-of-checkboxes-cs/_static/image4.gif)](adding-a-gridview-column-of-checkboxes-cs/_static/image7.png)</span><span class="sxs-lookup"><span data-stu-id="fe471-129">[![Set the Drop-Down Lists in the UPDATE, INSERT, and DELETE Tabs to (None)](adding-a-gridview-column-of-checkboxes-cs/_static/image4.gif)](adding-a-gridview-column-of-checkboxes-cs/_static/image7.png)</span></span>

<span data-ttu-id="fe471-130">**Şekil 4**: Aşağı açılan listeler güncelleştirme, ekleme ve silme sekmeler (hiçbiri) ayarlayın ([tam boyutlu görüntüyü görmek için tıklatın](adding-a-gridview-column-of-checkboxes-cs/_static/image8.png))</span><span class="sxs-lookup"><span data-stu-id="fe471-130">**Figure 4**: Set the Drop-Down Lists in the UPDATE, INSERT, and DELETE Tabs to (None) ([Click to view full-size image](adding-a-gridview-column-of-checkboxes-cs/_static/image8.png))</span></span>


<span data-ttu-id="fe471-131">Veri Kaynağı Yapılandırma Sihirbazı'nı tamamladıktan sonra BoundColumns ve ürünle ilgili veri alanları için bir CheckBoxColumn otomatik olarak Visual Studio oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fe471-131">After completing the Configure Data Source wizard, Visual Studio will automatically create BoundColumns and a CheckBoxColumn for the product-related data fields.</span></span> <span data-ttu-id="fe471-132">Önceki öğreticide yaptığımız gibi Kaldır dışındaki tüm `ProductName`, `CategoryName`, ve `UnitPrice` BoundFields, değiştirip `HeaderText` ürün, kategori ve fiyat özellikler.</span><span class="sxs-lookup"><span data-stu-id="fe471-132">Like we did in the previous tutorial, remove all but the `ProductName`, `CategoryName`, and `UnitPrice` BoundFields, and change the `HeaderText` properties to Product, Category, and Price.</span></span> <span data-ttu-id="fe471-133">Yapılandırma `UnitPrice` BoundField böylece değerini para birimi olarak biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="fe471-133">Configure the `UnitPrice` BoundField so that its value is formatted as a currency.</span></span> <span data-ttu-id="fe471-134">GridView'ın akıllı etiket sayfalama etkinleştir onay kontrol ederek disk belleği desteği de yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="fe471-134">Also configure the GridView to support paging by checking the Enable Paging checkbox from the smart tag.</span></span>

<span data-ttu-id="fe471-135">Ayrıca seçili ürünlerin silmek için kullanıcı arabirimi ekleme s olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="fe471-135">Let s also add the user interface for deleting the selected products.</span></span> <span data-ttu-id="fe471-136">Ayarı GridView altındaki bir düğme Web denetimi ekleyin, `ID` için `DeleteSelectedProducts` ve kendi `Text` özelliğini Sil ürün seçildi.</span><span class="sxs-lookup"><span data-stu-id="fe471-136">Add a Button Web control beneath the GridView, setting its `ID` to `DeleteSelectedProducts` and its `Text` property to Delete Selected Products.</span></span> <span data-ttu-id="fe471-137">Ürün veritabanından gerçekten silmek yerine, bu örnek için yalnızca, silinmiş ürünleri bildiren bir ileti görüntüleyeceğiz.</span><span class="sxs-lookup"><span data-stu-id="fe471-137">Rather than actually deleting products from the database, for this example we'll just display a message stating the products that would have been deleted.</span></span> <span data-ttu-id="fe471-138">Bunu yapabilmek için bir etiket Web denetimi düğmenin altına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fe471-138">To accommodate this, add a Label Web control beneath the Button.</span></span> <span data-ttu-id="fe471-139">Kimliğine ayarlayın `DeleteResults`kullanıma temizleyin, `Text` özelliği ve kümesi kendi `Visible` ve `EnableViewState` özelliklerine `false`.</span><span class="sxs-lookup"><span data-stu-id="fe471-139">Set its ID to `DeleteResults`, clear out its `Text` property, and set its `Visible` and `EnableViewState` properties to `false`.</span></span>

<span data-ttu-id="fe471-140">Bu değişiklikleri yaptıktan sonra GridView, ObjectDataSource, düğme ve etiket s bildirim temelli biçimlendirme aşağıdakine benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="fe471-140">After making these changes, the GridView, ObjectDataSource, Button, and Label s declarative markup should similar to the following:</span></span>


[!code-aspx[Main](adding-a-gridview-column-of-checkboxes-cs/samples/sample1.aspx)]

<span data-ttu-id="fe471-141">Sayfasını bir tarayıcıda görüntülemek için bir dakikanızı ayırın (bkz: Şekil 5).</span><span class="sxs-lookup"><span data-stu-id="fe471-141">Take a moment to view the page in a browser (see Figure 5).</span></span> <span data-ttu-id="fe471-142">Bu noktada ad, kategori ve fiyat ilk on ürün görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe471-142">At this point you should see the name, category, and price of the first ten products.</span></span>


<span data-ttu-id="fe471-143">[![Ad, kategori ve ilk on ürün fiyatı listelenir.](adding-a-gridview-column-of-checkboxes-cs/_static/image5.gif)](adding-a-gridview-column-of-checkboxes-cs/_static/image9.png)</span><span class="sxs-lookup"><span data-stu-id="fe471-143">[![The Name, Category, and Price of the First Ten Products are Listed](adding-a-gridview-column-of-checkboxes-cs/_static/image5.gif)](adding-a-gridview-column-of-checkboxes-cs/_static/image9.png)</span></span>

<span data-ttu-id="fe471-144">**Şekil 5**: Ad, kategori ve ilk on ürün fiyatı listelenir ([tam boyutlu görüntüyü görmek için tıklatın](adding-a-gridview-column-of-checkboxes-cs/_static/image10.png))</span><span class="sxs-lookup"><span data-stu-id="fe471-144">**Figure 5**: The Name, Category, and Price of the First Ten Products are Listed ([Click to view full-size image](adding-a-gridview-column-of-checkboxes-cs/_static/image10.png))</span></span>


## <a name="step-2-adding-a-column-of-checkboxes"></a><span data-ttu-id="fe471-145">2. Adım: Onay kutularından oluşan bir sütun ekleme</span><span class="sxs-lookup"><span data-stu-id="fe471-145">Step 2: Adding a Column of Checkboxes</span></span>

<span data-ttu-id="fe471-146">ASP.NET 2.0 bir CheckBoxField içerdiğinden, biri, bir sütun onay kutularından oluşan GridView için eklemek için kullanılabilir düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe471-146">Since ASP.NET 2.0 includes a CheckBoxField, one might think that it could be used to add a column of checkboxes to a GridView.</span></span> <span data-ttu-id="fe471-147">CheckBoxField Boole veri alanı ile çalışmak için tasarlandığı gibi ne yazık ki bu durumda değil.</span><span class="sxs-lookup"><span data-stu-id="fe471-147">Unfortunately, that is not the case, as the CheckBoxField is designed to work with a Boolean data field.</span></span> <span data-ttu-id="fe471-148">Diğer bir deyişle, CheckBoxField kullanmak için şu değeri işlenmiş onay kutusunun işaretli olup olmadığını belirlemek için alınmadığında temel alınan veri alanını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe471-148">That is, in order to use the CheckBoxField we must specify the underlying data field whose value is consulted to determine whether the rendered checkbox is checked.</span></span> <span data-ttu-id="fe471-149">Yalnızca işaretli onay kutularından oluşan bir sütun eklemek için biz CheckBoxField kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="fe471-149">We cannot use the CheckBoxField to just include a column of unchecked checkboxes.</span></span>

<span data-ttu-id="fe471-150">Bunun yerine, biz bir TemplateField ekleyin ve bir onay kutusu Web denetimi için eklemeniz gerekir, `ItemTemplate`.</span><span class="sxs-lookup"><span data-stu-id="fe471-150">Instead, we must add a TemplateField and add a CheckBox Web control to its `ItemTemplate`.</span></span> <span data-ttu-id="fe471-151">Bir tane eklemek için bir TemplateField `Products` GridView ve ilk (en sol) alanı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="fe471-151">Go ahead and add a TemplateField to the `Products` GridView and make it the first (far-left) field.</span></span> <span data-ttu-id="fe471-152">GridView s akıllı etiket Şablonları Düzenle bağlantısına tıklayın ve ardından araç kutusundan bir onay kutusu Web denetimi sürükleyin `ItemTemplate`.</span><span class="sxs-lookup"><span data-stu-id="fe471-152">From the GridView s smart tag, click on the Edit Templates link and then drag a CheckBox Web control from the Toolbox into the `ItemTemplate`.</span></span> <span data-ttu-id="fe471-153">Bu onay kutusu s ayarlamak `ID` özelliğini `ProductSelector`.</span><span class="sxs-lookup"><span data-stu-id="fe471-153">Set this CheckBox s `ID` property to `ProductSelector`.</span></span>


<span data-ttu-id="fe471-154">[![ProductSelector TemplateField s ItemTemplate için adlı bir onay kutusu Web denetimi ekleme](adding-a-gridview-column-of-checkboxes-cs/_static/image6.gif)](adding-a-gridview-column-of-checkboxes-cs/_static/image11.png)</span><span class="sxs-lookup"><span data-stu-id="fe471-154">[![Add a CheckBox Web Control Named ProductSelector to the TemplateField s ItemTemplate](adding-a-gridview-column-of-checkboxes-cs/_static/image6.gif)](adding-a-gridview-column-of-checkboxes-cs/_static/image11.png)</span></span>

<span data-ttu-id="fe471-155">**Şekil 6**: Bir onay kutusu Web denetimi adlı ekleme `ProductSelector` TemplateField s `ItemTemplate` ([tam boyutlu görüntüyü görmek için tıklatın](adding-a-gridview-column-of-checkboxes-cs/_static/image12.png))</span><span class="sxs-lookup"><span data-stu-id="fe471-155">**Figure 6**: Add a CheckBox Web Control Named `ProductSelector` to the TemplateField s `ItemTemplate` ([Click to view full-size image](adding-a-gridview-column-of-checkboxes-cs/_static/image12.png))</span></span>


<span data-ttu-id="fe471-156">Eklenen TemplateField ve onay kutusu Web denetimi ile her satır bir onay kutusu artık içerir.</span><span class="sxs-lookup"><span data-stu-id="fe471-156">With the TemplateField and CheckBox Web control added, each row now includes a checkbox.</span></span> <span data-ttu-id="fe471-157">Şekil 7, onay kutusunu ve TemplateField eklendikten sonra bir tarayıcıdan görüntülendiğinde bu sayfayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="fe471-157">Figure 7 shows this page, when viewed through a browser, after the TemplateField and CheckBox have been added.</span></span>


<span data-ttu-id="fe471-158">[![Her ürün satır bir onay kutusu artık içerir.](adding-a-gridview-column-of-checkboxes-cs/_static/image7.gif)](adding-a-gridview-column-of-checkboxes-cs/_static/image13.png)</span><span class="sxs-lookup"><span data-stu-id="fe471-158">[![Each Product Row Now Includes a Checkbox](adding-a-gridview-column-of-checkboxes-cs/_static/image7.gif)](adding-a-gridview-column-of-checkboxes-cs/_static/image13.png)</span></span>

<span data-ttu-id="fe471-159">**Şekil 7**: Her ürün satır bir onay kutusu artık içerir ([tam boyutlu görüntüyü görmek için tıklatın](adding-a-gridview-column-of-checkboxes-cs/_static/image14.png))</span><span class="sxs-lookup"><span data-stu-id="fe471-159">**Figure 7**: Each Product Row Now Includes a Checkbox ([Click to view full-size image](adding-a-gridview-column-of-checkboxes-cs/_static/image14.png))</span></span>


## <a name="step-3-determining-what-checkboxes-were-checked-on-postback"></a><span data-ttu-id="fe471-160">3. Adım: Hangi onay kutularını belirleme geri göndermede iade</span><span class="sxs-lookup"><span data-stu-id="fe471-160">Step 3: Determining What Checkboxes Were Checked On Postback</span></span>

<span data-ttu-id="fe471-161">Bu noktada bir onay kutularını ancak hiçbir şekilde geri göndermede hangi onay kutularını denetlenen belirlenemiyor sütununun sahibiz.</span><span class="sxs-lookup"><span data-stu-id="fe471-161">At this point we have a column of checkboxes but no way to determine what checkboxes were checked on postback.</span></span> <span data-ttu-id="fe471-162">Ancak, seçili ürünlerin Sil düğmesine tıklandığında, biz hangi onay kutularını bu ürünlerin silinmesi için denetlenen bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe471-162">When the Delete Selected Products button is clicked, though, we need to know what checkboxes were checked in order to delete those products.</span></span>

<span data-ttu-id="fe471-163">GridView s [ `Rows` özelliği](https://msdn.microsoft.com/library/system.web.ui.webcontrols.gridview.rows.aspx) GridView veri satırlarına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe471-163">The GridView s [`Rows` property](https://msdn.microsoft.com/library/system.web.ui.webcontrols.gridview.rows.aspx) provides access to the data rows in the GridView.</span></span> <span data-ttu-id="fe471-164">Biz bu satırlara yineleme onay kutusu denetimi programlı olarak erişmek ve ardından başvurun, `Checked` onay kutusunun seçili olup olmadığını belirlemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="fe471-164">We can iterate through these rows, programmatically access the CheckBox control, and then consult its `Checked` property to determine whether the CheckBox has been selected.</span></span>

<span data-ttu-id="fe471-165">İçin bir olay işleyicisi oluşturun `DeleteSelectedProducts` düğmesi Web denetimi s `Click` olay ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="fe471-165">Create an event handler for the `DeleteSelectedProducts` Button Web control s `Click` event and add the following code:</span></span>


[!code-csharp[Main](adding-a-gridview-column-of-checkboxes-cs/samples/sample2.cs)]

<span data-ttu-id="fe471-166">`Rows` Özellik koleksiyonunu döndürür `GridViewRow` GridView s veri satırları, düzenini örnekler.</span><span class="sxs-lookup"><span data-stu-id="fe471-166">The `Rows` property returns a collection of `GridViewRow` instances that makeup the GridView s data rows.</span></span> <span data-ttu-id="fe471-167">`foreach` Döngü burada bu koleksiyon numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="fe471-167">The `foreach` loop here enumerates this collection.</span></span> <span data-ttu-id="fe471-168">Her `GridViewRow` nesnesi, satır s onay kutusu, kullanarak program aracılığıyla erişildiğinde `row.FindControl("controlID")`.</span><span class="sxs-lookup"><span data-stu-id="fe471-168">For each `GridViewRow` object, the row s CheckBox is programmatically accessed using `row.FindControl("controlID")`.</span></span> <span data-ttu-id="fe471-169">Onay kutusu işaretli değilse, ilgili satır s `ProductID` değer alınır `DataKeys` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="fe471-169">If the CheckBox is checked, the row s corresponding `ProductID` value is retrieved from the `DataKeys` collection.</span></span> <span data-ttu-id="fe471-170">Bu alıştırmada, yalnızca bilgilendirici iletisinde görüntüleriz `DeleteResults` içinde çalışan bir uygulama d biz bunun yerine çağrı yapmak olsa da, etiket `ProductsBLL` s sınıfı `DeleteProduct(productID)` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fe471-170">In this exercise, we simply display an informative message in the `DeleteResults` Label, although in a working application we d instead make a call to the `ProductsBLL` class s `DeleteProduct(productID)` method.</span></span>

<span data-ttu-id="fe471-171">Bu olay işleyicisi'nın eklenmesiyle, seçili ürünlerin silme artık düğmesi görüntüler `ProductID` seçili ürünlerin s.</span><span class="sxs-lookup"><span data-stu-id="fe471-171">With the addition of this event handler, clicking the Delete Selected Products button now displays the `ProductID` s of the selected products.</span></span>


<span data-ttu-id="fe471-172">[![Seçili ürün ProductIDs Sil Seçili ürünleri düğmesine tıklandığında listelenir](adding-a-gridview-column-of-checkboxes-cs/_static/image8.gif)](adding-a-gridview-column-of-checkboxes-cs/_static/image15.png)</span><span class="sxs-lookup"><span data-stu-id="fe471-172">[![When the Delete Selected Products Button is Clicked the Selected Products ProductIDs are Listed](adding-a-gridview-column-of-checkboxes-cs/_static/image8.gif)](adding-a-gridview-column-of-checkboxes-cs/_static/image15.png)</span></span>

<span data-ttu-id="fe471-173">**Şekil 8**: Ne zaman Sil Seçili ürünleri düğmesine tıklandığında ürün seçildi `ProductID` s listelenir ([tam boyutlu görüntüyü görmek için tıklatın](adding-a-gridview-column-of-checkboxes-cs/_static/image16.png))</span><span class="sxs-lookup"><span data-stu-id="fe471-173">**Figure 8**: When the Delete Selected Products Button is Clicked the Selected Products `ProductID` s are Listed ([Click to view full-size image](adding-a-gridview-column-of-checkboxes-cs/_static/image16.png))</span></span>


## <a name="step-4-adding-check-all-and-uncheck-all-buttons"></a><span data-ttu-id="fe471-174">4. Adım: Ekleme tüm denetler ve tüm düğmeler işaretini kaldırın</span><span class="sxs-lookup"><span data-stu-id="fe471-174">Step 4: Adding Check All and Uncheck All Buttons</span></span>

<span data-ttu-id="fe471-175">Bir kullanıcı geçerli sayfadaki tüm ürünleri silme istiyorsa, bunlar her on onay kutularını işaretlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe471-175">If a user wants to delete all products on the current page, they must check each of the ten checkboxes.</span></span> <span data-ttu-id="fe471-176">Bir kontrol tüm ekleyerek bu işlemi hızlandırmak yardımcı olabiliriz, düğmesine tıklandığında, tüm onay kutularını kılavuzda seçer.</span><span class="sxs-lookup"><span data-stu-id="fe471-176">We can help expedite this process by adding a Check All button that, when clicked, selects all of the checkboxes in the grid.</span></span> <span data-ttu-id="fe471-177">Bir onay kutusunu temizleyin tüm düğmesi eşit yardımcı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="fe471-177">An Uncheck All button would be equally helpful.</span></span>

<span data-ttu-id="fe471-178">Bunları GridView yerleştirme sayfasına iki düğme Web denetimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fe471-178">Add two Button Web controls to the page, placing them above the GridView.</span></span> <span data-ttu-id="fe471-179">İlk s ayarlamak `ID` için `CheckAll` ve kendi `Text` özelliğini denetle; ikinci bir s kümesi `ID` için `UncheckAll` ve kendi `Text` özelliğini tüm işaretini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="fe471-179">Set the first one s `ID` to `CheckAll` and its `Text` property to Check All ; set the second one s `ID` to `UncheckAll` and its `Text` property to Uncheck All .</span></span>


[!code-aspx[Main](adding-a-gridview-column-of-checkboxes-cs/samples/sample3.aspx)]

<span data-ttu-id="fe471-180">Ardından, arka plan kod sınıfı adlı bir yöntem oluşturma `ToggleCheckState(checkState)` , çağrıldığında numaralandırır `Products` GridView s `Rows` koleksiyonu ve her onay kutusu s ayarlar `Checked` geçirilen değere içinde *checkState*  parametresi.</span><span class="sxs-lookup"><span data-stu-id="fe471-180">Next, create a method in the code-behind class named `ToggleCheckState(checkState)` that, when invoked, enumerates the `Products` GridView s `Rows` collection and sets each CheckBox s `Checked` property to the value of the passed in *checkState* parameter.</span></span>


[!code-csharp[Main](adding-a-gridview-column-of-checkboxes-cs/samples/sample4.cs)]

<span data-ttu-id="fe471-181">Ardından, oluşturma `Click` için olay işleyicileri `CheckAll` ve `UncheckAll` düğmeleri.</span><span class="sxs-lookup"><span data-stu-id="fe471-181">Next, create `Click` event handlers for the `CheckAll` and `UncheckAll` buttons.</span></span> <span data-ttu-id="fe471-182">İçinde `CheckAll` s olay işleyicisi, yalnızca çağrı `ToggleCheckState(true)`; `UncheckAll`, çağrı `ToggleCheckState(false)`.</span><span class="sxs-lookup"><span data-stu-id="fe471-182">In `CheckAll` s event handler, simply call `ToggleCheckState(true)`; in `UncheckAll`, call `ToggleCheckState(false)`.</span></span>


[!code-csharp[Main](adding-a-gridview-column-of-checkboxes-cs/samples/sample5.cs)]

<span data-ttu-id="fe471-183">Bu kod denetle düğmesine tıklayarak geri göndermeye neden olur ve tüm onay kutularını GridView de denetler.</span><span class="sxs-lookup"><span data-stu-id="fe471-183">With this code, clicking the Check All button causes a postback and checks all of the checkboxes in the GridView.</span></span> <span data-ttu-id="fe471-184">Benzer şekilde, tüm onay kutularının işaretini kaldırın tüm tıklayarak seçili olanları kaldırdığında.</span><span class="sxs-lookup"><span data-stu-id="fe471-184">Likewise, clicking Uncheck All unselects all checkboxes.</span></span> <span data-ttu-id="fe471-185">Şekil 9, denetle düğmesine kaydedildikten sonra ekranı gösterilir.</span><span class="sxs-lookup"><span data-stu-id="fe471-185">Figure 9 shows the screen after the Check All button has been checked.</span></span>


<span data-ttu-id="fe471-186">[![Tüm düğme denetimi tıklayarak tüm onay kutularının seçer](adding-a-gridview-column-of-checkboxes-cs/_static/image9.gif)](adding-a-gridview-column-of-checkboxes-cs/_static/image17.png)</span><span class="sxs-lookup"><span data-stu-id="fe471-186">[![Clicking the Check All Button Selects All Checkboxes](adding-a-gridview-column-of-checkboxes-cs/_static/image9.gif)](adding-a-gridview-column-of-checkboxes-cs/_static/image17.png)</span></span>

<span data-ttu-id="fe471-187">**Şekil 9**: Denetleme tüm düğmesini seçer tüm onay kutularını tıklayarak ([tam boyutlu görüntüyü görmek için tıklatın](adding-a-gridview-column-of-checkboxes-cs/_static/image18.png))</span><span class="sxs-lookup"><span data-stu-id="fe471-187">**Figure 9**: Clicking the Check All Button Selects All Checkboxes ([Click to view full-size image](adding-a-gridview-column-of-checkboxes-cs/_static/image18.png))</span></span>


> [!NOTE]
> <span data-ttu-id="fe471-188">Onay kutusunu seçerek veya onay kutularını tümünün seçimini için bir yaklaşım bir sütunu görüntüleme için başlık satırındaki onay kutusu aracılığıyla olduğunda.</span><span class="sxs-lookup"><span data-stu-id="fe471-188">When displaying a column of checkboxes, one approach for selecting or unselecting all of the checkboxes is through a checkbox in the header row.</span></span> <span data-ttu-id="fe471-189">Ayrıca, geçerli tüm denetleyin / işaretini kaldırın tüm uygulama bir geri gönderme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="fe471-189">Moreover, the current Check All / Uncheck All implementation requires a postback.</span></span> <span data-ttu-id="fe471-190">Onay kutularını, ancak işaretli veya işaretsiz, böylece snappier bir kullanıcı deneyimi sağlayan tamamen istemci tarafı komut dosyası, olabilir.</span><span class="sxs-lookup"><span data-stu-id="fe471-190">The checkboxes can be checked or unchecked, however, entirely through client-side script, thereby providing a snappier user experience.</span></span> <span data-ttu-id="fe471-191">Bir üst bilgi satırı onay kutusuna, istemci tarafı teknikleri kullanma hakkında bir tartışma yanı sıra ayrıntılı denetle ve tüm işaretini kaldırın kullanarak keşfetmek için kullanıma [denetimi tüm onay kutularının GridView kullanarak istemci tarafı komut dosyası ve bir onay tüm kutusu](http://aspnet.4guysfromrolla.com/articles/053106-1.aspx).</span><span class="sxs-lookup"><span data-stu-id="fe471-191">To explore using a header row checkbox for Check All and Uncheck All in detail, along with a discussion on using client-side techniques, check out [Checking All CheckBoxes in a GridView Using Client-Side Script and a Check All CheckBox](http://aspnet.4guysfromrolla.com/articles/053106-1.aspx).</span></span>


## <a name="summary"></a><span data-ttu-id="fe471-192">Özet</span><span class="sxs-lookup"><span data-stu-id="fe471-192">Summary</span></span>

<span data-ttu-id="fe471-193">Devam etmeden önce GridView satır rastgele bir sayıdan arasından kullanıcıların gerek duyduğunuz senaryolara durumda onay kutularından oluşan bir sütun ekleyerek bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="fe471-193">In cases where you need to let users choose an arbitrary number of rows from a GridView before proceeding, adding a column of checkboxes is one option.</span></span> <span data-ttu-id="fe471-194">Bu öğreticide gördüğümüz gibi GridView içinde onay kutularından oluşan bir sütun içeren bir onay kutusu Web denetimi ile bir TemplateField ekleme kapsar.</span><span class="sxs-lookup"><span data-stu-id="fe471-194">As we saw in this tutorial, including a column of checkboxes in the GridView entails adding a TemplateField with a CheckBox Web control.</span></span> <span data-ttu-id="fe471-195">Bir Web denetimi (biz önceki öğreticide yaptığınız gibi karşı biçimlendirme şablonuna doğrudan ekleme) kullanarak ASP.NET otomatik olarak hatırlar ne onay kutularını olan ve geri gönderme arasında işaretli değil.</span><span class="sxs-lookup"><span data-stu-id="fe471-195">By using a Web control (versus injecting markup directly into the template, as we did in the previous tutorial) ASP.NET automatically remembers what CheckBoxes were and were not checked across postback.</span></span> <span data-ttu-id="fe471-196">Biz, onay kutularını kodda belirli bir onay kutusunun işaretli olup olmadığını belirlemek için ya da işaretli durumu değiştirmek için program aracılığıyla da erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe471-196">We can also programmatically access the CheckBoxes in code to determine whether a given CheckBox is checked, or to chnage the checked state.</span></span>

<span data-ttu-id="fe471-197">Bu öğretici ve sonuncu GridView'a satır seçici sütun ekleme sırasında arıyordu.</span><span class="sxs-lookup"><span data-stu-id="fe471-197">This tutorial and the last one looked at adding a row selector column to the GridView.</span></span> <span data-ttu-id="fe471-198">Sonraki müşterilerimize öğreticide nasıl ile biraz iş ekleme özellikleri GridView'a ekleyebiliriz inceleyeceğiz.</span><span class="sxs-lookup"><span data-stu-id="fe471-198">In our next tutorial we'll examine how, with a bit of work, we can add inserting capabilities to the GridView.</span></span>

<span data-ttu-id="fe471-199">Mutlu programlama!</span><span class="sxs-lookup"><span data-stu-id="fe471-199">Happy Programming!</span></span>

## <a name="about-the-author"></a><span data-ttu-id="fe471-200">Yazar hakkında</span><span class="sxs-lookup"><span data-stu-id="fe471-200">About the Author</span></span>

<span data-ttu-id="fe471-201">[Scott Mitchell](http://www.4guysfromrolla.com/ScottMitchell.shtml), yazar yedi ASP/ASP.NET kitaplardan ve poshbeauty.com sitesinin [4GuysFromRolla.com](http://www.4guysfromrolla.com), Microsoft Web teknolojileriyle beri 1998'de çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fe471-201">[Scott Mitchell](http://www.4guysfromrolla.com/ScottMitchell.shtml), author of seven ASP/ASP.NET books and founder of [4GuysFromRolla.com](http://www.4guysfromrolla.com), has been working with Microsoft Web technologies since 1998.</span></span> <span data-ttu-id="fe471-202">Scott, bağımsız Danışman, Eğitimci ve yazıcı çalışır.</span><span class="sxs-lookup"><span data-stu-id="fe471-202">Scott works as an independent consultant, trainer, and writer.</span></span> <span data-ttu-id="fe471-203">En son nitelemiştir olan [ *Unleashed'i öğretin kendiniz ASP.NET 2.0 24 saat içindeki*](https://www.amazon.com/exec/obidos/ASIN/0672327384/4guysfromrollaco).</span><span class="sxs-lookup"><span data-stu-id="fe471-203">His latest book is [*Sams Teach Yourself ASP.NET 2.0 in 24 Hours*](https://www.amazon.com/exec/obidos/ASIN/0672327384/4guysfromrollaco).</span></span> <span data-ttu-id="fe471-204">He adresinden ulaşılabilir [ mitchell@4GuysFromRolla.com.](mailto:mitchell@4GuysFromRolla.com)</span><span class="sxs-lookup"><span data-stu-id="fe471-204">He can be reached at [mitchell@4GuysFromRolla.com.](mailto:mitchell@4GuysFromRolla.com)</span></span> <span data-ttu-id="fe471-205">veya kendi blog hangi bulunabilir [ http://ScottOnWriting.NET ](http://ScottOnWriting.NET).</span><span class="sxs-lookup"><span data-stu-id="fe471-205">or via his blog, which can be found at [http://ScottOnWriting.NET](http://ScottOnWriting.NET).</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="fe471-206">[Önceki](adding-a-gridview-column-of-radio-buttons-cs.md)
> [İleri](inserting-a-new-record-from-the-gridview-s-footer-cs.md)</span><span class="sxs-lookup"><span data-stu-id="fe471-206">[Previous](adding-a-gridview-column-of-radio-buttons-cs.md)
[Next](inserting-a-new-record-from-the-gridview-s-footer-cs.md)</span></span>