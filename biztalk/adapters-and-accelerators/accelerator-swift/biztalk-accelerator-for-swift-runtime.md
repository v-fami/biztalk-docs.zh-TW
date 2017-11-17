---
title: "BizTalk Accelerator for SWIFT 的執行階段 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- runtime, architecture
- developing, components
- architecture, topology
- messages, message flow diagram
- runtime, components
- SWIFT runtime
- architecture, runtime architecture
- SWIFT network
- A4SWIFT, network
- topology
ms.assetid: c0f59760-7d7d-4b22-a7dc-54e563971d4a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f312a91d403d125fe6d245b92bf83da57d1031fe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-accelerator-for-swift-runtime"></a><span data-ttu-id="e99ac-102">BizTalk Accelerator for SWIFT 的執行階段</span><span class="sxs-lookup"><span data-stu-id="e99ac-102">BizTalk Accelerator for SWIFT Runtime</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="e99ac-103">[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]提供兩種形式的功能： 開發資料和執行階段元件。</span><span class="sxs-lookup"><span data-stu-id="e99ac-103"> [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] provides functionality in two forms: development materials and runtime components.</span></span> <span data-ttu-id="e99ac-104">開發材料包括 XSD 結構描述，驗證規則和原則和範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="e99ac-104">Development materials include XSD schemas, validation rules and policies, and sample code.</span></span> <span data-ttu-id="e99ac-105">執行階段元件包括自訂 SWIFT 解譯器、 自訂 SWIFT 組譯工具、 Message Repair 和 New Submission 協調流程 (MrsrRepair.odx) 和 FIN 回應對帳協調流程 (FrrMain.odx)。</span><span class="sxs-lookup"><span data-stu-id="e99ac-105">Runtime components include the custom SWIFT disassembler, the custom SWIFT assembler, the Message Repair and New Submission orchestration (MrsrRepair.odx), and the FIN Response Reconciliation orchestration (FrrMain.odx).</span></span> <span data-ttu-id="e99ac-106">如需有關 Message Repair 和 New Submission 的詳細資訊，請參閱[Message Repair 和 New Submission](../../adapters-and-accelerators/accelerator-swift/message-repair-and-new-submission.md)。</span><span class="sxs-lookup"><span data-stu-id="e99ac-106">For more information on Message Repair and New Submission, see [Message Repair and New Submission](../../adapters-and-accelerators/accelerator-swift/message-repair-and-new-submission.md).</span></span> <span data-ttu-id="e99ac-107">如需有關 FRR 的詳細資訊，請參閱[FIN 回應對帳](../../adapters-and-accelerators/accelerator-swift/fin-response-reconciliation.md)。</span><span class="sxs-lookup"><span data-stu-id="e99ac-107">For more information on FRR, see [FIN Response Reconciliation](../../adapters-and-accelerators/accelerator-swift/fin-response-reconciliation.md).</span></span>  
  
 <span data-ttu-id="e99ac-108">如下圖所示的高層級的系統架構[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e99ac-108">The following figure shows the high-level system architecture of [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)].</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swiftsystemarchitecture-end-to-end.gif "A4SWIFTSystemArchitecture_End_to_End")  
  
 <span data-ttu-id="e99ac-109">下圖說明 A4SWIFT 與後端應用程式之間訊息的流程為何及如何使用 A4SWIFT [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] MRSR 中的表單的 Message Repair 和 New Submission 網站。</span><span class="sxs-lookup"><span data-stu-id="e99ac-109">The following figure illustrates how messages flow between A4SWIFT and a back-end application, and how A4SWIFT uses [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forms in MRSR site for Message Repair and New Submission.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swiftsystemarchitecture-interfaceswithbackendapplications.gif "A4SWIFTSystemArchitecture_InterfaceswithBackEndApplications")  
  
 <span data-ttu-id="e99ac-110">下圖說明訊息 A4SWIFT SWIFT 網路之間流動的方式。</span><span class="sxs-lookup"><span data-stu-id="e99ac-110">The following figure illustrates how messages flow between A4SWIFT and the SWIFT Network.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swiftsystemarchitecture-interfaceswiththeswiftnetwork.gif "A4SWIFTSystemArchitecture_InterfaceswiththeSWIFTNetwork")  
  
 <span data-ttu-id="e99ac-111">您可以定義所有 A4SWIFT 元件為垂直專屬實作[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]應用程式元件。</span><span class="sxs-lookup"><span data-stu-id="e99ac-111">You can define all A4SWIFT components as vertical-specific implementations of [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] application components.</span></span> <span data-ttu-id="e99ac-112">BizTalk 「 加速器 」 提供開發和執行階段以加速上方的垂直特定 BizTalk 應用程式開發功能[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e99ac-112">BizTalk accelerators provide development and runtime functionality to accelerate vertical-specific BizTalk application development on top of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="e99ac-113">因此，遵守，所有的 A4SWIFT 元件 （開發或執行階段），以及納入，[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]應用程式架構。</span><span class="sxs-lookup"><span data-stu-id="e99ac-113">Therefore, all A4SWIFT components (development or runtime) abide by, and fit into, the [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] application architecture.</span></span> <span data-ttu-id="e99ac-114">A4SWIFT 安裝到執行階段元件[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]做為自訂元件的執行階段。</span><span class="sxs-lookup"><span data-stu-id="e99ac-114">A4SWIFT installs runtime components into the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] runtime as custom components.</span></span> <span data-ttu-id="e99ac-115">在開發之後材料編譯和部署，A4SWIFT 和[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]執行階段使用它們來提供 SWIFT 訊息和自動化功能。</span><span class="sxs-lookup"><span data-stu-id="e99ac-115">After development materials are compiled and deployed, A4SWIFT and the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] runtime use them to provide SWIFT messaging and automation functionality.</span></span>  
  
 <span data-ttu-id="e99ac-116">如下圖所示的高階應用程式拓樸[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e99ac-116">The following figure shows the high-level application topology for [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/fsa-intro1.gif "FSA_Intro1")  
  
 <span data-ttu-id="e99ac-117">[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式模型使用的 MessageBox 資料庫和管理訊息流程進出 MessageBox 資料庫的發行者訂閱者模式。</span><span class="sxs-lookup"><span data-stu-id="e99ac-117">The [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application model uses the MessageBox database and the publisher-subscriber pattern that governs message flow into and out of the MessageBox database.</span></span> <span data-ttu-id="e99ac-118">如需 BizTalk 架構和應用程式設計的詳細資訊，請參閱[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="e99ac-118">For more information about BizTalk architecture and application design, see [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
 <span data-ttu-id="e99ac-119">A4SWIFT 應用程式模型繼承[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式模型，並將它加入 SWIFT 特有的元件，以便 SWIFT 相關解決方案上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e99ac-119">The A4SWIFT application model inherits the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application model and adds to it SWIFT-specific components to facilitate SWIFT-related solutions on [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="e99ac-120">下列清單描述這些 A4SWIFT 特有的元件：</span><span class="sxs-lookup"><span data-stu-id="e99ac-120">The following list describes these A4SWIFT-specific components:</span></span>  
  
-   <span data-ttu-id="e99ac-121">**執行階段元件。**</span><span class="sxs-lookup"><span data-stu-id="e99ac-121">**Runtime components.**</span></span> <span data-ttu-id="e99ac-122">SWIFT 中 SWIFT 組合器的傳送管線、 Message Repair 和 New Submission 協調流程和 FIN 回應對帳協調流程中，接收管線的解譯器。</span><span class="sxs-lookup"><span data-stu-id="e99ac-122">SWIFT disassembler in the receive pipeline, SWIFT assembler in the send pipeline, Message Repair and New Submission orchestration, and FIN Response Reconciliation orchestration.</span></span>  
  
-   <span data-ttu-id="e99ac-123">**開發材料。**</span><span class="sxs-lookup"><span data-stu-id="e99ac-123">**Development materials.**</span></span> <span data-ttu-id="e99ac-124">SWIFT 的結構描述、 規則、 協調流程和包含在客戶解決方案並部署到執行的執行階段的範例專案。</span><span class="sxs-lookup"><span data-stu-id="e99ac-124">SWIFT schemas, rules, orchestrations, and sample projects to be included in customer solutions and deployed onto the runtime for execution.</span></span>  
  
 <span data-ttu-id="e99ac-125">本章節描述 A4SWIFT 中的執行階段詳細資料。</span><span class="sxs-lookup"><span data-stu-id="e99ac-125">This section describes the A4SWIFT runtime in detail.</span></span>  
  
 <span data-ttu-id="e99ac-126">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="e99ac-126">This section contains:</span></span>  
  
-   [<span data-ttu-id="e99ac-127">SWIFT 反組譯工具</span><span class="sxs-lookup"><span data-stu-id="e99ac-127">SWIFT Disassembler</span></span>](../../adapters-and-accelerators/accelerator-swift/swift-disassembler.md)  
  
-   [<span data-ttu-id="e99ac-128">SWIFT 組譯工具</span><span class="sxs-lookup"><span data-stu-id="e99ac-128">SWIFT Assembler</span></span>](../../adapters-and-accelerators/accelerator-swift/swift-assembler.md)  
  
-   [<span data-ttu-id="e99ac-129">正在提交訊息到接收位置和 InfoPath 表單</span><span class="sxs-lookup"><span data-stu-id="e99ac-129">Submitting Messages Through Receive Locations and InfoPath Forms</span></span>](../../adapters-and-accelerators/accelerator-swift/submitting-messages-through-receive-locations-and-infopath-forms.md)  
  
-   [<span data-ttu-id="e99ac-130">訊息驗證引擎</span><span class="sxs-lookup"><span data-stu-id="e99ac-130">Message Validation Engine</span></span>](../../adapters-and-accelerators/accelerator-swift/message-validation-engine.md)