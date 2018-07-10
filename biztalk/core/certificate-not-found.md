---
title: 找不到憑證 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 629b199f-1884-4e88-beaa-a2e5c5e792e9
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e636d37f6b8758934a25e3b45338ca7b19a4d076
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005695"
---
# <a name="certificate-not-found"></a><span data-ttu-id="0f117-102">找不到憑證</span><span class="sxs-lookup"><span data-stu-id="0f117-102">Certificate not found</span></span>
## <a name="details"></a><span data-ttu-id="0f117-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0f117-103">Details</span></span>  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="0f117-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0f117-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="0f117-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="0f117-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="0f117-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0f117-106">Event ID</span></span>     |                                         <span data-ttu-id="0f117-107">0</span><span class="sxs-lookup"><span data-stu-id="0f117-107">0</span></span>                                          |
|  <span data-ttu-id="0f117-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="0f117-108">Event Source</span></span>   |                                         <span data-ttu-id="0f117-109">0</span><span class="sxs-lookup"><span data-stu-id="0f117-109">0</span></span>                                          |
|    <span data-ttu-id="0f117-110">元件</span><span class="sxs-lookup"><span data-stu-id="0f117-110">Component</span></span>    |                                         <span data-ttu-id="0f117-111">0</span><span class="sxs-lookup"><span data-stu-id="0f117-111">0</span></span>                                          |
|  <span data-ttu-id="0f117-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0f117-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="0f117-113">0</span><span class="sxs-lookup"><span data-stu-id="0f117-113">0</span></span>                                          |
|  <span data-ttu-id="0f117-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0f117-114">Message Text</span></span>   |                               <span data-ttu-id="0f117-115">找不到憑證。</span><span class="sxs-lookup"><span data-stu-id="0f117-115">Certificate not found.</span></span>                               |
  
## <a name="explanation"></a><span data-ttu-id="0f117-116">說明</span><span class="sxs-lookup"><span data-stu-id="0f117-116">Explanation</span></span>  
 <span data-ttu-id="0f117-117">找不到指定的搜尋準則的憑證。</span><span class="sxs-lookup"><span data-stu-id="0f117-117">A certificate could not be found for the given search criteria.</span></span>  

#### <a name="user-action"></a><span data-ttu-id="0f117-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0f117-118">User Action</span></span>
<span data-ttu-id="0f117-119">確認憑證的搜尋準則。</span><span class="sxs-lookup"><span data-stu-id="0f117-119">Verify search criteria for certificates.</span></span> 
  
## <a name="verify-search-criteria"></a><span data-ttu-id="0f117-120">驗證搜尋準則</span><span class="sxs-lookup"><span data-stu-id="0f117-120">Verify search criteria</span></span>  
  
1. <span data-ttu-id="0f117-121">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。</span><span class="sxs-lookup"><span data-stu-id="0f117-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="0f117-122">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="0f117-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3. <span data-ttu-id="0f117-123">找出您的應用程式，然後找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="0f117-123">Locate your application and then locate your transport.</span></span>  
  
4. <span data-ttu-id="0f117-124">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="0f117-124">Right-click the transport name.</span></span>  
  
5. <span data-ttu-id="0f117-125">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="0f117-125">Click **Properties**.</span></span>  
  
6. <span data-ttu-id="0f117-126">在 連接埠**型別**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="0f117-126">In the port **Type** list, select the correct port.</span></span>  
  
7. <span data-ttu-id="0f117-127">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="0f117-127">Click **Configure**.</span></span>  
  
8. <span data-ttu-id="0f117-128">在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**一般**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0f117-128">In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **General** tab.</span></span>  
  
9. <span data-ttu-id="0f117-129">按一下 **[編輯]**。</span><span class="sxs-lookup"><span data-stu-id="0f117-129">Click **Edit**.</span></span>  
  
10. <span data-ttu-id="0f117-130">在 **識別編輯器**對話方塊方塊中，請確定中的搜尋準則**憑證參考**區段表示的有效憑證的設定正確。</span><span class="sxs-lookup"><span data-stu-id="0f117-130">In the **Identity Editor** dialog box, make sure that the search criteria in the **Certificate Reference** section is configured properly to indicate valid certificates.</span></span>  
  
    <span data-ttu-id="0f117-131">對於 Wcf-custom 和 Wcf-customisolated 配接器，請確認中的搜尋準則**憑證參考**區段表示有效的憑證，憑證中的設定正確**存放區名稱**.</span><span class="sxs-lookup"><span data-stu-id="0f117-131">For the WCF-Custom and the WCF-CustomIsolated adapters, ensure that the search criteria in the **Certificate Reference** section is configured properly to indicate a valid certificate in the certificate **Store name**.</span></span>  
  
## <a name="verify-search-criteria-for-standard-wcf-adapters"></a><span data-ttu-id="0f117-132">確認標準 WCF 配接器的搜尋準則</span><span class="sxs-lookup"><span data-stu-id="0f117-132">Verify search criteria for standard WCF adapters</span></span>  
  
1. <span data-ttu-id="0f117-133">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。</span><span class="sxs-lookup"><span data-stu-id="0f117-133">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="0f117-134">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="0f117-134">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand **Applications**.</span></span>  
  
3. <span data-ttu-id="0f117-135">找出您的應用程式，然後找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="0f117-135">Locate your application and then locate your transport.</span></span>  
  
4. <span data-ttu-id="0f117-136">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="0f117-136">Right-click the transport name.</span></span>  
  
5. <span data-ttu-id="0f117-137">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="0f117-137">Click **Properties**.</span></span>  
  
6. <span data-ttu-id="0f117-138">在 連接埠**型別**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="0f117-138">In the port **Type** list, select the correct port.</span></span>  
  
7. <span data-ttu-id="0f117-139">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="0f117-139">Click **Configure**.</span></span>  
  
8. <span data-ttu-id="0f117-140">在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**安全性**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0f117-140">In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **Security** tab.</span></span>  
  
9. <span data-ttu-id="0f117-141">請確認**指紋**服務和用戶端憑證的屬性會指出在憑證存放區中的有效憑證。</span><span class="sxs-lookup"><span data-stu-id="0f117-141">Ensure that the **Thumbprint** properties for the service and client certificates indicate valid certificates in certificate stores.</span></span>  
  
10. <span data-ttu-id="0f117-142">在 [憑證] 嵌入式管理單元中，確定已安裝 WCF 傳輸的有效憑證。</span><span class="sxs-lookup"><span data-stu-id="0f117-142">In the Certificate snap-in, make sure that valid certificates are installed for the WCF transport.</span></span>  

## <a name="see-also"></a><span data-ttu-id="0f117-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f117-143">See also</span></span> 
  
-   [<span data-ttu-id="0f117-144">安裝 WCF 配接器的憑證</span><span class="sxs-lookup"><span data-stu-id="0f117-144">Installing Certificates for the WCF Adapters</span></span>](../core/installing-certificates-for-the-wcf-adapters.md)  
  
