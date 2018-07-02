---
title: 自訂 BAM 入口網站設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 507bd5f0-b2a0-4d52-85f8-9d984138ca79
caps.latest.revision: 47
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f1cf1bf2cb2400d4209686e6b1d3d3b11a4461c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987335"
---
# <a name="customizing-the-bam-portal-configuration"></a><span data-ttu-id="dd6bb-102">自訂 BAM 入口網站組態</span><span class="sxs-lookup"><span data-stu-id="dd6bb-102">Customizing the BAM Portal Configuration</span></span>
<span data-ttu-id="dd6bb-103">BAM 入口網站上有許多組態選項。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-103">There are a number of configurable options on the BAM portal.</span></span> <span data-ttu-id="dd6bb-104">下列程序顯示如何修改 BAM 入口網站，以獲得最佳使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-104">The following procedures show you how to modify the BAM portal to obtain the best user experience.</span></span>  

> [!NOTE]
>  <span data-ttu-id="dd6bb-105">以非系統管理員的模擬使用者設定入口網站時，您可能必須在存取 BAM 入口網站功能前先登出再登入，以避免系統要求您輸入認證。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-105">When configuring the portal as a non-administrator impersonated user, it may be necessary for you to log off and then log back on before you have access to the BAM portal features without being asked to enter your credentials.</span></span> <span data-ttu-id="dd6bb-106">例如，考慮下列實例：</span><span class="sxs-lookup"><span data-stu-id="dd6bb-106">For example, consider the following scenario:</span></span>  
>   
>  <span data-ttu-id="dd6bb-107">您使用非系統管理員的模擬使用者設定 Web 服務或 BAM 入口網站。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-107">You configure the Web service or BAM portal with a non-administrator impersonated user.</span></span> <span data-ttu-id="dd6bb-108">接著，您在入口網站上設定使用權限，如此 Everyone 群組便沒有入口網站的存取權限。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-108">You then set permissions on the portal such that the Everyone group does not have access to the portal.</span></span> <span data-ttu-id="dd6bb-109">然後，您建立名為 PortalUsersGroup 的本機群組，並指派該群組為「入口網站使用者群組」。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-109">You then create a local group called PortalUsersGroup and assign that group as the Portal Users group.</span></span> <span data-ttu-id="dd6bb-110">這表示只有該群組中的使用者可以存取入口網站。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-110">This means that only users in that group have access to the portal.</span></span> <span data-ttu-id="dd6bb-111">設定 BAM 入口網站之後，請將目前使用者新增至「入口網站使用者群組」。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-111">After you have configured the BAM portal, add the current user to the Portal Users group.</span></span> <span data-ttu-id="dd6bb-112">當您開啟 BAM 入口網站時，系統將會要求您輸入認證。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-112">When you open the BAM portal, you will be asked for your credentials.</span></span> <span data-ttu-id="dd6bb-113">然而，如果您登出並再次登入，就可以直接開啟 BAM 入口網站，而不會被要求輸入認證。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-113">If you log off and log back on, however, you are able to open the BAM portal without being asked for your credentials.</span></span>  
>   
>  <span data-ttu-id="dd6bb-114">BizTalk Server 僅在單一電腦組態中支援本機群組和使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-114">BizTalk Server supports local group and user accounts only in single computer configurations.</span></span> <span data-ttu-id="dd6bb-115">BizTalk Server 在單一電腦組態和多電腦組態中都支援網域群組和使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-115">BizTalk Server supports domain group and user accounts in both single and multiple computer configurations.</span></span>  

## <a name="running-the-bam-portal-in-a-64-bit-environment"></a><span data-ttu-id="dd6bb-116">在 64 位元環境中執行 BAM 入口網站</span><span class="sxs-lookup"><span data-stu-id="dd6bb-116">Running the BAM Portal in a 64-bit Environment</span></span>  
 <span data-ttu-id="dd6bb-117">如果您在 64 位元環境中使用 Internet Information Services (IIS)，您必須設定 IIS 以 32 位元模式來執行 BAM 入口網站。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-117">If you are using Internet Information Services (IIS) in a 64-bit environment, you must set IIS to 32-bit mode to run the BAM portal.</span></span> 

> [!IMPORTANT]
>  <span data-ttu-id="dd6bb-118">您不需要將 IIS7 設定為 32 位元模式。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-118">You do not have to set IIS7 to 32-bit mode.</span></span>  

