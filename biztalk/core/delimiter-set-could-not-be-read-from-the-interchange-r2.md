---
title: 無法從交換 (R2) 中讀取分隔符號集 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17bdd32e-d43f-4f59-af27-5d3054fd5432
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 778bfa7c417776e5baa78a6103e1075c7ccac27b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996271"
---
# <a name="delimiter-set-could-not-be-read-from-the-interchange-r2"></a><span data-ttu-id="5dbe0-102">無法從交換 (R2) 中讀取分隔符號集</span><span class="sxs-lookup"><span data-stu-id="5dbe0-102">Delimiter set could not be read from the interchange (R2)</span></span>
## <a name="details"></a><span data-ttu-id="5dbe0-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5dbe0-103">Details</span></span>  

|                 |                                                                                                                           |
|-----------------|---------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="5dbe0-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="5dbe0-104">Product Name</span></span>   |                    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                     |
| <span data-ttu-id="5dbe0-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="5dbe0-105">Product Version</span></span> |                                [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                 |
|    <span data-ttu-id="5dbe0-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="5dbe0-106">Event ID</span></span>     |                                                             -                                                             |
|  <span data-ttu-id="5dbe0-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="5dbe0-107">Event Source</span></span>   |                  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="5dbe0-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="5dbe0-108"> EDI</span></span>                   |
|    <span data-ttu-id="5dbe0-109">元件</span><span class="sxs-lookup"><span data-stu-id="5dbe0-109">Component</span></span>    |                                                        <span data-ttu-id="5dbe0-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="5dbe0-110">EDI Engine</span></span>                                                         |
|  <span data-ttu-id="5dbe0-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="5dbe0-111">Symbolic Name</span></span>  |                                                             -                                                             |
|  <span data-ttu-id="5dbe0-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="5dbe0-112">Message Text</span></span>   | <span data-ttu-id="5dbe0-113">無法從交換中讀取分隔符號集。</span><span class="sxs-lookup"><span data-stu-id="5dbe0-113">Delimiter set could not be read from the interchange.</span></span> <span data-ttu-id="5dbe0-114">從根節點遺失屬性 DelimiterSetSerializedData。</span><span class="sxs-lookup"><span data-stu-id="5dbe0-114">The attribute DelimiterSetSerializedData is missing from root node.</span></span> |

## <a name="explanation"></a><span data-ttu-id="5dbe0-115">說明</span><span class="sxs-lookup"><span data-stu-id="5dbe0-115">Explanation</span></span>  
 <span data-ttu-id="5dbe0-116">此錯誤表示交換不包含分隔符號設定的值。</span><span class="sxs-lookup"><span data-stu-id="5dbe0-116">This error indicates the interchange does not contain the delimiter set values.</span></span>  

## <a name="user-action"></a><span data-ttu-id="5dbe0-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="5dbe0-117">User Action</span></span>  
 <span data-ttu-id="5dbe0-118">若要解決這個錯誤，請執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="5dbe0-118">To resolve this error, do one of the following:</span></span>  

- <span data-ttu-id="5dbe0-119">加入分隔符號設定的值交換，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5dbe0-119">Add delimiter set values to the interchange, as follows:</span></span>  

  1.  <span data-ttu-id="5dbe0-120">開啟訊息。</span><span class="sxs-lookup"><span data-stu-id="5dbe0-120">Open up the message.</span></span>  

  2.  <span data-ttu-id="5dbe0-121">決定是否在交換沒有 UNA 區段。</span><span class="sxs-lookup"><span data-stu-id="5dbe0-121">Determine whether there is a UNA segment in the interchange.</span></span> <span data-ttu-id="5dbe0-122">如果沒有 UNA 區段，請要求合作夥伴將與交換的 UNA 區段。</span><span class="sxs-lookup"><span data-stu-id="5dbe0-122">If there is not a UNA segment, ask the partner to add the UNA segment to the interchange.</span></span>  

- <span data-ttu-id="5dbe0-123">輸入分隔符號值至 EfactDelimiters 管線屬性中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5dbe0-123">Enter the delimiter values to the EfactDelimiters pipeline property, as follows:</span></span>  

  1. <span data-ttu-id="5dbe0-124">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中，以滑鼠右鍵按一下使用您要設定屬性之管線的接收位置或傳送埠。</span><span class="sxs-lookup"><span data-stu-id="5dbe0-124">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the receive location or send port using the pipeline that you want to set properties for.</span></span> <span data-ttu-id="5dbe0-125">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="5dbe0-125">Click **Properties**.</span></span>  

  2. <span data-ttu-id="5dbe0-126">按一下要設定屬性之管線旁邊的省略符號按鈕 (?。</span><span class="sxs-lookup"><span data-stu-id="5dbe0-126">Click the ellipsis button (…) next to the pipeline that you want to set properties for.</span></span>  

  3. <span data-ttu-id="5dbe0-127">輸入 UNA 分隔符號為逗號分隔清單 （UNA1、 UNA2、 UNA3、 UNA4、 UNA5，與 UNA6），變更所需的預設值。</span><span class="sxs-lookup"><span data-stu-id="5dbe0-127">Enter values for the UNA delimiters as a comma-delimited list (for UNA1, UNA2, UNA3, UNA4, UNA5, and UNA6), changing the defaults as required.</span></span> <span data-ttu-id="5dbe0-128">預設值如下所示： 0x3A、 0x2B，0x2C、 0x3F，0x20，0x27。</span><span class="sxs-lookup"><span data-stu-id="5dbe0-128">The defaults are as follows: 0x3A, 0x2B, 0x2C, 0x3F, 0x20, 0x27.</span></span>  

  4. <span data-ttu-id="5dbe0-129">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="5dbe0-129">Click **OK**.</span></span>
