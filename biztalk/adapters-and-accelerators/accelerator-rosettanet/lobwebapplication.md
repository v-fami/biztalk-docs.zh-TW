---
title: "LOBWebApplication |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows SharePoint Services, LOBWebApplication
- ASPX pages, LOBWebApplication utility
- virtual servers
- ASPX pages, submitting actions
- LOBWebApplication
- ASPX pages, response messages
- LOBWebApplication utility
ms.assetid: 2d578efd-72a9-4621-9274-30792bf94b6c
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b00e29b51eac2c58ac7843cca75994efceb4085
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="lobwebapplication"></a><span data-ttu-id="2d63a-102">LOBWebApplication</span><span class="sxs-lookup"><span data-stu-id="2d63a-102">LOBWebApplication</span></span>
<span data-ttu-id="2d63a-103">您可以使用 LOBWebApplication 公用程式，透過 ASPX 頁面將動作或回應訊息提交給交易夥伴，藉以模擬實際的商務營運系統 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="2d63a-103">You use the LOBWebApplication utility to submit an action or response message from an ASPX page to a trading partner, simulating an actual line-of-business Web application.</span></span>  
  
 <span data-ttu-id="2d63a-104">設定 ASPX 頁面之後，您要啟動該頁面，然後輸入訊息的參數：主要組織和夥伴組織；PIP 代碼、版本和執行個體識別碼；以及訊息類別。</span><span class="sxs-lookup"><span data-stu-id="2d63a-104">After you have set up the ASPX page, you start the page, and enter the parameters for a message: the home and partner organizations; the PIP code, version, and instance ID; and the message category.</span></span> <span data-ttu-id="2d63a-105">然後，您便可以修改服務內容，並提交訊息。</span><span class="sxs-lookup"><span data-stu-id="2d63a-105">You can then modify the service content, and submit the message.</span></span>  
  
## <a name="location-in-sdk"></a><span data-ttu-id="2d63a-106">SDK 中的位置</span><span class="sxs-lookup"><span data-stu-id="2d63a-106">Location in SDK</span></span>  
 <span data-ttu-id="2d63a-107">\<*磁碟機*> \Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\LOBWebApplication</span><span class="sxs-lookup"><span data-stu-id="2d63a-107">\<*drive*>\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\LOBWebApplication</span></span>  
  
## <a name="adding-a-virtual-server-for-lobwebapplication"></a><span data-ttu-id="2d63a-108">新增 LOBWebApplication 的虛擬伺服器</span><span class="sxs-lookup"><span data-stu-id="2d63a-108">Adding a Virtual Server for LOBWebApplication</span></span>  
  
#### <a name="to-add-a-virtual-server"></a><span data-ttu-id="2d63a-109">新增虛擬伺服器</span><span class="sxs-lookup"><span data-stu-id="2d63a-109">To add a virtual server</span></span>  
  
1.  <span data-ttu-id="2d63a-110">按一下**啟動**，指向  **AllPrograms**，指向 **系統管理工具**，然後按一下 **網際網路資訊服務 (IIS) 管理員**.</span><span class="sxs-lookup"><span data-stu-id="2d63a-110">Click **Start**, point to **AllPrograms**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2.  <span data-ttu-id="2d63a-111">在 Information Services 管理員中，依序展開**\<電腦名稱 > （本機電腦）**，依序展開**網站**，然後以滑鼠右鍵按一下**Default Web Site**。</span><span class="sxs-lookup"><span data-stu-id="2d63a-111">In Information Services Manager, expand **\<Computer name> (local computer)**, expand **Web Sites**, and then right-click **Default Web Site**.</span></span>  
  
3.  <span data-ttu-id="2d63a-112">指向**新增**，然後按一下 **虛擬目錄**。</span><span class="sxs-lookup"><span data-stu-id="2d63a-112">Point to **New**, and then click **Virtual Directory**.</span></span>  
  
4.  <span data-ttu-id="2d63a-113">在**虛擬目錄建立精靈**頁面上，按一下**下一步**，然後輸入別名站台，例如**LOBWebApplication**。</span><span class="sxs-lookup"><span data-stu-id="2d63a-113">On the **Virtual Directory Creation Wizard** page, click **Next**, and then type an alias for the site, such as **LOBWebApplication**.</span></span>  
  
5.  <span data-ttu-id="2d63a-114">在**網站內容目錄**頁面上，按一下**瀏覽**，移至\<*磁碟機*> \Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\LOBWebApplication，按一下 **確定**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="2d63a-114">On the **Web Site Content Directory** page, click **Browse**, move to \<*drive*>\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\LOBWebApplication, click **OK**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="2d63a-115">在**虛擬目錄存取權限**頁面上，選取**讀取**和**執行指令碼**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="2d63a-115">On the **Virtual Directory Access Permissions** page, select **Read** and **Run scripts**, and then click **Next**.</span></span> <span data-ttu-id="2d63a-116">按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="2d63a-116">Click **Finish**.</span></span>  
  
