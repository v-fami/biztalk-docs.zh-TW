---
title: 迴圈包含分葉節點。 它只能包含其他迴圈或區段 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a0ee5e6-519d-4c95-8681-de5a37741d56
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8d88e0fb114255d19310eefb87e00c820b17420
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014231"
---
# <a name="the-loop-contains-a-leaf-node-it-can-only-contain-other-loops-or-segments"></a><span data-ttu-id="5c756-103">迴圈包含分葉節點。</span><span class="sxs-lookup"><span data-stu-id="5c756-103">The loop contains a leaf node.</span></span> <span data-ttu-id="5c756-104">它只能包含其他迴圈或區段</span><span class="sxs-lookup"><span data-stu-id="5c756-104">It can only contain other Loops or Segments</span></span>
## <a name="details"></a><span data-ttu-id="5c756-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5c756-105">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="5c756-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="5c756-106">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="5c756-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="5c756-107">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="5c756-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="5c756-108">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="5c756-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="5c756-109">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="5c756-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="5c756-110"> EDI</span></span> |
|    <span data-ttu-id="5c756-111">元件</span><span class="sxs-lookup"><span data-stu-id="5c756-111">Component</span></span>    |                                       <span data-ttu-id="5c756-112">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="5c756-112">EDI Engine</span></span>                                       |
|  <span data-ttu-id="5c756-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="5c756-113">Symbolic Name</span></span>  |                           <span data-ttu-id="5c756-114">SchemaCode125ELoopContainsLeafNode</span><span class="sxs-lookup"><span data-stu-id="5c756-114">SchemaCode125ELoopContainsLeafNode</span></span>                           |
|  <span data-ttu-id="5c756-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="5c756-115">Message Text</span></span>   |       <span data-ttu-id="5c756-116">迴圈包含分葉節點。</span><span class="sxs-lookup"><span data-stu-id="5c756-116">The loop contains a leaf node.</span></span> <span data-ttu-id="5c756-117">它只能包含其他迴圈或區段</span><span class="sxs-lookup"><span data-stu-id="5c756-117">It can only contain other Loops or Segments</span></span>       |
  
## <a name="explanation"></a><span data-ttu-id="5c756-118">說明</span><span class="sxs-lookup"><span data-stu-id="5c756-118">Explanation</span></span>  
 <span data-ttu-id="5c756-119">這個錯誤/警告/資訊事件表示接收管線無法處理內送的交換，因為不符合交換的文件結構描述。</span><span class="sxs-lookup"><span data-stu-id="5c756-119">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange, because the interchange did not conform to the document schema.</span></span> <span data-ttu-id="5c756-120">在此情況下，迴圈會包含 childless 分葉節點，而指定的結構描述的迴圈可能只會包含其他迴圈或區段。</span><span class="sxs-lookup"><span data-stu-id="5c756-120">In this case, a loop contained a childless leaf node, whereas the schema specified that the loop could only contain other loops or segments.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5c756-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="5c756-121">User Action</span></span>  
 <span data-ttu-id="5c756-122">若要解決這個錯誤，讓交換修正程式迴圈的傳送者，使其不包含分葉節點，然後再重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="5c756-122">To resolve this error, have the sender of the interchange fix the loop so that it does not contain leaf nodes, and then resend the interchange.</span></span>