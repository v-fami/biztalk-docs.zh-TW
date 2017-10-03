---
title: "保護傳送者 ASPX 頁面 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ASPX pages, protocol rules
- security, ASPX pages
- RNIFSend.aspx
- ASPX pages, security
- protocol rules [ASPX pages]
ms.assetid: 8214e3f5-a8e9-4d71-957d-ed0852035030
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0c5d5ec97d4d4aed862ffc1dbc0d75d0c0430d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="securing-the-sender-aspx-page"></a><span data-ttu-id="e0f9e-102">保護傳送者 ASPX 頁面</span><span class="sxs-lookup"><span data-stu-id="e0f9e-102">Securing the Sender ASPX Page</span></span>
<span data-ttu-id="e0f9e-103">本主題說明如何保護 RNIFSend.aspx 頁面，避免未經授權的使用。</span><span class="sxs-lookup"><span data-stu-id="e0f9e-103">This topic describes how to protect the RNIFSend.aspx page from unauthorized use.</span></span> <span data-ttu-id="e0f9e-104">您可以使用下列兩個程序：</span><span class="sxs-lookup"><span data-stu-id="e0f9e-104">There are two procedures that you can use:</span></span>  
  
-   <span data-ttu-id="e0f9e-105">在網際網路資訊服務 (IIS) 管理員中，保護 RNIFSend.aspx 以確保未經授權的伺服器，無法使用 RNIFSend.aspx 頁面從您的網路傳輸未經授權的訊息。</span><span class="sxs-lookup"><span data-stu-id="e0f9e-105">In Internet Information Services (IIS) Manager, secure RNIFSend.aspx to make sure that no unauthorized server will use the RNIFSend.aspx page to transmit unauthorized messages from your network.</span></span>  
  
-   <span data-ttu-id="e0f9e-106">使用 Microsoft Internet Security and Acceleration (ISA) Server 建立外寄 HTTP 要求的通訊協定規則。</span><span class="sxs-lookup"><span data-stu-id="e0f9e-106">Use Microsoft Internet Security and Acceleration (ISA) Server to create a protocol rule of outgoing HTTP requests.</span></span>  
  
### <a name="to-secure-rnifsendaspx"></a><span data-ttu-id="e0f9e-107">保護 RNIFSend.aspx</span><span class="sxs-lookup"><span data-stu-id="e0f9e-107">To secure RNIFSend.aspx</span></span>  
  
1.  <span data-ttu-id="e0f9e-108">在 Web 伺服器上您用於 RNIF 訊息傳輸，按一下 **啟動**，指向**所有程式**，指向 **系統管理工具**，然後按一下  **Internet Information Services (IIS) 管理員**。</span><span class="sxs-lookup"><span data-stu-id="e0f9e-108">On the Web server you use for RNIF message transmission, click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2.  <span data-ttu-id="e0f9e-109">在 [IIS 管理員] 中，展開 [本機電腦] 節點，再展開**網站**，然後展開**Default Web Site**。</span><span class="sxs-lookup"><span data-stu-id="e0f9e-109">In IIS Manager, expand the local computer node, expand **Web Sites**, and then expand **Default Web Site**.</span></span>  
  
3.  <span data-ttu-id="e0f9e-110">按一下**BTARNApp**，然後在右窗格中，以滑鼠右鍵按一下**RNIFSend.aspx**。</span><span class="sxs-lookup"><span data-stu-id="e0f9e-110">Click **BTARNApp**, and then in the right pane, right-click **RNIFSend.aspx**.</span></span>  
  
4.  <span data-ttu-id="e0f9e-111">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="e0f9e-111">Click **Properties**.</span></span> <span data-ttu-id="e0f9e-112">在**檔案安全性**索引標籤的**IP 位址及網域名稱限制**區段中，按一下**編輯**。</span><span class="sxs-lookup"><span data-stu-id="e0f9e-112">On the **File Security** tab, in the **IP address and domain name restrictions** section, click **Edit**.</span></span>  
  
5.  <span data-ttu-id="e0f9e-113">在 IP 位址和網域名稱限制 對話方塊中，按一下**拒絕存取**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="e0f9e-113">In the IP Address and Domain Name Restrictions dialog box, click **Denied Access**, and then click **Add**.</span></span>  
  
