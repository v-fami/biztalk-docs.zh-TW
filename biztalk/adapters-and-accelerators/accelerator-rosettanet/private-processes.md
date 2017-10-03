---
title: "私用程序 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- private processes, trading partners
- private processes, about private processes
- private processes, orchestrations
- private processes
- orchestrations, private-process orchestrations
- trading partners, private processes
- BTARN, private processes
- business processes, private processes
ms.assetid: 0c5895eb-22c1-431f-a769-ae6ca05d1e45
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b28bf49af1305220d96f129080b274b5391495eb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="private-processes"></a><span data-ttu-id="98977-102">私用程序</span><span class="sxs-lookup"><span data-stu-id="98977-102">Private Processes</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="98977-103">[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]實作做為私用程序將組織內部的商務程序。</span><span class="sxs-lookup"><span data-stu-id="98977-103"> [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] implements business processes that are internal to an organization as private processes.</span></span> <span data-ttu-id="98977-104">公開程序會處理與交易夥伴整合有關的商務程序。</span><span class="sxs-lookup"><span data-stu-id="98977-104">Public processes handle business processes that involve integration with trading partners.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="98977-105">隔離服務內容處理及後端整合 （在私用程序中） 從 RosettaNet 實作架構 (RNIF) 處理 （在公開程序）。</span><span class="sxs-lookup"><span data-stu-id="98977-105"> isolates service-content processing and back-end integration (in the private process) from RosettaNet Implementation Framework (RNIF) handling (in the public process).</span></span>  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="98977-106">做為長時間執行的 BizTalk 協調流程會實作私用程序。</span><span class="sxs-lookup"><span data-stu-id="98977-106"> implements private processes as long-running BizTalk orchestrations.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="98977-107">您可以使用一個私用程序協調流程上的起始端和回應者端的其中一個。</span><span class="sxs-lookup"><span data-stu-id="98977-107"> uses one private-process orchestration on the initiator side and one on the responder side.</span></span> <span data-ttu-id="98977-108">每個私用程序都會解譯並處理服務內容訊息部分 (不論是內送或是外寄)。</span><span class="sxs-lookup"><span data-stu-id="98977-108">Each private process interprets and processes the service-content message part, either incoming or outgoing.</span></span> <span data-ttu-id="98977-109">私用程序會傳送服務內容至公開程序，或是接收來自公開程序的服務內容。</span><span class="sxs-lookup"><span data-stu-id="98977-109">The private process sends the service content to, or receives it from, the public process.</span></span> <span data-ttu-id="98977-110">私用程序不會處理標頭，也不會執行 RNIF 處理。</span><span class="sxs-lookup"><span data-stu-id="98977-110">A private process does not handle headers, and does not perform RNIF processing.</span></span> <span data-ttu-id="98977-111">這些工作將留給公開程序來處理。</span><span class="sxs-lookup"><span data-stu-id="98977-111">It leaves that to the public process.</span></span>  
  
 <span data-ttu-id="98977-112">在企業實例中，通常每個 PIP 訊息結構描述都會有一個私用程序。</span><span class="sxs-lookup"><span data-stu-id="98977-112">In an enterprise scenario, there would typically be one private process for each PIP message schema.</span></span> <span data-ttu-id="98977-113">不過，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK 包含兩個可以處理任何 PIP 訊息的私用程序協調流程。</span><span class="sxs-lookup"><span data-stu-id="98977-113">However, the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK includes two private-process orchestrations that can process any PIP message.</span></span> <span data-ttu-id="98977-114">一個協調流程為啟動者程序 (PrivateInitiator.odx，請參閱[PrivateInitiator 範例 &#91;RN3 &#93;](../../adapters-and-accelerators/accelerator-rosettanet/privateinitiator-sample.md)) 另一個做為回應者程序 (PrivateResponder.odx，請參閱[PrivateResponder 範例 &#91;RN3 &#93;](../../adapters-and-accelerators/accelerator-rosettanet/privateresponder-sample.md)).</span><span class="sxs-lookup"><span data-stu-id="98977-114">One orchestration is for the initiator process (PrivateInitiator.odx, see [PrivateInitiator Sample &#91;RN3&#93;](../../adapters-and-accelerators/accelerator-rosettanet/privateinitiator-sample.md)) and one is for the responder process (PrivateResponder.odx, see [PrivateResponder Sample &#91;RN3&#93;](../../adapters-and-accelerators/accelerator-rosettanet/privateresponder-sample.md)).</span></span> <span data-ttu-id="98977-115">您必須自訂私用程序，使 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 適合您特定的商務程序。</span><span class="sxs-lookup"><span data-stu-id="98977-115">You will have to customize the private processes to adapt [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] to your specific business processes.</span></span>  
  
 <span data-ttu-id="98977-116">SDK 也包含實作特定 PIP 私用回應者程序以整合商務規則的處理序 (PIP3A4PrivateResponder.odx，請參閱[3A4 私用回應者協調流程使用商務規則](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md))。</span><span class="sxs-lookup"><span data-stu-id="98977-116">The SDK also includes a process that implements a PIP-specific private responder process incorporating a business rule (PIP3A4PrivateResponder.odx, see [3A4 Private Responder Orchestration Using a Business Rule](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md)).</span></span>  
  
 <span data-ttu-id="98977-117">私用程序會將服務內容從後端商務營運系統 (LOB) 格式變更為 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="98977-117">The private process changes the format of the service content from the back-end line-of-business (LOB) format to XML.</span></span> <span data-ttu-id="98977-118">變更為 XML 格式之後，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 便會處理服務內容，並且公開程序會將 RNIF 相容標頭新增至服務內容以進行傳輸。</span><span class="sxs-lookup"><span data-stu-id="98977-118">As soon as it is in XML format, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] processes the service content, and the public process adds RNIF-compliant headers to the service content for transmission.</span></span>  
  
 <span data-ttu-id="98977-119">私用程序會透過 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] 資料庫中的 MessageToLOB 及 MessagesFromLOB 資料表，連接至後端商務營運系統應用程式。</span><span class="sxs-lookup"><span data-stu-id="98977-119">The private process connects to the back-end line-of-business applications through the MessageToLOB and MessagesFromLOB tables in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] database.</span></span> <span data-ttu-id="98977-120">這個資料庫負責處理 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 與 LOB 應用程式之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="98977-120">This database handles the communication between [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] and the LOB applications.</span></span> <span data-ttu-id="98977-121">LOB 應用程式會使用介面取得資料庫資料表的存取權。</span><span class="sxs-lookup"><span data-stu-id="98977-121">The LOB application uses an interface to gain access to the database tables.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="98977-122">本節內容</span><span class="sxs-lookup"><span data-stu-id="98977-122">In This Section</span></span>  
  
-   [<span data-ttu-id="98977-123">啟動者私用程序</span><span class="sxs-lookup"><span data-stu-id="98977-123">Initiator Private Process</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/initiator-private-process.md)  
  
-   [<span data-ttu-id="98977-124">回應者私用程序</span><span class="sxs-lookup"><span data-stu-id="98977-124">Responder Private Process</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/responder-private-process.md)