7.  <span data-ttu-id="2d63a-117">將之前用來設定 BTARN 的服務帳戶使用者 (例如 hostsvc) 新增至 STS_WPG。</span><span class="sxs-lookup"><span data-stu-id="2d63a-117">Add the service account user that was used to configure BTARN, for example, hostsvc, to the STS_WPG.</span></span>  
  
8.  <span data-ttu-id="2d63a-118">刪除 C:\WINDOWS\Microsoft.NET\Framework\v2.0.\Temporary ASP.NET Files 中的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="2d63a-118">Delete all files from C:\WINDOWS\Microsoft.NET\Framework\v2.0.\Temporary ASP.NET Files.</span></span> <span data-ttu-id="2d63a-119">您可能必須先執行 iisreset 程式，才能解除鎖定那些檔案並加以刪除。</span><span class="sxs-lookup"><span data-stu-id="2d63a-119">You may have to run the iisreset program to unlock the files before you can delete them.</span></span>  
  
9. <span data-ttu-id="2d63a-120">在 [IIS 管理員] 中，將 LOBWebApplication 設定為在應用程式集區 BTARNHTTPReceivePool 下執行。</span><span class="sxs-lookup"><span data-stu-id="2d63a-120">In IIS Manager, set the LOBWebApplication to run under the Application Pool BTARNHTTPReceivePool.</span></span>  
  
10. <span data-ttu-id="2d63a-121">在 [IIS 管理員] 中，於 LOBWebApplication 公用程式的 [目錄安全性屬性] 區域中停用虛擬目錄的選項，以便用匿名身分執行。</span><span class="sxs-lookup"><span data-stu-id="2d63a-121">In IIS Manager, in the Directory Security Properties section for the LOBWebApplication utility, disable the option for the virtual directory to run as anonymous.</span></span>  
  
## <a name="building-lobwebapplication"></a><span data-ttu-id="2d63a-122">建置 LOBWebApplication</span><span class="sxs-lookup"><span data-stu-id="2d63a-122">Building LOBWebApplication</span></span>  
  
#### <a name="to-build-lobwebapplication"></a><span data-ttu-id="2d63a-123">建置 LOBWebApplication</span><span class="sxs-lookup"><span data-stu-id="2d63a-123">To build LOBWebApplication</span></span>  
  
