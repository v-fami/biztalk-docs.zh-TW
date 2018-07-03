---
title: Edifact 交換應該包含 UNA 或 UNB 作為第一個區段 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc43fd17-31d0-48df-93cd-524b40034764
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4ee9d5100c8378b5ee411673c4c185dcf5def365
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37017832"
---
# <a name="edifact-interchange-should-have-contained-una-or-unb-as-the-first-segment"></a><span data-ttu-id="2a68c-102">Edifact 交換應該包含 UNA 或 UNB 作為第一個區段</span><span class="sxs-lookup"><span data-stu-id="2a68c-102">Edifact interchange should have contained UNA or UNB as the first segment</span></span>
## <a name="details"></a><span data-ttu-id="2a68c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2a68c-103">Details</span></span>  
  
|                 |                                                                                                  |
|-----------------|--------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="2a68c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2a68c-104">Product Name</span></span>   |        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]        |
| <span data-ttu-id="2a68c-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="2a68c-105">Product Version</span></span> |                    [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                    |
|    <span data-ttu-id="2a68c-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2a68c-106">Event ID</span></span>     |                                                -                                                 |
|  <span data-ttu-id="2a68c-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="2a68c-107">Event Source</span></span>   |      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="2a68c-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="2a68c-108"> EDI</span></span>      |
|    <span data-ttu-id="2a68c-109">元件</span><span class="sxs-lookup"><span data-stu-id="2a68c-109">Component</span></span>    |                                            <span data-ttu-id="2a68c-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="2a68c-110">EDI Engine</span></span>                                            |
|  <span data-ttu-id="2a68c-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2a68c-111">Symbolic Name</span></span>  |                                                -                                                 |
|  <span data-ttu-id="2a68c-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2a68c-112">Message Text</span></span>   | <span data-ttu-id="2a68c-113">Edifact 交換應該包含 UNA 或 UNB 作為第一個區段。</span><span class="sxs-lookup"><span data-stu-id="2a68c-113">Edifact interchange should have contained UNA or UNB as the first segment.</span></span> <span data-ttu-id="2a68c-114">改為{0}找不到</span><span class="sxs-lookup"><span data-stu-id="2a68c-114">Instead {0} was found</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="2a68c-115">說明</span><span class="sxs-lookup"><span data-stu-id="2a68c-115">Explanation</span></span>  
 <span data-ttu-id="2a68c-116">這個錯誤/警告/資訊事件表示 EDI 接收管線無法處理內送 EDIFACT 交換，因為第一個區段不是 UNA 或 UNB 區段。</span><span class="sxs-lookup"><span data-stu-id="2a68c-116">This Error/Warning/Information event indicates that the EDI receive pipeline could not process the incoming EDIFACT interchange because the first segment was neither a UNA nor a UNB segment.</span></span> <span data-ttu-id="2a68c-117">UNA 區段是選擇性的。UNB 區段是必要的。</span><span class="sxs-lookup"><span data-stu-id="2a68c-117">The UNA segment is optional; the UNB segment is mandatory.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2a68c-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2a68c-118">User Action</span></span>  
 <span data-ttu-id="2a68c-119">若要解決這個錯誤，確定交換的寄件者包含 UNA 或 UNB 區段的第一個區段的交換，然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="2a68c-119">To resolve this error, ensure that the sender of the interchange includes the UNA or UNB segment as the first segment of the interchange, and then resends the interchange.</span></span>