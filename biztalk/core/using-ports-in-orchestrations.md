---
title: "協調流程中使用連接埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send ports, receiving
- ports, configuring manually
- send ports, messages
- ports, creating
- ports, messages
- creating, ports
- send ports, sending
- ports, operations
- configuring, ports
- ports, deleting
- deleting, ports
- orchestrations, ports
- Port Configuration Wizard [Orchestration Designer]
- ports
- ports, about ports
- ports, configuring
ms.assetid: 968b2d1b-e233-4eb0-8254-9ec6b7642cdf
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7f48c1c070e3a3a3e7ebe7e86618a4fd9ebc90d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-ports-in-orchestrations"></a><span data-ttu-id="65545-102">在協調流程中使用連接埠</span><span class="sxs-lookup"><span data-stu-id="65545-102">Using Ports in Orchestrations</span></span>
<span data-ttu-id="65545-103">連接埠指定您的協調流程和其他商務程序之間傳送和接收訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="65545-103">Ports specify how your orchestration will send messages to and receive messages from other business processes.</span></span> <span data-ttu-id="65545-104">每個連接埠都具有類型、方向和繫結，由這些決定通訊的方向、通訊的模式、傳送和接受訊息的位置，以及通訊進行的方式。</span><span class="sxs-lookup"><span data-stu-id="65545-104">Each port has a type, a direction, and a binding, which together determine the direction of communication, the pattern of communication, the location to or from which the message is sent or received, and how the communication takes place.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="65545-105">連接埠和連接埠類型不同。</span><span class="sxs-lookup"><span data-stu-id="65545-105">There is a distinction between a port and a port type.</span></span> <span data-ttu-id="65545-106">連接埠是連接埠類型的執行個體；數個不同的連接埠可以具有相同的連接埠類型。</span><span class="sxs-lookup"><span data-stu-id="65545-106">A port is an instance of a port type; several different ports may have the same port type.</span></span>  
  
 <span data-ttu-id="65545-107">基於這些因素，連接埠可能會有關聯的 URI (實體位置)、傳輸 (可能是 FILE、HTTP、SOAP、SMTP 或 BizTalk 訊息佇列)、準備訊息以供傳送的傳送管線 (例如，透過組合、加密、壓縮或對其執行某些其他動作)，以及準備接收訊息以供處理的接收管線 (例如透過解譯、解密或解壓縮)。</span><span class="sxs-lookup"><span data-stu-id="65545-107">Depending on these factors, a port may have associated with it a URI (a physical location), a transport (either FILE, HTTP, SOAP, SMTP or BizTalk Message Queuing), a send pipeline to prepare a message for sending (for example, by assembling, encrypting, compressing, or performing some other action on it), and a receive pipeline to prepare a received message for processing (for example, by disassembling, decrypting, or decompressing it).</span></span>  
  
 <span data-ttu-id="65545-108">新增連接埠到協調流程的方式，和新增控制項到 Web Form 或 Windows Form 的方式類似。</span><span class="sxs-lookup"><span data-stu-id="65545-108">You add ports to an orchestration in much the same way that you add controls to a Web Form or Windows Form.</span></span> <span data-ttu-id="65545-109">您也可以使用 [協調流程檢視] 視窗來新增連接埠。</span><span class="sxs-lookup"><span data-stu-id="65545-109">You can also add ports by using the Orchestration View window.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="65545-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="65545-110">In This Section</span></span>  
  
-   [<span data-ttu-id="65545-111">通訊模式</span><span class="sxs-lookup"><span data-stu-id="65545-111">Communication Pattern</span></span>](../core/communication-pattern.md)  
  
-   [<span data-ttu-id="65545-112">通訊方向</span><span class="sxs-lookup"><span data-stu-id="65545-112">Communication Direction</span></span>](../core/communication-direction.md)  
  
-   [<span data-ttu-id="65545-113">連接埠繫結</span><span class="sxs-lookup"><span data-stu-id="65545-113">Port Bindings</span></span>](../core/port-bindings.md)  
  
-   [<span data-ttu-id="65545-114">如何在協調流程中使用連接埠</span><span class="sxs-lookup"><span data-stu-id="65545-114">How to Use Ports in Orchestrations</span></span>](../core/how-to-use-ports-in-orchestrations.md)  
  
-   [<span data-ttu-id="65545-115">如何使用連接埠類型</span><span class="sxs-lookup"><span data-stu-id="65545-115">How to Work with Port Types</span></span>](../core/how-to-work-with-port-types.md)  
  
-   [<span data-ttu-id="65545-116">如何執行連接埠組態精靈</span><span class="sxs-lookup"><span data-stu-id="65545-116">How to Run the Port Configuration Wizard</span></span>](../core/how-to-run-the-port-configuration-wizard.md)  
  
-   [<span data-ttu-id="65545-117">使用 協調流程中的直接繫結連接埠</span><span class="sxs-lookup"><span data-stu-id="65545-117">Working with Direct Bound Ports in Orchestrations</span></span>](../core/working-with-direct-bound-ports-in-orchestrations.md)  
  
## <a name="see-also"></a><span data-ttu-id="65545-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65545-118">See Also</span></span>  
 <span data-ttu-id="65545-119">[如何執行連接埠組態精靈](../core/how-to-run-the-port-configuration-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="65545-119">[How to Run the Port Configuration Wizard](../core/how-to-run-the-port-configuration-wizard.md) </span></span>  
 [<span data-ttu-id="65545-120">協調流程中使用角色連結</span><span class="sxs-lookup"><span data-stu-id="65545-120">Using Role Links in Orchestrations</span></span>](../core/using-role-links-in-orchestrations.md)