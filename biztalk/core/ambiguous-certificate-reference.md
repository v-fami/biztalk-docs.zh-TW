---
title: 模稜兩可的憑證參考 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a7a6a60d-97e6-4c60-86be-83efb4a50f99
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ac43f85b590ede746bbd14065d8e01701d1e91f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988831"
---
# <a name="ambiguous-certificate-reference"></a><span data-ttu-id="cccca-102">模稜兩可的憑證參考</span><span class="sxs-lookup"><span data-stu-id="cccca-102">Ambiguous certificate reference</span></span>
## <a name="details"></a><span data-ttu-id="cccca-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="cccca-103">Details</span></span>  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="cccca-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="cccca-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="cccca-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="cccca-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="cccca-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="cccca-106">Event ID</span></span>     |                                         <span data-ttu-id="cccca-107">0</span><span class="sxs-lookup"><span data-stu-id="cccca-107">0</span></span>                                          |
|  <span data-ttu-id="cccca-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="cccca-108">Event Source</span></span>   |                                         <span data-ttu-id="cccca-109">0</span><span class="sxs-lookup"><span data-stu-id="cccca-109">0</span></span>                                          |
|    <span data-ttu-id="cccca-110">元件</span><span class="sxs-lookup"><span data-stu-id="cccca-110">Component</span></span>    |                                         <span data-ttu-id="cccca-111">0</span><span class="sxs-lookup"><span data-stu-id="cccca-111">0</span></span>                                          |
|  <span data-ttu-id="cccca-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="cccca-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="cccca-113">0</span><span class="sxs-lookup"><span data-stu-id="cccca-113">0</span></span>                                          |
|  <span data-ttu-id="cccca-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="cccca-114">Message Text</span></span>   |       <span data-ttu-id="cccca-115">模稜兩可的憑證參考。找到一個以上的有效憑證</span><span class="sxs-lookup"><span data-stu-id="cccca-115">Ambiguous certificate reference; more than one valid certificate found</span></span>       |
  
## <a name="explanation"></a><span data-ttu-id="cccca-116">說明</span><span class="sxs-lookup"><span data-stu-id="cccca-116">Explanation</span></span>  
 <span data-ttu-id="cccca-117">找不到一個以上的有效憑證。</span><span class="sxs-lookup"><span data-stu-id="cccca-117">More than one valid certificate was found.</span></span>  
  
#### <a name="user-action"></a><span data-ttu-id="cccca-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="cccca-118">User action</span></span>  
 <span data-ttu-id="cccca-119">請確認只有一個有效的憑證設定。</span><span class="sxs-lookup"><span data-stu-id="cccca-119">Verify only one valid certificate is configured.</span></span>  
  
## <a name="verify-certificate"></a><span data-ttu-id="cccca-120">驗證憑證</span><span class="sxs-lookup"><span data-stu-id="cccca-120">Verify certificate</span></span> 
  
1. <span data-ttu-id="cccca-121">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下**BizTalk Server 管理]**。</span><span class="sxs-lookup"><span data-stu-id="cccca-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="cccca-122">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="cccca-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand **Applications**.</span></span>  
  
3. <span data-ttu-id="cccca-123">找出您的應用程式，然後找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="cccca-123">Locate your application and then locate your transport.</span></span>  
  
4. <span data-ttu-id="cccca-124">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="cccca-124">Right-click the transport name.</span></span>  
  
5. <span data-ttu-id="cccca-125">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="cccca-125">Click **Properties**.</span></span>  
  
6. <span data-ttu-id="cccca-126">在 連接埠**型別**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="cccca-126">In the port **Type** list, select the correct port.</span></span>  
  
7. <span data-ttu-id="cccca-127">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="cccca-127">Click **Configure**.</span></span>  
  
8. <span data-ttu-id="cccca-128">在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**一般**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="cccca-128">In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **General** tab.</span></span>  
  
9. <span data-ttu-id="cccca-129">按一下 **[編輯]**。</span><span class="sxs-lookup"><span data-stu-id="cccca-129">Click **Edit**.</span></span>  
  
10. <span data-ttu-id="cccca-130">在 **識別編輯器**對話方塊方塊中，請確定中的搜尋準則**憑證參考**區段表示只有一個憑證，憑證中的設定正確**存放區名稱**。</span><span class="sxs-lookup"><span data-stu-id="cccca-130">In the **Identity Editor** dialog box, make sure the search criteria in the **Certificate Reference** section is configured properly to indicate only one certificate in the certificate **Store name**.</span></span>  
  
## <a name="verify-a-certificate-for-the-wcf-custom-and-the-wcf-customisolated-adapters"></a><span data-ttu-id="cccca-131">Wcf-custom 和 Wcf-customisolated 配接器的驗證憑證</span><span class="sxs-lookup"><span data-stu-id="cccca-131">Verify a certificate for the WCF-Custom and the WCF-CustomIsolated adapters</span></span>  
  
1. <span data-ttu-id="cccca-132">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cccca-132">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and click [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span></span>  
  
2. <span data-ttu-id="cccca-133">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="cccca-133">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand **Applications**.</span></span>  
  
3. <span data-ttu-id="cccca-134">找出您的應用程式，然後找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="cccca-134">Locate your application and then locate your transport.</span></span>  
  
4. <span data-ttu-id="cccca-135">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="cccca-135">Right-click the transport name.</span></span>  
  
5. <span data-ttu-id="cccca-136">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="cccca-136">Click **Properties**.</span></span>  
  
6. <span data-ttu-id="cccca-137">在 連接埠**型別**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="cccca-137">In the port **Type** list, select the correct port.</span></span>  
  
7. <span data-ttu-id="cccca-138">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="cccca-138">Click **Configure**.</span></span>  
  
8. <span data-ttu-id="cccca-139">在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**行為**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="cccca-139">In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **Behavior** tab.</span></span>  
  
9. <span data-ttu-id="cccca-140">請確定中的搜尋準則**憑證參考**區段來表示只有一個憑證，憑證中的設定正確**存放區名稱**。</span><span class="sxs-lookup"><span data-stu-id="cccca-140">Ensure the search criteria in the **Certificate Reference** section is configured properly to indicate only one certificate in the certificate **Store name**.</span></span>  
  
10. <span data-ttu-id="cccca-141">在 [憑證] 嵌入式管理單元中，請確定只有一個憑證已安裝您設定 WCF 傳輸的搜尋準則。</span><span class="sxs-lookup"><span data-stu-id="cccca-141">In the Certificate snap-in, make sure only one certificate is installed for the search criteria you configured to the WCF transport.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cccca-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cccca-142">See also</span></span>
[<span data-ttu-id="cccca-143">安裝 WCF 配接器的憑證</span><span class="sxs-lookup"><span data-stu-id="cccca-143">Installing Certificates for the WCF Adapters</span></span>](../core/installing-certificates-for-the-wcf-adapters.md)  
 