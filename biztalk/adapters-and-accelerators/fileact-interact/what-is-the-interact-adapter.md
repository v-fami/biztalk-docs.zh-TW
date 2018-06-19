---
title: 什麼是互動配接器？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a09063df-c6c4-41b9-96a1-e5059777fa72
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25877b95a440faef802d3d2ba7861687d7e4b108
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224750"
---
# <a name="what-is-the-interact-adapter"></a><span data-ttu-id="15092-103">什麼是互動配接器？</span><span class="sxs-lookup"><span data-stu-id="15092-103">What Is the InterAct Adapter?</span></span>
<span data-ttu-id="15092-104">SWIFTNet 互動配接器會提供 BizTalk Server 與 SWIFT 保護 IP 網路 (SIPN) 之間的連線傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="15092-104">The InterAct Adapter for SWIFTNet provides connectivity between BizTalk Server and the SWIFT Secure IP Network (SIPN) for the transfer of messages.</span></span> <span data-ttu-id="15092-105">SIPN 傳輸連接金融機構、 財務產業的基礎結構和客戶在安全私人網路上的訊息和檔案。</span><span class="sxs-lookup"><span data-stu-id="15092-105">The SIPN transfers messages and files over a secure private network which interconnects financial institutions, financial industry infrastructures, and customers.</span></span> <span data-ttu-id="15092-106">InterAct 配接器會使用 SWIFTNet 連結 (SNL) 應用程式開發介面 (API) s 連接到 SIPN。</span><span class="sxs-lookup"><span data-stu-id="15092-106">The InterAct adapter uses the SWIFTNet Link (SNL) application programming interface (API)s to connect to the SIPN.</span></span>  
  
 <span data-ttu-id="15092-107">SWIFTNet 互動提供安全、 可靠的個別結構化財務訊息交換。</span><span class="sxs-lookup"><span data-stu-id="15092-107">SWIFTNet InterAct provides secure and reliable exchange of individual structured financial messages.</span></span> <span data-ttu-id="15092-108">SWIFT 客戶傳訊需求不同客戶的但也從訊息至訊息。</span><span class="sxs-lookup"><span data-stu-id="15092-108">SWIFT customers’ messaging requirements vary from customer to customer but also from message to message.</span></span>  
  
 <span data-ttu-id="15092-109">它支援下列功能：</span><span class="sxs-lookup"><span data-stu-id="15092-109">It supports the following functionality:</span></span>  
  
-   <span data-ttu-id="15092-110">PKI 安全性</span><span class="sxs-lookup"><span data-stu-id="15092-110">PKI security</span></span>  
  
-   <span data-ttu-id="15092-111">訊息驗證</span><span class="sxs-lookup"><span data-stu-id="15092-111">Message validation</span></span>  
  
-   <span data-ttu-id="15092-112">可設定的中央路由</span><span class="sxs-lookup"><span data-stu-id="15092-112">Configurable central routing</span></span>  
  
-   <span data-ttu-id="15092-113">訊息優先順序</span><span class="sxs-lookup"><span data-stu-id="15092-113">Message priority</span></span>  
  
-   <span data-ttu-id="15092-114">存放與轉寄訊息的傳遞通知</span><span class="sxs-lookup"><span data-stu-id="15092-114">Delivery notification for store and forward messages</span></span>  
  
-   <span data-ttu-id="15092-115">不可否認性的發出和接收。</span><span class="sxs-lookup"><span data-stu-id="15092-115">Non-repudiation of emission and receipt.</span></span>  
  
 <span data-ttu-id="15092-116">您互動的介面卡的 SWIFTNet 搭配使用外部提供的應用程式使用互動功能。</span><span class="sxs-lookup"><span data-stu-id="15092-116">You use the InterAct Adapter for SWIFTNet with externally supplied applications to utilize the features of InterAct.</span></span> <span data-ttu-id="15092-117">此配接器不了解將傳輸，並不會稽核也不驗證訊息的內容，除了交換基本型別之訊息的內容。</span><span class="sxs-lookup"><span data-stu-id="15092-117">This adapter has no knowledge of the contents of the messages to be transferred, and will not audit nor validate the contents of the messages, except for the exchange primitives.</span></span>  
  
