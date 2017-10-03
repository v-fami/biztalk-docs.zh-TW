---
title: "如何設定 JD Edwards OneWorld 管線 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive pipelines
- send pipelines
- setting pipelines
- pipelines, setting
ms.assetid: 821d4081-a2d4-4957-abc0-d6370e719ba8
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e45ec6f6eb3be74e150e77de9ef6dbbe461a361a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-jd-edwards-oneworld-pipelines"></a><span data-ttu-id="100e3-102">如何設定 JD Edwards OneWorld 管線</span><span class="sxs-lookup"><span data-stu-id="100e3-102">How to Set JD Edwards OneWorld Pipelines</span></span>
<span data-ttu-id="100e3-103">Microsoft BizTalk Adapter for JD Edwards OneWorld 要求您分別針對傳送與接收管線選取 XMLTransmit 和 XMLReceive。</span><span class="sxs-lookup"><span data-stu-id="100e3-103">Microsoft BizTalk Adapter for JD Edwards OneWorld requires that you select XMLTransmit and XMLReceive for the send and receive pipelines respectively.</span></span>  
  
### <a name="to-set-pipelines"></a><span data-ttu-id="100e3-104">設定管線</span><span class="sxs-lookup"><span data-stu-id="100e3-104">To set pipelines</span></span>  
  
1.  <span data-ttu-id="100e3-105">上**啟動**功能表上，指向**Program Files**，指向  **Microsoft BizTalk Server** ，然後按一下  **BizTalk Server 管理**啟動 BizTalk Server 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="100e3-105">On the **Start** menu, point to **Program Files**, point to **Microsoft BizTalk Server** , and then click **BizTalk Server Administration** to start the BizTalk Server Administration Console.</span></span>  
  
2.  <span data-ttu-id="100e3-106">依序展開 BizTalk Server 管理**BizTalk 群組**，依序展開**應用程式**，然後展開所需的應用程式。</span><span class="sxs-lookup"><span data-stu-id="100e3-106">Expand BizTalk Server Administration, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
3.  <span data-ttu-id="100e3-107">選取**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="100e3-107">Select **Send Ports**.</span></span> <span data-ttu-id="100e3-108">在詳細資料窗格中，以滑鼠右鍵按一下選取的傳送埠，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="100e3-108">In the details pane, right-click the selected send port and click **Properties**.</span></span>  
  
4.  <span data-ttu-id="100e3-109">在**傳送埠屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="100e3-109">In the **Send Ports Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="100e3-110">選取傳送管線從**傳送管線**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="100e3-110">Select the send pipeline from the **Send Pipeline** drop-down list.</span></span>  
  
    2.  <span data-ttu-id="100e3-111">選取接收管線就會從**接收管線**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="100e3-111">Select the Receive pipeline from the **Receive Pipeline** drop-down list.</span></span>  
  
5.  <span data-ttu-id="100e3-112">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="100e3-112">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="100e3-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="100e3-113">See Also</span></span>  
 [<span data-ttu-id="100e3-114">建立 JD Edwards OneWorld 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="100e3-114">Creating JD Edwards OneWorld Send Handlers</span></span>](../core/creating-jd-edwards-oneworld-send-handlers.md)