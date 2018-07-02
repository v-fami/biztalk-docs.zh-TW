---
title: 如何使用自我相互關聯直接繫結連接埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: feb651fa-3e35-4598-b229-335448f6919c
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eaad102db33b4967c89cb78f944b93a688e4c213
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982319"
---
# <a name="how-to-use-self-correlating-direct-bound-ports"></a><span data-ttu-id="005f9-102">如何使用自我相互關聯的直接繫結連接埠</span><span class="sxs-lookup"><span data-stu-id="005f9-102">How to Use Self-Correlating Direct Bound Ports</span></span>
<span data-ttu-id="005f9-103">自我相互關聯的直接繫結連接埠是自我參考的。</span><span class="sxs-lookup"><span data-stu-id="005f9-103">Self-correlating direct bound ports are self referential.</span></span> <span data-ttu-id="005f9-104">這代表自我相互關聯的直接繫結連接埠會提供資訊，供協調流程將訊息傳回包含它的協調流程。</span><span class="sxs-lookup"><span data-stu-id="005f9-104">This means that a self-correlating direct bound port supplies the information that an orchestration can use to send messages back to its enclosing orchestration.</span></span> <span data-ttu-id="005f9-105">使用自我相互關聯的直接繫結時，協調流程引擎會在協調流程執行個體特定的訊息上產生相互關聯 Token。</span><span class="sxs-lookup"><span data-stu-id="005f9-105">When using the self-correlating direct binding, the orchestration engine generates a correlation token on a message that is particular to the orchestration instance.</span></span> <span data-ttu-id="005f9-106">這樣就可以將訊息傳回特定的協調流程執行個體，而不需使用相互關聯集合。</span><span class="sxs-lookup"><span data-stu-id="005f9-106">This provides the capability of getting messages back to a particular orchestration instance without using a correlation set.</span></span>  
  
 <span data-ttu-id="005f9-107">例如，您可以在其中建立接收的自我相互關聯直接繫結的連接埠在協調流程 A 中的指定**直接**如**連接埠繫結**，然後選取**自我相互關聯**連接埠組態精靈 中。</span><span class="sxs-lookup"><span data-stu-id="005f9-107">For example, you can create a receiving self-correlating direct bound port in Orchestration A by specifying **Direct** for **Port binding** and selecting **Self Correlating** in the Port Configuration Wizard.</span></span> <span data-ttu-id="005f9-108">然後在「協調流程 B」中，將連接埠宣告為「協調流程 A」所定義之相同連接埠類型的傳送埠協調流程參數。若要執行這項作業，請進行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="005f9-108">Then, in Orchestration B, you declare a port as a Send Port Orchestration Parameter of the same port type as defined in Orchestration A. To do so, do the following:</span></span>  
  
1. <span data-ttu-id="005f9-109">在 [協調流程檢視] 視窗中，以滑鼠右鍵按一下**協調流程參數**，然後按一下**新的連接埠參數**。</span><span class="sxs-lookup"><span data-stu-id="005f9-109">In the Orchestration View window, right-click **Orchestration Parameters**, and then click **New Port Parameter**.</span></span>  
  
