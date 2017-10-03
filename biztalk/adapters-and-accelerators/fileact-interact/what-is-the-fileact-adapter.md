---
title: "FileAct 配接器為何？ | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05ec8f1e-57f9-4e2d-ab8b-22b5c4b28055
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62b83fc723bbebce857eb442384b14179c1072ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-fileact-adapter"></a><span data-ttu-id="be214-103">FileAct 配接器為何？</span><span class="sxs-lookup"><span data-stu-id="be214-103">What Is the FileAct Adapter?</span></span>
<span data-ttu-id="be214-104">SWIFTNet 的 FileAct 配接器提供 BizTalk Server 與協會之間連線的全球 Interbank 財務 Telecommunication (SWIFT) 保護 IP 網路 (SIPN) 傳輸檔案。</span><span class="sxs-lookup"><span data-stu-id="be214-104">The FileAct adapter for SWIFTNet provides connectivity between BizTalk Server and the Society for Worldwide Interbank Financial Telecommunication (SWIFT) Secure IP Network (SIPN) for the transfer of files.</span></span> <span data-ttu-id="be214-105">SIPN 傳輸透過安全的私人網路連接金融機構、 財務產業的基礎結構和客戶的訊息和檔案。</span><span class="sxs-lookup"><span data-stu-id="be214-105">The SIPN transfers messages and files over a secure private network which connects financial institutions, financial industry infrastructures, and customers.</span></span> <span data-ttu-id="be214-106">FileAct 配接器會使用 SWIFTNet 連結 (SNL) 應用程式開發介面 (API) s 連接到 SIPN。</span><span class="sxs-lookup"><span data-stu-id="be214-106">The FileAct adapter uses the SWIFTNet Link (SNL) application programming interface (API)s to connect to the SIPN.</span></span>  
  
 <span data-ttu-id="be214-107">FileAct 配接器的 SWIFT 參與者會安全地提供一個機制，並可靠地交換檔案和這些檔案的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="be214-107">The FileAct adapter provides a mechanism for SWIFT participants to securely and reliably exchange files and information pertaining to those files.</span></span> <span data-ttu-id="be214-108">它支援下列功能：</span><span class="sxs-lookup"><span data-stu-id="be214-108">It supports the following functionality:</span></span>  
  
-   <span data-ttu-id="be214-109">將檔案傳送到 SWIFTNet 使用者</span><span class="sxs-lookup"><span data-stu-id="be214-109">Sending files to a SWIFTNet User</span></span>  
  
-   <span data-ttu-id="be214-110">SWIFTNet 使用者從擷取檔案</span><span class="sxs-lookup"><span data-stu-id="be214-110">Retrieving files from a SWIFTNet User</span></span>  
  
-   <span data-ttu-id="be214-111">確認收件者所接收的檔案傳遞通知</span><span class="sxs-lookup"><span data-stu-id="be214-111">Delivery notification confirming file receipt by a receiver</span></span>  
  
-   <span data-ttu-id="be214-112">中止的傳輸正在進行中</span><span class="sxs-lookup"><span data-stu-id="be214-112">Abort of transfers in progress</span></span>  
  
-   <span data-ttu-id="be214-113">檔案傳輸狀態監視</span><span class="sxs-lookup"><span data-stu-id="be214-113">File transfer state monitoring</span></span>  
  
-   <span data-ttu-id="be214-114">並行的檔案傳輸</span><span class="sxs-lookup"><span data-stu-id="be214-114">Concurrent file transfers</span></span>  
  
-   <span data-ttu-id="be214-115">資料的真實性和完整性 assurance</span><span class="sxs-lookup"><span data-stu-id="be214-115">Assurance of data authenticity and integrity</span></span>  
  
-   <span data-ttu-id="be214-116">在傳輸過程中的檔案資料的機密性</span><span class="sxs-lookup"><span data-stu-id="be214-116">Confidentiality of file data in transit</span></span>  
  
-   <span data-ttu-id="be214-117">不可否認性的檔案傳輸</span><span class="sxs-lookup"><span data-stu-id="be214-117">Non-repudiation of file transfers</span></span>  
  