#### <a name="to-set-a-64-bit-mode-iis-installation-to-32-bit-mode"></a><span data-ttu-id="dd6bb-119">若要將 64 位元模式的 IIS 安裝設定成 32 位元模式</span><span class="sxs-lookup"><span data-stu-id="dd6bb-119">To set a 64-bit mode IIS installation to 32-bit mode</span></span>  

1.  <span data-ttu-id="dd6bb-120">開啟命令提示字元並執行**adsutil**命令。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-120">Open a command prompt and run the **adsutil** command.</span></span> <span data-ttu-id="dd6bb-121">若要這樣做，請按一下**開始**，按一下**執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-121">To do this, click **Start**, click **Run**, and then type **cmd**.</span></span>  

2.  <span data-ttu-id="dd6bb-122">在命令提示字元輸入下列命令： `cscript c:\inetpub\adminscripts\adsutil.vbs SET W3SVC/AppPools/Enable32bitAppOnWin64 1`。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-122">Type the following at the command prompt: `cscript c:\inetpub\adminscripts\adsutil.vbs SET W3SVC/AppPools/Enable32bitAppOnWin64 1`.</span></span>  

3.  <span data-ttu-id="dd6bb-123">關閉命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-123">Close the command prompt.</span></span>  

## <a name="configuring-the-bam-portal-banner"></a><span data-ttu-id="dd6bb-124">設定 BAM 入口網站橫幅</span><span class="sxs-lookup"><span data-stu-id="dd6bb-124">Configuring the BAM Portal Banner</span></span>  
 <span data-ttu-id="dd6bb-125">您可以修改 BAM 入口網站頁面，以顯示與商務相關的文字和圖形：</span><span class="sxs-lookup"><span data-stu-id="dd6bb-125">You can modify the BAM portal page to display similar text and graphics about your business:</span></span>  

- <span data-ttu-id="dd6bb-126">Windows Server System 標誌，位於 BAM 入口網站頁面的右上角。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-126">The Windows Server System logo, which is located in the upper-right corner of the BAM portal page.</span></span>  

  <span data-ttu-id="dd6bb-127">在下列程序中，您將編輯階層式樣式表檔案 (.css 檔案) 以自訂 BAM 入口網站的外觀。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-127">In the following procedure you edit a cascading style sheet file (.css file) to customize the look of the BAM portal.</span></span> <span data-ttu-id="dd6bb-128">只支援修改特定的類別。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-128">Modifications to the specified classes are the only modifications supported.</span></span> <span data-ttu-id="dd6bb-129">修改類別所造成的影響已經儘可能地加以隔離，如此，在修改過程中造成的錯誤會將 BAM 入口網站保持在運作狀態。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-129">As much as possible, the impact of modifications to classes has been isolated so that errors made during the modification process leave the BAM portal in a working state.</span></span>  

> [!CAUTION]
>  <span data-ttu-id="dd6bb-130">修改 styles.css 檔案中的其他類別將會隱藏資料和入口網站功能，並且可能造成入口網站無法使用。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-130">Modifying other classes in the styles.css file will hide data and portal features, and may make the portal unusable.</span></span>  

#### <a name="to-configure-the-banner"></a><span data-ttu-id="dd6bb-131">若要設定橫幅</span><span class="sxs-lookup"><span data-stu-id="dd6bb-131">To configure the banner</span></span>  

1. <span data-ttu-id="dd6bb-132">編輯 BAM 入口網站的 web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-132">Edit the BAM portal web.config file.</span></span> <span data-ttu-id="dd6bb-133">若要這樣做，請按一下**開始**，按一下**執行**，輸入 notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-133">To do this, click **Start**, click **Run**, type notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config, and then click **OK**.</span></span>  

2. <span data-ttu-id="dd6bb-134">主頁面的快速入門內容均可取代藉由修改下面這行：\<新增機碼 ="MainPageContentUrl"value="~/MainPageContent.htm"/\>。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-134">The main page quick-start contents are replaceable by modifying the following line: \<add key="MainPageContentUrl" value="~/MainPageContent.htm"/\>.</span></span> <span data-ttu-id="dd6bb-135">變更**MainPageContent.htm**值欄位，以指向您自己的 HTML 檔案中。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-135">Change **MainPageContent.htm** in the value field to point to your own HTML file.</span></span> <span data-ttu-id="dd6bb-136">HTML 檔案必須位於與 web.config 檔案相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-136">The HTML file must be in the same directory as the web.config file.</span></span>  

