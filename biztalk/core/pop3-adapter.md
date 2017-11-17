---
title: "POP3 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- POP3 adapters, about POP3 adapters
- authenticating, POP3 adapters
- POP3 adapters
- POP3 adapters, receive adapters
- POP3 adapters, authenticating
- receive adapters, POP3 adapters
ms.assetid: 008f7fa7-60c3-4ea3-b90d-821e4029a04c
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cbe21a3cf0e611a690cf22c88b1344926fa72744
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="pop3-adapter"></a><span data-ttu-id="333de-102">POP3 配接器</span><span class="sxs-lookup"><span data-stu-id="333de-102">POP3 Adapter</span></span>
<span data-ttu-id="333de-103">您使用「郵局通訊協定第三版」(POP3) 配接器，經由 POP3 通訊協定，將資料從裝載 POP3 信箱的伺服器擷取到執行 Microsoft BizTalk Server 的伺服器上。</span><span class="sxs-lookup"><span data-stu-id="333de-103">You use the Post Office Protocol 3 (POP3) adapter to retrieve data from a server that houses POP3 mailboxes into a server running Microsoft BizTalk Server by means of the POP3 protocol.</span></span>  
  
 <span data-ttu-id="333de-104">POP3 配接器僅由一個接收配接器組成。</span><span class="sxs-lookup"><span data-stu-id="333de-104">The POP3 adapter consists of only one adapter, a receive adapter.</span></span> <span data-ttu-id="333de-105">接收配接器控制了使用 POP3 配接器的接收位置。</span><span class="sxs-lookup"><span data-stu-id="333de-105">The receive adapter controls the receive locations that use the POP3 adapter.</span></span>  
  
 <span data-ttu-id="333de-106">本主題討論 POP3 接收配接器的工作流程。</span><span class="sxs-lookup"><span data-stu-id="333de-106">This topic discusses the workflow of the POP3 receive adapter.</span></span>  
  
 <span data-ttu-id="333de-107">**POP3 接收配接器**</span><span class="sxs-lookup"><span data-stu-id="333de-107">**POP3 Receive Adapter**</span></span>  
  
 <span data-ttu-id="333de-108">POP3 接收配接器從指定的 POP3 伺服器上指定的信箱中擷取電子郵件。</span><span class="sxs-lookup"><span data-stu-id="333de-108">The POP3 receive adapter retrieves e-mail from a specified mailbox on a specified POP3 server.</span></span> <span data-ttu-id="333de-109">依照預設，POP3 接收配接器會套用 MIME 處理到電子郵件訊息，配接器將這些訊息視為 Multipart BizTalk 訊息，下載及提交到 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="333de-109">By default, the POP3 receive adapter applies MIME processing to the e-mail messages that it downloads and submits these messages to BizTalk Server as multipart BizTalk messages.</span></span> <span data-ttu-id="333de-110">POP3 接收配接器可以透過下列格式擷取及處理電子郵件：</span><span class="sxs-lookup"><span data-stu-id="333de-110">The POP3 receive adapter can receive and process e-mail in the following formats:</span></span>  
  
-   <span data-ttu-id="333de-111">純文字</span><span class="sxs-lookup"><span data-stu-id="333de-111">Plain text</span></span>  
  
-   <span data-ttu-id="333de-112">MIME 編碼</span><span class="sxs-lookup"><span data-stu-id="333de-112">MIME encoded</span></span>  
  
-   <span data-ttu-id="333de-113">MIME 加密</span><span class="sxs-lookup"><span data-stu-id="333de-113">MIME encrypted</span></span>  
  
-   <span data-ttu-id="333de-114">MIME 編碼和簽署</span><span class="sxs-lookup"><span data-stu-id="333de-114">MIME encoded and signed</span></span>  
  
-   <span data-ttu-id="333de-115">MIME 加密和簽署</span><span class="sxs-lookup"><span data-stu-id="333de-115">MIME encrypted and signed</span></span>  
  
 <span data-ttu-id="333de-116">**POP3 接收配接器批次支援**</span><span class="sxs-lookup"><span data-stu-id="333de-116">**Batching Support for the POP3 Receive Adapter**</span></span>  
  
 <span data-ttu-id="333de-117">POP3 接收配接器不支援批次。</span><span class="sxs-lookup"><span data-stu-id="333de-117">The POP3 receive adapter does not support batching.</span></span>  
  
 <span data-ttu-id="333de-118">**POP3 伺服器驗證**</span><span class="sxs-lookup"><span data-stu-id="333de-118">**Authentication with POP3 Server**</span></span>  
  
 <span data-ttu-id="333de-119">使用 POP3 配接器時支援以下驗證方法：</span><span class="sxs-lookup"><span data-stu-id="333de-119">The following authentication methods are supported for use with the POP3 adapter:</span></span>  
  
-   <span data-ttu-id="333de-120">**基本。**</span><span class="sxs-lookup"><span data-stu-id="333de-120">**Basic.**</span></span> <span data-ttu-id="333de-121">POP3 伺服器利用使用者提供認證以進行驗證。</span><span class="sxs-lookup"><span data-stu-id="333de-121">The POP3 server uses user provided credentials for authentication.</span></span>  <span data-ttu-id="333de-122">這些認證以純文字格式傳送。</span><span class="sxs-lookup"><span data-stu-id="333de-122">These credentials are sent in clear text.</span></span>  
  
-   <span data-ttu-id="333de-123">**摘要 (APOP)。**</span><span class="sxs-lookup"><span data-stu-id="333de-123">**Digest (APOP).**</span></span> <span data-ttu-id="333de-124">POP3 伺服器利用摘要字串進行驗證。</span><span class="sxs-lookup"><span data-stu-id="333de-124">The POP3 server uses a digest string for authentication.</span></span>  
  
-   <span data-ttu-id="333de-125">**安全密碼驗證 (SPA)。**</span><span class="sxs-lookup"><span data-stu-id="333de-125">**Secure Password Authentication (SPA).**</span></span> <span data-ttu-id="333de-126">POP3 伺服器利用目前的程序認證進行驗證。</span><span class="sxs-lookup"><span data-stu-id="333de-126">The POP3 server uses current process credentials for authentication.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="333de-127">本節內容</span><span class="sxs-lookup"><span data-stu-id="333de-127">In This Section</span></span>  
  
-   [<span data-ttu-id="333de-128">何謂 POP3 配接器？</span><span class="sxs-lookup"><span data-stu-id="333de-128">What Is the POP3 Adapter?</span></span>](../core/what-is-the-pop3-adapter.md)  
  
-   [<span data-ttu-id="333de-129">設定 POP3 配接器</span><span class="sxs-lookup"><span data-stu-id="333de-129">Configuring the POP3 Adapter</span></span>](../core/configuring-the-pop3-adapter.md)  
  
-   [<span data-ttu-id="333de-130">逐步解說： 建立使用 POP3 配接器的 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="333de-130">Walkthrough: Creating a BizTalk Application That Uses the POP3 Adapter</span></span>](../core/walkthrough-creating-a-biztalk-application-that-uses-the-pop3-adapter.md)  
  
-   [<span data-ttu-id="333de-131">處理多部分訊息，POP3 配接器</span><span class="sxs-lookup"><span data-stu-id="333de-131">Processing Multi Part Messages with the POP3 Adapter</span></span>](../core/processing-multi-part-messages-with-the-pop3-adapter.md)