1.  <span data-ttu-id="2d63a-124">啟動 [!INCLUDE[vs2012](../../includes/vs2012-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2d63a-124">Start [!INCLUDE[vs2012](../../includes/vs2012-md.md)].</span></span>  
  
2.  <span data-ttu-id="2d63a-125">在**檔案**，指向 **開啟**，然後按一下 **開啟的方案**。</span><span class="sxs-lookup"><span data-stu-id="2d63a-125">On the **File**, point to **Open**, and then click **Open Solution**.</span></span>  
  
3.  <span data-ttu-id="2d63a-126">移至\<*磁碟機*> \Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\LOBWebApplication，選取**LOBWebApplication.sln**，然後按一下  **開啟**。</span><span class="sxs-lookup"><span data-stu-id="2d63a-126">Move to \<*drive*>\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\LOBWebApplication, select **LOBWebApplication.sln**, and then click **Open**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2d63a-127">如果您尚未新增 LOBWebApplication 的虛擬伺服器，方案將無法正確地在 [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] 中開啟。</span><span class="sxs-lookup"><span data-stu-id="2d63a-127">If you have not added a virtual server for LOBWebApplication, the solution will not open correctly in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span>  
  
4.  <span data-ttu-id="2d63a-128">以滑鼠右鍵按一下**參考**，然後按一下 **加入參考**。</span><span class="sxs-lookup"><span data-stu-id="2d63a-128">Right-click **References**, and then click **Add Reference**.</span></span>  
  
5.  <span data-ttu-id="2d63a-129">在**加入參考**對話方塊中，按一下 **瀏覽**，移至\<*磁碟機*>: \Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\Bin，選取 Microsoft.Solutions.BTARN.ConfigurationManager.dll 和 Microsoft.Solutions.BTARN.Shared.dll 檔案，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="2d63a-129">In the **Add Reference** dialog box, click **Browse**, move to \<*drive*>:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\Bin, select the Microsoft.Solutions.BTARN.ConfigurationManager.dll and Microsoft.Solutions.BTARN.Shared.dll files, and then click **Open**.</span></span>  
  
6.  <span data-ttu-id="2d63a-130">以滑鼠右鍵按一下**LOBWebApplication**，然後按一下 **建置**。</span><span class="sxs-lookup"><span data-stu-id="2d63a-130">Right-click **LOBWebApplication**, and then click **Build**.</span></span>  
  
## <a name="running-lobwebapplication"></a><span data-ttu-id="2d63a-131">執行 LOBWebApplication</span><span class="sxs-lookup"><span data-stu-id="2d63a-131">Running LOBWebApplication</span></span>  
  
#### <a name="to-run-lobwebapplication-and-submit-a-message"></a><span data-ttu-id="2d63a-132">執行 LOBWebApplication 並提交訊息</span><span class="sxs-lookup"><span data-stu-id="2d63a-132">To run LOBWebApplication and submit a message</span></span>  
  
1.  <span data-ttu-id="2d63a-133">按一下**啟動**，指向 **所有程式**，然後按一下  **Internet Explorer**。</span><span class="sxs-lookup"><span data-stu-id="2d63a-133">Click **Start**, point to **All Programs**, and then click **Internet Explorer**.</span></span>  
  
2.  <span data-ttu-id="2d63a-134">在 Internet Explorer 中 **位址** 方塊、 輸入 http://localhost/LOBWebApplication ，然後按一下 **移** 。</span><span class="sxs-lookup"><span data-stu-id="2d63a-134">In Internet Explorer, in the **Address** box, type http://localhost/LOBWebApplication, and then click **Go**.</span></span>  
  
3.  <span data-ttu-id="2d63a-135">在**提交訊息**對話方塊方塊中，輸入主要組織、 夥伴組織、 PIP 代碼、 PIP 版本、 PIP 執行個體識別碼和訊息類別。</span><span class="sxs-lookup"><span data-stu-id="2d63a-135">In the **Submit Message** dialog box, type the home organization, the partner organization, the PIP code, the PIP version, the PIP Instance ID, and the message category.</span></span>  
  
4.  <span data-ttu-id="2d63a-136">視需要修改服務內容。</span><span class="sxs-lookup"><span data-stu-id="2d63a-136">Modify the service content as needed.</span></span>  
  
5.  <span data-ttu-id="2d63a-137">按一下 [提交]。</span><span class="sxs-lookup"><span data-stu-id="2d63a-137">Click **Submit**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d63a-138">備註</span><span class="sxs-lookup"><span data-stu-id="2d63a-138">Remarks</span></span>  
 <span data-ttu-id="2d63a-139">LOBWebApplication 公用程式會透過指定的 PIP 產生訊息的執行個體，再將產生的訊息執行個體中的服務內容輸入 ASPX 頁面。</span><span class="sxs-lookup"><span data-stu-id="2d63a-139">The LOBWebApplication utility generates an instance of the message from the specified PIP, and enters service content from the generated message instance into the ASPX page.</span></span> <span data-ttu-id="2d63a-140">為了執行這項操作，公用程式會使用與直接從 PIP 產生格式正確之訊息執行個體相同的技術。</span><span class="sxs-lookup"><span data-stu-id="2d63a-140">To do this, the utility uses the same technique that it uses to generate a well-formed message instance directly from a PIP.</span></span> <span data-ttu-id="2d63a-141">如需詳細資訊，請參閱[從 PIP 建立格式正確的訊息執行個體](../../adapters-and-accelerators/accelerator-rosettanet/creating-a-well-formed-message-instance-from-a-pip.md)。</span><span class="sxs-lookup"><span data-stu-id="2d63a-141">For more information, see [Creating a Well-Formed Message Instance from a PIP](../../adapters-and-accelerators/accelerator-rosettanet/creating-a-well-formed-message-instance-from-a-pip.md).</span></span> <span data-ttu-id="2d63a-142">在 ASPX 頁面中，您可以將實際資料填入服務內容的任何欄位，以產生實際的訊息執行個體。</span><span class="sxs-lookup"><span data-stu-id="2d63a-142">You can populate any field of the service content in the ASPX page with actual data to generate an actual message instance.</span></span>  
  
 <span data-ttu-id="2d63a-143">您可以使用 LOBWebApplication 公用程式，模擬商務營運系統 Web 應用程式提交訊息。</span><span class="sxs-lookup"><span data-stu-id="2d63a-143">You use the LOBWebApplication utility to simulate a line-of-business Web application submitting a message.</span></span> <span data-ttu-id="2d63a-144">您可以使用 LOBApplication 公用程式，模擬商務營運系統桌面應用程式以提交訊息。</span><span class="sxs-lookup"><span data-stu-id="2d63a-144">You use the LOBApplication utility to simulate a line-of-business desktop application submitting a message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d63a-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d63a-145">See Also</span></span>  
 <span data-ttu-id="2d63a-146">[公用程式](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md) </span><span class="sxs-lookup"><span data-stu-id="2d63a-146">[Utilities](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md) </span></span>  
 [<span data-ttu-id="2d63a-147">LOBApplication</span><span class="sxs-lookup"><span data-stu-id="2d63a-147">LOBApplication</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/lobapplication.md)