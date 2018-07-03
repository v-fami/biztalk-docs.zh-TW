---
title: 步驟 5： 建立鏡像協議 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, mirror agreements
- loopback tutorial, creating mirror agreements
- agreements, mirror agreements
ms.assetid: 6aa70b1e-7d38-49f7-9d5f-f008cbe3df66
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9fde79b9ee5cdbb5cd34440aa59e79e842f79b0b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006463"
---
# <a name="step-5-create-a-mirror-agreement"></a><span data-ttu-id="98c96-102">步驟 5： 建立鏡像協議</span><span class="sxs-lookup"><span data-stu-id="98c96-102">Step 5: Create a Mirror Agreement</span></span>
<span data-ttu-id="98c96-103">在此步驟中，您將使用回送公用程式，在設定主要組織的相同電腦上，建立模擬交易夥伴的鏡像協議。</span><span class="sxs-lookup"><span data-stu-id="98c96-103">In this step, you use the Loopback utility to create a mirror agreement simulating the trading partner on the same computer on which you configured the home organization.</span></span> <span data-ttu-id="98c96-104">回送公用程式是命令列工具。</span><span class="sxs-lookup"><span data-stu-id="98c96-104">The Loopback utility is a command-line tool.</span></span>  
  
### <a name="to-create-a-mirror-agreement-using-the-loopback-utility"></a><span data-ttu-id="98c96-105">使用回送公用程式建立鏡像協議</span><span class="sxs-lookup"><span data-stu-id="98c96-105">To create a mirror agreement using the Loopback utility</span></span>  
  
1. <span data-ttu-id="98c96-106">按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="98c96-106">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2. <span data-ttu-id="98c96-107">在命令提示字元中，移至\<*磁碟機*\>: \Program 檔案 (x86) \Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK。</span><span class="sxs-lookup"><span data-stu-id="98c96-107">At the command prompt, move to \<*drive*\>:\Program Files (x86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK.</span></span> <span data-ttu-id="98c96-108">輸入下列命令，然後按**Enter**:</span><span class="sxs-lookup"><span data-stu-id="98c96-108">Type the following command and then press **Enter**:</span></span>  
  
   ```  
   Loopback /enable HOME  
   ```  
  
3. <span data-ttu-id="98c96-109">步驟 2 中執行的命令完成之後，在命令提示字元中，輸入下列命令，然後按**Enter**:</span><span class="sxs-lookup"><span data-stu-id="98c96-109">After the command executed in step 2 has completed, type the following command in the command prompt, and then press **Enter**:</span></span>  
  
   ```  
   Loopback /mirror "Trade Agreement"   
   ```  
  
   <span data-ttu-id="98c96-110">回送公用程式會自動為主要組織 (啟動者) 建立傳送埠，並為交易夥伴組織建立鏡像交易協議。</span><span class="sxs-lookup"><span data-stu-id="98c96-110">The Loopback utility automatically creates send ports for the home organization (initiator) and a mirror trade agreement for the partner organization.</span></span> <span data-ttu-id="98c96-111">交易夥伴將使用這兩個新的傳送埠與主要組織通訊。</span><span class="sxs-lookup"><span data-stu-id="98c96-111">The partner uses the two new send ports to communicate with the home organization.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98c96-112">每當您更新原始交易協議，就必須重新建立鏡像交易協議。</span><span class="sxs-lookup"><span data-stu-id="98c96-112">You must re-mirror the trade agreement whenever you update the original trade agreement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98c96-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98c96-113">See Also</span></span>  
 [<span data-ttu-id="98c96-114">步驟 6：啟動協調流程</span><span class="sxs-lookup"><span data-stu-id="98c96-114">Step 6: Start Orchestrations</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-6-start-orchestrations.md)
