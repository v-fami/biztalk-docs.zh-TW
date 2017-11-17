---
title: "如何測試 HTTP 節點 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP node, testing
- testing HTTP node
ms.assetid: f6881e8f-9f92-4312-bb5e-06bbfb9fe0bb
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2790a4e3fa0ff1ed9a9b9b0c2018108c9cbb1282
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-test-the-http-node"></a><span data-ttu-id="e2f0f-102">如何測試 HTTP 節點</span><span class="sxs-lookup"><span data-stu-id="e2f0f-102">How to Test the HTTP Node</span></span>
<span data-ttu-id="e2f0f-103">請依照以下步驟來測試 HTTP 節點。</span><span class="sxs-lookup"><span data-stu-id="e2f0f-103">Follow these steps to test the HTTP node.</span></span>  
  
### <a name="to-test-the-http-node"></a><span data-ttu-id="e2f0f-104">若要測試 HTTP 節點</span><span class="sxs-lookup"><span data-stu-id="e2f0f-104">To test the HTTP node</span></span>  
  
1.  <span data-ttu-id="e2f0f-105">在 PeopleSoft Enterprise 中，瀏覽至**PeopleTools**， **Integration Broker**，**監視器**， **Monitor Message**。</span><span class="sxs-lookup"><span data-stu-id="e2f0f-105">In PeopleSoft Enterprise, navigate to **PeopleTools**, **Integration Broker**, **Monitor**, **Monitor Message**.</span></span>  
  
     ![](../core/media/psadapter-40-task-gatewaytestnode.gif "PSAdapter_40_Task_GatewayTestNode")  
  
2.  <span data-ttu-id="e2f0f-106">按一下**節點狀態** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e2f0f-106">Click the **Node Status** tab.</span></span>  
  
3.  <span data-ttu-id="e2f0f-107">在**Message Node Name**欄位中，輸入`MSEXTERNAL`，然後按一下 **查閱**圖示。</span><span class="sxs-lookup"><span data-stu-id="e2f0f-107">In the **Message Node Name** field, enter `MSEXTERNAL`, and then click the **Lookup** icon.</span></span>  
  
4.  <span data-ttu-id="e2f0f-108">在下**Message Node Name**，選取**MSEXTERNAL**。</span><span class="sxs-lookup"><span data-stu-id="e2f0f-108">Under **Message Node Name**, select **MSEXTERNAL**.</span></span>  
  
     <span data-ttu-id="e2f0f-109">一則訊息隨即出現，並表示 PeopleSoft 正在透過 HTTP 進行通訊。</span><span class="sxs-lookup"><span data-stu-id="e2f0f-109">A message appears and indicates that PeopleSoft is communicating through HTTP.</span></span>  
  
     ![](../core/media/psadapter-41-task-gatewaytestsuccess.gif "PSAdapter_41_Task_GatewayTestSuccess")  
  
     <span data-ttu-id="e2f0f-110">如果您沒有收到訊息，請確認下列事項：</span><span class="sxs-lookup"><span data-stu-id="e2f0f-110">If you do not receive the message, verify the following:</span></span>  
  
    1.  <span data-ttu-id="e2f0f-111">在接收埠與節點之間的 IP 位址和連接埠都相符。</span><span class="sxs-lookup"><span data-stu-id="e2f0f-111">The IP addresses and ports match between the receive port and the node.</span></span>  
  
    2.  <span data-ttu-id="e2f0f-112">BizTalk Server 正在執行。</span><span class="sxs-lookup"><span data-stu-id="e2f0f-112">BizTalk Server is running.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2f0f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2f0f-113">See Also</span></span>  
 [<span data-ttu-id="e2f0f-114">建立 PeopleSoft HTTP 主控件和連接埠</span><span class="sxs-lookup"><span data-stu-id="e2f0f-114">Creating a PeopleSoft HTTP Host and Port</span></span>](../core/creating-a-peoplesoft-http-host-and-port.md)