---
title: "如何設定 SMTP 傳送處理常式 |Microsoft 文件"
ms.custom: 
ms.date: 2015-10-22
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send handlers, SMTP adapters
- SMTP adapters, send handlers
- configuring [SMTP adapters], send handlers
ms.assetid: b68a36ce-f0a5-4302-a405-bb154c935f47
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 99dc71cf04d8a80b3a88630908a814957c83b8cb
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-configure-an-smtp-send-handler"></a><span data-ttu-id="333b8-102">如何設定 SMTP 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="333b8-102">How to Configure an SMTP Send Handler</span></span>
<span data-ttu-id="333b8-103">您可以在「BizTalk 管理」主控台中設定 SMTP 傳送處理常式屬性。</span><span class="sxs-lookup"><span data-stu-id="333b8-103">You can set SMTP send handler properties in the BizTalk Administration console.</span></span> <span data-ttu-id="333b8-104">若屬性不是在個別 SMTP 傳送埠中設定，這些傳送處理常式屬性就會當作傳送埠組態值。</span><span class="sxs-lookup"><span data-stu-id="333b8-104">These send handler properties are used as the send port configuration values if the properties are not set on the individual SMTP send port.</span></span>  
  
### <a name="to-change-global-variables-for-an-smtp-send-handler"></a><span data-ttu-id="333b8-105">變更 SMTP 傳送處理常式的全域變數</span><span class="sxs-lookup"><span data-stu-id="333b8-105">To change global variables for an SMTP send handler</span></span>  
  