3. <span data-ttu-id="dd6bb-137">變更頁面識別文字將下行新增至 web.config 檔案：\<新增機碼 ="PortalTitle"value ="新識別 text"/\>。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-137">Change the page identifying text by adding the following line to the web.config file: \<add key=”PortalTitle” value=”New Identifying text”/\>.</span></span> <span data-ttu-id="dd6bb-138">變更數值欄位以包含用來識別入口網站的文字。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-138">Change the value field to contain the text to identify the portal.</span></span>  

4. <span data-ttu-id="dd6bb-139">編輯 BAM 入口網站的 styles.css 檔案。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-139">Edit the BAM portal styles.css file.</span></span> <span data-ttu-id="dd6bb-140">按一下 **開始**，按一下**執行**，輸入 notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\Styles.css，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-140">Click **Start**, click **Run**, type notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\Styles.css, and then click **OK**.</span></span>  

5. <span data-ttu-id="dd6bb-141">找出.headerLogo div 類別，並將下列行以變更右上角中的標誌： 背景影像： url("../ images/WSS_Logo.gif");以指向您所建立的映像檔。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-141">Change the logo in the upper-right corner by locating the .headerLogo div class and changing the following line:   background-image: url("../images/WSS_Logo.gif"); to point to the image file you have created.</span></span> <span data-ttu-id="dd6bb-142">我們建議您使用 .gif 格式影像。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-142">We recommend that you use a .gif format image.</span></span>  

6. <span data-ttu-id="dd6bb-143">找出.headerPageIcon div 類別，並將下列這一行來變更 SharePoint 圖示： 背景影像： url("../ images/btsSuiteProduction.gif");以指向您所建立的映像檔。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-143">Change the SharePoint icon by locating the .headerPageIcon div class and changing the following line: background-image: url("../images/btsSuiteProduction.gif"); to point to the image file you have created.</span></span>  

7. <span data-ttu-id="dd6bb-144">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-144">Save the file.</span></span>  

8. <span data-ttu-id="dd6bb-145">開啟 BAM 入口網站以檢視變更。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-145">Open the BAM portal to view your changes.</span></span>  

## <a name="modifying-the-bam-portal-webconfig-file"></a><span data-ttu-id="dd6bb-146">修改 BAM 入口網站的 web.config 檔案</span><span class="sxs-lookup"><span data-stu-id="dd6bb-146">Modifying the BAM Portal web.config File</span></span>  
 <span data-ttu-id="dd6bb-147">如果您的 BAM 入口網站位於使用企業單一登入 (SSO) 憑證以實作安全通訊端層 (SSL) 的伺服器上，您必須設定入口網站接受適當的憑證 URL。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-147">If your BAM portal resides on a server that uses Enterprise Single Sign-On (SSO) certificates for Secure Sockets Layer (SSL), you must configure the portal to accept the proper URL for the certificate.</span></span>  

#### <a name="to-modify-the-bam-portal-to-support-ssl-sites"></a><span data-ttu-id="dd6bb-148">若要修改 BAM 入口網站以支援 SSL 網站</span><span class="sxs-lookup"><span data-stu-id="dd6bb-148">To modify the BAM portal to support SSL sites</span></span>  

1. <span data-ttu-id="dd6bb-149">使用 [記事本] 開啟 web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-149">Open the web.config file using Notepad.</span></span> <span data-ttu-id="dd6bb-150">按一下 **開始**，按一下**執行**，輸入 notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-150">Click **Start**, click **Run**, type notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config, and then click **OK**.</span></span>  

2. <span data-ttu-id="dd6bb-151">修改檔案中的下列兩行以指向啟用 SSL 的入口網站位置：</span><span class="sxs-lookup"><span data-stu-id="dd6bb-151">Modify the following two lines in the file to point to the location of your SSL-enabled portal:</span></span>  

   ```  
   <add key="BamQueryWSUrl" value="http://localhost/BAM/BamQueryService/BamQueryService.asmx"/>  
   <add key="BamManagementWSUrl" value="http://localhost/BAM/BamManagementService/BamManagementService.asmx"/>  
   ```  