## <a name="interact-message-exchange"></a><span data-ttu-id="15092-118">InterAct 訊息交換</span><span class="sxs-lookup"><span data-stu-id="15092-118">InterAct Message Exchange</span></span>  
 <span data-ttu-id="15092-119">SWIFTNet 互動提供安全、 可靠的個別結構化財務訊息交換。</span><span class="sxs-lookup"><span data-stu-id="15092-119">SWIFTNet InterAct provides secure and reliable exchange of individual structured financial messages.</span></span> <span data-ttu-id="15092-120">SWIFT 客戶傳訊需求不同客戶的但也從訊息至訊息。</span><span class="sxs-lookup"><span data-stu-id="15092-120">SWIFT customers’ messaging requirements vary from customer to customer but also from message to message.</span></span> <span data-ttu-id="15092-121">SWIFTNet 互動提供廣泛的電信模式：</span><span class="sxs-lookup"><span data-stu-id="15092-121">SWIFTNet InterAct offers you a broad range of telecommunication modes:</span></span>  
  
-   <span data-ttu-id="15092-122">**儲存和轉送訊息。**</span><span class="sxs-lookup"><span data-stu-id="15092-122">**Store-and-forward messaging.**</span></span> <span data-ttu-id="15092-123">SWIFTNet 互動的儲存和轉送功能被設計用於目的地為大量的對應，許多使用者可能無法線上傳輸時訊息。</span><span class="sxs-lookup"><span data-stu-id="15092-123">SWIFTNet InterAct’s store-and-forward capability is designed for messages destined for a large number of correspondents, many of whom may not be online at the time of transmission.</span></span> <span data-ttu-id="15092-124">它會移除的不確定性和的擔心您的對應為線上傳送訊息時所造成的不便。</span><span class="sxs-lookup"><span data-stu-id="15092-124">It removes the uncertainty and inconvenience of worrying about whether or not your correspondents are on-line at the time you send the message.</span></span> <span data-ttu-id="15092-125">收件者已準備好接收它之後儘速傳遞訊息。</span><span class="sxs-lookup"><span data-stu-id="15092-125">The message is delivered as soon as the recipient is ready to receive it.</span></span> <span data-ttu-id="15092-126">如此一來，它會提供將個別的指示、 確認及報表傳送到大量的對應，其中有些可能會在不同時區的理想方式。</span><span class="sxs-lookup"><span data-stu-id="15092-126">As a result, it provides an ideal way to send individual instructions, confirmations and reports to large numbers of correspondents, some of which may be in different time zones.</span></span>  
  
-   <span data-ttu-id="15092-127">**即時訊息。**</span><span class="sxs-lookup"><span data-stu-id="15092-127">**Real-time messaging.**</span></span> <span data-ttu-id="15092-128">即時訊息提供低成本的替代方式來儲存和轉送訊息目的地為傳輸的時間在線上的對應。</span><span class="sxs-lookup"><span data-stu-id="15092-128">Real-time messaging offers a low-cost alternative to store and forward for messages which are destined for correspondents that are online at the time of transmission.</span></span> <span data-ttu-id="15092-129">如此一來，很適合用來傳送個別的指示，確認和報表，少數的大型對應或行銷的基礎結構訊息。</span><span class="sxs-lookup"><span data-stu-id="15092-129">As a result, it is ideal for sending individual instructions, confirmations and reports, to a few large correspondents or for messages to market infrastructures.</span></span>  
  
 <span data-ttu-id="15092-130">（根據訊息的訊息） 的選擇性 SWIFTNet 互動功能包括：</span><span class="sxs-lookup"><span data-stu-id="15092-130">The optional SWIFTNet InterAct features (on a message by message basis) include:</span></span>  
  
