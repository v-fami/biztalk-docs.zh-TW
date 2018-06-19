---
title: 無法讀取的分隔符號集從交換 (R2) |Microsoft 文件
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
ms.openlocfilehash: d3836b218ac3596bef25edb29eaf72c38f65b6e9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239078"
---
# <a name="delimiter-set-could-not-be-read-from-the-interchange-r2"></a><span data-ttu-id="aa36f-102">無法讀取的分隔符號集從交換 (R2)</span><span class="sxs-lookup"><span data-stu-id="aa36f-102">Delimiter set could not be read from the interchange (R2)</span></span>
## <a name="details"></a><span data-ttu-id="aa36f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="aa36f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aa36f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="aa36f-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="aa36f-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="aa36f-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="aa36f-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="aa36f-106">Event ID</span></span>|-|  
|<span data-ttu-id="aa36f-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="aa36f-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="aa36f-108">EDI</span><span class="sxs-lookup"><span data-stu-id="aa36f-108"> EDI</span></span>|  
|<span data-ttu-id="aa36f-109">元件</span><span class="sxs-lookup"><span data-stu-id="aa36f-109">Component</span></span>|<span data-ttu-id="aa36f-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="aa36f-110">EDI Engine</span></span>|  
|<span data-ttu-id="aa36f-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="aa36f-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="aa36f-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="aa36f-112">Message Text</span></span>|<span data-ttu-id="aa36f-113">無法從交換中讀取的分隔符號集。</span><span class="sxs-lookup"><span data-stu-id="aa36f-113">Delimiter set could not be read from the interchange.</span></span> <span data-ttu-id="aa36f-114">從根節點遺漏 DelimiterSetSerializedData 屬性。</span><span class="sxs-lookup"><span data-stu-id="aa36f-114">The attribute DelimiterSetSerializedData is missing from root node.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="aa36f-115">說明</span><span class="sxs-lookup"><span data-stu-id="aa36f-115">Explanation</span></span>  
 <span data-ttu-id="aa36f-116">此錯誤表示交換不包含分隔符號設定的值。</span><span class="sxs-lookup"><span data-stu-id="aa36f-116">This error indicates the interchange does not contain the delimiter set values.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="aa36f-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="aa36f-117">User Action</span></span>  
 <span data-ttu-id="aa36f-118">若要解決這個錯誤，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="aa36f-118">To resolve this error, do one of the following:</span></span>  
  
-   <span data-ttu-id="aa36f-119">加入分隔符號設定的值交換，如下所示：</span><span class="sxs-lookup"><span data-stu-id="aa36f-119">Add delimiter set values to the interchange, as follows:</span></span>  
  
    1.  <span data-ttu-id="aa36f-120">開啟訊息。</span><span class="sxs-lookup"><span data-stu-id="aa36f-120">Open up the message.</span></span>  
  
    2.  <span data-ttu-id="aa36f-121">決定是否在交換沒有 UNA 區段。</span><span class="sxs-lookup"><span data-stu-id="aa36f-121">Determine whether there is a UNA segment in the interchange.</span></span> <span data-ttu-id="aa36f-122">如果不是 UNA 區段，要求的夥伴加入交換的 UNA 區段。</span><span class="sxs-lookup"><span data-stu-id="aa36f-122">If there is not a UNA segment, ask the partner to add the UNA segment to the interchange.</span></span>  
  
-   <span data-ttu-id="aa36f-123">輸入分隔符號值至 EfactDelimiters 管線屬性中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="aa36f-123">Enter the delimiter values to the EfactDelimiters pipeline property, as follows:</span></span>  
  
    1.  <span data-ttu-id="aa36f-124">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中，以滑鼠右鍵按一下使用您要設定屬性之管線的接收位置或傳送埠。</span><span class="sxs-lookup"><span data-stu-id="aa36f-124">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the receive location or send port using the pipeline that you want to set properties for.</span></span> <span data-ttu-id="aa36f-125">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="aa36f-125">Click **Properties**.</span></span>  
  
    2.  <span data-ttu-id="aa36f-126">按一下要設定屬性之管線旁邊的省略符號按鈕 (?。</span><span class="sxs-lookup"><span data-stu-id="aa36f-126">Click the ellipsis button (…) next to the pipeline that you want to set properties for.</span></span>  
  
    3.  <span data-ttu-id="aa36f-127">UNA 分隔符號輸入值為逗號分隔清單 （適用於 UNA1、 UNA2、 UNA3、 UNA4、 UNA5、 和 UNA6），變更所需的預設值。</span><span class="sxs-lookup"><span data-stu-id="aa36f-127">Enter values for the UNA delimiters as a comma-delimited list (for UNA1, UNA2, UNA3, UNA4, UNA5, and UNA6), changing the defaults as required.</span></span> <span data-ttu-id="aa36f-128">預設值如下： 0x3A、 0x2B、 0x2C、 0x3F、 0x20、 0x27。</span><span class="sxs-lookup"><span data-stu-id="aa36f-128">The defaults are as follows: 0x3A, 0x2B, 0x2C, 0x3F, 0x20, 0x27.</span></span>  
  
    4.  <span data-ttu-id="aa36f-129">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="aa36f-129">Click **OK**.</span></span>