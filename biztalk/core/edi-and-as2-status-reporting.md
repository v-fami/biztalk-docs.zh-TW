---
title: EDI 和 AS2 狀態報告 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a9e58b29-9be0-41d6-ad35-1aae28e1a784
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a109398f4b3bff99ce7f45493839df6c3e5320f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993135"
---
# <a name="edi-and-as2-status-reporting"></a><span data-ttu-id="0ea75-102">EDI 和 AS2 狀態報告</span><span class="sxs-lookup"><span data-stu-id="0ea75-102">EDI and AS2 Status Reporting</span></span>
<span data-ttu-id="0ea75-103">EDI 狀態報告可以讓作業人員追蹤 EDI 和 AS2 傳輸的狀態。</span><span class="sxs-lookup"><span data-stu-id="0ea75-103">EDI status reporting enables operations personnel to track the status of EDI and AS2 transmissions.</span></span> <span data-ttu-id="0ea75-104">如果啟用，狀態報告會提供文件交換交易的完整狀態，包括交換以及與交換相互關聯的任何通知。</span><span class="sxs-lookup"><span data-stu-id="0ea75-104">If enabled, status reports provide comprehensive status of a document exchange transaction, including an interchange and any acknowledgments correlated to the interchange.</span></span> <span data-ttu-id="0ea75-105">這些報告提供 EDI 和 AS2 訊息處理的接收、驗證、批次處理和通知相關資料。</span><span class="sxs-lookup"><span data-stu-id="0ea75-105">These reports provide data on receipt, validation, batching, and acknowledgment processing of EDI and AS2 messages.</span></span>  
  
 <span data-ttu-id="0ea75-106">您可以使用這些報告取得擱置中和未通知的交換、完整交換、錯誤實例或商務實例等項目的狀態。</span><span class="sxs-lookup"><span data-stu-id="0ea75-106">You can use these reports to get the status of pending and unacknowledged interchanges, complete interchanges, error scenarios, or business scenarios.</span></span> <span data-ttu-id="0ea75-107">使用這些報告，您可以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="0ea75-107">With these reports, you can do the following:</span></span>  
  
- <span data-ttu-id="0ea75-108">確認接收交換</span><span class="sxs-lookup"><span data-stu-id="0ea75-108">Confirm the receipt of interchanges</span></span>  
  
- <span data-ttu-id="0ea75-109">列出等待通知的外寄交換</span><span class="sxs-lookup"><span data-stu-id="0ea75-109">List outgoing interchanges awaiting acknowledgment</span></span>  
  
- <span data-ttu-id="0ea75-110">列出所有已拒絕的已接收交換</span><span class="sxs-lookup"><span data-stu-id="0ea75-110">List all rejected interchanges received</span></span>  
  
- <span data-ttu-id="0ea75-111">列出報告為已拒絕或已部分接受的外寄交換。</span><span class="sxs-lookup"><span data-stu-id="0ea75-111">List outgoing interchanges that are reported as rejected or partially accepted.</span></span>  
  
  <span data-ttu-id="0ea75-112">狀態報告中所包含的資料取自交換控制區段，例如 ISA、TA1、GS、UNB 和 UNG (功能通知狀態除外)。</span><span class="sxs-lookup"><span data-stu-id="0ea75-112">Data included in the status reports is obtained from interchange control segments, such as ISA, TA1, GS, UNB, and UNG (with the exception of the Functional ACK status).</span></span>  
  
  <span data-ttu-id="0ea75-113">**狀態報告 UI**</span><span class="sxs-lookup"><span data-stu-id="0ea75-113">**Status Reporting UI**</span></span>  
  
  <span data-ttu-id="0ea75-114">EDI 和 AS2 狀態報告可從 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台] 取得。</span><span class="sxs-lookup"><span data-stu-id="0ea75-114">EDI and AS2 status reports are available from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span> <span data-ttu-id="0ea75-115">從**群組中樞**頁面**BizTalk 群組** 節點，您會有 EDI 交換和相互關聯的通知狀態、 批次狀態，以及 AS2 訊息和相互關聯的 MDN 狀態的連結。</span><span class="sxs-lookup"><span data-stu-id="0ea75-115">From the **Group Hub** page of the **BizTalk Group** node, you have links to EDI interchange and correlated acknowledgment status, batch status, and AS2 message and correlated MDN status.</span></span> <span data-ttu-id="0ea75-116">這些報告會提供您可以從查詢運算式包含或排除的狀態參數範圍，讓您建置所需的狀態報告。</span><span class="sxs-lookup"><span data-stu-id="0ea75-116">Each of these reports provides a range of status parameters that you can include or exclude from a query expression, enabling you to build the status report that they need.</span></span>  
  
  <span data-ttu-id="0ea75-117">除了能看到 EDI 交換的狀態，還可以檢視交換中的交易集。</span><span class="sxs-lookup"><span data-stu-id="0ea75-117">In addition to seeing the status of an EDI interchange, you can also view the transaction sets in an interchange.</span></span> <span data-ttu-id="0ea75-118">只要啟用追蹤 (BizTalkDTADb) 資料庫 EDI 資料表中的訊息內容儲存區，就能達到此目的。</span><span class="sxs-lookup"><span data-stu-id="0ea75-118">You do so by enabling the storage of message payloads in the EDI tables of the tracking (BizTalkDTADb) database.</span></span> <span data-ttu-id="0ea75-119">使用狀態報告 UI 中的檢視詳細資料命令，即可檢視交易集。</span><span class="sxs-lookup"><span data-stu-id="0ea75-119">You can view the transaction sets by using the view details command in the status reporting UI.</span></span>  
  
  <span data-ttu-id="0ea75-120">您也可以將輸入或輸出 AS2 訊息或 MDN 儲存在不可否認性的資料庫中。</span><span class="sxs-lookup"><span data-stu-id="0ea75-120">You can also store inbound or outbound AS2 messages or MDNs in the non-repudiation database.</span></span> <span data-ttu-id="0ea75-121">以滑鼠右鍵按一下狀態報告中的訊息並選取適當的命令，即可檢視交易集或 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="0ea75-121">You can view the transaction sets or AS2 messages by right-clicking the message in the status report and selecting the appropriate command.</span></span>  
  
  <span data-ttu-id="0ea75-122">**狀態報告元件**</span><span class="sxs-lookup"><span data-stu-id="0ea75-122">**Status Report Components**</span></span>  
  
  <span data-ttu-id="0ea75-123">狀態報告的相關 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 元件如下：</span><span class="sxs-lookup"><span data-stu-id="0ea75-123">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] components involved in status reporting are the following:</span></span>  
  
