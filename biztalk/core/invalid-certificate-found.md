---
title: "找到無效的憑證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b3a9ae8-a9d7-4025-bacd-443e136ff980
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fdf1d80818dd8e7dba349ea1dec9b69fa66a2fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-certificate-found"></a><span data-ttu-id="fbc2b-102">找到無效的憑證</span><span class="sxs-lookup"><span data-stu-id="fbc2b-102">Invalid certificate found</span></span>
## <a name="details"></a><span data-ttu-id="fbc2b-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fbc2b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fbc2b-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="fbc2b-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="fbc2b-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="fbc2b-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="fbc2b-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="fbc2b-106">Event ID</span></span>|<span data-ttu-id="fbc2b-107">0</span><span class="sxs-lookup"><span data-stu-id="fbc2b-107">0</span></span>|  
|<span data-ttu-id="fbc2b-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="fbc2b-108">Event Source</span></span>|<span data-ttu-id="fbc2b-109">0</span><span class="sxs-lookup"><span data-stu-id="fbc2b-109">0</span></span>|  
|<span data-ttu-id="fbc2b-110">元件</span><span class="sxs-lookup"><span data-stu-id="fbc2b-110">Component</span></span>|<span data-ttu-id="fbc2b-111">0</span><span class="sxs-lookup"><span data-stu-id="fbc2b-111">0</span></span>|  
|<span data-ttu-id="fbc2b-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="fbc2b-112">Symbolic Name</span></span>|<span data-ttu-id="fbc2b-113">0</span><span class="sxs-lookup"><span data-stu-id="fbc2b-113">0</span></span>|  
|<span data-ttu-id="fbc2b-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="fbc2b-114">Message Text</span></span>|<span data-ttu-id="fbc2b-115">找到無效的憑證</span><span class="sxs-lookup"><span data-stu-id="fbc2b-115">Invalid certificate found</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="fbc2b-116">說明</span><span class="sxs-lookup"><span data-stu-id="fbc2b-116">Explanation</span></span>  
 <span data-ttu-id="fbc2b-117">未提供 WCF 傳輸的有效憑證。</span><span class="sxs-lookup"><span data-stu-id="fbc2b-117">You did not provide a valid certificate for a WCF transport.</span></span>  

#### <a name="user-action"></a><span data-ttu-id="fbc2b-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="fbc2b-118">User Action</span></span>
<span data-ttu-id="fbc2b-119">新增憑證。</span><span class="sxs-lookup"><span data-stu-id="fbc2b-119">Add a certificate.</span></span> 
  
## <a name="add-a-certificate"></a><span data-ttu-id="fbc2b-120">加入憑證</span><span class="sxs-lookup"><span data-stu-id="fbc2b-120">Add a certificate</span></span>  
  
1.  <span data-ttu-id="fbc2b-121">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="fbc2b-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="fbc2b-122">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="fbc2b-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="fbc2b-123">找出您的應用程式，然後再找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="fbc2b-123">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="fbc2b-124">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="fbc2b-124">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="fbc2b-125">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="fbc2b-125">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="fbc2b-126">在 連接埠**類型**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="fbc2b-126">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="fbc2b-127">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="fbc2b-127">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="fbc2b-128">在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**一般**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="fbc2b-128">In the **WCF [***transport type***] Transport Properties** dialog box, click the **General** tab.</span></span>  
  
9. <span data-ttu-id="fbc2b-129">按一下 **[編輯]**。</span><span class="sxs-lookup"><span data-stu-id="fbc2b-129">Click **Edit**.</span></span>  
  
10. <span data-ttu-id="fbc2b-130">在**識別編輯器**對話方塊方塊中，請確定中的搜尋準則**憑證參考**區段已正確設定成指出有效的憑證。</span><span class="sxs-lookup"><span data-stu-id="fbc2b-130">In the **Identity Editor** dialog box, make sure the search criteria in the **Certificate Reference** section is configured properly to indicate valid certificates.</span></span>  
  
 <span data-ttu-id="fbc2b-131">對於 Wcf-custom 和 Wcf-customisolated 配接器，請確認中的搜尋準則**憑證參考**區段已正確設定成指出有效的憑證，憑證中**存放區名稱**.</span><span class="sxs-lookup"><span data-stu-id="fbc2b-131">For the WCF-Custom and the WCF-CustomIsolated adapters, ensure that the search criteria in the **Certificate Reference** section is configured properly to indicate a valid certificate in the certificate **Store name**.</span></span>  
  
## <a name="add-a-certificate-for-standard-wcf-adapters"></a><span data-ttu-id="fbc2b-132">新增標準 WCF 配接器的憑證</span><span class="sxs-lookup"><span data-stu-id="fbc2b-132">Add a certificate for standard WCF adapters</span></span>  
  
1.  <span data-ttu-id="fbc2b-133">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="fbc2b-133">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="fbc2b-134">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="fbc2b-134">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="fbc2b-135">找出您的應用程式，然後再找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="fbc2b-135">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="fbc2b-136">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="fbc2b-136">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="fbc2b-137">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="fbc2b-137">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="fbc2b-138">在 連接埠**類型**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="fbc2b-138">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="fbc2b-139">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="fbc2b-139">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="fbc2b-140">在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**安全性**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="fbc2b-140">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Security** tab.</span></span>  
  
9. <span data-ttu-id="fbc2b-141">請確認**指紋**服務與用戶端憑證的屬性指出有效的憑證，憑證中**存放區名稱**。</span><span class="sxs-lookup"><span data-stu-id="fbc2b-141">Ensure that the **Thumbprint** properties for the service and client certificates indicate valid certificates in the certificate **Store name**.</span></span>  
  
 <span data-ttu-id="fbc2b-142">在 [憑證] 嵌入式管理單元，請確定已安裝 WCF 傳輸的有效憑證。</span><span class="sxs-lookup"><span data-stu-id="fbc2b-142">In the Certificate snap-in, make sure that valid certificates are installed for the WCF transport.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbc2b-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbc2b-143">See also</span></span> 
  
[<span data-ttu-id="fbc2b-144">WCF 配接器安裝憑證</span><span class="sxs-lookup"><span data-stu-id="fbc2b-144">Installing Certificates for the WCF Adapters</span></span>](../core/installing-certificates-for-the-wcf-adapters.md)  