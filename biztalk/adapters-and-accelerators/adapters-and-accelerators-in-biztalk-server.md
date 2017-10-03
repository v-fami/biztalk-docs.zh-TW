---
title: "配接器和 BizTalk Server 中的快速鍵 |Microsoft 文件"
description: "所有配接器和在 BizTalk 中，包括內建配接器、 BAP、 HL7、 Swift、 RosettaNet、 FileAct，以及互動的加速器概觀"
caps.latest.revision: "3"
author: MandiOhlinger
manager: anneta
ms.custom: 
ms.date: 08/09/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df7f26a1-e47b-4323-b9f0-58842c55a6f8
ms.author: mandia
ms.openlocfilehash: 9f3f73fd4b53161e5d3e0aa81ee660a56d8ff850
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="adapters-and-accelerators-in-biztalk-server"></a><span data-ttu-id="0e7be-103">配接器和 BizTalk Server 中的快速鍵</span><span class="sxs-lookup"><span data-stu-id="0e7be-103">Adapters and Accelerators in BizTalk Server</span></span>
 [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="0e7be-104">包含不同的配接器和為您建立應用程式接收資料，並將資料傳送至不同的服務和 LOB 系統的快速鍵。</span><span class="sxs-lookup"><span data-stu-id="0e7be-104"> includes different adapters and accelerators for you to create applications that receive data, and send data to different services and LOB systems.</span></span> 
 
<span data-ttu-id="0e7be-105">本章節描述的不同配接器和適用於加速器[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0e7be-105">This section describes the different adapters and accelerators available with  [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span> 

## <a name="out-of-the-box-adapters"></a><span data-ttu-id="0e7be-106">方塊外配接器</span><span class="sxs-lookup"><span data-stu-id="0e7be-106">Out-of-the-box adapters</span></span>
<span data-ttu-id="0e7be-107">當您安裝 BizTalk Server 時，您也可以安裝會立即可用的內建配接器。</span><span class="sxs-lookup"><span data-stu-id="0e7be-107">When you install BizTalk Server, you also install the built-in adapters that are ready to be used.</span></span> <span data-ttu-id="0e7be-108">這些配接器包括檔案、 FTP、 MQ Series、 服務匯流排、 Logic Apps、 POP3、 SharePoint、 等等。</span><span class="sxs-lookup"><span data-stu-id="0e7be-108">Some of these adapters include File, FTP, MQ Series, Service Bus, Logic Apps, POP3, SharePoint, and more.</span></span>

<span data-ttu-id="0e7be-109">**[使用配接器](../core/using-adapters.md)列出的所有項目，而也示範如何使用每張介面卡。**</span><span class="sxs-lookup"><span data-stu-id="0e7be-109">**[Using Adapters](../core/using-adapters.md) lists all of them, and also shows you how to use each adapter.**</span></span>
 
## <a name="biztalk-adapter-pack"></a><span data-ttu-id="0e7be-110">BizTalk 配接器封包</span><span class="sxs-lookup"><span data-stu-id="0e7be-110">BizTalk Adapter Pack</span></span>
<span data-ttu-id="0e7be-111">[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]隨附[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，並提供 WCF 配接器來連接您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Oracle、 SAP、 Siebel 和 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="0e7be-111">The [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] is included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and provides WCF-based adapters to connect your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to Oracle, SAP, Siebel, and SQL Server.</span></span> <span data-ttu-id="0e7be-112">您也可以建立自己 WCF 架構的配接器使用[!INCLUDE[afproductnameshort_md](../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0e7be-112">You can also create your own WCF-based adapters using the [!INCLUDE[afproductnameshort_md](../includes/afproductnameshort-md.md)].</span></span> 

<span data-ttu-id="0e7be-113">**請參閱[BizTalk Adapter Pack](../adapters-and-accelerators/biztalk-adapter-pack.md)安裝及設定這些配接器逐步教學課程和情況下，使用不同的配接器，建立應用程式及充分了解如何以 WCF 為基礎的服務處理訊息的**.</span><span class="sxs-lookup"><span data-stu-id="0e7be-113">**See [BizTalk Adapter Pack](../adapters-and-accelerators/biztalk-adapter-pack.md) to install and configure these adapters, step through tutorials and scenarios, create applications using the different adapters, and get a good idea of how WCF-based services process messages**.</span></span> 

<span data-ttu-id="0e7be-114">某些範例也會提供在[http://go.microsoft.com/fwlink/p/?LinkID=196854](http://go.microsoft.com/fwlink/p/?LinkID=196854)。</span><span class="sxs-lookup"><span data-stu-id="0e7be-114">Some samples are also available at [http://go.microsoft.com/fwlink/p/?LinkID=196854](http://go.microsoft.com/fwlink/p/?LinkID=196854).</span></span> 

## <a name="fileact-and-interact"></a><span data-ttu-id="0e7be-115">FileAct 和互動</span><span class="sxs-lookup"><span data-stu-id="0e7be-115">FileAct and InterAct</span></span>
<span data-ttu-id="0e7be-116">[!INCLUDE[swift_adapter_md](../includes/swift-adapter-md.md)]隨附於[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]，並提供之間的連線程式[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]和協會的全球 Interbank 財務 Telecommunication (SWIFT) 保護 IP 網路 (SIPN)。</span><span class="sxs-lookup"><span data-stu-id="0e7be-116">The [!INCLUDE[swift_adapter_md](../includes/swift-adapter-md.md)] are included with [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], and provide connectivity between your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] and the Society for Worldwide Interbank Financial Telecommunication (SWIFT) Secure IP Network (SIPN).</span></span> 

<span data-ttu-id="0e7be-117">FileAct 配接器提供檔案及這些檔案的相關資訊的安全而可靠的交換。</span><span class="sxs-lookup"><span data-stu-id="0e7be-117">The FileAct adapter provides secure and reliable exchange of files, and information pertaining to those files.</span></span> 

<span data-ttu-id="0e7be-118">InterAct 配接器會提供安全、 可靠的訊息交換，個別結構化財務。</span><span class="sxs-lookup"><span data-stu-id="0e7be-118">The InterAct adapter provides secure and reliable exchange of individual structured financial messages.</span></span> 

<span data-ttu-id="0e7be-119">**請參閱[FileAct 和 InterAct](../adapters-and-accelerators/fileact-interact/microsoft-biztalk-server-fileact-and-interact-adapters-documentation.md)來安裝和設定這些介面卡，逐步執行某些教學課程和案例，並取得充分的了解架構的**。</span><span class="sxs-lookup"><span data-stu-id="0e7be-119">**See [FileAct and InterAct](../adapters-and-accelerators/fileact-interact/microsoft-biztalk-server-fileact-and-interact-adapters-documentation.md) to install and configure these adapters, step through some tutorials and scenarios, and get a good understanding of the architecture**.</span></span> 

## <a name="hl7"></a><span data-ttu-id="0e7be-120">HL7</span><span class="sxs-lookup"><span data-stu-id="0e7be-120">HL7</span></span>

<span data-ttu-id="0e7be-121">[!INCLUDE[btaBTAHL7NoNumber_md](../includes/btabtahl7nonumber-md.md)]隨附[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]，並提供之間的連線程式[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]和醫療保健電腦健全狀況層級七 (HL7) 標準為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0e7be-121">The [!INCLUDE[btaBTAHL7NoNumber_md](../includes/btabtahl7nonumber-md.md)] is included with [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], and provides connectivity between your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] and health care computer applications based on the Health Level Seven (HL7) standard.</span></span>

<span data-ttu-id="0e7be-122">**請參閱[HL7](../adapters-and-accelerators/accelerator-hl7/microsoft-biztalk-accelerator-for-hl7-documentation.md)安裝及設定配接器，逐步執行數個教學課程和案例，了解配接器的運作方式，以及使用不同的功能，包括結構描述、 通知、 批次處理、 驗證和更多**.</span><span class="sxs-lookup"><span data-stu-id="0e7be-122">**See [HL7](../adapters-and-accelerators/accelerator-hl7/microsoft-biztalk-accelerator-for-hl7-documentation.md) to install and configure the adapter, step through several tutorials and scenarios, learn how the adapter works, and use the different features, including schemas, acknowledgments, batching, validation, and more**.</span></span>

## <a name="rosettanet"></a><span data-ttu-id="0e7be-123">RosettaNet</span><span class="sxs-lookup"><span data-stu-id="0e7be-123">RosettaNet</span></span>
<span data-ttu-id="0e7be-124">BizTalk Accelerator for RosettaNet (BTARN) 隨附於 BizTalk Server 中，並簡化開發和部署的 RosettaNet 標準架構整合解決方案。</span><span class="sxs-lookup"><span data-stu-id="0e7be-124">The BizTalk Accelerator for RosettaNet (BTARN) is included with BizTalk Server, and streamlines the development and deployment of RosettaNet standards-based integration solutions.</span></span> <span data-ttu-id="0e7be-125">BTARN 支援 RosettaNet 實作架構 (RNIF);這是開放型的網路應用程式架構，讓商務夥伴協同執行 RosettaNet 夥伴介面程序 (Pip)。</span><span class="sxs-lookup"><span data-stu-id="0e7be-125">BTARN supports the RosettaNet Implementation Framework (RNIF); which is an open network application framework that enables business partners to collaboratively run RosettaNet Partner Interface Processes (PIPs).</span></span> 

<span data-ttu-id="0e7be-126">**請參閱[RosettaNet](../adapters-and-accelerators/accelerator-rosettanet/microsoft-biztalk-accelerator-for-rosettanet-documentation.md)若要深入了解此快速鍵，並使用與 BizTalk Server 解決方案。**</span><span class="sxs-lookup"><span data-stu-id="0e7be-126">**See [RosettaNet](../adapters-and-accelerators/accelerator-rosettanet/microsoft-biztalk-accelerator-for-rosettanet-documentation.md) to learn more about this accelerator, and using it with your BizTalk Server solutions.**</span></span> 

## <a name="swift"></a><span data-ttu-id="0e7be-127">SWIFT</span><span class="sxs-lookup"><span data-stu-id="0e7be-127">SWIFT</span></span>
<span data-ttu-id="0e7be-128">[!INCLUDE[btaA4SWIFTNoVersion_md](../includes/btaa4swiftnoversion-md.md)]隨附[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]，並提供之間的連線您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]和協會的全球 Interbank 財務 Telecommunication (SWIFT) 訊息格式。</span><span class="sxs-lookup"><span data-stu-id="0e7be-128">The [!INCLUDE[btaA4SWIFTNoVersion_md](../includes/btaa4swiftnoversion-md.md)] is included with [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], and provides connectivity between your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] and the Society for Worldwide Interbank Financial Telecommunication (SWIFT) message formats.</span></span>

<span data-ttu-id="0e7be-129">使用配接器與[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]，客戶、 合作夥伴和系統整合者可以簡化開發、 部署和支援的整合方案的核心涵蓋了金融服務應用程式基礎結構和商務程序。</span><span class="sxs-lookup"><span data-stu-id="0e7be-129">Using the adapter with [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], customers, partners, and system integrators can streamline the development, deployment, and support of integration solutions for core financial services application infrastructure and business processes.</span></span>

<span data-ttu-id="0e7be-130">**請參閱[SWIFT](../adapters-and-accelerators/accelerator-swift/microsoft-biztalk-accelerator-for-swift-documentation.md)安裝及設定配接器，以逐步執行某些教學課程，及使用訊息修復、 FIN 回應和 FRR 成品和多個**。</span><span class="sxs-lookup"><span data-stu-id="0e7be-130">**See [SWIFT](../adapters-and-accelerators/accelerator-swift/microsoft-biztalk-accelerator-for-swift-documentation.md) to install and configure the adapter, step through some tutorials, and use the message repair, FIN response and FRR artifacts, and more**.</span></span>

## <a name="get-some-help"></a><span data-ttu-id="0e7be-131">取得相關協助</span><span class="sxs-lookup"><span data-stu-id="0e7be-131">Get some help</span></span> 
<span data-ttu-id="0e7be-132">取得相關協助，並幫助其他人在[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]論壇[http://go.microsoft.com/fwlink/p/?LinkId=87695](http://go.microsoft.com/fwlink/p/?LinkId=87695)。</span><span class="sxs-lookup"><span data-stu-id="0e7be-132">Get some help, and help others in the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] forums [http://go.microsoft.com/fwlink/p/?LinkId=87695](http://go.microsoft.com/fwlink/p/?LinkId=87695).</span></span>