---
title: 收到的 AS2 訊息不包含 AS2-To 標頭 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 343a9b41-fcd9-4508-ac65-9b6e05ec6496
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a2390406d202bebd74f45efd84fd3aae6db1137
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983463"
---
# <a name="an-as2-message-was-received-that-did-not-contain-the-as2-to-header"></a><span data-ttu-id="21ebd-102">收到的 AS2 訊息不包含 AS2-To 標頭</span><span class="sxs-lookup"><span data-stu-id="21ebd-102">An AS2 message was received that did not contain the AS2-To header</span></span>
## <a name="details"></a><span data-ttu-id="21ebd-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="21ebd-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="21ebd-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="21ebd-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="21ebd-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="21ebd-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="21ebd-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="21ebd-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="21ebd-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="21ebd-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="21ebd-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="21ebd-108"> EDI</span></span> |
|    <span data-ttu-id="21ebd-109">元件</span><span class="sxs-lookup"><span data-stu-id="21ebd-109">Component</span></span>    |                                       <span data-ttu-id="21ebd-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="21ebd-110">AS2 Engine</span></span>                                       |
|  <span data-ttu-id="21ebd-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="21ebd-111">Symbolic Name</span></span>  |                                           -                                            |
|  <span data-ttu-id="21ebd-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="21ebd-112">Message Text</span></span>   |           <span data-ttu-id="21ebd-113">收到的 AS2 訊息不包含 AS2-To 標頭</span><span class="sxs-lookup"><span data-stu-id="21ebd-113">An AS2 message was received that did not contain the AS2-To header</span></span>           |
  
## <a name="explanation"></a><span data-ttu-id="21ebd-114">說明</span><span class="sxs-lookup"><span data-stu-id="21ebd-114">Explanation</span></span>  
 <span data-ttu-id="21ebd-115">這個錯誤/警告/資訊事件表示 BizTalk Server 無法處理內送 AS2 訊息，因為訊息不包含 AS2-To 標頭指出訊息的來源。</span><span class="sxs-lookup"><span data-stu-id="21ebd-115">This Error/Warning/Information event indicates BizTalk Server could not process the incoming AS2 message because the message did not contain an AS2-To header indicating the source of the message.</span></span> <span data-ttu-id="21ebd-116">AS2 訊息必須具有 AS2-To 標頭。</span><span class="sxs-lookup"><span data-stu-id="21ebd-116">An AS2 message must have an AS2-To header.</span></span> <span data-ttu-id="21ebd-117">將會擱置訊息，如果它不需要 AS2-To 標頭。</span><span class="sxs-lookup"><span data-stu-id="21ebd-117">The message will be suspended if it does not have an AS2-To header.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="21ebd-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="21ebd-118">User Action</span></span>  
 <span data-ttu-id="21ebd-119">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="21ebd-119">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="21ebd-120">請確定傳送合作對象將 AS2-To 標頭與 AS2 訊息，再將它傳送的 HTTP、 AS2 和 MIME 標頭。</span><span class="sxs-lookup"><span data-stu-id="21ebd-120">Ensure the sending party adds an AS2-To header to the HTTP, AS2, and MIME header of the AS2 message before sending it.</span></span>