3. <span data-ttu-id="dd6bb-152">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-152">Save the file.</span></span>  

   <span data-ttu-id="dd6bb-153">BAM 入口網站會根據所設定的文化特性顯示並接受格式化的資料。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-153">The BAM portal displays and accepts data formatted according to the culture for which it has been configured.</span></span> <span data-ttu-id="dd6bb-154">組態可以在 web.config 檔案中指定。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-154">The configuration is specified in the web.config file.</span></span> <span data-ttu-id="dd6bb-155">入口網站會忽略 Internet Explorer 所傳送的「接受語言」資訊。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-155">The Web portal ignores the “Accept Language” information sent by Internet Explorer.</span></span> <span data-ttu-id="dd6bb-156">例如，假設您正在執行 Internet Explorer 設定為 「 日文 」 文化特性設定，且已設定 BAM 入口網站使用美國英文文化特性設定。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-156">For example, suppose that you are running Internet Explorer which is set for a Japanese culture setting and have configured the BAM portal to use the U.S. English culture setting.</span></span> <span data-ttu-id="dd6bb-157">在此情況下資料的項目，例如日期與整數，將會顯示，接受，以及排序使用適用於美國英文的文化特性設定而不是適用於 「 日文 」 文化特性設定。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-157">In this case data items, such as dates and integers, will be displayed, accepted, and sorted using rules appropriate to the U.S. English culture setting rather than rules appropriate to the Japanese culture setting.</span></span> <span data-ttu-id="dd6bb-158">使用 「 日文 」 格式輸入任何特定文化特性的資訊會視為無效，BAM 入口網站因為它會預期適用於美國格式化資料英國)」。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-158">Any culture-specific information entered using Japanese formatting will be considered invalid by the BAM portal because it will expect data formatted for U.S. English.</span></span>  

   <span data-ttu-id="dd6bb-159">若要以一致的處理方式顯示和格式化隨著文化特性設定而變更的資料，請選擇適用於所有 BAM 入口網站用戶端的語言。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-159">To obtain consistent handling of display and formatting of data that is variable based on the culture settings, choose a language that is appropriate for all BAM portal clients.</span></span> <span data-ttu-id="dd6bb-160">請設定 BAM 入口網站使用此文化特性。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-160">Configure the BAM portal for this culture.</span></span> <span data-ttu-id="dd6bb-161">您必須確認每個用戶端都已安裝「多語系使用者介面 (MUI) 套件」且已設定為選擇的文化特性。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-161">You must ensure that every client is set to the chosen culture by installing the Multilingual User Interface Pack.</span></span>  

   <span data-ttu-id="dd6bb-162">非美國BAM 的英文版安裝可能需要在 web.config 檔案中設定文化特性參數。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-162">For non-U.S. English installations of BAM it may be necessary to set the culture parameter in the web.config file.</span></span> <span data-ttu-id="dd6bb-163">在下列情況中，您可能需要執行這項操作：</span><span class="sxs-lookup"><span data-stu-id="dd6bb-163">Cases where you may need to do this are:</span></span>  

-   <span data-ttu-id="dd6bb-164">當地語系化日期和時間顯示的格式。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-164">To localize the format of date and time displays.</span></span>  

-   <span data-ttu-id="dd6bb-165">當地語系化貨幣顯示的格式。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-165">To localize the format of currency displays.</span></span>  

#### <a name="to-modify-the-culture-setting-of-the-portal"></a><span data-ttu-id="dd6bb-166">若要修改入口網站的文化特性設定</span><span class="sxs-lookup"><span data-stu-id="dd6bb-166">To modify the culture setting of the portal</span></span>  

1. <span data-ttu-id="dd6bb-167">使用 [記事本] 開啟 web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-167">Open the web.config file using Notepad.</span></span> <span data-ttu-id="dd6bb-168">按一下 **開始**，按一下**執行**，輸入 notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-168">Click **Start**, click **Run**, type notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config, and then click **OK**.</span></span>  

2. <span data-ttu-id="dd6bb-169">修改檔案下列行中的文化特性屬性，以反映適當的全球化設定：</span><span class="sxs-lookup"><span data-stu-id="dd6bb-169">Modify the culture attributes in the following line in the file to reflect the appropriate globalization settings:</span></span>  

   ```  
   <globalization requestEncoding="utf-8" responseEncoding="utf-8" culture="de-DE" uiCulture="en" />  
   ```  

3. <span data-ttu-id="dd6bb-170">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-170">Save the file.</span></span>  

   <span data-ttu-id="dd6bb-171">如果您在等候大量 SQL 查詢時遇到逾時的情形，可能必須增加查詢服務逾時值。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-171">In cases where you are experiencing time-outs while waiting for large SQL queries, it may be necessary to increase the query service time-out value.</span></span>  