-   <span data-ttu-id="15092-131">**訊息優先順序。**</span><span class="sxs-lookup"><span data-stu-id="15092-131">**Message priority.**</span></span> <span data-ttu-id="15092-132">訊息可以標示為 「 緊急 」，在訊息中，以提供適當處理您的對應。</span><span class="sxs-lookup"><span data-stu-id="15092-132">Messages can be flagged as “Urgent” in the message, to allow for appropriate processing by your correspondents.</span></span>  
  
-   <span data-ttu-id="15092-133">**傳遞通知 （儲存和轉送模式）。**</span><span class="sxs-lookup"><span data-stu-id="15092-133">**Delivery notification (store-and-forward mode).**</span></span> <span data-ttu-id="15092-134">提供您的對應已收到訊息的確認</span><span class="sxs-lookup"><span data-stu-id="15092-134">Provides confirmation that your correspondent received your message</span></span>  
  
-   <span data-ttu-id="15092-135">**不可否認性的發出和接收。**</span><span class="sxs-lookup"><span data-stu-id="15092-135">**Non-repudiation of emission and reception.**</span></span> <span data-ttu-id="15092-136">發生爭議，可讓 SWIFT 確認訊息交換未宣告為會發生。</span><span class="sxs-lookup"><span data-stu-id="15092-136">In case of dispute, allows SWIFT to confirm that the message exchange did take place as claimed.</span></span>  
  
 <span data-ttu-id="15092-137">標準的 SWIFTNet 互動功能包括 SWIFTNet PKI 安全性。</span><span class="sxs-lookup"><span data-stu-id="15092-137">The standard SWIFTNet InterAct features include SWIFTNet PKI security.</span></span> <span data-ttu-id="15092-138">SWIFTNet FileAct 受到 SWIFTNet PKI，並提供訊息驗證和完整性控制。</span><span class="sxs-lookup"><span data-stu-id="15092-138">SWIFTNet FileAct is secured with SWIFTNet PKI and offers message authentication and integrity control.</span></span>  
  
 <span data-ttu-id="15092-139">所有的訊息和檔案上 SWIFTNet 交換接受一組常用的檢查，以確保沒有任何使用者可以略過安全性、 驗證和平台的路由規則。</span><span class="sxs-lookup"><span data-stu-id="15092-139">All messages and files exchanged on SWIFTNet undergo a common set of checks to ensure that no user can bypass the security, validation and routing rules of the platform.</span></span> <span data-ttu-id="15092-140">SWIFTAlliance 閘道 (SAG) 應用程式會執行這些檢查。</span><span class="sxs-lookup"><span data-stu-id="15092-140">These checks are performed by the SWIFTAlliance Gateway (SAG) application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15092-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15092-141">See Also</span></span>  
 <span data-ttu-id="15092-142">[開始使用 FileAct 和 InterAct Adapters](../../adapters-and-accelerators/fileact-interact/getting-started-with-the-fileact-and-interact-adapters.md) </span><span class="sxs-lookup"><span data-stu-id="15092-142">[Getting Started with the FileAct and InterAct Adapters](../../adapters-and-accelerators/fileact-interact/getting-started-with-the-fileact-and-interact-adapters.md) </span></span>  
 <span data-ttu-id="15092-143">[SWIFTNet 是什麼？](../../adapters-and-accelerators/fileact-interact/what-is-swiftnet.md) </span><span class="sxs-lookup"><span data-stu-id="15092-143">[What Is SWIFTNet?](../../adapters-and-accelerators/fileact-interact/what-is-swiftnet.md) </span></span>  
 [<span data-ttu-id="15092-144">FileAct 配接器為何？</span><span class="sxs-lookup"><span data-stu-id="15092-144">What Is the FileAct Adapter?</span></span>](../../adapters-and-accelerators/fileact-interact/what-is-the-fileact-adapter.md)