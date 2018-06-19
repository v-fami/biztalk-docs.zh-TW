---
title: 是無效的配置通知選項 |Microsoft 文件
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
ms.openlocfilehash: 72221c98dfcac42f735f63a1ce01a7c26bc45387
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239046"
---
# <a name="disposition-notification-option-is-invalid"></a><span data-ttu-id="216b8-102">Disposition-Notification-Option 無效</span><span class="sxs-lookup"><span data-stu-id="216b8-102">Disposition-Notification-Option is invalid</span></span>
## <a name="details"></a><span data-ttu-id="216b8-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="216b8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="216b8-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="216b8-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="216b8-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="216b8-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="216b8-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="216b8-106">Event ID</span></span>|-|  
|<span data-ttu-id="216b8-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="216b8-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="216b8-108">EDI</span><span class="sxs-lookup"><span data-stu-id="216b8-108"> EDI</span></span>|  
|<span data-ttu-id="216b8-109">元件</span><span class="sxs-lookup"><span data-stu-id="216b8-109">Component</span></span>|<span data-ttu-id="216b8-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="216b8-110">AS2 Engine</span></span>|  
|<span data-ttu-id="216b8-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="216b8-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="216b8-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="216b8-112">Message Text</span></span>|<span data-ttu-id="216b8-113">配置通知選項的值:"{0}"無效。</span><span class="sxs-lookup"><span data-stu-id="216b8-113">Disposition-Notification-Option value: "{0}" is invalid.</span></span> <span data-ttu-id="216b8-114">{1}</span><span class="sxs-lookup"><span data-stu-id="216b8-114">{1}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="216b8-115">說明</span><span class="sxs-lookup"><span data-stu-id="216b8-115">Explanation</span></span>  
 <span data-ttu-id="216b8-116">這個錯誤/警告/資訊事件表示，由於 Disposition-Notification-Option 標頭無效，因此 AS2 接收管線無法產生 MDN。</span><span class="sxs-lookup"><span data-stu-id="216b8-116">This Error/Warning/Information event indicates that the AS2 receive pipeline could not generate the MDN because the Disposition-Notification-Option header was invalid.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="216b8-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="216b8-117">User Action</span></span>  
 <span data-ttu-id="216b8-118">若要解決這個錯誤，請確認 AS2 訊息中的 Disposition-Notification-Option 標頭符合 RFC 4130「使用 HTTP 以 MIME 為基礎的安全點對點商務資料交換 Applicability Statement 2 (AS2)」描述的語法。</span><span class="sxs-lookup"><span data-stu-id="216b8-118">To resolve this error, make sure that the Disposition-Notification-Option header in the AS2 message conforms to the syntax described in RFC 4130, "MIME-Based Secure Peer-to-Peer Business Data Interchange Using HTTP, Applicability Statement 2 (AS2").</span></span> <span data-ttu-id="216b8-119">請確認簽署回條通訊協定標頭設為 「 選用 」 或 「 pcks7-簽章 」，且簽章-回條-MICAlg 標頭，設定為 「 選用 」，"MD5"或"SHA1"。</span><span class="sxs-lookup"><span data-stu-id="216b8-119">Ensure that the Signed-Receipt-Protocol header is set to "optional" or "pcks7-signature", and that the Signed-Receipt-MICAlg header is set to "optional", "MD5", or "SHA1".</span></span> <span data-ttu-id="216b8-120">（這兩個這些標頭包含配置通知選項標頭中。）</span><span class="sxs-lookup"><span data-stu-id="216b8-120">(Both of these headers are included in the Disposition-Notification-Option header.)</span></span>