-   <span data-ttu-id="be214-118">時間戳記</span><span class="sxs-lookup"><span data-stu-id="be214-118">Time-stamping</span></span>  
  
## <a name="the-fileact-service"></a><span data-ttu-id="be214-119">FileAct 服務</span><span class="sxs-lookup"><span data-stu-id="be214-119">The FileAct Service</span></span>  
 <span data-ttu-id="be214-120">SWIFTNet 的 FileAct 配接器提供的檔案，例如批次結構化之財務訊息或大型報表的安全而可靠的傳輸。</span><span class="sxs-lookup"><span data-stu-id="be214-120">The FileAct adapter for SWIFTNet provides secure and reliable transfer of files, such as batches of structured financial messages or large reports.</span></span> <span data-ttu-id="be214-121">一般應用程式包含重複的信用額度傳送，例如 pension 或薪資付款、 股票所分配到加值資訊和報表，以及設定報告的法規。</span><span class="sxs-lookup"><span data-stu-id="be214-121">Typical applications include repetitive credit transfers such as pension or salary payments, securities value-added information and reporting, and regulatory reporting.</span></span> <span data-ttu-id="be214-122">SWIFTNet FileAct 提供各種不同的訊息模式：</span><span class="sxs-lookup"><span data-stu-id="be214-122">SWIFTNet FileAct offers a variety of messaging modes:</span></span>  
  
-   <span data-ttu-id="be214-123">**儲存和轉送的檔案傳輸。**</span><span class="sxs-lookup"><span data-stu-id="be214-123">**Store-and-forward file transfer.**</span></span> <span data-ttu-id="be214-124">SWIFTNet FileAct 儲存和轉送功能中移除的不確定性和擔心對應您的時間在線上傳送檔案，您的不便。</span><span class="sxs-lookup"><span data-stu-id="be214-124">SWIFTNet FileAct’s store-and-forward capability removes the uncertainty and inconvenience of worrying about whether or not your correspondents are online at the time you transmit the file.</span></span> <span data-ttu-id="be214-125">收件者已準備好接收它之後儘速傳遞檔案。</span><span class="sxs-lookup"><span data-stu-id="be214-125">The file is delivered as soon as the recipient is ready to receive it.</span></span> <span data-ttu-id="be214-126">如此一來，它會提供將檔案傳送到大量的對應，其中有些可能會在不同時區的理想方式。</span><span class="sxs-lookup"><span data-stu-id="be214-126">As a result, it provides an ideal way to send files to large numbers of correspondents, some of which may be in different time zones.</span></span>  
  
-   <span data-ttu-id="be214-127">**即時的檔案傳輸。**</span><span class="sxs-lookup"><span data-stu-id="be214-127">**Real-time file transfer.**</span></span> <span data-ttu-id="be214-128">即時訊息提供低成本的替代方式來儲存和轉送的檔案傳輸的時間在線上的相關者為目標。</span><span class="sxs-lookup"><span data-stu-id="be214-128">Real-time messaging offers a lower-cost alternative to store and forward for files that are destined for correspondents that are online at the time of transmission.</span></span> <span data-ttu-id="be214-129">如此一來會適用於幾個大型的對應或市場基礎結構傳送檔案。</span><span class="sxs-lookup"><span data-stu-id="be214-129">As a result it is ideal for sending files to a few large correspondents or market infrastructures.</span></span>  
  
-   <span data-ttu-id="be214-130">**即時檔案擷取。**</span><span class="sxs-lookup"><span data-stu-id="be214-130">**Real-time file retrieval.**</span></span> <span data-ttu-id="be214-131">這是通常用來擷取檔案的工作站系統內容中，且通常搭配 SWIFTNet 瀏覽互動服務。</span><span class="sxs-lookup"><span data-stu-id="be214-131">This is an interactive service typically used to retrieve files in the context of workstation-based systems and often in conjunction with SWIFTNet Browse.</span></span> <span data-ttu-id="be214-132">我們將會支援這個模式。</span><span class="sxs-lookup"><span data-stu-id="be214-132">We will support this mode.</span></span>  
  
 <span data-ttu-id="be214-133">（根據檔案的檔案） 的選擇性 SWIFTNet FileAct 功能包括：</span><span class="sxs-lookup"><span data-stu-id="be214-133">The optional SWIFTNet FileAct features (on a file by file basis) include:</span></span>  
  
