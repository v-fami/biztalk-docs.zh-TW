---
title: 設定使用 Wcf-siebel 配接器的連接埠 |Microsoft Docs
description: 建立 Wcf-siebel 傳送埠，以使用 BizTalk Server 中的 Siebel eBusiness 應用程式配接器
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e6314104-c742-440c-b530-b5a82295353a
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6eec0ca12c8b77d9327ddc7fae6136c75ff99202
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975519"
---
# <a name="configure-a-port-using-the-wcf-siebel-adapter"></a><span data-ttu-id="c5688-103">設定使用 Wcf-siebel 配接器的連接埠</span><span class="sxs-lookup"><span data-stu-id="c5688-103">Configure a port using the WCF-Siebel adapter</span></span>
<span data-ttu-id="c5688-104">如何設定 Wcf-siebel 輸出上執行作業使用 Siebel 系統的傳送埠[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c5688-104">How to configure WCF-Siebel send ports to perform outbound operations on a Siebel system using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c5688-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="c5688-105">Prerequisites</span></span>  
<span data-ttu-id="c5688-106">使用成員的帳戶登入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]系統管理員 」 或 「 BizTalk 操作員群組。</span><span class="sxs-lookup"><span data-stu-id="c5688-106">Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators or BizTalk Operators group.</span></span> <span data-ttu-id="c5688-107">如需詳細的權限的相關資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)，並[最低安全性權限](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx)。</span><span class="sxs-lookup"><span data-stu-id="c5688-107">For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), and [Minimum Security Rights ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx).</span></span>
  
## <a name="deploy-adapters-for-sending-messages-to-a-siebel-system"></a><span data-ttu-id="c5688-108">部署配接器將訊息傳送至 Siebel 系統</span><span class="sxs-lookup"><span data-stu-id="c5688-108">Deploy adapters for sending messages to a Siebel system</span></span>  
 <span data-ttu-id="c5688-109">執行下列步驟來設定 Wcf-siebel 傳送埠將訊息傳送至 Siebel 系統使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="c5688-109">Perform the following steps to configure a WCF-Siebel send port for sending messages to a Siebel system using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
