---
title: "如何為 TIBCO Rendezvous 建立傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating send ports
- ports, send
- send ports, creating
ms.assetid: 0c8d9fdc-b273-4876-9f93-b5a85539a3c1
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d0b6e7dbb1a3b32979c94ec1af9483bd9fcb7cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-send-ports-for-tibco-rendezvous"></a><span data-ttu-id="3e27c-102">如何為 TIBCO Rendezvous 建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="3e27c-102">How to Create Send Ports for TIBCO Rendezvous</span></span>
<span data-ttu-id="3e27c-103">遵循下列步驟，使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 來建立傳送埠。</span><span class="sxs-lookup"><span data-stu-id="3e27c-103">Follow these steps to create a send port using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
### <a name="to-create-a-send-port"></a><span data-ttu-id="3e27c-104">建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="3e27c-104">To create a send port</span></span>  
  
1.  <span data-ttu-id="3e27c-105">在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開 所需應用程式。</span><span class="sxs-lookup"><span data-stu-id="3e27c-105">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="3e27c-106">以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態請求-回應傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="3e27c-106">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
3.  <span data-ttu-id="3e27c-107">在**傳送埠屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="3e27c-107">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="3e27c-108">輸入傳送埠名稱，例如`SendToTIBCORV`。</span><span class="sxs-lookup"><span data-stu-id="3e27c-108">Type a name for the send port, for example, `SendToTIBCORV`.</span></span>  
  
    2.  <span data-ttu-id="3e27c-109">從**類型**下拉式清單中，選取**TIBCO Rendezvous**。</span><span class="sxs-lookup"><span data-stu-id="3e27c-109">From the **Type** drop-down list, select **TIBCO Rendezvous**.</span></span>  
  
    3.  <span data-ttu-id="3e27c-110">從**傳送處理常式**下拉式清單中，選取 URI。</span><span class="sxs-lookup"><span data-stu-id="3e27c-110">From the **Send handler** drop-down list, select the URI.</span></span>  
  
    4.  <span data-ttu-id="3e27c-111">從 傳送管線 下拉式清單中，選取  **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="3e27c-111">From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span>  
  
    5.  <span data-ttu-id="3e27c-112">從**接收管線**下拉式清單中，選取**[microsoft.biztalk.defaultpiplelines.xmlreceive]**。</span><span class="sxs-lookup"><span data-stu-id="3e27c-112">From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  
  
    6.  <span data-ttu-id="3e27c-113">按一下**設定**以設定傳送埠。</span><span class="sxs-lookup"><span data-stu-id="3e27c-113">Click **Configure** to configure the send port.</span></span>  
  
4.  <span data-ttu-id="3e27c-114">在**TIBCO Rendezvous 傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="3e27c-114">In the **TIBCO Rendezvous Transport Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="3e27c-115">輸入屬性。</span><span class="sxs-lookup"><span data-stu-id="3e27c-115">Enter the properties.</span></span>  
  
         <span data-ttu-id="3e27c-116">您不需要設定登入資訊。</span><span class="sxs-lookup"><span data-stu-id="3e27c-116">You do not have to set the logon information.</span></span>  
  
    2.  <span data-ttu-id="3e27c-117">在此清單中，選取您建立來代表 TIBCO Rendezvous 系統的 SSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="3e27c-117">In the list, select the SSO affiliate application you created to represent the TIBCO Rendezvous system.</span></span>  
  
    3.  <span data-ttu-id="3e27c-118">如**使用 SSO**，選取**是**。</span><span class="sxs-lookup"><span data-stu-id="3e27c-118">For **Use SSO**, select **Yes**.</span></span>  
  
    4.  <span data-ttu-id="3e27c-119">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="3e27c-119">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="3e27c-120">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="3e27c-120">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e27c-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e27c-121">See Also</span></span>  
 [<span data-ttu-id="3e27c-122">建立 TIBCO Rendezvous 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="3e27c-122">Creating TIBCO Rendezvous Send Handlers</span></span>](../core/creating-tibco-rendezvous-send-handlers.md)