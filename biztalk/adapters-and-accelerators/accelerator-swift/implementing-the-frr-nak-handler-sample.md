---
title: 實作 FRR NAK 處理常式範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fa5fb7-6864-4923-b641-e76d2b95d923
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42885d6c487c6f088bfab113891ec5425d3fc82e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990279"
---
# <a name="implementing-the-frr-nak-handler-sample"></a><span data-ttu-id="fa7d9-102">實作 FRR NAK 處理常式範例</span><span class="sxs-lookup"><span data-stu-id="fa7d9-102">Implementing the FRR NAK Handler Sample</span></span>
<span data-ttu-id="fa7d9-103">若要實作範例 FRR NAK 自訂處理常式，將範例專案新增至您的解決方案、 建置和部署專案、 繫結和啟動協調流程，然後停止並重新啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fa7d9-103">To implement the sample FRR NAK custom handler, add the sample project to your solution, build and deploy the project, bind and start the orchestration, and then stop and restart [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  

### <a name="to-implement-the-frr-nak-custom-handler"></a><span data-ttu-id="fa7d9-104">實作 FRR NAK 自訂處理常式</span><span class="sxs-lookup"><span data-stu-id="fa7d9-104">To implement the FRR NAK Custom Handler</span></span>  

1. <span data-ttu-id="fa7d9-105">在  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，開啟您的方案。</span><span class="sxs-lookup"><span data-stu-id="fa7d9-105">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], open your solution.</span></span> <span data-ttu-id="fa7d9-106">在 [方案總管] 中，以滑鼠右鍵按一下方案，指向**新增**，然後按一下**現有專案**。</span><span class="sxs-lookup"><span data-stu-id="fa7d9-106">In Solution Explorer, right-click the solution, point to **Add**, and then click **Existing Project**.</span></span>  

2. <span data-ttu-id="fa7d9-107">在 [**加入現有專案**] 對話方塊中，移至*\<磁碟機\>*: \Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Samples\FrrHandler。</span><span class="sxs-lookup"><span data-stu-id="fa7d9-107">In the **Add Existing Project** dialog box, move to *\<drive\>*:\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Samples\FrrHandler.</span></span> <span data-ttu-id="fa7d9-108">選取  **RepairSWIFTRejectedMessage.btproj**，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="fa7d9-108">Select **RepairSWIFTRejectedMessage.btproj**, and then click **Open**.</span></span>  

3. <span data-ttu-id="fa7d9-109">產生金鑰，並指派給專案的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="fa7d9-109">Generate a key and assign the key to the project.</span></span>  

4. <span data-ttu-id="fa7d9-110">建置和部署 RepairSWIFTRejectedMessage.btproj 專案。</span><span class="sxs-lookup"><span data-stu-id="fa7d9-110">Build and deploy the RepairSWIFTRejectedMessage.btproj project.</span></span>  

5. <span data-ttu-id="fa7d9-111">在 [BizTalk 總管] 中，展開**BizTalk 組態資料庫**，  **\<*伺服器名稱*\>，.biztalkmgmtdb.dbo**，和**協調流程**，以滑鼠右鍵按一下**RepairSWIFTRejectedMessage.Orchestration_1**，然後按一下**繫結**。</span><span class="sxs-lookup"><span data-stu-id="fa7d9-111">In BizTalk Explorer, expand **BizTalk Configuration Databases**, **\<*server name*\>,BizTalkMgmtDb.dbo**, and **Orchestrations**, right-click **RepairSWIFTRejectedMessage.Orchestration_1**, and then click **Bind**.</span></span>  

6. <span data-ttu-id="fa7d9-112">在 [**連接埠繫結內容**] 對話方塊中，選取您的主機，例如 [biztalkserverapplication]，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="fa7d9-112">In the **Port Binding Properties** dialog box, select your host, such as BizTalkServerApplication, and then click **OK**.</span></span>  

7. <span data-ttu-id="fa7d9-113">在 [BizTalk 總管] 中，以滑鼠右鍵按一下**RepairSWIFTRejectedMessage.Orchestration_1**，然後按一下**開始**。</span><span class="sxs-lookup"><span data-stu-id="fa7d9-113">In BizTalk Explorer, right-click **RepairSWIFTRejectedMessage.Orchestration_1**, and then click **Start**.</span></span>  

8. <span data-ttu-id="fa7d9-114">在 [**快速啟動**] 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="fa7d9-114">In the **Express Start** dialog box, click **OK**.</span></span>  

9. <span data-ttu-id="fa7d9-115">按一下 **[開始]**，然後按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="fa7d9-115">Click **Start**, and then click **Run**.</span></span> <span data-ttu-id="fa7d9-116">請輸入**services.msc**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="fa7d9-116">Enter **services.msc**, and then click **OK**.</span></span> <span data-ttu-id="fa7d9-117">以滑鼠右鍵按一下**BizTalk 服務**，然後按一下**重新啟動**。</span><span class="sxs-lookup"><span data-stu-id="fa7d9-117">Right-click **BizTalk Service**, and then click **Restart**.</span></span>