1.  <span data-ttu-id="333b8-106">在 BizTalk Server 管理主控台中，依序展開[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後展開 **配接器**。</span><span class="sxs-lookup"><span data-stu-id="333b8-106">In the BizTalk Server Administration Console, expand [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  
  
2.  <span data-ttu-id="333b8-107">在展開的配接器清單中，按一下  **SMTP**, ，在右窗格，以滑鼠右鍵按一下您想要設定的傳送處理常式，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="333b8-107">In the expanded adapter list, click **SMTP**, in the right pane, right-click the send handler that you want to configure, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="333b8-108">在 **配接器處理常式屬性** 對話方塊的  **一般** 索引標籤的 **主機名稱** 清單中，選取主控件與傳送處理常式將會產生關聯，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="333b8-108">In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the send handler will be associated, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="333b8-109">在 **SMTP 傳輸屬性** 對話方塊的  **屬性** 索引標籤上，執行下列動作︰</span><span class="sxs-lookup"><span data-stu-id="333b8-109">In the **SMTP Transport Properties** dialog box, on the **Properties** tab, do the following:</span></span>  
  
    |<span data-ttu-id="333b8-110">使用</span><span class="sxs-lookup"><span data-stu-id="333b8-110">Use this</span></span>|<span data-ttu-id="333b8-111">動作</span><span class="sxs-lookup"><span data-stu-id="333b8-111">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="333b8-112">**SMTP 伺服器名稱和 TCP 連接埠**</span><span class="sxs-lookup"><span data-stu-id="333b8-112">**SMTP server name and TCP port**</span></span>|**[!INCLUDE[bts2013r2](../includes/bts2013r2-md.md)]**<br /><br /> <span data-ttu-id="333b8-113">必要。</span><span class="sxs-lookup"><span data-stu-id="333b8-113">Required.</span></span> <span data-ttu-id="333b8-114">輸入 SMTP 伺服器名稱和 （選擇性） 若要傳送訊息時使用的 TCP 連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="333b8-114">Enter the SMTP server  name and the TCP port number (optional) to use when sending messages.</span></span> <span data-ttu-id="333b8-115">例如，您可以輸入︰</span><span class="sxs-lookup"><span data-stu-id="333b8-115">For example, you can enter:</span></span><br /><br /> <span data-ttu-id="333b8-116">-mySMTPserver</span><span class="sxs-lookup"><span data-stu-id="333b8-116">-   mySMTPserver</span></span><br /><span data-ttu-id="333b8-117">-mySMTPserver.internet.com:2525</span><span class="sxs-lookup"><span data-stu-id="333b8-117">-   mySMTPserver.internet.com:2525</span></span><br /><br /> <span data-ttu-id="333b8-118">**在舊版的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**  （包括 BizTalk Server 2013)，僅輸入 SMTP 伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="333b8-118">**In previous versions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]** (including BizTalk Server 2013), enter only the SMTP server name.</span></span> <span data-ttu-id="333b8-119">TCP 連接埠 25 是硬式編碼。</span><span class="sxs-lookup"><span data-stu-id="333b8-119">TCP Port 25 is hard-coded.</span></span><br /><br /> <span data-ttu-id="333b8-120">最大長度：256</span><span class="sxs-lookup"><span data-stu-id="333b8-120">Maximum length: 256</span></span>|  
    |<span data-ttu-id="333b8-121">**（電子郵件地址）**</span><span class="sxs-lookup"><span data-stu-id="333b8-121">**From (e-mail address)**</span></span>|<span data-ttu-id="333b8-122">必要。</span><span class="sxs-lookup"><span data-stu-id="333b8-122">Required.</span></span> <span data-ttu-id="333b8-123">輸入電子郵件地址，放在 SMTP **從** 標頭。</span><span class="sxs-lookup"><span data-stu-id="333b8-123">Enter the e-mail address to put on the SMTP **From** header.</span></span><br /><br /> <span data-ttu-id="333b8-124">最大長度：256</span><span class="sxs-lookup"><span data-stu-id="333b8-124">Maximum length: 256</span></span>|  
    |<span data-ttu-id="333b8-125">**驗證類型**</span><span class="sxs-lookup"><span data-stu-id="333b8-125">**Authentication type**</span></span>|<span data-ttu-id="333b8-126">輸入要使用的 SMTP 伺服器的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="333b8-126">Enter the type of authentication to use with the SMTP server.</span></span><br /><br /> <span data-ttu-id="333b8-127">選項：</span><span class="sxs-lookup"><span data-stu-id="333b8-127">Options:</span></span><br /><br /> <span data-ttu-id="333b8-128">-   **不需要驗證**</span><span class="sxs-lookup"><span data-stu-id="333b8-128">-   **No authentication**</span></span><br /><span data-ttu-id="333b8-129">-   **基本驗證**</span><span class="sxs-lookup"><span data-stu-id="333b8-129">-   **Basic authentication**</span></span><br /><span data-ttu-id="333b8-130">-   **處理序帳戶 (NTLM)**</span><span class="sxs-lookup"><span data-stu-id="333b8-130">-   **Process account (NTLM)**</span></span><br /><br /> <span data-ttu-id="333b8-131">預設值：處理帳戶 (NTLM)</span><span class="sxs-lookup"><span data-stu-id="333b8-131">Default value: Process account (NTLM)</span></span>|  
    |<span data-ttu-id="333b8-132">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="333b8-132">**User name**</span></span>|<span data-ttu-id="333b8-133">輸入要用於 SMTP 伺服器驗證的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="333b8-133">Enter the user name to use for authentication with the SMTP server.</span></span><br /><br /> <span data-ttu-id="333b8-134">此屬性需要一個值，如果 **驗證類型** 是 **基本驗證**。</span><span class="sxs-lookup"><span data-stu-id="333b8-134">This property requires a value if **Authentication type** is **Basic authentication**.</span></span><br /><br /> <span data-ttu-id="333b8-135">最小長度：00</span><span class="sxs-lookup"><span data-stu-id="333b8-135">Minimum length: 0</span></span><br /><br /> <span data-ttu-id="333b8-136">最大長度：256</span><span class="sxs-lookup"><span data-stu-id="333b8-136">Maximum length: 256</span></span>|  
    |<span data-ttu-id="333b8-137">**密碼**</span><span class="sxs-lookup"><span data-stu-id="333b8-137">**Password**</span></span>|<span data-ttu-id="333b8-138">輸入要用於驗證的 SMTP 伺服器的密碼。</span><span class="sxs-lookup"><span data-stu-id="333b8-138">Enter the password to use for authentication with the SMTP server.</span></span><br /><br /> <span data-ttu-id="333b8-139">此屬性需要一個值，如果 **驗證類型** 是 **基本驗證**。</span><span class="sxs-lookup"><span data-stu-id="333b8-139">This property requires a value if **Authentication type** is **Basic authentication**.</span></span><br /><br /> <span data-ttu-id="333b8-140">最小長度：00</span><span class="sxs-lookup"><span data-stu-id="333b8-140">Minimum length: 0</span></span><br /><br /> <span data-ttu-id="333b8-141">最大長度：256</span><span class="sxs-lookup"><span data-stu-id="333b8-141">Maximum length: 256</span></span>|  
  
5.  <span data-ttu-id="333b8-142">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="333b8-142">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="333b8-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="333b8-143">See Also</span></span>  
 [<span data-ttu-id="333b8-144">設定 SMTP 配接器</span><span class="sxs-lookup"><span data-stu-id="333b8-144">Configuring the SMTP Adapter</span></span>](../core/configuring-the-smtp-adapter.md)