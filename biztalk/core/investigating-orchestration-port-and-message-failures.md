---
title: "調查協調流程、 連接埠和訊息失敗 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Administration Console [BizTalk Server], Group Hub page
- orchestrations, errors
- errors, ports
- errors, orchestrations
- Group Hub page [Administration Console]
- ports, errors
- MessageBox database, accessing data
- errors, messages
- messages, errors
- data, MessageBox database
ms.assetid: 50b0d272-2d48-4e0f-82ce-6ecc7a65b064
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94417135f707d77377686745e35e6fb1f02087b9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="investigating-orchestration-port-and-message-failures"></a><span data-ttu-id="6850e-102">調查協調流程、連接埠和訊息失敗</span><span class="sxs-lookup"><span data-stu-id="6850e-102">Investigating Orchestration, Port, and Message Failures</span></span>
<span data-ttu-id="6850e-103">您可使用 [BizTalk Server 管理] 主控台中的「群組中樞」頁面，來調查協調流程、連接埠和訊息失敗。</span><span class="sxs-lookup"><span data-stu-id="6850e-103">You can use the Group Hub page in the BizTalk Server Administration Console to investigate orchestration, port, and message failures.</span></span> <span data-ttu-id="6850e-104">「群組中樞」頁面提供系統目前即時狀態的存取，可供您存取 MessageBox 資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="6850e-104">The Group Hub page provides access to the current real-time state of the system, accessing data in the MessageBox database.</span></span> <span data-ttu-id="6850e-105">您可檢視所有服務執行個體 (如協調流程、連接埠和傳訊)，及其關聯的訊息。</span><span class="sxs-lookup"><span data-stu-id="6850e-105">You can view all service instances such as orchestrations, ports, and messaging, along with their associated messages.</span></span> <span data-ttu-id="6850e-106">使用「群組中樞」頁面可以：</span><span class="sxs-lookup"><span data-stu-id="6850e-106">Using the Group Hub page you can:</span></span>  
  
-   <span data-ttu-id="6850e-107">查看目前正在執行的服務執行個體 (如協調流程與傳訊) 及其關聯訊息。</span><span class="sxs-lookup"><span data-stu-id="6850e-107">See currently running service instances such as orchestrations and messaging, and their associated messages.</span></span>  
  
-   <span data-ttu-id="6850e-108">查看 MessageBox 資料庫中的目前資料與系統即時狀態檢視。</span><span class="sxs-lookup"><span data-stu-id="6850e-108">Look into the MessageBox database for a view of the current data and the real-time state of the system.</span></span>  
  
-   <span data-ttu-id="6850e-109">擱置、終止與繼續服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="6850e-109">Suspend, terminate, and resume service instances.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6850e-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="6850e-110">In This Section</span></span>  
  
-   [<span data-ttu-id="6850e-111">協調流程失敗</span><span class="sxs-lookup"><span data-stu-id="6850e-111">Orchestration Failures</span></span>](../core/orchestration-failures.md)  
  
-   [<span data-ttu-id="6850e-112">訊息失敗的類型</span><span class="sxs-lookup"><span data-stu-id="6850e-112">Types of Message Failures</span></span>](../core/types-of-message-failures.md)  
  
-   [<span data-ttu-id="6850e-113">如何擱置協調流程執行個體或連接埠</span><span class="sxs-lookup"><span data-stu-id="6850e-113">How to Suspend Orchestration Instances or Ports</span></span>](../core/how-to-suspend-orchestration-instances-or-ports.md)  
  
-   [<span data-ttu-id="6850e-114">如何終止擱置的協調流程執行個體</span><span class="sxs-lookup"><span data-stu-id="6850e-114">How to Terminate Suspended Orchestration Instances</span></span>](../core/how-to-terminate-suspended-orchestration-instances.md)  
  
-   [<span data-ttu-id="6850e-115">如何繼續擱置的協調流程執行個體</span><span class="sxs-lookup"><span data-stu-id="6850e-115">How to Resume Suspended Orchestration Instances</span></span>](../core/how-to-resume-suspended-orchestration-instances.md)