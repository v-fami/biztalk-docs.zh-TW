---
title: 配置通知選項無效 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a1b807a8-eec9-45a5-83cc-075c91b4bc9e
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 50831c03bc7dc0412cdb6fcd40ca981e87cf43f3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023188"
---
# <a name="disposition-notification-option-is-invalid"></a><span data-ttu-id="d5ecd-102">Disposition-Notification-Option 無效</span><span class="sxs-lookup"><span data-stu-id="d5ecd-102">Disposition-Notification-Option is invalid</span></span>
## <a name="details"></a><span data-ttu-id="d5ecd-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d5ecd-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="d5ecd-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d5ecd-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="d5ecd-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="d5ecd-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="d5ecd-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d5ecd-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="d5ecd-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="d5ecd-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d5ecd-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="d5ecd-108"> EDI</span></span> |
|    <span data-ttu-id="d5ecd-109">元件</span><span class="sxs-lookup"><span data-stu-id="d5ecd-109">Component</span></span>    |                                       <span data-ttu-id="d5ecd-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="d5ecd-110">AS2 Engine</span></span>                                       |
|  <span data-ttu-id="d5ecd-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d5ecd-111">Symbolic Name</span></span>  |                                           -                                            |
|  <span data-ttu-id="d5ecd-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d5ecd-112">Message Text</span></span>   |              <span data-ttu-id="d5ecd-113">配置通知選項值:"{0}"無效。</span><span class="sxs-lookup"><span data-stu-id="d5ecd-113">Disposition-Notification-Option value: "{0}" is invalid.</span></span> <span data-ttu-id="d5ecd-114">{1}</span><span class="sxs-lookup"><span data-stu-id="d5ecd-114">{1}</span></span>              |
  
## <a name="explanation"></a><span data-ttu-id="d5ecd-115">說明</span><span class="sxs-lookup"><span data-stu-id="d5ecd-115">Explanation</span></span>  
 <span data-ttu-id="d5ecd-116">這個錯誤/警告/資訊事件表示，由於 Disposition-Notification-Option 標頭無效，因此 AS2 接收管線無法產生 MDN。</span><span class="sxs-lookup"><span data-stu-id="d5ecd-116">This Error/Warning/Information event indicates that the AS2 receive pipeline could not generate the MDN because the Disposition-Notification-Option header was invalid.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d5ecd-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d5ecd-117">User Action</span></span>  
 <span data-ttu-id="d5ecd-118">若要解決這個錯誤，請確認 AS2 訊息中的 Disposition-Notification-Option 標頭符合 RFC 4130「使用 HTTP 以 MIME 為基礎的安全點對點商務資料交換 Applicability Statement 2 (AS2)」描述的語法。</span><span class="sxs-lookup"><span data-stu-id="d5ecd-118">To resolve this error, make sure that the Disposition-Notification-Option header in the AS2 message conforms to the syntax described in RFC 4130, "MIME-Based Secure Peer-to-Peer Business Data Interchange Using HTTP, Applicability Statement 2 (AS2").</span></span> <span data-ttu-id="d5ecd-119">請確定簽署回條通訊協定標頭設定為"optional"或"pcks7-signature"，並確認簽章-回條-MICAlg 標頭已設為"optional"，"MD5"或"SHA1"。</span><span class="sxs-lookup"><span data-stu-id="d5ecd-119">Ensure that the Signed-Receipt-Protocol header is set to "optional" or "pcks7-signature", and that the Signed-Receipt-MICAlg header is set to "optional", "MD5", or "SHA1".</span></span> <span data-ttu-id="d5ecd-120">（這兩個這些標頭包含配置通知選項標頭中。）</span><span class="sxs-lookup"><span data-stu-id="d5ecd-120">(Both of these headers are included in the Disposition-Notification-Option header.)</span></span>