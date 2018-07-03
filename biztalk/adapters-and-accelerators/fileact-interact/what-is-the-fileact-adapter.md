---
title: 何謂 FileAct 配接器？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 05ec8f1e-57f9-4e2d-ab8b-22b5c4b28055
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc6fe9b28e4ea2b5eee087b61866827a766c3e3f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971487"
---
# <a name="what-is-the-fileact-adapter"></a><span data-ttu-id="431b2-103">何謂 FileAct 配接器？</span><span class="sxs-lookup"><span data-stu-id="431b2-103">What Is the FileAct Adapter?</span></span>
<span data-ttu-id="431b2-104">FileAct 配接器的 SWIFTNet 提供 BizTalk Server 與協會之間的連線能力的全球 Interbank 財務電信 (SWIFT) 安全 IP 網路 (SIPN) 傳輸檔案。</span><span class="sxs-lookup"><span data-stu-id="431b2-104">The FileAct adapter for SWIFTNet provides connectivity between BizTalk Server and the Society for Worldwide Interbank Financial Telecommunication (SWIFT) Secure IP Network (SIPN) for the transfer of files.</span></span> <span data-ttu-id="431b2-105">SIPN 傳輸安全的私人網路連線到金融機構、 金融業基礎結構和客戶的郵件和檔案。</span><span class="sxs-lookup"><span data-stu-id="431b2-105">The SIPN transfers messages and files over a secure private network which connects financial institutions, financial industry infrastructures, and customers.</span></span> <span data-ttu-id="431b2-106">FileAct 配接器使用 SWIFTNet 連結 (SNL) 應用程式開發介面 (API) s 要連接到 SIPN。</span><span class="sxs-lookup"><span data-stu-id="431b2-106">The FileAct adapter uses the SWIFTNet Link (SNL) application programming interface (API)s to connect to the SIPN.</span></span>  
  
 <span data-ttu-id="431b2-107">FileAct 配接器安全地提供 SWIFT 參與者的機制，並可靠地交換檔案和這些檔案的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="431b2-107">The FileAct adapter provides a mechanism for SWIFT participants to securely and reliably exchange files and information pertaining to those files.</span></span> <span data-ttu-id="431b2-108">它支援下列功能：</span><span class="sxs-lookup"><span data-stu-id="431b2-108">It supports the following functionality:</span></span>  
  
-   <span data-ttu-id="431b2-109">傳送檔案至 SWIFTNet 使用者</span><span class="sxs-lookup"><span data-stu-id="431b2-109">Sending files to a SWIFTNet User</span></span>  
  
-   <span data-ttu-id="431b2-110">SWIFTNet 使用者從擷取的檔案</span><span class="sxs-lookup"><span data-stu-id="431b2-110">Retrieving files from a SWIFTNet User</span></span>  
  
-   <span data-ttu-id="431b2-111">確認檔案接收者收到的傳遞通知</span><span class="sxs-lookup"><span data-stu-id="431b2-111">Delivery notification confirming file receipt by a receiver</span></span>  
  
-   <span data-ttu-id="431b2-112">中止的進行中的傳輸</span><span class="sxs-lookup"><span data-stu-id="431b2-112">Abort of transfers in progress</span></span>  
  
-   <span data-ttu-id="431b2-113">檔案傳輸狀態監視</span><span class="sxs-lookup"><span data-stu-id="431b2-113">File transfer state monitoring</span></span>  
  
-   <span data-ttu-id="431b2-114">並行的檔案傳輸</span><span class="sxs-lookup"><span data-stu-id="431b2-114">Concurrent file transfers</span></span>  
  
-   <span data-ttu-id="431b2-115">資料的真實性和完整性的保證</span><span class="sxs-lookup"><span data-stu-id="431b2-115">Assurance of data authenticity and integrity</span></span>  
  
-   <span data-ttu-id="431b2-116">在傳輸過程中的檔案資料的機密性</span><span class="sxs-lookup"><span data-stu-id="431b2-116">Confidentiality of file data in transit</span></span>  
  
-   <span data-ttu-id="431b2-117">不可否認性的檔案傳輸</span><span class="sxs-lookup"><span data-stu-id="431b2-117">Non-repudiation of file transfers</span></span>  
  
