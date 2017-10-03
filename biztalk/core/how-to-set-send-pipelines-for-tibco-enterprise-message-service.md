---
title: "如何設定傳送管線 for TIBCO Enterprise Message Service |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send pipelines
- setting send pipelines
- pipelines, send
ms.assetid: 6a84d874-4b4d-4b23-913f-f5c72af1e96e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d037782e2580d52c6609c3669e2805aae92ce9eb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-send-pipelines-for-tibco-enterprise-message-service"></a><span data-ttu-id="1c274-102">如何設定 TIBCO Enterprise Message Service 的傳送管線</span><span class="sxs-lookup"><span data-stu-id="1c274-102">How to Set Send Pipelines for TIBCO Enterprise Message Service</span></span>
<span data-ttu-id="1c274-103">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service 需要您分別為傳送管線和接收管線選取 XMLTransmit 與 XMLReceive。</span><span class="sxs-lookup"><span data-stu-id="1c274-103">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service requires that you select XMLTransmit and XMLReceive for the Send and Receive pipelines respectively.</span></span>  
  
### <a name="to-set-pipelines"></a><span data-ttu-id="1c274-104">設定管線</span><span class="sxs-lookup"><span data-stu-id="1c274-104">To set pipelines</span></span>  
  
1.  <span data-ttu-id="1c274-105">在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開 所需應用程式。</span><span class="sxs-lookup"><span data-stu-id="1c274-105">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="1c274-106">以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態請求-回應傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="1c274-106">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
3.  <span data-ttu-id="1c274-107">在**傳送埠屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="1c274-107">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="1c274-108">輸入傳送埠名稱，例如`SendToTIBCOEMS`。</span><span class="sxs-lookup"><span data-stu-id="1c274-108">Type a name for the send port, for example, `SendToTIBCOEMS`.</span></span>  
  
    2.  <span data-ttu-id="1c274-109">從**類型**下拉式清單中，選取**TIBCO EMS**。</span><span class="sxs-lookup"><span data-stu-id="1c274-109">From the **Type** drop-down list, select **TIBCO EMS**.</span></span>  
  
    3.  <span data-ttu-id="1c274-110">從**傳送處理常式**下拉式清單中，選取 URI。</span><span class="sxs-lookup"><span data-stu-id="1c274-110">From the **Send handler** drop-down list, select the URI.</span></span>  
  
    4.  <span data-ttu-id="1c274-111">從 傳送管線 下拉式清單中，選取  **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="1c274-111">From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span>  
  
    5.  <span data-ttu-id="1c274-112">從**接收管線**下拉式清單中，選取**[microsoft.biztalk.defaultpiplelines.xmlreceive]**。</span><span class="sxs-lookup"><span data-stu-id="1c274-112">From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  
  
4.  <span data-ttu-id="1c274-113">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="1c274-113">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c274-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c274-114">See Also</span></span>  
 [<span data-ttu-id="1c274-115">如何設定 TIBCO Enterprise Message Service 的接收管線</span><span class="sxs-lookup"><span data-stu-id="1c274-115">How to Set Receive Pipelines for TIBCO Enterprise Message Service</span></span>](../core/how-to-set-receive-pipelines-for-tibco-enterprise-message-service.md)