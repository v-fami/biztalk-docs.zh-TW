---
title: 無效的 AS2-From 標頭接收 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9d773e09-8526-4533-9066-8e743e65a688
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c418aaf34e3748505493fd68d578cce2c428c56
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983959"
---
# <a name="invalid-as2-from-header-received"></a><span data-ttu-id="2a51a-102">收到無效的 AS2-From 標頭</span><span class="sxs-lookup"><span data-stu-id="2a51a-102">Invalid AS2-From header received</span></span>
## <a name="details"></a><span data-ttu-id="2a51a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2a51a-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="2a51a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2a51a-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="2a51a-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="2a51a-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="2a51a-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2a51a-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="2a51a-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="2a51a-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="2a51a-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="2a51a-108"> EDI</span></span> |
|    <span data-ttu-id="2a51a-109">元件</span><span class="sxs-lookup"><span data-stu-id="2a51a-109">Component</span></span>    |                                       <span data-ttu-id="2a51a-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="2a51a-110">AS2 Engine</span></span>                                       |
|  <span data-ttu-id="2a51a-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2a51a-111">Symbolic Name</span></span>  |                         <span data-ttu-id="2a51a-112">InvalidAS2FromNameHeaderReceivedError</span><span class="sxs-lookup"><span data-stu-id="2a51a-112">InvalidAS2FromNameHeaderReceivedError</span></span>                          |
|  <span data-ttu-id="2a51a-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2a51a-113">Message Text</span></span>   |                     <span data-ttu-id="2a51a-114">收到無效的 AS2-From 標頭。</span><span class="sxs-lookup"><span data-stu-id="2a51a-114">Invalid AS2-From header received.</span></span>  <span data-ttu-id="2a51a-115">值： {0}</span><span class="sxs-lookup"><span data-stu-id="2a51a-115">Value: {0}</span></span>                      |
  
## <a name="explanation"></a><span data-ttu-id="2a51a-116">說明</span><span class="sxs-lookup"><span data-stu-id="2a51a-116">Explanation</span></span>  
 <span data-ttu-id="2a51a-117">這個錯誤/警告/資訊事件表示，由於訊息中的 AS2-From 標頭值不符合 AS2 RFC 4130 中的規格，因此接收管線無法處理內送交換。</span><span class="sxs-lookup"><span data-stu-id="2a51a-117">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the value of the AS2-From header in the message did not conform to the specifications in AS2 RFC 4130.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2a51a-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2a51a-118">User Action</span></span>  
 <span data-ttu-id="2a51a-119">若要解決這個錯誤，請確認訊息之 AS2-From 標頭中的值符合 AS2 RFC 4130 第 6.2 節的規格，然後再重新傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="2a51a-119">To resolve this error, make sure that the value in the AS2-From header of the message conforms to the specifications in section 6.2 of AS2 RFC 4130, and then have the message resent.</span></span>