- <span data-ttu-id="0ea75-124">EDI 接收管線中的 EDI 解譯器，會在內送交換的資料存放區中建立並更新狀態項目</span><span class="sxs-lookup"><span data-stu-id="0ea75-124">The EDI Disassembler in the EDI receive pipeline that creates and updates status entries in the data store for an incoming interchange</span></span>  
  
- <span data-ttu-id="0ea75-125">EDI 傳送管線中的 EDI 組合器，會在外送交換的資料存放區中建立並更新狀態項目</span><span class="sxs-lookup"><span data-stu-id="0ea75-125">The EDI Assembler in the EDI send pipeline that creates and updates status entries in the data store for an outgoing interchange</span></span>  
  
- <span data-ttu-id="0ea75-126">存放狀態報告項目的資料存放區。</span><span class="sxs-lookup"><span data-stu-id="0ea75-126">The data stores that store the status report entries.</span></span> <span data-ttu-id="0ea75-127">包括用來追蹤資料的 BAM 主要匯入資料庫，以及 EDI 交易集和 (或) AS2 訊息內容專用之 BizTalk 追蹤資料庫 (BizTalkDTADb) 的 EDI Message Content 資料表</span><span class="sxs-lookup"><span data-stu-id="0ea75-127">These are the BAM Primary Import database for tracking data and the EDI Message Content table of the BizTalk tracking database (BizTalkDTADb) for EDI transaction sets and/or AS2 message contents</span></span>  
  
- <span data-ttu-id="0ea75-128">狀態報告 UI 上**群組中樞**頁[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，用來顯示狀態報告資料</span><span class="sxs-lookup"><span data-stu-id="0ea75-128">Status reporting UI on the **Group Hub** page of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, which is used to display status reporting data</span></span>  
  
- <span data-ttu-id="0ea75-129">[[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台] 中的協議屬性和後援協議屬性選項，可用來啟用及設定狀態報告</span><span class="sxs-lookup"><span data-stu-id="0ea75-129">Agreement property and fallback agreement property options in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, which is used to enable and configure status reporting</span></span>  
  
- <span data-ttu-id="0ea75-130">運用 BAM 基礎結構的 DTA 和 SQL 分析伺服器。</span><span class="sxs-lookup"><span data-stu-id="0ea75-130">DTA and SQL Analysis Server that leverage the BAM infrastructure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0ea75-131">本節內容</span><span class="sxs-lookup"><span data-stu-id="0ea75-131">In This Section</span></span>  
  
-   [<span data-ttu-id="0ea75-132">EDI 和 AS2 狀態報告的設定</span><span class="sxs-lookup"><span data-stu-id="0ea75-132">Configuration of EDI and AS2 Status Reporting</span></span>](../core/configuration-of-edi-and-as2-status-reporting.md)  
  
-   [<span data-ttu-id="0ea75-133">EDI 和 AS2 狀態報告的類型</span><span class="sxs-lookup"><span data-stu-id="0ea75-133">Types of EDI and AS2 Status Reports</span></span>](../core/types-of-edi-and-as2-status-reports.md)  
  
-   [<span data-ttu-id="0ea75-134">EDI 和 AS2 狀態報告的儲存資料</span><span class="sxs-lookup"><span data-stu-id="0ea75-134">Data Stored for EDI and AS2 Status Reports</span></span>](../core/data-stored-for-edi-and-as2-status-reports.md)  
  
-   [<span data-ttu-id="0ea75-135">如何儲存 EDI 和 AS2 狀態報告的資料</span><span class="sxs-lookup"><span data-stu-id="0ea75-135">How Data Is Stored for EDI and AS2 Status Reports</span></span>](../core/how-data-is-stored-for-edi-and-as2-status-reports.md)