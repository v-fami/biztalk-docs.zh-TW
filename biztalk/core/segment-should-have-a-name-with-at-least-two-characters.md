---
title: 區段應該有至少兩個字元的名稱 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f80bbc4a-151a-4094-8640-1944e8812730
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: def67be8b1c146bd6da37b669a71f2be15e22e2d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985959"
---
# <a name="segment-should-have-a-name-with-at-least-two-characters"></a><span data-ttu-id="acbf9-102">區段應該有至少兩個字元的名稱</span><span class="sxs-lookup"><span data-stu-id="acbf9-102">Segment should have a name with at least two characters</span></span>
## <a name="details"></a><span data-ttu-id="acbf9-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="acbf9-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="acbf9-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="acbf9-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="acbf9-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="acbf9-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="acbf9-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="acbf9-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="acbf9-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="acbf9-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="acbf9-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="acbf9-108"> EDI</span></span> |
|    <span data-ttu-id="acbf9-109">元件</span><span class="sxs-lookup"><span data-stu-id="acbf9-109">Component</span></span>    |                                       <span data-ttu-id="acbf9-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="acbf9-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="acbf9-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="acbf9-111">Symbolic Name</span></span>  |                             <span data-ttu-id="acbf9-112">SchemaCode103EInvalidTagLength</span><span class="sxs-lookup"><span data-stu-id="acbf9-112">SchemaCode103EInvalidTagLength</span></span>                             |
|  <span data-ttu-id="acbf9-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="acbf9-113">Message Text</span></span>   |                 <span data-ttu-id="acbf9-114">區段應該有至少 2 個字元的名稱</span><span class="sxs-lookup"><span data-stu-id="acbf9-114">Segment should have a name with at least 2 characters</span></span>                  |
  
## <a name="explanation"></a><span data-ttu-id="acbf9-115">說明</span><span class="sxs-lookup"><span data-stu-id="acbf9-115">Explanation</span></span>  
 <span data-ttu-id="acbf9-116">這個錯誤/警告/資訊事件表示接收管線無法處理內送交換，因為交換中的區段名稱沒有至少 2 個字元。</span><span class="sxs-lookup"><span data-stu-id="acbf9-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the name of a segment in the interchange does not have at least two characters.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="acbf9-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="acbf9-117">User Action</span></span>  
 <span data-ttu-id="acbf9-118">若要解決此錯誤，請指示交換的傳送者確定交換的每個區段名稱都有至少 2 個字元，然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="acbf9-118">To resolve this error, have the sender of the interchange ensure that the name of each segment in the interchange has at least two characters, and then resend the interchange.</span></span>