-   <span data-ttu-id="431b2-118">時間戳記</span><span class="sxs-lookup"><span data-stu-id="431b2-118">Time-stamping</span></span>  
  
## <a name="the-fileact-service"></a><span data-ttu-id="431b2-119">FileAct 服務</span><span class="sxs-lookup"><span data-stu-id="431b2-119">The FileAct Service</span></span>  
 <span data-ttu-id="431b2-120">FileAct 配接器的 SWIFTNet 提供安全且可靠地傳輸檔案，例如批次的結構化的財務訊息或大型報表。</span><span class="sxs-lookup"><span data-stu-id="431b2-120">The FileAct adapter for SWIFTNet provides secure and reliable transfer of files, such as batches of structured financial messages or large reports.</span></span> <span data-ttu-id="431b2-121">應用程式通常會包含重複的信用額度傳輸，例如年金或薪資付款、 證券附加價值的資訊和報告和法規報告。</span><span class="sxs-lookup"><span data-stu-id="431b2-121">Typical applications include repetitive credit transfers such as pension or salary payments, securities value-added information and reporting, and regulatory reporting.</span></span> <span data-ttu-id="431b2-122">SWIFTNet FileAct 提供各種不同的傳訊模式：</span><span class="sxs-lookup"><span data-stu-id="431b2-122">SWIFTNet FileAct offers a variety of messaging modes:</span></span>  
  
- <span data-ttu-id="431b2-123">**儲存和轉寄檔案傳輸。**</span><span class="sxs-lookup"><span data-stu-id="431b2-123">**Store-and-forward file transfer.**</span></span> <span data-ttu-id="431b2-124">SWIFTNet FileAct 儲存和轉送功能會移除不確定性和擔心您的回覆者便都在線上時傳送檔案，請將您的不便。</span><span class="sxs-lookup"><span data-stu-id="431b2-124">SWIFTNet FileAct’s store-and-forward capability removes the uncertainty and inconvenience of worrying about whether or not your correspondents are online at the time you transmit the file.</span></span> <span data-ttu-id="431b2-125">當收件者已準備好接收其傳遞檔案。</span><span class="sxs-lookup"><span data-stu-id="431b2-125">The file is delivered as soon as the recipient is ready to receive it.</span></span> <span data-ttu-id="431b2-126">如此一來，它會提供將檔案傳送到大量的回覆者便，其中有些可能會在不同時區的理想方式。</span><span class="sxs-lookup"><span data-stu-id="431b2-126">As a result, it provides an ideal way to send files to large numbers of correspondents, some of which may be in different time zones.</span></span>  
  
- <span data-ttu-id="431b2-127">**即時的檔案傳輸。**</span><span class="sxs-lookup"><span data-stu-id="431b2-127">**Real-time file transfer.**</span></span> <span data-ttu-id="431b2-128">即時傳訊提供低成本替代方式來儲存和轉送目的地為傳輸時都在線上的回覆者便的檔案。</span><span class="sxs-lookup"><span data-stu-id="431b2-128">Real-time messaging offers a lower-cost alternative to store and forward for files that are destined for correspondents that are online at the time of transmission.</span></span> <span data-ttu-id="431b2-129">如此一來，它是適合用來傳送檔案至幾個大型的回覆者便或市場的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="431b2-129">As a result it is ideal for sending files to a few large correspondents or market infrastructures.</span></span>  
  
- <span data-ttu-id="431b2-130">**擷取即時的檔案。**</span><span class="sxs-lookup"><span data-stu-id="431b2-130">**Real-time file retrieval.**</span></span> <span data-ttu-id="431b2-131">這是通常用來擷取檔案的工作站為基礎的系統內容中，並經常搭配 SWIFTNet 瀏覽互動服務。</span><span class="sxs-lookup"><span data-stu-id="431b2-131">This is an interactive service typically used to retrieve files in the context of workstation-based systems and often in conjunction with SWIFTNet Browse.</span></span> <span data-ttu-id="431b2-132">我們將支援這個模式。</span><span class="sxs-lookup"><span data-stu-id="431b2-132">We will support this mode.</span></span>  
  
  <span data-ttu-id="431b2-133">（在以檔案的方式為單位） 的選擇性 SWIFTNet FileAct 功能包括：</span><span class="sxs-lookup"><span data-stu-id="431b2-133">The optional SWIFTNet FileAct features (on a file by file basis) include:</span></span>  
  
