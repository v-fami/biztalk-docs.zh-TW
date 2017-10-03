---
title: "設定 FIN 回應對帳 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FIN Response Reconciliation, configuring
- configuring, FIN Response Reconciliation
ms.assetid: dc934530-76ff-4cdb-b182-46f9ea0343b7
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 384a2ea27e3d208864c8b16ec52562e6e1cfa28e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fin-response-reconciliation"></a><span data-ttu-id="9db53-102">設定 FIN 回應對帳</span><span class="sxs-lookup"><span data-stu-id="9db53-102">Configuring FIN Response Reconciliation</span></span>
<span data-ttu-id="9db53-103">您必須執行的步驟來設定下列各節[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] FIN 回應對帳 (FRR) 功能，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="9db53-103">You must perform the steps in the following sections to configure the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] FIN Response Reconciliation (FRR) feature, as shown in the following figure.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swift-frr-configuration.jpg "A4SWIFT_FRR_Configuration")  
  
 <span data-ttu-id="9db53-104">在 [A4SWIFT 安裝精靈] 中，您可以選擇安裝 Message Repair 和 New Submission 和 FRR，或訊息修復和新送出，而不需 FRR 或不含 Message Repair 和 New Submission FRR。</span><span class="sxs-lookup"><span data-stu-id="9db53-104">In the A4SWIFT Installation Wizard, you can choose to install Message Repair and New Submission and FRR, or Message Repair and New Submission without FRR, or FRR without Message Repair and New Submission.</span></span> <span data-ttu-id="9db53-105">如此一來，本節中的指示請勿假設您安裝與設定訊息修復和新送出。</span><span class="sxs-lookup"><span data-stu-id="9db53-105">As a result, the instructions in this section do not assume that you are installing and configuring Message Repair and New Submission.</span></span> <span data-ttu-id="9db53-106">它們執行動作，不過，假設您已經執行中的步驟[設定 A4SWIFT Runtime](../../adapters-and-accelerators/accelerator-swift/configuring-the-a4swift-runtime.md)。</span><span class="sxs-lookup"><span data-stu-id="9db53-106">They do, however, assume that you have performed the steps in the [Configuring the A4SWIFT Runtime](../../adapters-and-accelerators/accelerator-swift/configuring-the-a4swift-runtime.md).</span></span>  
  
 <span data-ttu-id="9db53-107">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="9db53-107">This section contains:</span></span>  
  
-   [<span data-ttu-id="9db53-108">繫結和啟動 FRR 協調流程</span><span class="sxs-lookup"><span data-stu-id="9db53-108">Binding and Starting the FRR Orchestration</span></span>](../../adapters-and-accelerators/accelerator-swift/binding-and-starting-the-frr-orchestration.md)  
  
-   [<span data-ttu-id="9db53-109">建立 FRR 接收管線</span><span class="sxs-lookup"><span data-stu-id="9db53-109">Creating the FRR Receive Pipeline</span></span>](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-receive-pipeline.md)  
  
-   [<span data-ttu-id="9db53-110">建立 FRR 接收位置從後端應用程式接收</span><span class="sxs-lookup"><span data-stu-id="9db53-110">Creating the FRR Receive Location for Receiving from the Back-End Application</span></span>](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-receive-location-for-receiving-from-the-back-end-application.md)  
  
-   [<span data-ttu-id="9db53-111">建立 FRR 用於接收來自 SWIFT 接收位置</span><span class="sxs-lookup"><span data-stu-id="9db53-111">Creating the FRR Receive Location for Receiving from SWIFT</span></span>](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-receive-location-for-receiving-from-swift.md)  
  
-   [<span data-ttu-id="9db53-112">建立 FRR 傳送管線</span><span class="sxs-lookup"><span data-stu-id="9db53-112">Creating the FRR Send Pipeline</span></span>](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-pipeline.md)  
  
-   [<span data-ttu-id="9db53-113">建立傳送至 SWIFT FRR 傳送埠</span><span class="sxs-lookup"><span data-stu-id="9db53-113">Creating the FRR Send Port for Sending to SWIFT</span></span>](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-port-for-sending-to-swift.md)  
  
-   [<span data-ttu-id="9db53-114">建立 FRR 傳送埠以傳送到自訂處理常式</span><span class="sxs-lookup"><span data-stu-id="9db53-114">Creating the FRR Send Ports for Sending to the Custom Handlers</span></span>](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md)