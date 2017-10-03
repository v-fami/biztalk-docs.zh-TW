---
title: "FileAct 配接器即時的端對端原型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8591120-7259-49cb-90ac-954d8be226ed
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c95e52d4fbd5ec0df8ee580583f429ffe9e0f08d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="fileact-adapter-real-time-end-to-end-primitives"></a><span data-ttu-id="04033-102">FileAct 配接器即時的端對端原型</span><span class="sxs-lookup"><span data-stu-id="04033-102">FileAct Adapter Real-Time End-to-End Primitives</span></span>
<span data-ttu-id="04033-103">SWIFTNet 原型是一組應用程式與 SWIFTNet 連結 (SNL) 之間交換的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="04033-103">SWIFTNet primitives are a pair of XML documents exchanged between the application and SWIFTNet Link (SNL).</span></span> <span data-ttu-id="04033-104">針對每個端對端基本，那里兩個基本項目 – 一個在用戶端 （或傳送） 端，在伺服器上的另一個版本 （或接收） 側邊。</span><span class="sxs-lookup"><span data-stu-id="04033-104">For each end-to-end primitive, there are two versions of the primitive – one at the client (or send) side and one at the server (or receive) side.</span></span> <span data-ttu-id="04033-105">這包含四個訊息總數： 放置檔案的基本類型、 取得檔案的基本類型和每個傳送傳遞通知。</span><span class="sxs-lookup"><span data-stu-id="04033-105">This comprises a total of four messages: Put File primitive, Get File primitive, and a Send Delivery Notification for each.</span></span>  
  
 <span data-ttu-id="04033-106">下圖顯示 FileAct 端對端原型。</span><span class="sxs-lookup"><span data-stu-id="04033-106">The following figure shows the FileAct end-to-end primitives.</span></span>  
  
 <span data-ttu-id="04033-107">![FileAct 端 &#45; 至 &#45; 端點基本型別](../../adapters-and-accelerators/fileact-interact/media/6e3520cc-9ec4-445c-9114-c7cb760c1068.gif "6e3520cc-9ec4-445c-9114-c7cb760c1068")</span><span class="sxs-lookup"><span data-stu-id="04033-107">![FileAct end&#45;to&#45;end primitives](../../adapters-and-accelerators/fileact-interact/media/6e3520cc-9ec4-445c-9114-c7cb760c1068.gif "6e3520cc-9ec4-445c-9114-c7cb760c1068")</span></span>  
  
## <a name="put-file"></a><span data-ttu-id="04033-108">將檔案放</span><span class="sxs-lookup"><span data-stu-id="04033-108">Put File</span></span>  
 <span data-ttu-id="04033-109">應用程式初始化放置檔案將檔案傳送至另一個 SWIFTNet 使用者的檔案系統基本項目。</span><span class="sxs-lookup"><span data-stu-id="04033-109">An application initiates the Put File primitive to send a file to the file system of another SWIFTNet user.</span></span> <span data-ttu-id="04033-110">為端對端函式中，沒有用戶端和伺服器端將檔案基本型別。</span><span class="sxs-lookup"><span data-stu-id="04033-110">As an end-to-end function, there are both client-side and server side Put File primitives.</span></span> <span data-ttu-id="04033-111">這些一起合作完成檔案傳輸。</span><span class="sxs-lookup"><span data-stu-id="04033-111">These collaborate together to successfully complete a file transfer.</span></span>  
  
 <span data-ttu-id="04033-112">每個這類的共同作業會傳送到單一檔案。</span><span class="sxs-lookup"><span data-stu-id="04033-112">Each such collaboration sends a single file.</span></span> <span data-ttu-id="04033-113">可能會以平行方式執行多個放置檔案的基本類型。</span><span class="sxs-lookup"><span data-stu-id="04033-113">Multiple Put File primitives may be exercised in parallel.</span></span>  
  
## <a name="get-file"></a><span data-ttu-id="04033-114">取得檔案</span><span class="sxs-lookup"><span data-stu-id="04033-114">Get File</span></span>  
 <span data-ttu-id="04033-115">應用程式初始化取得檔案基本項目從另一個 SWIFTNet 使用者的檔案系統中擷取。</span><span class="sxs-lookup"><span data-stu-id="04033-115">An application initiates the Get File primitive to retrieve a file from the file system of another SWIFTNet user.</span></span> <span data-ttu-id="04033-116">為端對端函式中，沒有用戶端和伺服器端取得檔案的原始物件。</span><span class="sxs-lookup"><span data-stu-id="04033-116">As an end-to-end function, there are both client-side and server-side Get File primitives.</span></span> <span data-ttu-id="04033-117">這些一起合作完成檔案傳輸。</span><span class="sxs-lookup"><span data-stu-id="04033-117">These collaborate together to successfully complete a file transfer.</span></span>  
  
 <span data-ttu-id="04033-118">每個這類的共同作業會擷取單一檔案。</span><span class="sxs-lookup"><span data-stu-id="04033-118">Each such collaboration retrieves a single file.</span></span> <span data-ttu-id="04033-119">可能會以平行方式執行多個取得檔案的基本類型。</span><span class="sxs-lookup"><span data-stu-id="04033-119">Multiple Get File primitives may be exercised in parallel.</span></span>  
  
## <a name="send-delivery-notification"></a><span data-ttu-id="04033-120">傳遞通知</span><span class="sxs-lookup"><span data-stu-id="04033-120">Send Delivery Notification</span></span>  
 <span data-ttu-id="04033-121">每個將檔案和每個基本的取得檔案有選擇讓接收端會傳回傳遞通知相關的檔案傳輸的檔案要求的傳送端。</span><span class="sxs-lookup"><span data-stu-id="04033-121">Every Put File and every Get File primitive has the option of having the sending side of the file request that the receiving side return a delivery notification related to the file transfer.</span></span> <span data-ttu-id="04033-122">對於放置檔案的基本操作，要求訊息會包含傳遞通知的要求。</span><span class="sxs-lookup"><span data-stu-id="04033-122">For a Put File primitive, the request message contains the request for a delivery notification.</span></span>  
  
 <span data-ttu-id="04033-123">如果是取得檔案基本，回應訊息會包含傳遞通知的要求。</span><span class="sxs-lookup"><span data-stu-id="04033-123">In the case of a Get File primitive, the response message contains the request for a delivery notification.</span></span>  
  
 <span data-ttu-id="04033-124">在任一情況下，（比方說，在上一步 office 系統），確認檔案已收到的完整 （使用其中一個要檢查傳送到達的狀態已完成的狀態基本型別），以及檔案已經適當地安全儲存後接收應用程式分別會執行傳遞通知傳回給傳送者傳遞正面確認基本項目。</span><span class="sxs-lookup"><span data-stu-id="04033-124">In either case, after verifying that the file was received in its entirety (by exercising one of the status primitives to check that the transfer reaches the state Completed) and that the file has been adequately safe stored (for example, on a back-office system), the receiving application separately exercises the Delivery Notification primitive to return a positive confirmation of delivery to the sender.</span></span> <span data-ttu-id="04033-125">為端對端函式，沒有用戶端和伺服器端傳遞通知基本項目。</span><span class="sxs-lookup"><span data-stu-id="04033-125">As an end-to-end function, there are both client-side and server-side Delivery Notification primitives.</span></span> <span data-ttu-id="04033-126">這些一起合作完成檔案傳遞通知。</span><span class="sxs-lookup"><span data-stu-id="04033-126">These collaborate together to successfully complete a file delivery notification.</span></span>  
  
 <span data-ttu-id="04033-127">傳遞通知，需要服務設計工具來建立與強制寄件者和接收者的檔案之間的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="04033-127">Delivery notification requires the service designer to establish and enforce a protocol between the senders and receivers of files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04033-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04033-128">See Also</span></span>  
 <span data-ttu-id="04033-129">[FileAct 配接器架構](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="04033-129">[FileAct Adapter Architecture](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md) </span></span>  
 <span data-ttu-id="04033-130">[FileAct 配接器即時區域基本型別](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md) </span><span class="sxs-lookup"><span data-stu-id="04033-130">[FileAct Adapter Real-Time Local Primitives](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md) </span></span>  
 <span data-ttu-id="04033-131">[FileAct 配接器儲存與轉送](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="04033-131">[FileAct Adapter Store and Forward](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md) </span></span>  
 <span data-ttu-id="04033-132">[FileAct 配接器安全性架構](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="04033-132">[FileAct Adapter Security Architecture](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md) </span></span>  
 <span data-ttu-id="04033-133">[FileAct 配接器檔案和傳輸識別碼](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md) </span><span class="sxs-lookup"><span data-stu-id="04033-133">[FileAct Adapter File and Transfer Identification](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md) </span></span>  
 <span data-ttu-id="04033-134">[FileAct 配接器支援資訊傳輸](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md) </span><span class="sxs-lookup"><span data-stu-id="04033-134">[FileAct Adapter Supporting Information Transfer](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md) </span></span>  
 <span data-ttu-id="04033-135">[FileAct 配接器傳遞通知](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md) </span><span class="sxs-lookup"><span data-stu-id="04033-135">[FileAct Adapter Delivery Notification](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md) </span></span>  
 [<span data-ttu-id="04033-136">FileAct 配接器狀態監視</span><span class="sxs-lookup"><span data-stu-id="04033-136">FileAct Adapter Status Monitoring</span></span>](../../adapters-and-accelerators/fileact-interact/fileact-adapter-status-monitoring.md)