#### <a name="to-increase-the-query-service-time-out-value"></a><span data-ttu-id="dd6bb-172">增加查詢服務逾時值</span><span class="sxs-lookup"><span data-stu-id="dd6bb-172">To increase the query service time-out value</span></span>  

1. <span data-ttu-id="dd6bb-173">使用 [記事本] 開啟 web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-173">Open the web.config file using Notepad.</span></span> <span data-ttu-id="dd6bb-174">按一下 **開始**，按一下**執行**，輸入 notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\BAMManagementService\web.config，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-174">Click **Start**, click **Run**, type notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\BAMManagementService\web.config, and then click **OK**.</span></span>  

2. <span data-ttu-id="dd6bb-175">QueryServiceTimeout 的預設值為 45 秒。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-175">The default value for the QueryServiceTimeout is 45 seconds.</span></span> <span data-ttu-id="dd6bb-176">請修改下列行中的值以增加或減少逾時間隔：</span><span class="sxs-lookup"><span data-stu-id="dd6bb-176">Modify the value in the following line to increase or decrease the time-out interval:</span></span>  

   ```  
   <add key="QueryServiceTimeout" value="45" />  
   ```  

3. <span data-ttu-id="dd6bb-177">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-177">Save the file.</span></span>  

   <span data-ttu-id="dd6bb-178">在多伺服器環境中，有時可能會發生伺服器離線的情況。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-178">In a multiserver environment there may be times when a server is offline.</span></span> <span data-ttu-id="dd6bb-179">發生這種情況時，入口網站的使用者可能因為 BAM 入口網站停止回應而遭遇到時間延遲。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-179">When this happens, users of the portal may experience time delays where the BAM portal stops responding.</span></span> <span data-ttu-id="dd6bb-180">為了改善使用者體驗，您可以修改伺服器重試間隔。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-180">To improve the user experience you can modify the server retry interval.</span></span> <span data-ttu-id="dd6bb-181">這將會增加 BAM 查詢 Web 服務在連線失敗後，假設伺服器處於離線狀態的最小時間。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-181">This creates a minimum time during which the BAM query Web service assumes that the server is offline after a connection has failed once.</span></span>  

   <span data-ttu-id="dd6bb-182">這個值表示，如果本機資料庫嘗試連線遠端資料庫逾時，資料會標示為未完成，並且本機電腦在經過指定的時間之前，將不會嘗試連線到遠端資料庫。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-182">The value indicates that if a local database times out while trying to contact a remote database, the data is marked as incomplete and the local computer will not attempt to connect to the remote database until the specified time has elapsed.</span></span>  

#### <a name="to-increase-the-retry-interval-for-distributed-activities-in-a-multiserver-environment"></a><span data-ttu-id="dd6bb-183">若要增加多伺服器環境中分散式活動的重試間隔</span><span class="sxs-lookup"><span data-stu-id="dd6bb-183">To increase the retry interval for distributed activities in a multiserver environment</span></span>  

1. <span data-ttu-id="dd6bb-184">使用 [記事本] 開啟 web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-184">Open the web.config file using Notepad.</span></span> <span data-ttu-id="dd6bb-185">按一下 **開始**，按一下**執行**，輸入 notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\BAMManagementService\web.config，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-185">Click **Start**, click **Run**, type notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\BAMManagementService\web.config, and then click **OK**.</span></span>  

2. <span data-ttu-id="dd6bb-186">ServerRetryInterval 的預設值為 5 分鐘。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-186">The default value for the ServerRetryInterval is five minutes.</span></span> <span data-ttu-id="dd6bb-187">請修改下列行中的值以增加或減少伺服器重試間隔：</span><span class="sxs-lookup"><span data-stu-id="dd6bb-187">Modify the value in the following line to increase or decrease the server retry interval:</span></span>  

   ```  
   <add key="ServerRetryInterval" value="5"/>  
   ```  

3. <span data-ttu-id="dd6bb-188">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-188">Save the file.</span></span>  

#### <a name="to-configure-how-alert-notification-options-are-presented-in-the-bam-portal"></a><span data-ttu-id="dd6bb-189">若要設定 BAM 入口網站顯示警示通知選項的方式</span><span class="sxs-lookup"><span data-stu-id="dd6bb-189">To configure how alert notification options are presented in the BAM portal</span></span>  