1. <span data-ttu-id="c5688-110">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="c5688-110">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2. <span data-ttu-id="c5688-111">新增 Wcf-siebel 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="c5688-111">Add the WCF-Siebel adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="c5688-112">如需相關指示，請參閱 < [Siebel 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="c5688-112">For instructions, see [Add the Siebel Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3. <span data-ttu-id="c5688-113">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="c5688-113">In the console tree, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
4. <span data-ttu-id="c5688-114">展開想要部署您的應用程式[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c5688-114">Expand the application under which you wish to deploy the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
5. <span data-ttu-id="c5688-115">以滑鼠右鍵按一下**傳送埠**，指向**新增**，並指向您想要根據 BizTalk Server 和 Siebel 系統之間的通訊模式所設定的連接埠類型。</span><span class="sxs-lookup"><span data-stu-id="c5688-115">Right-click **Send Ports**, point to **New**, and point to a type of port you want to configure depending on the mode of communication between BizTalk Server and the Siebel system.</span></span>  
  
6. <span data-ttu-id="c5688-116">在 **傳送埠屬性**對話方塊的 **一般**索引標籤上，輸入傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="c5688-116">In the **Send Port Properties** dialog box, on the **General** tab, type a name for the send port.</span></span>  
  
7. <span data-ttu-id="c5688-117">從**型別**下拉式清單中，選取 Wcf-siebel 配接器中，使用您稍早新增，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="c5688-117">From the **Type** drop-down list, select the WCF-Siebel adapter you added earlier and click **Configure**.</span></span>  
  
8. <span data-ttu-id="c5688-118">在 [傳輸屬性] 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="c5688-118">In the transport properties dialog box, do the following:</span></span>  
  
   1. <span data-ttu-id="c5688-119">按一下 **一般**索引標籤上，按一下**設定**按鈕，然後提供連接參數的值。</span><span class="sxs-lookup"><span data-stu-id="c5688-119">Click the **General** tab, click the **Configure** button, and provide values for the connection parameters.</span></span> <span data-ttu-id="c5688-120">如需連線 URI 的詳細資訊，請參閱[建立 Siebel 系統連接 URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="c5688-120">For more information about the connection URI, see [Create the Siebel system connection URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md).</span></span>  
  
   2. <span data-ttu-id="c5688-121">在 **一般**索引標籤中，於**動作**文字方塊中，輸入作業的動作。</span><span class="sxs-lookup"><span data-stu-id="c5688-121">On the **General** tab, in the **Action** text box, type the action for the operation.</span></span> <span data-ttu-id="c5688-122">請參閱[訊息和訊息結構描述](messages-and-message-schemas-for-siebel-adapter-in-biztalk.md)的每個作業的動作清單。</span><span class="sxs-lookup"><span data-stu-id="c5688-122">See [Messages and message schemas](messages-and-message-schemas-for-siebel-adapter-in-biztalk.md) for a list of actions for each operation.</span></span> <span data-ttu-id="c5688-123">例如，叫用的帳戶在商務元件上的插入作業的動作是：</span><span class="sxs-lookup"><span data-stu-id="c5688-123">For example, the action to invoke the Insert operation on the Account business component is:</span></span>  
  
      ```  
      http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert  
      ```  
  
   3. <span data-ttu-id="c5688-124">按一下 **繫結**索引標籤，然後指定繫結屬性的值。</span><span class="sxs-lookup"><span data-stu-id="c5688-124">Click the **Binding** tab and specify values for the binding properties.</span></span> <span data-ttu-id="c5688-125">如需詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for Siebel 繫結屬性](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="c5688-125">For more information, see [Read about BizTalk Adapter for Siebel Binding Properties](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).</span></span>  
  
   4. <span data-ttu-id="c5688-126">按一下 **認證**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="c5688-126">Click the **Credentials** tab and do one of the following:</span></span>  
  
      - <span data-ttu-id="c5688-127">選取 **不會使用單一登入**選項，並指定使用者名稱和密碼來連接至 Siebel 系統。</span><span class="sxs-lookup"><span data-stu-id="c5688-127">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to a Siebel system.</span></span>  
  
      - <span data-ttu-id="c5688-128">選取 **使用單一登入**選項，並指定分支機構 ESSO 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c5688-128">Select the **Use Single Sign-On** option, and specify an affiliate ESSO application.</span></span>  
  
        <span data-ttu-id="c5688-129">如需安全性相對於 BizTalk Server 的詳細資訊，請參閱[Siebel 配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="c5688-129">For more information about security with respect to BizTalk Server, see [Security with Siebel adapter and BizTalk Server](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md).</span></span>  
  
   5. <span data-ttu-id="c5688-130">若要返回**傳送埠屬性** 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c5688-130">To return to the **Send Port Properties** dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="c5688-131">從**傳送處理常式**下拉式清單中，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="c5688-131">From the **Send handler** drop-down list, select **BizTalkServerApplication**.</span></span>  
  
10. <span data-ttu-id="c5688-132">如果您在步驟 5 中選擇靜態單向傳送埠，指定傳送管線。</span><span class="sxs-lookup"><span data-stu-id="c5688-132">If you chose Static One-Way Send Port in step 5, specify a send pipeline.</span></span> <span data-ttu-id="c5688-133">從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="c5688-133">From the **Send pipeline** drop-down list, select the pipeline corresponding to XMLTransmit.</span></span>  
  
11. <span data-ttu-id="c5688-134">如果您在步驟 5 中選擇靜態請求-回應連接埠，指定傳送和接收管線。</span><span class="sxs-lookup"><span data-stu-id="c5688-134">If you chose Static Solicit-Response Port in step 5, specify send and receive pipelines.</span></span>  
  
    1.  <span data-ttu-id="c5688-135">從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="c5688-135">From the **Send pipeline** drop-down list, select the pipeline corresponding to XMLTransmit.</span></span>  
  
    2.  <span data-ttu-id="c5688-136">從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。</span><span class="sxs-lookup"><span data-stu-id="c5688-136">From the **Receive pipeline** drop-down list, select the pipeline corresponding to XMLReceive.</span></span>  
  
12. <span data-ttu-id="c5688-137">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="c5688-137">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5688-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5688-138">See Also</span></span>  
[<span data-ttu-id="c5688-139">手動設定 Siebel 配接器的實體連接埠繫結</span><span class="sxs-lookup"><span data-stu-id="c5688-139">Manually configure a physical port binding to the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/manually-configure-a-physical-port-binding-to-the-siebel-adapter.md)