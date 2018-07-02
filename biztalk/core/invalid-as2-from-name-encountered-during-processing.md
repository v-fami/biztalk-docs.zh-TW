---
title: 無效的 AS2-在處理期間發生的名稱從 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba658119-9171-4851-835c-72c188275b73
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 30277473c0b5bdae8eeb3228b9f53275498842a4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975807"
---
# <a name="invalid-as2-from-name-encountered-during-processing"></a><span data-ttu-id="67418-102">無效的 AS2-在處理期間發生的名稱</span><span class="sxs-lookup"><span data-stu-id="67418-102">Invalid AS2-From name encountered during processing</span></span>
## <a name="details"></a><span data-ttu-id="67418-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="67418-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="67418-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="67418-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="67418-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="67418-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="67418-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="67418-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="67418-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="67418-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="67418-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="67418-108"> EDI</span></span> |
|    <span data-ttu-id="67418-109">元件</span><span class="sxs-lookup"><span data-stu-id="67418-109">Component</span></span>    |                                       <span data-ttu-id="67418-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="67418-110">AS2 Engine</span></span>                                       |
|  <span data-ttu-id="67418-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="67418-111">Symbolic Name</span></span>  |                           <span data-ttu-id="67418-112">InvalidAS2FromNameEncounteredError</span><span class="sxs-lookup"><span data-stu-id="67418-112">InvalidAS2FromNameEncounteredError</span></span>                           |
|  <span data-ttu-id="67418-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="67418-113">Message Text</span></span>   |            <span data-ttu-id="67418-114">無效的 AS2-在處理期間發生的名稱。</span><span class="sxs-lookup"><span data-stu-id="67418-114">Invalid AS2-From name encountered during processing.</span></span>  <span data-ttu-id="67418-115">值： {0}</span><span class="sxs-lookup"><span data-stu-id="67418-115">Value: {0}</span></span>            |
  
## <a name="explanation"></a><span data-ttu-id="67418-116">說明</span><span class="sxs-lookup"><span data-stu-id="67418-116">Explanation</span></span>  
 <span data-ttu-id="67418-117">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換或傳送管線無法處理外寄交換，因為值的 AS2-From 標頭不符合AS2 RFC 4130 中的規格。</span><span class="sxs-lookup"><span data-stu-id="67418-117">This Error/Warning/Information event indicates that either the receive pipeline could not process the incoming interchange or the send pipeline could not process the outgoing interchange because the value of the AS2-From header did not conform to the specifications in AS2 RFC 4130.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="67418-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="67418-118">User Action</span></span>  
 <span data-ttu-id="67418-119">若要解決這個錯誤，請確定 AS2-From 傳入或傳出訊息中的標頭符合 AS2 RFC 4130 6.2 節的規格，並再重新傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="67418-119">To resolve this error, make sure that the AS2-From header in the incoming or outgoing message conforms to the specifications in section 6.2 of AS2 RFC 4130, and then have the message resent.</span></span>