1. <span data-ttu-id="dd6bb-190">使用 [記事本] 開啟 web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-190">Open the web.config file using Notepad.</span></span> <span data-ttu-id="dd6bb-191">按一下 **開始**，按一下**執行**，輸入 notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-191">Click **Start**, click **Run**, type notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config, and then click **OK**.</span></span>  

2. <span data-ttu-id="dd6bb-192">修改中的 [值] 欄位\<新增機碼 ="AlertNotificationOptions"value =""/\>列 web.config 檔案以逗點分隔的清單，使用下列值之一，指定有效的通知選項。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-192">Modify the value field in the \<add key="AlertNotificationOptions" value="" /\> line of the web.config file with a comma-delimited list specifying valid notification options with one of the following values.</span></span> <span data-ttu-id="dd6bb-193">如果設定為空值，將會以伺服器傳回的順序在伺服器上顯示所有可用的通知選項。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-193">An empty value displays all notification options available on the server in the order returned by the server.</span></span> <span data-ttu-id="dd6bb-194">任何無法辨識的值同等於空值。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-194">Any unrecognized value is equivalent to an empty value.</span></span>  


   |    <span data-ttu-id="dd6bb-195">ReplTest1</span><span class="sxs-lookup"><span data-stu-id="dd6bb-195">Value</span></span>    |                                              <span data-ttu-id="dd6bb-196">描述</span><span class="sxs-lookup"><span data-stu-id="dd6bb-196">Description</span></span>                                               |
   |-------------|--------------------------------------------------------------------------------------------------------|
   | <span data-ttu-id="dd6bb-197">檔案、電子郵件</span><span class="sxs-lookup"><span data-stu-id="dd6bb-197">File, Email</span></span> | <span data-ttu-id="dd6bb-198">顯示檔案和電子郵件選項。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-198">File and E-mail options are displayed.</span></span> <span data-ttu-id="dd6bb-199">在下拉式清單中，會先顯示檔案，再顯示電子郵件。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-199">In the drop-down list, File is displayed first and then E-mail.</span></span> |
   | <span data-ttu-id="dd6bb-200">電子郵件、檔案</span><span class="sxs-lookup"><span data-stu-id="dd6bb-200">Email, File</span></span> | <span data-ttu-id="dd6bb-201">顯示檔案和電子郵件選項。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-201">File and E-mail options are displayed.</span></span> <span data-ttu-id="dd6bb-202">在下拉式清單中，會先顯示電子郵件，再顯示檔案。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-202">In the drop-down list, E-mail is displayed first and then File.</span></span> |
   |    <span data-ttu-id="dd6bb-203">檔案</span><span class="sxs-lookup"><span data-stu-id="dd6bb-203">File</span></span>     |                             <span data-ttu-id="dd6bb-204">只會在入口網站中顯示「檔案」通知。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-204">Only File notification is displayed in portal.</span></span>                             |
   |    <span data-ttu-id="dd6bb-205">Email</span><span class="sxs-lookup"><span data-stu-id="dd6bb-205">Email</span></span>    |                            <span data-ttu-id="dd6bb-206">只會在入口網站中顯示「電子郵件」通知。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-206">Only E-mail notification is displayed in portal.</span></span>                            |


3. <span data-ttu-id="dd6bb-207">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-207">Save the file.</span></span>  

## <a name="distributed-server-environments"></a><span data-ttu-id="dd6bb-208">分散式伺服器環境</span><span class="sxs-lookup"><span data-stu-id="dd6bb-208">Distributed Server Environments</span></span>  
 <span data-ttu-id="dd6bb-209">如果您安裝 BAM 入口網站會將警示和 BAM 入口網站放在不同伺服器上，您會看到事件記錄檔中的下列錯誤:"System.Reflection.TargetInvocationException： 叫用的目標，已擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-209">If your installation of the BAM portal places the alerts and the BAM portal on different servers, you will see the following error in the event log: "System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation.</span></span> <span data-ttu-id="dd6bb-210">---> 的登錄找不到指定的 Notification Services 執行個體的項目。 」</span><span class="sxs-lookup"><span data-stu-id="dd6bb-210">---> The registry entries for the specified instance of Notification Services could not be found."</span></span>  

