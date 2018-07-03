---
title: 設定 FIN 回應對帳 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FIN Response Reconciliation, configuring
- configuring, FIN Response Reconciliation
ms.assetid: dc934530-76ff-4cdb-b182-46f9ea0343b7
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77f2260c8e6096e2bef926fea45aaf778f4bdfa3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997903"
---
# <a name="configuring-fin-response-reconciliation"></a><span data-ttu-id="6251b-102">設定 FIN 回應對帳</span><span class="sxs-lookup"><span data-stu-id="6251b-102">Configuring FIN Response Reconciliation</span></span>
<span data-ttu-id="6251b-103">您必須執行的步驟來設定 Microsoft 以下幾節[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]FIN 回應對帳 (FRR) 功能，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="6251b-103">You must perform the steps in the following sections to configure the Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] FIN Response Reconciliation (FRR) feature, as shown in the following figure.</span></span>  
  
 <span data-ttu-id="6251b-104">![](../../adapters-and-accelerators/accelerator-swift/media/a4swift-frr-configuration.jpg "A4SWIFT_FRR_Configuration")</span><span class="sxs-lookup"><span data-stu-id="6251b-104">![](../../adapters-and-accelerators/accelerator-swift/media/a4swift-frr-configuration.jpg "A4SWIFT_FRR_Configuration")</span></span>  
  
 <span data-ttu-id="6251b-105">在 [A4SWIFT 安裝精靈] 中，您可以選擇安裝 Message Repair 和 New Submission、 FRR，或 Message Repair 和 New Submission 沒有 FRR 或不含 Message Repair 和 New Submission 的 FRR。</span><span class="sxs-lookup"><span data-stu-id="6251b-105">In the A4SWIFT Installation Wizard, you can choose to install Message Repair and New Submission and FRR, or Message Repair and New Submission without FRR, or FRR without Message Repair and New Submission.</span></span> <span data-ttu-id="6251b-106">如此一來，這一節的指示請勿假設您已安裝且設定 Message Repair 和 New Submission。</span><span class="sxs-lookup"><span data-stu-id="6251b-106">As a result, the instructions in this section do not assume that you are installing and configuring Message Repair and New Submission.</span></span> <span data-ttu-id="6251b-107">它們執行動作，不過，假設您已執行中的步驟[設定 A4SWIFT 執行階段](../../adapters-and-accelerators/accelerator-swift/configuring-the-a4swift-runtime.md)。</span><span class="sxs-lookup"><span data-stu-id="6251b-107">They do, however, assume that you have performed the steps in the [Configuring the A4SWIFT Runtime](../../adapters-and-accelerators/accelerator-swift/configuring-the-a4swift-runtime.md).</span></span>  
  
 <span data-ttu-id="6251b-108">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="6251b-108">This section contains:</span></span>  
  
-   [<span data-ttu-id="6251b-109">繫結和啟動 FRR 協調流程</span><span class="sxs-lookup"><span data-stu-id="6251b-109">Binding and Starting the FRR Orchestration</span></span>](../../adapters-and-accelerators/accelerator-swift/binding-and-starting-the-frr-orchestration.md)  
  
-   [<span data-ttu-id="6251b-110">建立 FRR 接收管線</span><span class="sxs-lookup"><span data-stu-id="6251b-110">Creating the FRR Receive Pipeline</span></span>](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-receive-pipeline.md)  
  
-   [<span data-ttu-id="6251b-111">建立接收自後端應用程式的 FRR 接收位置</span><span class="sxs-lookup"><span data-stu-id="6251b-111">Creating the FRR Receive Location for Receiving from the Back-End Application</span></span>](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-receive-location-for-receiving-from-the-back-end-application.md)  
  
-   [<span data-ttu-id="6251b-112">建立接收自 SWIFT 的 FRR 接收位置</span><span class="sxs-lookup"><span data-stu-id="6251b-112">Creating the FRR Receive Location for Receiving from SWIFT</span></span>](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-receive-location-for-receiving-from-swift.md)  
  
-   [<span data-ttu-id="6251b-113">建立 FRR 傳送管線</span><span class="sxs-lookup"><span data-stu-id="6251b-113">Creating the FRR Send Pipeline</span></span>](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-pipeline.md)  
  
-   [<span data-ttu-id="6251b-114">建立傳送至 SWIFT 的 FRR 傳送埠</span><span class="sxs-lookup"><span data-stu-id="6251b-114">Creating the FRR Send Port for Sending to SWIFT</span></span>](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-port-for-sending-to-swift.md)  
  
-   [<span data-ttu-id="6251b-115">建立 FRR 傳送埠來傳送至自訂處理常式</span><span class="sxs-lookup"><span data-stu-id="6251b-115">Creating the FRR Send Ports for Sending to the Custom Handlers</span></span>](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md)