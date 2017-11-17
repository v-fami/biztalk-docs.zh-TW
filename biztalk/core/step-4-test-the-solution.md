---
title: "步驟 4： 測試方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60c39521-eee2-49f7-a9f9-2dfb9ab468e9
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64f0ae6cb124ea9d8710797790b9176289faafc3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-test-the-solution"></a><span data-ttu-id="142de-102">步驟 4： 測試方案</span><span class="sxs-lookup"><span data-stu-id="142de-102">Step 4: Test the Solution</span></span>
<span data-ttu-id="142de-103">本主題，您會測試方案，藉由在您與檔案相關聯的資料夾中放置虛擬要求訊息在接收埠。</span><span class="sxs-lookup"><span data-stu-id="142de-103">In this topic you test the solution by dropping a dummy request message in the folder you associated with the FILE receive port.</span></span> <span data-ttu-id="142de-104">中所述，而叫用虛擬要求訊息置放**Wcf-webhttp**傳送埠。</span><span class="sxs-lookup"><span data-stu-id="142de-104">As explained in, you drop a dummy request message only to invoke the **WCF-WebHttp** send port.</span></span> <span data-ttu-id="142de-105">您可以建立虛擬要求訊息，如下所示：</span><span class="sxs-lookup"><span data-stu-id="142de-105">You can create a dummy request message like the following:</span></span>  
  
```  
<Root>  
  <Input>Azure Market Place REST API integration</Input>  
<Root>  
```  
  
### <a name="to-test-the-solution"></a><span data-ttu-id="142de-106">測試方案</span><span class="sxs-lookup"><span data-stu-id="142de-106">To test the solution</span></span>  
  
1.  <span data-ttu-id="142de-107">從 BizTalk Server 管理主控台，啟動**BizTalk Application 1**。</span><span class="sxs-lookup"><span data-stu-id="142de-107">From the BizTalk Server Administration Console, start **BizTalk Application 1**.</span></span> <span data-ttu-id="142de-108">這樣會啟動在先前步驟中建立的所有連接埠。</span><span class="sxs-lookup"><span data-stu-id="142de-108">This starts all the ports that we created in previous steps.</span></span>  
  
2.  <span data-ttu-id="142de-109">開啟 Windows 檔案總管並瀏覽至您與檔案相關聯的位置接收位置。</span><span class="sxs-lookup"><span data-stu-id="142de-109">Open Windows Explorer, and navigate to the location that you associated with the FILE receive location.</span></span> <span data-ttu-id="142de-110">在這個位置，複製虛擬要求訊息。</span><span class="sxs-lookup"><span data-stu-id="142de-110">At this location, copy the dummy request message.</span></span>  
  
3.  <span data-ttu-id="142de-111">當檔案消失時，請檢查您與使用 REST 介面的回應訊息的 FILE 傳送埠相關聯的位置。</span><span class="sxs-lookup"><span data-stu-id="142de-111">When the file disappears, check the location you associated with FILE send port that consumes the response message from the REST interface.</span></span> <span data-ttu-id="142de-112">它應該包含的 XML 回應訊息。</span><span class="sxs-lookup"><span data-stu-id="142de-112">It should contain an XML response message.</span></span> <span data-ttu-id="142de-113">開啟該 XML 訊息，以查看從美國空中會延遲班機的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="142de-113">Open the XML message to see the details of flights from US air carries that are delayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="142de-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="142de-114">See Also</span></span>  
 [<span data-ttu-id="142de-115">教學課程 5： 叫用 REST 介面使用 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="142de-115">Tutorial 5: Invoking a REST Interface Using BizTalk Server</span></span>](../core/tutorial-5-invoking-a-rest-interface-using-biztalk-server.md)