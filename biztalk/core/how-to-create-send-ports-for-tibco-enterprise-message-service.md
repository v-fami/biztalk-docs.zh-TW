---
title: "如何建立 TIBCO Enterprise Message Service 的傳送埠 |Microsoft 文件"
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
ms.assetid: 6e569244-494e-4db4-8030-eda3b390d073
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bfadeb3306687bfcbea27c0df41973b12b003563
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-send-ports-for-tibco-enterprise-message-service"></a><span data-ttu-id="8d94d-102">如何建立 TIBCO Enterprise Message Service 的傳送埠</span><span class="sxs-lookup"><span data-stu-id="8d94d-102">How to Create Send Ports for TIBCO Enterprise Message Service</span></span>
<span data-ttu-id="8d94d-103">依照下列步驟建立傳送埠。</span><span class="sxs-lookup"><span data-stu-id="8d94d-103">Follow these steps to create a send port.</span></span>  
  
## <a name="creating-a-send-port"></a><span data-ttu-id="8d94d-104">建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="8d94d-104">Creating a Send Port</span></span>  
  
#### <a name="to-create-a-send-port"></a><span data-ttu-id="8d94d-105">建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="8d94d-105">To create a send port</span></span>  
  
1.  <span data-ttu-id="8d94d-106">在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開 所需應用程式。</span><span class="sxs-lookup"><span data-stu-id="8d94d-106">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="8d94d-107">以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態請求-回應傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="8d94d-107">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
3.  <span data-ttu-id="8d94d-108">在**傳送埠屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="8d94d-108">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="8d94d-109">輸入傳送埠名稱，例如`SendToTIBCOEMS`。</span><span class="sxs-lookup"><span data-stu-id="8d94d-109">Type a name for the send port, for example, `SendToTIBCOEMS`.</span></span>  
  
    2.  <span data-ttu-id="8d94d-110">從**類型**下拉式清單中，選取**TIBCO EMS**。</span><span class="sxs-lookup"><span data-stu-id="8d94d-110">From the **Type** drop-down list, select **TIBCO EMS**.</span></span>  
  
    3.  <span data-ttu-id="8d94d-111">從**傳送處理常式**下拉式清單中，選取 URI。</span><span class="sxs-lookup"><span data-stu-id="8d94d-111">From the **Send handler** drop-down list, select the URI.</span></span>  
  
    4.  <span data-ttu-id="8d94d-112">從 傳送管線 下拉式清單中，選取  **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="8d94d-112">From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span>  
  
    5.  <span data-ttu-id="8d94d-113">從**接收管線**下拉式清單中，選取**[microsoft.biztalk.defaultpiplelines.xmlreceive]**。</span><span class="sxs-lookup"><span data-stu-id="8d94d-113">From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  
  
    6.  <span data-ttu-id="8d94d-114">按一下**設定**以設定傳送埠。</span><span class="sxs-lookup"><span data-stu-id="8d94d-114">Click **Configure** to configure the send port.</span></span>  
  
4.  <span data-ttu-id="8d94d-115">在**TIBCO EMS 傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="8d94d-115">In the **TIBCO EMS Transport Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="8d94d-116">輸入**訊息處理**，**伺服器連線定義**，**交易支援**， **Username**，而**密碼**。</span><span class="sxs-lookup"><span data-stu-id="8d94d-116">Enter **Message Handling**, **Server Connection Definition**, **Transaction Support**, **Username**, and the **password**.</span></span>  
  
         <span data-ttu-id="8d94d-117">您不需要設定登入資訊。</span><span class="sxs-lookup"><span data-stu-id="8d94d-117">You do not have to set the logon information.</span></span>  
  
    2.  <span data-ttu-id="8d94d-118">在此清單中，選取您建立用來代表 TIBCO EMS 系統的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="8d94d-118">In the list, select the affiliate application you created to represent the TIBCO EMS system.</span></span>  
  
    3.  <span data-ttu-id="8d94d-119">如**使用 SSO**，選取**是**。</span><span class="sxs-lookup"><span data-stu-id="8d94d-119">For **Use SSO**, select **Yes**.</span></span>  
  
    4.  <span data-ttu-id="8d94d-120">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="8d94d-120">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="8d94d-121">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="8d94d-121">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d94d-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d94d-122">See Also</span></span>  
 <span data-ttu-id="8d94d-123">[設定 TIBCO 企業訊息服務傳輸傳送埠屬性](../core/setting-tibco-enterprise-message-service-transport-properties-for-the-send-port.md) </span><span class="sxs-lookup"><span data-stu-id="8d94d-123">[Setting TIBCO Enterprise Message Service Transport Properties for the Send Port](../core/setting-tibco-enterprise-message-service-transport-properties-for-the-send-port.md) </span></span>  
 [<span data-ttu-id="8d94d-124">建立 TIBCO 企業訊息服務傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="8d94d-124">Creating  TIBCO Enterprise Message Service Send Handlers</span></span>](../core/creating-tibco-enterprise-message-service-send-handlers.md)