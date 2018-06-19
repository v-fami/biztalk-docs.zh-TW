---
title: Windows SharePoint Services 4.0 支援 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 84be7aa0-2ff2-4e40-9c39-5cb89549c636
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff27ebd5804f3603aabf3bae24e469c2028234f2
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
ms.locfileid: "26009967"
---
# <a name="windows-sharepoint-services-40-support"></a><span data-ttu-id="2b8f3-102">Windows SharePoint Services 4.0 支援</span><span class="sxs-lookup"><span data-stu-id="2b8f3-102">Windows SharePoint Services 4.0 Support</span></span>
<span data-ttu-id="2b8f3-103">BizTalk Server 的 Windows SharePoint Services 配接器提供的 Windows SharePoint Services 配接器的功能同位檢查[!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-103">The Windows SharePoint Services adapter for BizTalk Server provides feature/functionality parity with the Windows SharePoint Services adapter for [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)].</span></span> <span data-ttu-id="2b8f3-104">BizTalk Server 的 Windows SharePoint Services 配接器也支援 Windows SharePoint Services 4.0 提供的下列功能：</span><span class="sxs-lookup"><span data-stu-id="2b8f3-104">The Windows SharePoint Services adapter for BizTalk Server also supports the following functionality available with Windows SharePoint Services 4.0:</span></span>  
  
-   <span data-ttu-id="2b8f3-105">傳送訊息至 Windows SharePoint Services 4.0 部落格網站。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-105">Sending messages to a Windows SharePoint Services 4.0 blog site.</span></span>  
  
-   <span data-ttu-id="2b8f3-106">傳送訊息至 Windows SharePoint Services 4.0 Wiki 網站，以及從 Windows SharePoint Services 4.0 Wiki 網站接收訊息。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-106">Sending messages to and receiving message from a Windows SharePoint Services 4.0 Wiki site.</span></span>  
  
 <span data-ttu-id="2b8f3-107">BizTalk Server 的 Windows SharePoint Services 配接器不支援 Windows SharePoint Services 4.0 中可用的下列功能：</span><span class="sxs-lookup"><span data-stu-id="2b8f3-107">The Windows SharePoint Services adapter for BizTalk Server does not provide support for the following features that are available in Windows SharePoint Services 4.0:</span></span>  
  
-   <span data-ttu-id="2b8f3-108">**資源回收筒**： 為 BizTalk Server 配接器的 Windows SharePoint Services 配接器不支援接收，或明確傳送訊息從至資源回收筒。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-108">**Recycle Bin**: The Windows SharePoint Services adapter for BizTalk Server adapter does not support receiving, or explicitly sending messages from/to the Recycle Bin.</span></span>  
  
-   <span data-ttu-id="2b8f3-109">**列出資料夾**: BizTalk server 的 Windows SharePoint Services 配接器傳送訊息至清單，但不是能從清單接收訊息。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-109">**Lists folders**: The Windows SharePoint Services adapter for BizTalk Server can send messages to lists but it cannot receive messages from lists.</span></span> <span data-ttu-id="2b8f3-110">Windows SharePoint Services 4.0 支援清單中的資料夾，但 BizTalk Server 的 Windows SharePoint Services 配接器不支援這項功能。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-110">Windows SharePoint Services 4.0 supports folders in lists but the Windows SharePoint Services adapter for BizTalk Server does not support this feature.</span></span> <span data-ttu-id="2b8f3-111">因此，BizTalk Server 的 Windows SharePoint Services 配接器無法在根資料夾以外的清單資料夾中建立清單項目。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-111">Therefore, the Windows SharePoint Services adapter for BizTalk Server cannot create list items in a list folder other than the root folder.</span></span>  
  
-   <span data-ttu-id="2b8f3-112">下列章節將更詳細地如何使用 BizTalk Server 的 Windows SharePoint Services 配接器傳送訊息至 Windows SharePoint Services 4.0 部落格網站，以及如何傳送訊息至而從 Windows SharePoint Services 接收訊息4.0 Wiki 網站。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-112">The following sections describe in greater detail how to use the Windows SharePoint Services adapter for BizTalk Server to send messages to a Windows SharePoint Services 4.0 blog site and how to send messages to and receive messages from a Windows SharePoint Services 4.0 Wiki site.</span></span>  
  
## <a name="sending-to-a-windows-sharepoint-services-40-blog-site"></a><span data-ttu-id="2b8f3-113">傳送至 Windows SharePoint Services 4.0 部落格網站</span><span class="sxs-lookup"><span data-stu-id="2b8f3-113">Sending to a Windows SharePoint Services 4.0 Blog Site</span></span>  
 <span data-ttu-id="2b8f3-114">在 Windows SharePoint Services 4.0 部落格網站中，文章儲存在 **文章** 中所定義的清單，而文章類別 **類別** 清單。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-114">In a Windows SharePoint Services 4.0 blog site, posts are stored in the **Posts** list and post categories are defined in the **Categories** list.</span></span>  
  
 <span data-ttu-id="2b8f3-115">若要張貼訊息至 Windows SharePoint Services 4.0 部落格網站，配接器中，輸入下列值 **傳輸屬性** 時設定使用 Windows SharePoint Services 配接器的傳送埠 對話方塊︰</span><span class="sxs-lookup"><span data-stu-id="2b8f3-115">To post a message to a Windows SharePoint Services 4.0 blog site, enter the following values in the adapter **Transport Properties** dialog box when configuring a send port that uses the Windows SharePoint Services adapter:</span></span>  
  
|<span data-ttu-id="2b8f3-116">屬性</span><span class="sxs-lookup"><span data-stu-id="2b8f3-116">Property</span></span>|<span data-ttu-id="2b8f3-117">Value</span><span class="sxs-lookup"><span data-stu-id="2b8f3-117">Value</span></span>|  
|--------------|-----------|  
|<span data-ttu-id="2b8f3-118">目的資料夾 URL</span><span class="sxs-lookup"><span data-stu-id="2b8f3-118">Destination Folder URL</span></span>|<span data-ttu-id="2b8f3-119">相對於 SharePoint 網站之 Posts 清單 (例如 "Lists/Posts") 的目的資料夾 URL。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-119">Destination folder URL of the Posts list, relative to the SharePoint site, for example "Lists/Posts".</span></span>|  
|<span data-ttu-id="2b8f3-120">SharePoint 網站 URL</span><span class="sxs-lookup"><span data-stu-id="2b8f3-120">SharePoint Site URL</span></span>|<span data-ttu-id="2b8f3-121">Windows SharePoint Services 4.0 部落格網站，例如 http:// URL*\<servername\>*/sites/部落格/其中*\<servername\>* 是Web 伺服器的實際名稱的預留位置。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-121">URL of the Windows SharePoint Services 4.0 blog site, for example http://*\<servername\>*/sites/blog/ where *\<servername\>* is a placeholder for the actual name of the Web server.</span></span>|  
  
 <span data-ttu-id="2b8f3-122">然後設定的值 **類別**, ，**發佈**, ，**標題**, ，和 **主體** 部落格張貼在 WSS 中設定對應值的屬性。ConfigPropertiesXml 的訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-122">Then set the values for the **Category**, **Published**, **Title**, and **Body** properties for the blog posting by setting corresponding values in the WSS.ConfigPropertiesXml context property of the message.</span></span> <span data-ttu-id="2b8f3-123">此步驟可以在自訂管線或協調流程中進行。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-123">This can be done with a custom pipeline or in an orchestration.</span></span> <span data-ttu-id="2b8f3-124">例如，協調流程中的下列運算式會設定 Message_Out 訊息之 WSS.ConfigPropertiesXml 內容屬性中的值：</span><span class="sxs-lookup"><span data-stu-id="2b8f3-124">For example, the following expression in an orchestration would set values in the WSS.ConfigPropertiesXml context property of the Message_Out message.</span></span>  
  
```  
int_Category = 1;  
str_Published = Microsoft.SharePoint.Utilities.SPUtility.CreateISO8601DateTimeFromSystemDateTime(System.DateTime.Now);  
// requires a reference to Microsoft.SharePoint.dll  
str_Title = "This is the title of the post from the WSS adapter";  
str_Body = "This is the body of the post from the WSS adapter";  
  
Message_Out(WSS.ConfigPropertiesXml) = “<ConfigPropertiesXml>  
<PropertyName1>Category</PropertyName1>  
<PropertySource1>” + int_Category + “</PropertySource1>  
<PropertyName2>Published</PropertyName2>  
<PropertySource2>” + str_Published + “</PropertySource2>  
<PropertyName3>Title</PropertyName3>  
<PropertySource3>” + str_Title + “</PropertySource3>  
<PropertyName4>Body</PropertyName4>  
<PropertySource4>” + str_Body + “</PropertySource4>  
</ConfigPropertiesXml>”;  
```  
  
 <span data-ttu-id="2b8f3-125">此運算式中的變數會使用下列型別：</span><span class="sxs-lookup"><span data-stu-id="2b8f3-125">The variables in this expression would use the following types:</span></span>  
  
|<span data-ttu-id="2b8f3-126">變數名稱</span><span class="sxs-lookup"><span data-stu-id="2b8f3-126">Variable name</span></span>|<span data-ttu-id="2b8f3-127">型別</span><span class="sxs-lookup"><span data-stu-id="2b8f3-127">Type</span></span>|  
|-------------------|----------|  
|<span data-ttu-id="2b8f3-128">int_Category</span><span class="sxs-lookup"><span data-stu-id="2b8f3-128">int_Category</span></span>|<span data-ttu-id="2b8f3-129">System.Int32</span><span class="sxs-lookup"><span data-stu-id="2b8f3-129">System.Int32</span></span>|  
|<span data-ttu-id="2b8f3-130">str_Published</span><span class="sxs-lookup"><span data-stu-id="2b8f3-130">str_Published</span></span>|<span data-ttu-id="2b8f3-131">System.String</span><span class="sxs-lookup"><span data-stu-id="2b8f3-131">System.String</span></span>|  
|<span data-ttu-id="2b8f3-132">str_Title</span><span class="sxs-lookup"><span data-stu-id="2b8f3-132">str_Title</span></span>|<span data-ttu-id="2b8f3-133">System.String</span><span class="sxs-lookup"><span data-stu-id="2b8f3-133">System.String</span></span>|  
|<span data-ttu-id="2b8f3-134">str_Body</span><span class="sxs-lookup"><span data-stu-id="2b8f3-134">str_Body</span></span>|<span data-ttu-id="2b8f3-135">System.String</span><span class="sxs-lookup"><span data-stu-id="2b8f3-135">System.String</span></span>|  
  
 <span data-ttu-id="2b8f3-136">這種方式建立的文章將設定的狀態 **未核准**, ，這會需要部落格擁有者的核准，才能顯示在網站上。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-136">A post created this way will be set to a state of **not approved**, which will require approval by the blog owner before it is visible on the site.</span></span>  
  
 <span data-ttu-id="2b8f3-137">支援的清單資料行類型可以在清單的設定頁面上檢視。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-137">The supported column types for the list can be viewed on the settings page for the list.</span></span> <span data-ttu-id="2b8f3-138">如需 Windows SharePoint Services 配接器所支援的 Windows SharePoint Services 資料行類型的詳細資訊，請參閱[Windows SharePoint Services 配接器屬性參考](../core/windows-sharepoint-services-adapter-properties-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-138">For more information about the Windows SharePoint Services column types that are supported by the Windows SharePoint Services adapter, see [Windows SharePoint Services Adapter Properties Reference](../core/windows-sharepoint-services-adapter-properties-reference.md).</span></span>  
  
## <a name="sending-to-and-receiving-from-a-windows-sharepoint-services-40-wiki-document-library"></a><span data-ttu-id="2b8f3-139">傳送訊息至 Windows SharePoint Services 4.0 Wiki 文件庫，以及從 Windows SharePoint Services 4.0 Wiki 文件庫接收訊息</span><span class="sxs-lookup"><span data-stu-id="2b8f3-139">Sending to and Receiving from a Windows SharePoint Services 4.0 Wiki Document Library</span></span>  
 <span data-ttu-id="2b8f3-140">在 Windows SharePoint Services 4.0 網站中，Wiki 網站會使用 **Wiki 頁面** 文件庫。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-140">In a Windows SharePoint Services 4.0 site, a Wiki site uses the **Wiki Pages** document library.</span></span> <span data-ttu-id="2b8f3-141">Wiki Pages 文件庫儲存的文字中的 Wiki 頁面 **Wiki 內容** 使用 UI 類型的資料行 **多行文字**。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-141">The Wiki Pages document library stores the text of the Wiki page in a **Wiki Content** column which uses a UI type of **Multiple lines of text**.</span></span> <span data-ttu-id="2b8f3-142">**多行文字** UI 型別與 **SPFieldType.Note** SharePoint 物件模型類型。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-142">The **Multiple lines of text** UI type correlates to the **SPFieldType.Note** SharePoint object model type.</span></span> <span data-ttu-id="2b8f3-143">如需 Windows SharePoint Services 配接器所支援的 Windows SharePoint Services 資料行類型詳細資訊，請參閱[Windows SharePoint Services 配接器屬性參考](../core/windows-sharepoint-services-adapter-properties-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-143">For more information about the Windows SharePoint Services column types that are supported by the Windows SharePoint Services adapter see [Windows SharePoint Services Adapter Properties Reference](../core/windows-sharepoint-services-adapter-properties-reference.md).</span></span>  
  
### <a name="sending-to-a-windows-sharepoint-services-40-wiki-document-library"></a><span data-ttu-id="2b8f3-144">傳送至 Windows SharePoint Services 4.0 Wiki 文件庫</span><span class="sxs-lookup"><span data-stu-id="2b8f3-144">Sending to a Windows SharePoint Services 4.0 Wiki Document Library</span></span>  
 <span data-ttu-id="2b8f3-145">當訊息傳送到 Windows SharePoint Services 4.0 Wiki 網站，Wiki 頁面的內容會儲存在名為 Windows SharePoint Services 配接器內容屬性 **WSS。ConfigPropertiesXml**。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-145">When sending messages to a Windows SharePoint Services 4.0 Wiki site, the contents of the Wiki page are stored within the Windows SharePoint Services adapter context property named **WSS.ConfigPropertiesXml**.</span></span> <span data-ttu-id="2b8f3-146">若要張貼訊息至 Windows SharePoint Services 4.0 Wiki 網站，配接器中，輸入下列值 **傳輸屬性** 時設定使用 Windows SharePoint Services 配接器的傳送埠 對話方塊︰</span><span class="sxs-lookup"><span data-stu-id="2b8f3-146">To post a message to a Windows SharePoint Services 4.0 Wiki site, enter the following values in the adapter **Transport Properties** dialog box when configuring a send port that uses the Windows SharePoint Services adapter:</span></span>  
  
|<span data-ttu-id="2b8f3-147">屬性</span><span class="sxs-lookup"><span data-stu-id="2b8f3-147">Property</span></span>|<span data-ttu-id="2b8f3-148">Value</span><span class="sxs-lookup"><span data-stu-id="2b8f3-148">Value</span></span>|  
|--------------|-----------|  
|<span data-ttu-id="2b8f3-149">目的資料夾 URL</span><span class="sxs-lookup"><span data-stu-id="2b8f3-149">Destination Folder URL</span></span>|<span data-ttu-id="2b8f3-150">相對於 SharePoint 網站的 Wiki 網站 (例如 "wikiSP") 首頁 URL。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-150">URL of the Wiki site home page, relative to the SharePoint site, for example "wikiSP".</span></span>|  
|<span data-ttu-id="2b8f3-151">SharePoint 網站 URL</span><span class="sxs-lookup"><span data-stu-id="2b8f3-151">SharePoint Site URL</span></span>|<span data-ttu-id="2b8f3-152">Windows SharePoint Services 4.0 Wiki 網站，例如 http:// URL*\<servername\>*/sites/wiki/其中*\<servername\>* 是web 伺服器的實際名稱的預留位置。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-152">URL of the Windows SharePoint Services 4.0 Wiki site, for example http://*\<servername\>*/sites/wiki/ where *\<servername\>* is a placeholder for the actual name of the web server.</span></span>|  
  
 <span data-ttu-id="2b8f3-153">接著設定值 **Wiki 內容** Wiki 頁面，在 WSS 中設定對應值的屬性。ConfigPropertiesXml 的訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-153">Then set the value for the **Wiki Content** property for the Wiki page by setting the corresponding value in the WSS.ConfigPropertiesXml context property of the message.</span></span> <span data-ttu-id="2b8f3-154">此步驟可以在自訂管線或協調流程中進行。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-154">This can be done with a custom pipeline or in an orchestration.</span></span> <span data-ttu-id="2b8f3-155">例如，協調流程中的下列運算式會設定 Message_Out 訊息之 WSS.ConfigPropertiesXml 內容屬性中的值：</span><span class="sxs-lookup"><span data-stu-id="2b8f3-155">For example, the following expression in an orchestration would set values in the WSS.ConfigPropertiesXml context property of the Message_Out message:</span></span>  
  
```  
str_Wiki = "This is a sample Wiki page entry.";  
Message_Out(WSS.ConfigPropertiesXml) = “<ConfigPropertiesXml>  
<PropertyName1>Wiki Content</PropertyName1>  
<PropertySource1>” + str_Wiki + “</PropertySource1>  
</ConfigPropertiesXml>”;  
```  
  
 <span data-ttu-id="2b8f3-156">此運算式中的 str_Wiki 變數會使用 **System.String** 資料型別。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-156">The str_Wiki variable in this expression would use the **System.String** data type.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2b8f3-157">Windows SharePoint Services 4.0 Wiki 文件庫支援版本設定，不過，BizTalk Server 2010does 的 Windows SharePoint Services 配接器不支援版本控制。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-157">The Windows SharePoint Services 4.0 Wiki document library supports versioning, however, the Windows SharePoint Services adapter for BizTalk Server 2010does not support versioning.</span></span> <span data-ttu-id="2b8f3-158">因此，BizTalk Server 的 Windows SharePoint Services 配接器所更新的 Wiki 頁面將會失去其先前版本。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-158">Therefore, Wiki pages that are updated by the Windows SharePoint Services adapter for BizTalk Server will lose their previous versions.</span></span> <span data-ttu-id="2b8f3-159">由於此限制，是 BizTalk Server 的 Windows SharePoint Services 配接器接收和封存在其他 Wiki 文件庫的 Wiki 頁面僅會保留其最後一個版本，與所有其他版本都會被刪除。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-159">Because of this limitation, a Wiki page that is received by the Windows SharePoint Services adapter for BizTalk Server and archived in a different Wiki document library will preserve only its last version, with all other versions being deleted.</span></span>  
  
### <a name="receiving-from-a-windows-sharepoint-services-40-wiki-document-library"></a><span data-ttu-id="2b8f3-160">從 Windows SharePoint Services 4.0 Wiki 文件庫接收</span><span class="sxs-lookup"><span data-stu-id="2b8f3-160">Receiving from a Windows SharePoint Services 4.0 Wiki Document Library</span></span>  
 <span data-ttu-id="2b8f3-161">從 Windows SharePoint Services 4.0 Wiki 網站接收訊息時，Wiki 頁面的內容會儲存在名為 Windows SharePoint Services 配接器內容屬性 **WSS。InPropertiesXml**。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-161">When receiving messages from a Windows SharePoint Services 4.0 Wiki site, the contents of the Wiki page are stored within the Windows SharePoint Services adapter context property named **WSS.InPropertiesXml**.</span></span>  
  
 <span data-ttu-id="2b8f3-162">若要從 Windows SharePoint Services 4.0 Wiki 頁面接收訊息，配接器中，輸入下列值 **傳輸屬性**  對話方塊中設定使用 Windows SharePoint Services 配接器的接收位置時︰</span><span class="sxs-lookup"><span data-stu-id="2b8f3-162">To receive a message from a Windows SharePoint Services 4.0 Wiki page, enter the following values in the adapter **Transport Properties** dialog box when configuring a receive location that uses the Windows SharePoint Services adapter:</span></span>  
  
|<span data-ttu-id="2b8f3-163">屬性</span><span class="sxs-lookup"><span data-stu-id="2b8f3-163">Property</span></span>|<span data-ttu-id="2b8f3-164">Value</span><span class="sxs-lookup"><span data-stu-id="2b8f3-164">Value</span></span>|  
|--------------|-----------|  
|<span data-ttu-id="2b8f3-165">SharePoint 網站 URL</span><span class="sxs-lookup"><span data-stu-id="2b8f3-165">SharePoint Site URL</span></span>|<span data-ttu-id="2b8f3-166">相對於 SharePoint 網站的 Wiki 網站 (例如 "wiki") 首頁 URL。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-166">URL of the Wiki site home page, relative to the SharePoint site, for example "wiki".</span></span>|  
|<span data-ttu-id="2b8f3-167">來源文件庫 URL</span><span class="sxs-lookup"><span data-stu-id="2b8f3-167">Source Document Library URL</span></span>|<span data-ttu-id="2b8f3-168">相對於 SharePoint 網站的 Wiki 網站 (例如 "wikiRL") 首頁 URL。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-168">URL of the Wiki site home page, relative to the SharePoint site, for example "wikiRL".</span></span>|  
  
 <span data-ttu-id="2b8f3-169">然後，擷取 wiki 頁面內容，從 **Wiki 內容** 節點 **WSS。InPropertiesXml** 所接收訊息的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-169">Then retrieve the wiki page contents from the **Wiki Content** node of the **WSS.InPropertiesXml** context property of the received message.</span></span> <span data-ttu-id="2b8f3-170">此步驟可以在自訂管線或協調流程中進行。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-170">This can be done with a custom pipeline or in an orchestration.</span></span> <span data-ttu-id="2b8f3-171">例如，在下列的協調流程運算式 **str_Wiki** 填入變數值是 **Wiki 內容** 節點從 **WSS。InPropertiesXml** 內容屬性 **str_wiki** 訊息。</span><span class="sxs-lookup"><span data-stu-id="2b8f3-171">For example, in the following orchestration expression, the **str_Wiki** variable is populated with the value of the **Wiki Content** node from the **WSS.InPropertiesXml** context property of the **Message_In** message.</span></span> <span data-ttu-id="2b8f3-172">然後， **Wiki 內容** 屬性 **WSS。ConfigPropertiesXml** 內容屬性 **Message_Out** 訊息設定的值為 **str_Wiki** 變數︰</span><span class="sxs-lookup"><span data-stu-id="2b8f3-172">Then, the **Wiki Content** property of the **WSS.ConfigPropertiesXml** context property of the **Message_Out** message is set to the value of the **str_Wiki** variable:</span></span>  
  
```  
str_PropertiesXml = Message_In(WSS.InPropertiesXml);  
doc = doc.LoadXml(str_PropertiesXml);  
node = doc.SelectSingleNode("InPropertiesXml/Property[@name='Wiki Content']);  
str_Wiki = node.InnerText;  
Message_Out(WSS.ConfigPropertiesXml) = “<ConfigPropertiesXml>  
<PropertyName1>Wiki Content</PropertyName1>  
<PropertySource1>” + str_Wiki + “</PropertySource1>  
</ConfigPropertiesXml>”;  
```  
  
 <span data-ttu-id="2b8f3-173">此運算式中的變數會使用下列型別：</span><span class="sxs-lookup"><span data-stu-id="2b8f3-173">The variables in this expression would use the following types:</span></span>  
  
|<span data-ttu-id="2b8f3-174">變數名稱</span><span class="sxs-lookup"><span data-stu-id="2b8f3-174">Variable name</span></span>|<span data-ttu-id="2b8f3-175">型別</span><span class="sxs-lookup"><span data-stu-id="2b8f3-175">Type</span></span>|  
|-------------------|----------|  
|<span data-ttu-id="2b8f3-176">str_PropertiesXml</span><span class="sxs-lookup"><span data-stu-id="2b8f3-176">str_PropertiesXml</span></span>|<span data-ttu-id="2b8f3-177">System.Xml.XmlDocument</span><span class="sxs-lookup"><span data-stu-id="2b8f3-177">System.Xml.XmlDocument</span></span>|  
|<span data-ttu-id="2b8f3-178">doc</span><span class="sxs-lookup"><span data-stu-id="2b8f3-178">doc</span></span>|<span data-ttu-id="2b8f3-179">System.Xml.XmlDocument</span><span class="sxs-lookup"><span data-stu-id="2b8f3-179">System.Xml.XmlDocument</span></span>|  
|<span data-ttu-id="2b8f3-180">node</span><span class="sxs-lookup"><span data-stu-id="2b8f3-180">node</span></span>|<span data-ttu-id="2b8f3-181">System.Xml.XmlNode</span><span class="sxs-lookup"><span data-stu-id="2b8f3-181">System.Xml.XmlNode</span></span>|  
|<span data-ttu-id="2b8f3-182">str_Wiki</span><span class="sxs-lookup"><span data-stu-id="2b8f3-182">str_Wiki</span></span>|<span data-ttu-id="2b8f3-183">System.String</span><span class="sxs-lookup"><span data-stu-id="2b8f3-183">System.String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2b8f3-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b8f3-184">See Also</span></span>  
 [<span data-ttu-id="2b8f3-185">Windows SharePoint Services 配接器</span><span class="sxs-lookup"><span data-stu-id="2b8f3-185">Windows SharePoint Services Adapter</span></span>](../core/windows-sharepoint-services-adapter.md)