- <span data-ttu-id="431b2-134">**訊息優先權。**</span><span class="sxs-lookup"><span data-stu-id="431b2-134">**Message priority.**</span></span> <span data-ttu-id="431b2-135">檔案傳輸在訊息中，以提供適當處理您的回覆者便可標示為 「 Urgent 」。</span><span class="sxs-lookup"><span data-stu-id="431b2-135">File transfers can be flagged as “Urgent” in the message, to allow for appropriate processing by your correspondents.</span></span>  
  
- <span data-ttu-id="431b2-136">**交貨通知 （即時和儲存和轉寄的模式）。**</span><span class="sxs-lookup"><span data-stu-id="431b2-136">**Delivery notification (real-time and store-and-forward modes).**</span></span> <span data-ttu-id="431b2-137">提供您的對應已收到您的檔案的確認。</span><span class="sxs-lookup"><span data-stu-id="431b2-137">Provides confirmation that your correspondent received your file.</span></span>  
  
- <span data-ttu-id="431b2-138">**不可否認性的發出和接收。**</span><span class="sxs-lookup"><span data-stu-id="431b2-138">**Non-repudiation of emission and reception.**</span></span> <span data-ttu-id="431b2-139">發生爭議，可讓 SWIFT 確認檔案傳輸未宣告為會發生。</span><span class="sxs-lookup"><span data-stu-id="431b2-139">In case of dispute, allows SWIFT to confirm that the file transfer did take place as claimed.</span></span>  
  
  <span data-ttu-id="431b2-140">標準的 SWIFTNet FileAct 功能包括 SWIFTNet PKI 安全性<strong>。</strong></span><span class="sxs-lookup"><span data-stu-id="431b2-140">The standard SWIFTNet FileAct features include SWIFTNet PKI security<strong>.</strong></span></span> <span data-ttu-id="431b2-141">SWIFTNet FileAct 受到 SWIFTNet PKI，並提供訊息驗證和完整性控制。</span><span class="sxs-lookup"><span data-stu-id="431b2-141">SWIFTNet FileAct is secured with SWIFTNet PKI and offers message authentication and integrity control.</span></span>  
  
  <span data-ttu-id="431b2-142">所有的訊息和交換 SWIFTNet 上的檔案進行一組常用的檢查，以確保沒有任何使用者可以略過安全性、 驗證和路由規則的平台。</span><span class="sxs-lookup"><span data-stu-id="431b2-142">All messages and files exchanged on SWIFTNet undergo a common set of checks to ensure that no user can bypass the security, validation and routing rules of the platform.</span></span> <span data-ttu-id="431b2-143">SWIFTAlliance 閘道 (SAG) 應用程式會執行這些檢查。</span><span class="sxs-lookup"><span data-stu-id="431b2-143">These checks are performed by the SWIFTAlliance Gateway (SAG) application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="431b2-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="431b2-144">See Also</span></span>  
 <span data-ttu-id="431b2-145">[開始使用 FileAct 和 InterAct 配接器](../../adapters-and-accelerators/fileact-interact/getting-started-with-the-fileact-and-interact-adapters.md) </span><span class="sxs-lookup"><span data-stu-id="431b2-145">[Getting Started with the FileAct and InterAct Adapters](../../adapters-and-accelerators/fileact-interact/getting-started-with-the-fileact-and-interact-adapters.md) </span></span>  
 <span data-ttu-id="431b2-146">[何謂 SWIFTNet？](../../adapters-and-accelerators/fileact-interact/what-is-swiftnet.md) </span><span class="sxs-lookup"><span data-stu-id="431b2-146">[What Is SWIFTNet?](../../adapters-and-accelerators/fileact-interact/what-is-swiftnet.md) </span></span>  
 [<span data-ttu-id="431b2-147">何謂 InterAct 配接器？</span><span class="sxs-lookup"><span data-stu-id="431b2-147">What Is the InterAct Adapter?</span></span>](../../adapters-and-accelerators/fileact-interact/what-is-the-interact-adapter.md)