---
title: 迴圈包含分葉節點。 它只可以包含其他迴圈或區段 |Microsoft 文件
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
ms.openlocfilehash: d03349389fb108d434cce67afc5be13fd2a3d513
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278830"
---
# <a name="the-loop-contains-a-leaf-node-it-can-only-contain-other-loops-or-segments"></a><span data-ttu-id="4ac92-103">迴圈包含分葉節點。</span><span class="sxs-lookup"><span data-stu-id="4ac92-103">The loop contains a leaf node.</span></span> <span data-ttu-id="4ac92-104">它只能包含其他迴圈或區段</span><span class="sxs-lookup"><span data-stu-id="4ac92-104">It can only contain other Loops or Segments</span></span>
## <a name="details"></a><span data-ttu-id="4ac92-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4ac92-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4ac92-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="4ac92-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="4ac92-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="4ac92-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="4ac92-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="4ac92-108">Event ID</span></span>|-|  
|<span data-ttu-id="4ac92-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="4ac92-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="4ac92-110">EDI</span><span class="sxs-lookup"><span data-stu-id="4ac92-110"> EDI</span></span>|  
|<span data-ttu-id="4ac92-111">元件</span><span class="sxs-lookup"><span data-stu-id="4ac92-111">Component</span></span>|<span data-ttu-id="4ac92-112">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="4ac92-112">EDI Engine</span></span>|  
|<span data-ttu-id="4ac92-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="4ac92-113">Symbolic Name</span></span>|<span data-ttu-id="4ac92-114">SchemaCode125ELoopContainsLeafNode</span><span class="sxs-lookup"><span data-stu-id="4ac92-114">SchemaCode125ELoopContainsLeafNode</span></span>|  
|<span data-ttu-id="4ac92-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="4ac92-115">Message Text</span></span>|<span data-ttu-id="4ac92-116">迴圈包含分葉節點。</span><span class="sxs-lookup"><span data-stu-id="4ac92-116">The loop contains a leaf node.</span></span> <span data-ttu-id="4ac92-117">它只能包含其他迴圈或區段</span><span class="sxs-lookup"><span data-stu-id="4ac92-117">It can only contain other Loops or Segments</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4ac92-118">說明</span><span class="sxs-lookup"><span data-stu-id="4ac92-118">Explanation</span></span>  
 <span data-ttu-id="4ac92-119">這個錯誤/警告/資訊事件表示接收管線無法處理內送的交換，因為文件結構描述不符合交換。</span><span class="sxs-lookup"><span data-stu-id="4ac92-119">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange, because the interchange did not conform to the document schema.</span></span> <span data-ttu-id="4ac92-120">在此情況下，由於迴圈包含 childless 分葉節點，而指定的結構描述的迴圈可能只會包含其他迴圈或區段。</span><span class="sxs-lookup"><span data-stu-id="4ac92-120">In this case, a loop contained a childless leaf node, whereas the schema specified that the loop could only contain other loops or segments.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4ac92-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="4ac92-121">User Action</span></span>  
 <span data-ttu-id="4ac92-122">若要解決這個錯誤，具有寄件者的交換修正迴圈，使其不包含分葉節點，然後再重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="4ac92-122">To resolve this error, have the sender of the interchange fix the loop so that it does not contain leaf nodes, and then resend the interchange.</span></span>