6.  <span data-ttu-id="e0f9e-114">在**授與存取權**對話方塊中，新增全部 BizTalk Servers 執行傳送作業。</span><span class="sxs-lookup"><span data-stu-id="e0f9e-114">In the **Grant Access** dialog box, add all BizTalk Servers performing send operations.</span></span> <span data-ttu-id="e0f9e-115">如果新增單一伺服器，請按一下**單一電腦**。</span><span class="sxs-lookup"><span data-stu-id="e0f9e-115">If adding a single server, click **Single computer**.</span></span> <span data-ttu-id="e0f9e-116">在**IP 位址**方塊中，輸入電腦的 IP 位址，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="e0f9e-116">In the **IP Address** box, type the IP address for the computer, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="e0f9e-117">如果新增的伺服器群組，按一下 **電腦群組**，然後執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="e0f9e-117">If adding a group of servers, click **Group of Computers**, and then do the following:</span></span>  
  
    |<span data-ttu-id="e0f9e-118">使用</span><span class="sxs-lookup"><span data-stu-id="e0f9e-118">Use this</span></span>|<span data-ttu-id="e0f9e-119">動作</span><span class="sxs-lookup"><span data-stu-id="e0f9e-119">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="e0f9e-120">**網路識別碼**</span><span class="sxs-lookup"><span data-stu-id="e0f9e-120">**Network ID**</span></span>|<span data-ttu-id="e0f9e-121">輸入您想使用的網路。</span><span class="sxs-lookup"><span data-stu-id="e0f9e-121">Type the network you want to use.</span></span>|  
    |<span data-ttu-id="e0f9e-122">**子網路遮罩**</span><span class="sxs-lookup"><span data-stu-id="e0f9e-122">**Subnet mask**</span></span>|<span data-ttu-id="e0f9e-123">輸入您想使用的子網路遮罩。</span><span class="sxs-lookup"><span data-stu-id="e0f9e-123">Type the subnet mask you want to use.</span></span>|  
  
8.  <span data-ttu-id="e0f9e-124">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e0f9e-124">Click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e0f9e-125">如果您將所有的傳送作業放到另一台執行不同執行個體的主機上，只要新增這台電腦就可以了。</span><span class="sxs-lookup"><span data-stu-id="e0f9e-125">If you have separated all your send operations to a separate host running on a separate instance, then you only have to add this computer.</span></span> <span data-ttu-id="e0f9e-126">您可以拒絕其他電腦的存取。</span><span class="sxs-lookup"><span data-stu-id="e0f9e-126">You can deny all others access.</span></span>  
  
9. <span data-ttu-id="e0f9e-127">按一下**確定**，然後按一下 **確定**一次。</span><span class="sxs-lookup"><span data-stu-id="e0f9e-127">Click **OK**, and then click **OK** again.</span></span>  
  
### <a name="to-create-a-protocol-rule-of-outgoing-http-requests"></a><span data-ttu-id="e0f9e-128">建立外寄 HTTP 要求的通訊協定規則</span><span class="sxs-lookup"><span data-stu-id="e0f9e-128">To create a protocol rule of outgoing HTTP requests</span></span>  
  
1.  <span data-ttu-id="e0f9e-129">在 ISA 管理按一下**存取原則**，然後按一下 **通訊協定規則**。</span><span class="sxs-lookup"><span data-stu-id="e0f9e-129">In ISA Management, click **Access Policy**, and then click **Protocol Rules**.</span></span>  
  
2.  <span data-ttu-id="e0f9e-130">建立新的通訊協定規則，名為**HTTP**使用 TCP 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="e0f9e-130">Create a new protocol rule named **HTTP** that uses TCP protocol.</span></span>  
  
3.  <span data-ttu-id="e0f9e-131">在屬性頁面中的新的 HTTP 通訊協定規則，在**套用至**索引標籤上，選取**適用於下面指定的用戶端位址組**。</span><span class="sxs-lookup"><span data-stu-id="e0f9e-131">In the property page of your new HTTP protocol rule, in the **Applies To** tab, select **Applies to Client address sets specified below**.</span></span> <span data-ttu-id="e0f9e-132">輸入您想要存取該頁面的用戶端 IP。</span><span class="sxs-lookup"><span data-stu-id="e0f9e-132">Enter only those client IPs that you want to access the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0f9e-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0f9e-133">See Also</span></span>  
 [<span data-ttu-id="e0f9e-134">管理設定、 憑證、 資料庫和安全性</span><span class="sxs-lookup"><span data-stu-id="e0f9e-134">Manage configuration, certificates, databases, and security</span></span>](manage-configuration-certificates-databases-security.md)