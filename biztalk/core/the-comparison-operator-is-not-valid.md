---
title: 比較運算子無效。 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8383230d-9bf6-4bc5-9300-4cfd0ad38f28
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87b44f68168570c229b66cb6ee767cf38229dc74
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989711"
---
# <a name="the-comparison-operator-is-not-valid"></a><span data-ttu-id="aa6d7-102">比較運算子無效</span><span class="sxs-lookup"><span data-stu-id="aa6d7-102">The comparison operator is not valid</span></span>
## <a name="details"></a><span data-ttu-id="aa6d7-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="aa6d7-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="aa6d7-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="aa6d7-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="aa6d7-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="aa6d7-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="aa6d7-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="aa6d7-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="aa6d7-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="aa6d7-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="aa6d7-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="aa6d7-108"> EDI</span></span> |
|    <span data-ttu-id="aa6d7-109">元件</span><span class="sxs-lookup"><span data-stu-id="aa6d7-109">Component</span></span>    |                                    <span data-ttu-id="aa6d7-110">批次引擎</span><span class="sxs-lookup"><span data-stu-id="aa6d7-110">Batching Engine</span></span>                                     |
|  <span data-ttu-id="aa6d7-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="aa6d7-111">Symbolic Name</span></span>  |                               <span data-ttu-id="aa6d7-112">InvalidComparisonOperator</span><span class="sxs-lookup"><span data-stu-id="aa6d7-112">InvalidComparisonOperator</span></span>                                |
|  <span data-ttu-id="aa6d7-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="aa6d7-113">Message Text</span></span>   |             <span data-ttu-id="aa6d7-114">比較運算子無效。</span><span class="sxs-lookup"><span data-stu-id="aa6d7-114">The comparison operator is not valid.</span></span> <span data-ttu-id="aa6d7-115">例外狀況訊息 = {0}</span><span class="sxs-lookup"><span data-stu-id="aa6d7-115">Exception message = {0}</span></span>              |
  
## <a name="explanation"></a><span data-ttu-id="aa6d7-116">說明</span><span class="sxs-lookup"><span data-stu-id="aa6d7-116">Explanation</span></span>  
 <span data-ttu-id="aa6d7-117">這個錯誤/警告/資訊事件表示某一列的 [批次篩選條件] 對話方塊中輸入的比較運算子不是有效的屬性和值。</span><span class="sxs-lookup"><span data-stu-id="aa6d7-117">This Error/Warning/Information event indicates that the comparison operator entered for a row of the Batch Filter dialog box was not valid for the property and the value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="aa6d7-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="aa6d7-118">User Action</span></span>  
 <span data-ttu-id="aa6d7-119">若要解決這個錯誤，開啟 [批次篩選條件] 對話方塊中從 [交換批次建立設定] 頁面中的 [EDI 屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="aa6d7-119">To resolve this error, open the Batch Filter dialog box from within the Interchange Batch Creation Settings page of the EDI Properties dialog box.</span></span> <span data-ttu-id="aa6d7-120">請確定輸入的批次篩選條件的方格中的資料列的比較運算子是有效的屬性和值。</span><span class="sxs-lookup"><span data-stu-id="aa6d7-120">Make sure that the comparison operators entered for rows in the Batch Filter grid are valid for the property and the value.</span></span>