2. <span data-ttu-id="005f9-110">在 [屬性] 視窗中，如**通訊方向**，選取**傳送**，以及**連接埠類型**，協調流程 a 中所定義，請選取相同的連接埠類型</span><span class="sxs-lookup"><span data-stu-id="005f9-110">In the Properties window, for **Communication Direction**, select **Send**, and for **Port Type**, select the same port type as defined in Orchestration A.</span></span>  
  
   <span data-ttu-id="005f9-111">這個宣告會建立邏輯傳送埠協調流程設計師中的連接埠介面上。</span><span class="sxs-lookup"><span data-stu-id="005f9-111">This declaration creates a logical send port on the Port Surface in Orchestration Designer.</span></span> <span data-ttu-id="005f9-112">協調流程 A 呼叫協調流程 B 」: 使用**啟動協調流程**圖形並將新的連接埠做為參數，以及其他協調流程的參數，傳遞到協調流程 b 的協調流程 B，然後執行其商務邏輯及傳送新的連接埠傳遞給它的訊息。</span><span class="sxs-lookup"><span data-stu-id="005f9-112">Orchestration A calls Orchestration B using the **Start Orchestration** shape and passes the new port as a parameter, along with the other orchestration parameters, to Orchestration B. Orchestration B then performs its business logic and sends a message on the new port that was passed to it.</span></span> <span data-ttu-id="005f9-113">該訊息會傳送到「協調流程 A」執行個體的接收端自我相互關聯直接繫結連接埠 (「協調流程 A」即為啟動「協調流程 B」的協調流程)。</span><span class="sxs-lookup"><span data-stu-id="005f9-113">The message is sent to the receiving self-correlating direct bound port of the instance of Orchestration A that started Orchestration B.</span></span>  
  
   <span data-ttu-id="005f9-114">雖然上述事件的順序也都適用於**呼叫的協調流程**圖形，它才有意義時使用**啟動協調流程**圖形。</span><span class="sxs-lookup"><span data-stu-id="005f9-114">Although the preceding sequence of events can also be done with a **Call Orchestration** shape, it only makes sense when using a **Start Orchestration** shape.</span></span> <span data-ttu-id="005f9-115">這是因為使用時**呼叫的協調流程**圖形，參考所傳遞的連接埠。</span><span class="sxs-lookup"><span data-stu-id="005f9-115">This is because when using a **Call Orchestration** shape, ports are passed by reference.</span></span> <span data-ttu-id="005f9-116">兩個協調流程都必須具有相同的連接埠極性。</span><span class="sxs-lookup"><span data-stu-id="005f9-116">The polarity of the port must be same in both of the orchestrations.</span></span> <span data-ttu-id="005f9-117">因此，您從一個協調流程進行傳遞時所使用的連接埠通訊方向，必須與所呼叫之協調流程中的連接埠參考方向相同。</span><span class="sxs-lookup"><span data-stu-id="005f9-117">Therefore, the communication direction of the port you pass in from one orchestration must be the same as the direction of the port reference in the called orchestration.</span></span> <span data-ttu-id="005f9-118">不過，使用時**啟動協調流程**圖形，就會產生非同步的協調流程具現化，而且不得有**Out**或是**Ref**參數;因此，自我相互關聯直接繫結連接埠可以讓協調流程以回應執行個體化該協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="005f9-118">However, when using the **Start Orchestration** shape, an asynchronous instantiation of an orchestration is generated and it cannot have **Out** or **Ref** parameters; therefore, the self-correlating direct bound port provides a way for an orchestration to respond back to the orchestration instance that instantiated it.</span></span>  
  
   <span data-ttu-id="005f9-119">如何使用自我相互關聯直接繫結的連接埠的範例，請參閱 SDK 範例 「 實作 Scatter 和 Gather 模式 」，網址[ http://go.microsoft.com/fwlink/?LinkId=73703 ](http://go.microsoft.com/fwlink/?LinkId=73703)。</span><span class="sxs-lookup"><span data-stu-id="005f9-119">For an example of how to use self-correlating direct bound ports, see the SDK sample "Implementing Scatter and Gather Pattern" at [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="005f9-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="005f9-120">See Also</span></span>  
 <span data-ttu-id="005f9-121">[如何使用 MessageBox 直接繫結連接埠](../core/how-to-use-messagebox-direct-bound-ports.md) </span><span class="sxs-lookup"><span data-stu-id="005f9-121">[How to Use MessageBox Direct Bound Ports](../core/how-to-use-messagebox-direct-bound-ports.md) </span></span>  
 [<span data-ttu-id="005f9-122">如何使用夥伴協調流程直接繫結連接埠</span><span class="sxs-lookup"><span data-stu-id="005f9-122">How to Use Partner Orchestration Direct Bound Ports</span></span>](../core/how-to-use-partner-orchestration-direct-bound-ports.md)