---
title: 功能群組後發現 TA1 區段 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee3d090a-0916-4a0e-82dc-2c9af9f97683
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87613f9482c5c54e99544b96ddd0d1cfc94d3c85
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018136"
---
# <a name="ta1-segment-found-after-a-functional-group"></a><span data-ttu-id="05e65-102">功能群組後發現 TA1 區段</span><span class="sxs-lookup"><span data-stu-id="05e65-102">TA1 segment found after a functional group</span></span>
## <a name="details"></a><span data-ttu-id="05e65-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="05e65-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="05e65-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="05e65-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="05e65-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="05e65-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="05e65-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="05e65-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="05e65-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="05e65-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="05e65-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="05e65-108"> EDI</span></span> |
|    <span data-ttu-id="05e65-109">元件</span><span class="sxs-lookup"><span data-stu-id="05e65-109">Component</span></span>    |                                       <span data-ttu-id="05e65-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="05e65-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="05e65-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="05e65-111">Symbolic Name</span></span>  |                              <span data-ttu-id="05e65-112">TA1FoundAfterFunctionalGroup</span><span class="sxs-lookup"><span data-stu-id="05e65-112">TA1FoundAfterFunctionalGroup</span></span>                              |
|  <span data-ttu-id="05e65-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="05e65-113">Message Text</span></span>   |     <span data-ttu-id="05e65-114">在功能群組後發現 TA1 區段。</span><span class="sxs-lookup"><span data-stu-id="05e65-114">TA1 segment found after a functional group.</span></span> <span data-ttu-id="05e65-115">因此，即將拒絕訊息</span><span class="sxs-lookup"><span data-stu-id="05e65-115">So, the message is being rejected</span></span>      |
  
## <a name="explanation"></a><span data-ttu-id="05e65-116">說明</span><span class="sxs-lookup"><span data-stu-id="05e65-116">Explanation</span></span>  
 <span data-ttu-id="05e65-117">這個錯誤/警告/資訊事件表示，接收管線無法處理內送通知因為通知所包含功能的群組]，然後按一下 [TA1 區段。</span><span class="sxs-lookup"><span data-stu-id="05e65-117">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming acknowledgment because the acknowledgment contained a functional group and then a TA1 segment.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="05e65-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="05e65-118">User Action</span></span>  
 <span data-ttu-id="05e65-119">若要解決這個錯誤，有的 TA1 通知確保，交換不包含 TA1 區段中之前, 的功能群組，然後再重新傳送通知的寄件者。</span><span class="sxs-lookup"><span data-stu-id="05e65-119">To resolve this error, have the sender of the TA1 acknowledgment ensure that the interchange does not contain a functional group before the TA1 segment, and then resend the acknowledgment.</span></span>