#### <a name="to-configure-the-portal-and-alerts-on-different-servers"></a><span data-ttu-id="dd6bb-211">若要在不同伺服器上設定入口網站和警示</span><span class="sxs-lookup"><span data-stu-id="dd6bb-211">To configure the portal and alerts on different servers</span></span>  

1. <span data-ttu-id="dd6bb-212">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-212">Open a command prompt.</span></span>  

2. <span data-ttu-id="dd6bb-213">執行**C:\Program Files\Microsoft SQL Server\90\Notification Services\9.0.242\Bin\nscontrol register-name bamalerts-server**<em>\<伺服器名稱\></em>取代*\<伺服器名稱\>* 與伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-213">Run **C:\Program Files\Microsoft SQL Server\90\Notification Services\9.0.242\Bin\nscontrol register -name bamalerts -server**<em>\<server name\></em> Replace *\<server name\>* with the name of the server.</span></span>  

3. <span data-ttu-id="dd6bb-214">按下 F5 以重新整理瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-214">Press F5 to refresh your browser.</span></span>  

## <a name="configuring-iis-to-allow-the-bam-portal-to-use-the-kerberos-network-protocol"></a><span data-ttu-id="dd6bb-215">設定 IIS 以允許 BAM 入口網站使用 Kerberos 網路通訊協定</span><span class="sxs-lookup"><span data-stu-id="dd6bb-215">Configuring IIS to Allow the BAM Portal to Use the Kerberos Network Protocol</span></span>  
 <span data-ttu-id="dd6bb-216">如果您想要在 BAM 入口網站使用 Kerberos 網路通訊協定，您必須修改入口網站的 ACL 安全性。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-216">If you want to use the Kerberos network protocol with the BAM portal you must modify the ACL security for the Web portal.</span></span> <span data-ttu-id="dd6bb-217">如果 IIS 未正確地設定，使用者將收到下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="dd6bb-217">If IIS is not configured properly, users will receive the following error:</span></span>  

 <span data-ttu-id="dd6bb-218">HTTP 錯誤 401.1 – 未經授權： 因為認證無效而拒絕存取。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-218">HTTP Error 401.1 - Unauthorized: Access is denied due to invalid credentials.</span></span>  

 <span data-ttu-id="dd6bb-219">如需有關修改 IIS 安全性設定的詳細資訊，請參閱知識庫文章，網址[ http://go.microsoft.com/fwlink/?LinkId=57922 ](http://go.microsoft.com/fwlink/?LinkId=57922)。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-219">For additional information about modifying the IIS security settings, see the Knowledge Base article at [http://go.microsoft.com/fwlink/?LinkId=57922](http://go.microsoft.com/fwlink/?LinkId=57922).</span></span>  

## <a name="viewing-aggregate-bam-data-in-the-bam-portal-in-sql-server-2008--deployments"></a><span data-ttu-id="dd6bb-220">在 SQL Server 2008 部署 BAM 入口網站中檢視彙總 BAM 資料</span><span class="sxs-lookup"><span data-stu-id="dd6bb-220">Viewing Aggregate BAM Data in the BAM Portal in SQL Server 2008  Deployments</span></span>  
 <span data-ttu-id="dd6bb-221">若要檢視 BAM 入口網站，從用戶端電腦連接到 BAM 入口網站時的部署環境使用 SQL Server 2008 中的彙總資料，您必須在用戶端電腦上安裝 Microsoft SQL Server 2008 Analysis Services 10.0 OLE DB 提供者。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-221">To view aggregate data in the BAM portal from a client computer connecting to the BAM portal when the deployment environment uses SQL Server 2008, you must install Microsoft SQL Server 2008 Analysis Services 10.0 OLE DB Provider on the client computer.</span></span> <span data-ttu-id="dd6bb-222">如果未安裝分析服務，使用者便會收到下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="dd6bb-222">If the analysis services are not installed users will receive the following error message:</span></span>  

 <span data-ttu-id="dd6bb-223">伺服器*\<servername\>* 無法連絡或太忙碌。</span><span class="sxs-lookup"><span data-stu-id="dd6bb-223">The server *\<servername\>* cannot be contacted or is too busy.</span></span>  



## <a name="see-also"></a><span data-ttu-id="dd6bb-224">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd6bb-224">See Also</span></span>  
 [<span data-ttu-id="dd6bb-225">規劃 BAM 入口網站</span><span class="sxs-lookup"><span data-stu-id="dd6bb-225">Planning for the BAM Portal</span></span>](../core/planning-for-the-bam-portal.md)