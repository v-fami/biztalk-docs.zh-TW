---
title: "模稜兩可的憑證參考 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7a6a60d-97e6-4c60-86be-83efb4a50f99
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 304ded9572ba6598f7f2132a678a14b2b3301c10
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="ambiguous-certificate-reference"></a><span data-ttu-id="02770-102">模稜兩可的憑證參考</span><span class="sxs-lookup"><span data-stu-id="02770-102">Ambiguous certificate reference</span></span>
## <a name="details"></a><span data-ttu-id="02770-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="02770-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="02770-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="02770-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="02770-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="02770-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="02770-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="02770-106">Event ID</span></span>|<span data-ttu-id="02770-107">0</span><span class="sxs-lookup"><span data-stu-id="02770-107">0</span></span>|  
|<span data-ttu-id="02770-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="02770-108">Event Source</span></span>|<span data-ttu-id="02770-109">0</span><span class="sxs-lookup"><span data-stu-id="02770-109">0</span></span>|  
|<span data-ttu-id="02770-110">元件</span><span class="sxs-lookup"><span data-stu-id="02770-110">Component</span></span>|<span data-ttu-id="02770-111">0</span><span class="sxs-lookup"><span data-stu-id="02770-111">0</span></span>|  
|<span data-ttu-id="02770-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="02770-112">Symbolic Name</span></span>|<span data-ttu-id="02770-113">0</span><span class="sxs-lookup"><span data-stu-id="02770-113">0</span></span>|  
|<span data-ttu-id="02770-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="02770-114">Message Text</span></span>|<span data-ttu-id="02770-115">模稜兩可的憑證參考。找到一個以上的有效憑證</span><span class="sxs-lookup"><span data-stu-id="02770-115">Ambiguous certificate reference; more than one valid certificate found</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="02770-116">說明</span><span class="sxs-lookup"><span data-stu-id="02770-116">Explanation</span></span>  
 <span data-ttu-id="02770-117">找不到一個以上的有效憑證。</span><span class="sxs-lookup"><span data-stu-id="02770-117">More than one valid certificate was found.</span></span>  
  
#### <a name="user-action"></a><span data-ttu-id="02770-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="02770-118">User action</span></span>  
 <span data-ttu-id="02770-119">請確認只有一個已設定有效的憑證。</span><span class="sxs-lookup"><span data-stu-id="02770-119">Verify only one valid certificate is configured.</span></span>  
  
## <a name="verify-certificate"></a><span data-ttu-id="02770-120">驗證憑證</span><span class="sxs-lookup"><span data-stu-id="02770-120">Verify certificate</span></span> 
  
1.  <span data-ttu-id="02770-121">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="02770-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="02770-122">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="02770-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="02770-123">找出您的應用程式，然後再找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="02770-123">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="02770-124">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="02770-124">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="02770-125">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="02770-125">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="02770-126">在 連接埠**類型**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="02770-126">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="02770-127">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="02770-127">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="02770-128">在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**一般**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="02770-128">In the **WCF [***transport type***] Transport Properties** dialog box, click the **General** tab.</span></span>  
  
9. <span data-ttu-id="02770-129">按一下 **[編輯]**。</span><span class="sxs-lookup"><span data-stu-id="02770-129">Click **Edit**.</span></span>  
  
10. <span data-ttu-id="02770-130">在**識別編輯器**對話方塊方塊中，請確定中的搜尋準則**憑證參考**區段已正確設定成指出憑證中的只有一個憑證**存放區名稱**。</span><span class="sxs-lookup"><span data-stu-id="02770-130">In the **Identity Editor** dialog box, make sure the search criteria in the **Certificate Reference** section is configured properly to indicate only one certificate in the certificate **Store name**.</span></span>  
  
## <a name="verify-a-certificate-for-the-wcf-custom-and-the-wcf-customisolated-adapters"></a><span data-ttu-id="02770-131">Wcf-custom 和 Wcf-customisolated 配接器的驗證認證</span><span class="sxs-lookup"><span data-stu-id="02770-131">Verify a certificate for the WCF-Custom and the WCF-CustomIsolated adapters</span></span>  
  
1.  <span data-ttu-id="02770-132">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="02770-132">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and click [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span></span>  
  
2.  <span data-ttu-id="02770-133">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="02770-133">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="02770-134">找出您的應用程式，然後再找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="02770-134">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="02770-135">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="02770-135">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="02770-136">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="02770-136">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="02770-137">在 連接埠**類型**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="02770-137">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="02770-138">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="02770-138">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="02770-139">在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**行為**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="02770-139">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Behavior** tab.</span></span>  
  
9. <span data-ttu-id="02770-140">請確定中的搜尋準則**憑證參考**區段已正確設定成指出憑證中的只有一個憑證**存放區名稱**。</span><span class="sxs-lookup"><span data-stu-id="02770-140">Ensure the search criteria in the **Certificate Reference** section is configured properly to indicate only one certificate in the certificate **Store name**.</span></span>  
  
10. <span data-ttu-id="02770-141">在 [憑證] 嵌入式管理單元，請確定只有一個憑證已安裝 WCF 傳輸到您設定的搜尋準則。</span><span class="sxs-lookup"><span data-stu-id="02770-141">In the Certificate snap-in, make sure only one certificate is installed for the search criteria you configured to the WCF transport.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02770-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02770-142">See also</span></span>
[<span data-ttu-id="02770-143">WCF 配接器安裝憑證</span><span class="sxs-lookup"><span data-stu-id="02770-143">Installing Certificates for the WCF Adapters</span></span>](../core/installing-certificates-for-the-wcf-adapters.md)  
 