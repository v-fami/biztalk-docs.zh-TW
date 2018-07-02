---
title: BizTalk Accelerator for SWIFT 執行階段 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2fc0e7a7cb00e16263e537e24abcc144e5c7d0a4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966119"
---
# <a name="biztalk-accelerator-for-swift-runtime"></a><span data-ttu-id="d4003-102">BizTalk Accelerator for SWIFT 執行階段</span><span class="sxs-lookup"><span data-stu-id="d4003-102">BizTalk Accelerator for SWIFT Runtime</span></span>
<span data-ttu-id="d4003-103">Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]提供兩種形式的功能： 開發資料和執行階段元件。</span><span class="sxs-lookup"><span data-stu-id="d4003-103">Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] provides functionality in two forms: development materials and runtime components.</span></span> <span data-ttu-id="d4003-104">開發資料包括 XSD 結構描述、 驗證規則和原則，以及範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="d4003-104">Development materials include XSD schemas, validation rules and policies, and sample code.</span></span> <span data-ttu-id="d4003-105">執行階段元件包括自訂的 SWIFT 解譯器、 自訂的 SWIFT 組合器、 Message Repair 和 New Submission 協調流程 (MrsrRepair.odx) 和 FIN 回應對帳協調流程 (FrrMain.odx)。</span><span class="sxs-lookup"><span data-stu-id="d4003-105">Runtime components include the custom SWIFT disassembler, the custom SWIFT assembler, the Message Repair and New Submission orchestration (MrsrRepair.odx), and the FIN Response Reconciliation orchestration (FrrMain.odx).</span></span> <span data-ttu-id="d4003-106">如需有關 Message Repair 和 New Submission 的詳細資訊，請參閱 < [Message Repair 和 New Submission](../../adapters-and-accelerators/accelerator-swift/message-repair-and-new-submission.md)。</span><span class="sxs-lookup"><span data-stu-id="d4003-106">For more information on Message Repair and New Submission, see [Message Repair and New Submission](../../adapters-and-accelerators/accelerator-swift/message-repair-and-new-submission.md).</span></span> <span data-ttu-id="d4003-107">如需有關 FRR 的詳細資訊，請參閱[FIN 回應對帳](../../adapters-and-accelerators/accelerator-swift/fin-response-reconciliation.md)。</span><span class="sxs-lookup"><span data-stu-id="d4003-107">For more information on FRR, see [FIN Response Reconciliation](../../adapters-and-accelerators/accelerator-swift/fin-response-reconciliation.md).</span></span>  

 <span data-ttu-id="d4003-108">下圖顯示高階系統的架構[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d4003-108">The following figure shows the high-level system architecture of [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)].</span></span>  

 <span data-ttu-id="d4003-109">![](../../adapters-and-accelerators/accelerator-swift/media/a4swiftsystemarchitecture-end-to-end.gif "A4SWIFTSystemArchitecture_End_to_End")</span><span class="sxs-lookup"><span data-stu-id="d4003-109">![](../../adapters-and-accelerators/accelerator-swift/media/a4swiftsystemarchitecture-end-to-end.gif "A4SWIFTSystemArchitecture_End_to_End")</span></span>  

 <span data-ttu-id="d4003-110">下圖說明訊息 A4SWIFT 和後端應用程式之間流動的方式以及如何使用 A4SWIFT [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] Message Repair 和 New Submission 的表單中 MRSR 網站。</span><span class="sxs-lookup"><span data-stu-id="d4003-110">The following figure illustrates how messages flow between A4SWIFT and a back-end application, and how A4SWIFT uses [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forms in MRSR site for Message Repair and New Submission.</span></span>  

 <span data-ttu-id="d4003-111">![](../../adapters-and-accelerators/accelerator-swift/media/a4swiftsystemarchitecture-interfaceswithbackendapplications.gif "A4SWIFTSystemArchitecture_InterfaceswithBackEndApplications")</span><span class="sxs-lookup"><span data-stu-id="d4003-111">![](../../adapters-and-accelerators/accelerator-swift/media/a4swiftsystemarchitecture-interfaceswithbackendapplications.gif "A4SWIFTSystemArchitecture_InterfaceswithBackEndApplications")</span></span>  

 <span data-ttu-id="d4003-112">下圖說明訊息 A4SWIFT 和 SWIFT 網路之間流動的方式。</span><span class="sxs-lookup"><span data-stu-id="d4003-112">The following figure illustrates how messages flow between A4SWIFT and the SWIFT Network.</span></span>  

 <span data-ttu-id="d4003-113">![](../../adapters-and-accelerators/accelerator-swift/media/a4swiftsystemarchitecture-interfaceswiththeswiftnetwork.gif "A4SWIFTSystemArchitecture_InterfaceswiththeSWIFTNetwork")</span><span class="sxs-lookup"><span data-stu-id="d4003-113">![](../../adapters-and-accelerators/accelerator-swift/media/a4swiftsystemarchitecture-interfaceswiththeswiftnetwork.gif "A4SWIFTSystemArchitecture_InterfaceswiththeSWIFTNetwork")</span></span>  

 <span data-ttu-id="d4003-114">您可以定義所有 A4SWIFT 元件，為 BizTalk Server 應用程式元件垂直專屬實作。</span><span class="sxs-lookup"><span data-stu-id="d4003-114">You can define all A4SWIFT components as vertical-specific implementations of BizTalk Server application components.</span></span> <span data-ttu-id="d4003-115">BizTalk 「 加速器 」 提供開發和執行階段功能，以加速垂直特定 BizTalk 應用程式開發最上層的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d4003-115">BizTalk accelerators provide development and runtime functionality to accelerate vertical-specific BizTalk application development on top of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="d4003-116">因此，所有 A4SWIFT 元件 （「 開發 」 或 「 執行階段 」） 會遵守，並放入 BizTalk Server 應用程式架構。</span><span class="sxs-lookup"><span data-stu-id="d4003-116">Therefore, all A4SWIFT components (development or runtime) abide by, and fit into, the BizTalk Server application architecture.</span></span> <span data-ttu-id="d4003-117">A4SWIFT 安裝到執行階段元件[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]做為自訂元件的執行階段。</span><span class="sxs-lookup"><span data-stu-id="d4003-117">A4SWIFT installs runtime components into the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] runtime as custom components.</span></span> <span data-ttu-id="d4003-118">之後開發編譯和部署，A4SWIFT 教材和[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]執行階段會使用它們來提供 SWIFT 訊息處理和自動化功能。</span><span class="sxs-lookup"><span data-stu-id="d4003-118">After development materials are compiled and deployed, A4SWIFT and the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] runtime use them to provide SWIFT messaging and automation functionality.</span></span>  

 <span data-ttu-id="d4003-119">下圖顯示 BizTalk server 的高層級的應用程式拓樸。</span><span class="sxs-lookup"><span data-stu-id="d4003-119">The following figure shows the high-level application topology for BizTalk Server.</span></span>  

 <span data-ttu-id="d4003-120">![](../../adapters-and-accelerators/accelerator-swift/media/fsa-intro1.gif "FSA_Intro1")</span><span class="sxs-lookup"><span data-stu-id="d4003-120">![](../../adapters-and-accelerators/accelerator-swift/media/fsa-intro1.gif "FSA_Intro1")</span></span>  

 <span data-ttu-id="d4003-121">[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式模型會使用 MessageBox 資料庫和訂閱者的 「 發行者 」 模式，其可控制傳入和傳出的 MessageBox 資料庫的訊息流程。</span><span class="sxs-lookup"><span data-stu-id="d4003-121">The [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application model uses the MessageBox database and the publisher-subscriber pattern that governs message flow into and out of the MessageBox database.</span></span> <span data-ttu-id="d4003-122">如需 BizTalk 架構和應用程式的設計的詳細資訊，請參閱 BizTalk Server 說明。</span><span class="sxs-lookup"><span data-stu-id="d4003-122">For more information about BizTalk architecture and application design, see BizTalk Server Help.</span></span>  

 <span data-ttu-id="d4003-123">A4SWIFT 應用程式模型會繼承[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式模型，並將它加入 SWIFT 特有的元件，以便 SWIFT 相關解決方案上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d4003-123">The A4SWIFT application model inherits the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application model and adds to it SWIFT-specific components to facilitate SWIFT-related solutions on [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="d4003-124">下列清單描述這些 A4SWIFT 特有的元件：</span><span class="sxs-lookup"><span data-stu-id="d4003-124">The following list describes these A4SWIFT-specific components:</span></span>  

- <span data-ttu-id="d4003-125">**執行階段元件。**</span><span class="sxs-lookup"><span data-stu-id="d4003-125">**Runtime components.**</span></span> <span data-ttu-id="d4003-126">在接收管線，在傳送管線、 Message Repair 和 New Submission 的協調流程和 FIN 回應對帳協調流程的 SWIFT 組合器的 SWIFT 解譯器。</span><span class="sxs-lookup"><span data-stu-id="d4003-126">SWIFT disassembler in the receive pipeline, SWIFT assembler in the send pipeline, Message Repair and New Submission orchestration, and FIN Response Reconciliation orchestration.</span></span>  

- <span data-ttu-id="d4003-127">**開發資料。**</span><span class="sxs-lookup"><span data-stu-id="d4003-127">**Development materials.**</span></span> <span data-ttu-id="d4003-128">SWIFT 結構描述、 規則、 協調流程和包含在客戶解決方案並部署到執行階段執行的範例專案。</span><span class="sxs-lookup"><span data-stu-id="d4003-128">SWIFT schemas, rules, orchestrations, and sample projects to be included in customer solutions and deployed onto the runtime for execution.</span></span>  

  <span data-ttu-id="d4003-129">本章節描述 A4SWIFT 執行階段，在 詳細資料。</span><span class="sxs-lookup"><span data-stu-id="d4003-129">This section describes the A4SWIFT runtime in detail.</span></span>  

  <span data-ttu-id="d4003-130">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="d4003-130">This section contains:</span></span>  

- [<span data-ttu-id="d4003-131">SWIFT 解譯器</span><span class="sxs-lookup"><span data-stu-id="d4003-131">SWIFT Disassembler</span></span>](../../adapters-and-accelerators/accelerator-swift/swift-disassembler.md)  

- [<span data-ttu-id="d4003-132">SWIFT 組合器</span><span class="sxs-lookup"><span data-stu-id="d4003-132">SWIFT Assembler</span></span>](../../adapters-and-accelerators/accelerator-swift/swift-assembler.md)  

- [<span data-ttu-id="d4003-133">透過接收位置和 InfoPath 表單提交訊息</span><span class="sxs-lookup"><span data-stu-id="d4003-133">Submitting Messages Through Receive Locations and InfoPath Forms</span></span>](../../adapters-and-accelerators/accelerator-swift/submitting-messages-through-receive-locations-and-infopath-forms.md)  

- [<span data-ttu-id="d4003-134">訊息驗證引擎</span><span class="sxs-lookup"><span data-stu-id="d4003-134">Message Validation Engine</span></span>](../../adapters-and-accelerators/accelerator-swift/message-validation-engine.md)
