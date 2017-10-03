---
title: "比較運算子無效。 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8383230d-9bf6-4bc5-9300-4cfd0ad38f28
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12652fbd59fde08d8321c6fdd85bb0998ce8ccc6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-comparison-operator-is-not-valid"></a><span data-ttu-id="d1626-102">比較運算子無效。</span><span class="sxs-lookup"><span data-stu-id="d1626-102">The comparison operator is not valid</span></span>
## <a name="details"></a><span data-ttu-id="d1626-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d1626-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d1626-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d1626-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="d1626-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="d1626-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="d1626-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d1626-106">Event ID</span></span>|-|  
|<span data-ttu-id="d1626-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="d1626-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d1626-108">EDI</span><span class="sxs-lookup"><span data-stu-id="d1626-108"> EDI</span></span>|  
|<span data-ttu-id="d1626-109">元件</span><span class="sxs-lookup"><span data-stu-id="d1626-109">Component</span></span>|<span data-ttu-id="d1626-110">批次處理引擎</span><span class="sxs-lookup"><span data-stu-id="d1626-110">Batching Engine</span></span>|  
|<span data-ttu-id="d1626-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d1626-111">Symbolic Name</span></span>|<span data-ttu-id="d1626-112">InvalidComparisonOperator</span><span class="sxs-lookup"><span data-stu-id="d1626-112">InvalidComparisonOperator</span></span>|  
|<span data-ttu-id="d1626-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d1626-113">Message Text</span></span>|<span data-ttu-id="d1626-114">比較運算子無效。</span><span class="sxs-lookup"><span data-stu-id="d1626-114">The comparison operator is not valid.</span></span> <span data-ttu-id="d1626-115">例外狀況訊息 = {0}</span><span class="sxs-lookup"><span data-stu-id="d1626-115">Exception message = {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d1626-116">說明</span><span class="sxs-lookup"><span data-stu-id="d1626-116">Explanation</span></span>  
 <span data-ttu-id="d1626-117">這個錯誤/警告/資訊事件表示輸入批次篩選條件 對話方塊中的資料列的比較運算子不是有效的屬性和值。</span><span class="sxs-lookup"><span data-stu-id="d1626-117">This Error/Warning/Information event indicates that the comparison operator entered for a row of the Batch Filter dialog box was not valid for the property and the value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d1626-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d1626-118">User Action</span></span>  
 <span data-ttu-id="d1626-119">若要解決這個錯誤，開啟 [批次篩選條件] 對話方塊從內 [交換批次建立設定] 頁面的 [EDI 屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d1626-119">To resolve this error, open the Batch Filter dialog box from within the Interchange Batch Creation Settings page of the EDI Properties dialog box.</span></span> <span data-ttu-id="d1626-120">請確定輸入的資料列批次篩選條件方格中的比較運算子是有效的屬性和值。</span><span class="sxs-lookup"><span data-stu-id="d1626-120">Make sure that the comparison operators entered for rows in the Batch Filter grid are valid for the property and the value.</span></span>