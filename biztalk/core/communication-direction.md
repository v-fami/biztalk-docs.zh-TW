---
title: "通訊方向 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port types, communication direction
- communication direction [port types]
ms.assetid: b278325e-a1da-49a6-8332-80a5f640cc22
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d6c664643629971366805d08600677d22d7c419
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="communication-direction"></a><span data-ttu-id="f2a72-102">通訊方向</span><span class="sxs-lookup"><span data-stu-id="f2a72-102">Communication Direction</span></span>
<span data-ttu-id="f2a72-103">每個*連接埠*都有它自己的通訊方向。</span><span class="sxs-lookup"><span data-stu-id="f2a72-103">Each *port* has its own communication direction.</span></span> <span data-ttu-id="f2a72-104">通訊方向是與連接埠類型的通訊模式結合使用，以完成如何使用連接埠的定義。</span><span class="sxs-lookup"><span data-stu-id="f2a72-104">The communication direction is used in combination with the communication pattern of the port's type to complete the definition of how a port can be used.</span></span> <span data-ttu-id="f2a72-105">通訊方向 (或極性) 可決定透過該連接埠傳輸之訊息的方向。</span><span class="sxs-lookup"><span data-stu-id="f2a72-105">The communication direction, or polarity, determines in which direction messages will be transmitted over that port.</span></span>  
  
 <span data-ttu-id="f2a72-106">若連接埠類型具有單向通訊模式，則其通訊方向可能是「傳送」或「接收」。</span><span class="sxs-lookup"><span data-stu-id="f2a72-106">If the port's type has a one-way communication pattern, its communication direction can be either Send or Receive.</span></span> <span data-ttu-id="f2a72-107">若連接埠類型具有雙向 (要求-回應) 通訊模式，則其通訊方向可能是「傳送-接收」(傳送要求並接收回應)，或「接收-傳送」(接收要求並傳送回應)。</span><span class="sxs-lookup"><span data-stu-id="f2a72-107">If the port's type has a two-way (request-response) communication pattern, its communication direction can be Send-Receive, in which a request is sent and a response is received, or Receive-Send, in which a request is received and a response is sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2a72-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2a72-108">See Also</span></span>  
 [<span data-ttu-id="f2a72-109">通訊模式</span><span class="sxs-lookup"><span data-stu-id="f2a72-109">Communication Pattern</span></span>](../core/communication-pattern.md)  
 <span data-ttu-id="f2a72-110">[如何執行連接埠組態精靈](../core/how-to-run-the-port-configuration-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="f2a72-110">[How to Run the Port Configuration Wizard](../core/how-to-run-the-port-configuration-wizard.md) </span></span>  
 [<span data-ttu-id="f2a72-111">協調流程中使用連接埠</span><span class="sxs-lookup"><span data-stu-id="f2a72-111">Using Ports in Orchestrations</span></span>](../core/using-ports-in-orchestrations.md)