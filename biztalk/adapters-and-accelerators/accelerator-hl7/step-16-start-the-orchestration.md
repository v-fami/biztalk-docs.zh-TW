---
title: 步驟 16： 啟動協調流程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, starting
- message enrichment tutorial, orchestrations
ms.assetid: a9032b0b-1497-4f6a-8474-a94c14976be0
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5256d33dc6751db34d1d827624d2dbe2644639e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22206174"
---
# <a name="step-16-start-the-orchestration"></a><span data-ttu-id="f7c6f-102">步驟 16： 啟動協調流程</span><span class="sxs-lookup"><span data-stu-id="f7c6f-102">Step 16: Start the Orchestration</span></span>
<span data-ttu-id="f7c6f-103">在此步驟中，您可以登錄服務為了讓您在協調流程與協調流程將在其中執行的實體環境中設計的商務程序產生關聯。</span><span class="sxs-lookup"><span data-stu-id="f7c6f-103">In this step, you enlist the service in order to associate the business process that you designed in the orchestration with the physical environment in which the orchestration will run.</span></span> <span data-ttu-id="f7c6f-104">此外，啟動協調流程的處理，以便您可以測試您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f7c6f-104">Additionally, you start the processing of the orchestration so that you can test your application.</span></span>  
  
### <a name="to-start-the-orchestration"></a><span data-ttu-id="f7c6f-105">若要啟動協調流程</span><span class="sxs-lookup"><span data-stu-id="f7c6f-105">To start the orchestration</span></span>  
  
1.  <span data-ttu-id="f7c6f-106">在[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台的主控台樹狀目錄窗格中，在**協調流程**，以滑鼠右鍵按一下**BTAHL7_Project.Doorbell_Orchestration**，然後按一下 **登錄**.</span><span class="sxs-lookup"><span data-stu-id="f7c6f-106">In the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, in the console tree pane, under **Orchestrations**, right-click **BTAHL7_Project.Doorbell_Orchestration**, and then click **Enlist**.</span></span>  
  
2.  <span data-ttu-id="f7c6f-107">以滑鼠右鍵按一下**BTAHL7_Project.Doorbell_Orchestration**，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="f7c6f-107">Right-click **BTAHL7_Project.Doorbell_Orchestration**, and then click **Start**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f7c6f-108">請確定您已經啟動**MLLPSendPort**傳送埠，然後啟用**WebService_BTAHL7_Project_Proxy/BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort**接收位置。</span><span class="sxs-lookup"><span data-stu-id="f7c6f-108">Ensure that you have started the **MLLPSendPort** send port and enabled the **WebService_BTAHL7_Project_Proxy/BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort** receive location.</span></span>  
  
 <span data-ttu-id="f7c6f-109">若要繼續[步驟 17： 建立 WSClient 應用程式](../../adapters-and-accelerators/accelerator-hl7/step-17-create-the-wsclient-application.md)。</span><span class="sxs-lookup"><span data-stu-id="f7c6f-109">Proceed to [Step 17: Create the WSClient Application](../../adapters-and-accelerators/accelerator-hl7/step-17-create-the-wsclient-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7c6f-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7c6f-110">See Also</span></span>  
 [<span data-ttu-id="f7c6f-111">訊息擴充教學課程</span><span class="sxs-lookup"><span data-stu-id="f7c6f-111">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)