---
title: "A4SWIFT 元件組態指南 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: A4SWIFT, configuration guide
ms.assetid: ff4a3ee7-2fd9-44e7-8aa3-c3d214a6ce68
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 396e28d49b3e6a43e188e8358a045c3c91a627cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="a4swift-component-configuration-guide"></a><span data-ttu-id="dfe02-102">A4SWIFT 元件組態指南</span><span class="sxs-lookup"><span data-stu-id="dfe02-102">A4SWIFT Component Configuration Guide</span></span>
<span data-ttu-id="dfe02-103">本指南提供有關設定資訊[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="dfe02-103">This guide provides information about configuring [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)].</span></span> <span data-ttu-id="dfe02-104">您已安裝 A4SWIFT 並完成 A4SWIFT 組態精靈 （如安裝指南中所述） 之後，請執行此組態指南中的步驟。</span><span class="sxs-lookup"><span data-stu-id="dfe02-104">Perform the steps in this configuration guide after you have installed A4SWIFT and completed the A4SWIFT Configuration Wizard (as described in the Installation Guide).</span></span> <span data-ttu-id="dfe02-105">此組態指南 》 包含下列指示：</span><span class="sxs-lookup"><span data-stu-id="dfe02-105">This configuration guide includes the following instructions:</span></span>  
  
-   <span data-ttu-id="dfe02-106">安裝後設定 A4SWIFT 執行階段的傳訊案例的步驟。</span><span class="sxs-lookup"><span data-stu-id="dfe02-106">Post-installation steps for configuring the A4SWIFT runtime for messaging scenarios.</span></span>  
  
-   <span data-ttu-id="dfe02-107">如何設定訊息修復和新送出。</span><span class="sxs-lookup"><span data-stu-id="dfe02-107">How to configure Message Repair and New Submission.</span></span> <span data-ttu-id="dfe02-108">若要這樣做，您必須先手動設定 A4SWIFT 執行階段。</span><span class="sxs-lookup"><span data-stu-id="dfe02-108">To do so, you must first manually configure the A4SWIFT runtime.</span></span> <span data-ttu-id="dfe02-109">這不需要您設定 FIN 回應對帳資料。</span><span class="sxs-lookup"><span data-stu-id="dfe02-109">This does not require that you configure FIN Response Reconciliation.</span></span>  
  
-   <span data-ttu-id="dfe02-110">如何設定 FIN 回應對帳資料。</span><span class="sxs-lookup"><span data-stu-id="dfe02-110">How to configure FIN Response Reconciliation.</span></span> <span data-ttu-id="dfe02-111">若要這樣做，您必須先手動設定 A4SWIFT 執行階段。</span><span class="sxs-lookup"><span data-stu-id="dfe02-111">To do so, you must first manually configure the A4SWIFT runtime.</span></span> <span data-ttu-id="dfe02-112">這不需要您設定訊息修復和新送出。</span><span class="sxs-lookup"><span data-stu-id="dfe02-112">This does not require that you configure Message Repair and New Submission.</span></span>  
  
 <span data-ttu-id="dfe02-113">下圖顯示將會設定 A4SWIFT 元件。</span><span class="sxs-lookup"><span data-stu-id="dfe02-113">The following figure shows the A4SWIFT components that you will configure.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swift-component-configuration.gif "A4SWIFT_Component_Configuration")  
  
 <span data-ttu-id="dfe02-114">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="dfe02-114">This section contains:</span></span>  
  
-   [<span data-ttu-id="dfe02-115">設定 A4SWIFT 執行階段</span><span class="sxs-lookup"><span data-stu-id="dfe02-115">Configuring the A4SWIFT Runtime</span></span>](../../adapters-and-accelerators/accelerator-swift/configuring-the-a4swift-runtime.md)  
  
-   [<span data-ttu-id="dfe02-116">設定訊息修復和新送出</span><span class="sxs-lookup"><span data-stu-id="dfe02-116">Configuring Message Repair and New Submission</span></span>](../../adapters-and-accelerators/accelerator-swift/configuring-message-repair-and-new-submission.md)  
  
-   [<span data-ttu-id="dfe02-117">設定 FIN 回應對帳</span><span class="sxs-lookup"><span data-stu-id="dfe02-117">Configuring FIN Response Reconciliation</span></span>](../../adapters-and-accelerators/accelerator-swift/configuring-fin-response-reconciliation.md)