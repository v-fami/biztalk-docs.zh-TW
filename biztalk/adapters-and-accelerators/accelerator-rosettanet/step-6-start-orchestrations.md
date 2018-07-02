---
title: 步驟 6： 啟動協調流程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, starting
- loopback tutorial, starting orchestratrations
ms.assetid: f16a4a77-04fe-4e73-8517-556668174eb9
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 973d0c5e8628d2363e8192c7faffeaebcc6d63b6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993183"
---
# <a name="step-6-start-orchestrations"></a><span data-ttu-id="ae2ae-102">步驟 6： 啟動協調流程</span><span class="sxs-lookup"><span data-stu-id="ae2ae-102">Step 6: Start Orchestrations</span></span>
<span data-ttu-id="ae2ae-103">在此步驟中，您可以使用 Microsoft[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]以啟動 Microsoft 協調流程[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ae2ae-103">In this step, you use Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to start the orchestrations for Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)].</span></span>  
  
### <a name="to-start-the-btarn-orchestrations-using-visual-studio"></a><span data-ttu-id="ae2ae-104">啟動 BTARN 協調流程使用 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ae2ae-104">To start the BTARN orchestrations using Visual Studio</span></span>  
  
1.  <span data-ttu-id="ae2ae-105">在 [ **BTARN**管理主控台中，展開**BizTalk Server 管理]**，展開**BizTalk 群組**，展開**應用程式**，和然後展開**BizTalk Application 1**。</span><span class="sxs-lookup"><span data-stu-id="ae2ae-105">In the **BTARN** Management Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.</span></span>  
  
2.  <span data-ttu-id="ae2ae-106">按一下 **傳送埠**，然後啟動**PrivateInitiator_To_LOB**並**PrivateResponder_To_LOB**傳送埠。</span><span class="sxs-lookup"><span data-stu-id="ae2ae-106">Click **Send Ports**, and then start **PrivateInitiator_To_LOB** and **PrivateResponder_To_LOB** send ports.</span></span>  
  
3.  <span data-ttu-id="ae2ae-107">按一下 **接收位置**，然後再啟用**LOB_To_PrivateInitiator**， **LOB_To_PrivateResponder**，**且**，並**Sync_Http_Receive**接收位置。</span><span class="sxs-lookup"><span data-stu-id="ae2ae-107">Click **Receive Locations**, and then enable **LOB_To_PrivateInitiator**, **LOB_To_PrivateResponder**, **Async_Http_Receive**, and **Sync_Http_Receive** receive locations.</span></span>  
  
4.  <span data-ttu-id="ae2ae-108">按一下 **協調流程**，並啟動所有**BTARN 協調流程**。</span><span class="sxs-lookup"><span data-stu-id="ae2ae-108">Click **Orchestrations**, and start all **BTARN orchestrations**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae2ae-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae2ae-109">See Also</span></span>  
 <span data-ttu-id="ae2ae-110">[步驟 7： 建立範例 LOB 訊息](../../adapters-and-accelerators/accelerator-rosettanet/step-7-create-a-sample-lob-message.md) </span><span class="sxs-lookup"><span data-stu-id="ae2ae-110">[Step 7: Create a Sample LOB Message](../../adapters-and-accelerators/accelerator-rosettanet/step-7-create-a-sample-lob-message.md) </span></span>  
 [<span data-ttu-id="ae2ae-111">以程式控制方式停止及啟動協調流程、傳送埠和接收位置</span><span class="sxs-lookup"><span data-stu-id="ae2ae-111">Stopping and Starting Orchestrations, Send Ports, and Receive Locations Programmatically</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/code-to-stop-and-start-orchestrations-send-ports-and-receive-locations.md)