-   <span data-ttu-id="be214-134">**訊息優先順序。**</span><span class="sxs-lookup"><span data-stu-id="be214-134">**Message priority.**</span></span> <span data-ttu-id="be214-135">檔案傳輸可以標示為 「 緊急 」，在訊息中，以提供適當處理您的對應。</span><span class="sxs-lookup"><span data-stu-id="be214-135">File transfers can be flagged as “Urgent” in the message, to allow for appropriate processing by your correspondents.</span></span>  
  
-   <span data-ttu-id="be214-136">**傳遞通知 （即時和儲存和轉送模式）。**</span><span class="sxs-lookup"><span data-stu-id="be214-136">**Delivery notification (real-time and store-and-forward modes).**</span></span> <span data-ttu-id="be214-137">提供您的對應已收到您的檔案的確認。</span><span class="sxs-lookup"><span data-stu-id="be214-137">Provides confirmation that your correspondent received your file.</span></span>  
  
-   <span data-ttu-id="be214-138">**不可否認性的發出和接收。**</span><span class="sxs-lookup"><span data-stu-id="be214-138">**Non-repudiation of emission and reception.**</span></span> <span data-ttu-id="be214-139">發生爭議，可讓 SWIFT 確認檔案傳送未宣告為會發生。</span><span class="sxs-lookup"><span data-stu-id="be214-139">In case of dispute, allows SWIFT to confirm that the file transfer did take place as claimed.</span></span>  
  
 <span data-ttu-id="be214-140">標準的 SWIFTNet FileAct 功能包括 SWIFTNet PKI 安全性**。**</span><span class="sxs-lookup"><span data-stu-id="be214-140">The standard SWIFTNet FileAct features include SWIFTNet PKI security**.**</span></span> <span data-ttu-id="be214-141">SWIFTNet FileAct 受到 SWIFTNet PKI，並提供訊息驗證和完整性控制。</span><span class="sxs-lookup"><span data-stu-id="be214-141">SWIFTNet FileAct is secured with SWIFTNet PKI and offers message authentication and integrity control.</span></span>  
  
 <span data-ttu-id="be214-142">所有的訊息和檔案上 SWIFTNet 交換接受一組常用的檢查，以確保沒有任何使用者可以略過安全性、 驗證和平台的路由規則。</span><span class="sxs-lookup"><span data-stu-id="be214-142">All messages and files exchanged on SWIFTNet undergo a common set of checks to ensure that no user can bypass the security, validation and routing rules of the platform.</span></span> <span data-ttu-id="be214-143">SWIFTAlliance 閘道 (SAG) 應用程式會執行這些檢查。</span><span class="sxs-lookup"><span data-stu-id="be214-143">These checks are performed by the SWIFTAlliance Gateway (SAG) application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be214-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be214-144">See Also</span></span>  
 <span data-ttu-id="be214-145">[開始使用 FileAct 和 InterAct Adapters](../../adapters-and-accelerators/fileact-interact/getting-started-with-the-fileact-and-interact-adapters.md) </span><span class="sxs-lookup"><span data-stu-id="be214-145">[Getting Started with the FileAct and InterAct Adapters](../../adapters-and-accelerators/fileact-interact/getting-started-with-the-fileact-and-interact-adapters.md) </span></span>  
 <span data-ttu-id="be214-146">[SWIFTNet 是什麼？](../../adapters-and-accelerators/fileact-interact/what-is-swiftnet.md) </span><span class="sxs-lookup"><span data-stu-id="be214-146">[What Is SWIFTNet?](../../adapters-and-accelerators/fileact-interact/what-is-swiftnet.md) </span></span>  
 [<span data-ttu-id="be214-147">什麼是互動配接器？</span><span class="sxs-lookup"><span data-stu-id="be214-147">What Is the InterAct Adapter?</span></span>](../../adapters-and-accelerators/fileact-interact/what-is-the-interact-adapter.md)