---
title: "值不可為空白或 null 以外 Exists 運算子 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 44de42c8-eab7-4b13-b55a-d33eabe75c52
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b5e257b78df8bf872764542d711637d33714349
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-value-cannot-be-empty-or-null-for-an-operator-other-than-exists"></a><span data-ttu-id="aee93-102">值不可為空白或 null Exists 以外的運算子</span><span class="sxs-lookup"><span data-stu-id="aee93-102">The value cannot be empty or null for an operator other than Exists</span></span>
## <a name="details"></a><span data-ttu-id="aee93-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="aee93-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aee93-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="aee93-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="aee93-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="aee93-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="aee93-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="aee93-106">Event ID</span></span>|-|  
|<span data-ttu-id="aee93-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="aee93-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="aee93-108">EDI</span><span class="sxs-lookup"><span data-stu-id="aee93-108"> EDI</span></span>|  
|<span data-ttu-id="aee93-109">元件</span><span class="sxs-lookup"><span data-stu-id="aee93-109">Component</span></span>|<span data-ttu-id="aee93-110">批次處理引擎</span><span class="sxs-lookup"><span data-stu-id="aee93-110">Batching Engine</span></span>|  
|<span data-ttu-id="aee93-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="aee93-111">Symbolic Name</span></span>|<span data-ttu-id="aee93-112">ValueCannotBeNullOrEmpty</span><span class="sxs-lookup"><span data-stu-id="aee93-112">ValueCannotBeNullOrEmpty</span></span>|  
|<span data-ttu-id="aee93-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="aee93-113">Message Text</span></span>|<span data-ttu-id="aee93-114">值不可為空白或 null Exists 以外的運算子</span><span class="sxs-lookup"><span data-stu-id="aee93-114">The value cannot be empty or null for an operator other than Exists</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="aee93-115">說明</span><span class="sxs-lookup"><span data-stu-id="aee93-115">Explanation</span></span>  
 <span data-ttu-id="aee93-116">這個錯誤/警告/資訊事件表示批次篩選條件 對話方塊中的資料列中的屬性輸入的值無效，因為運算子不存在，但輸入的值是空白或 null。</span><span class="sxs-lookup"><span data-stu-id="aee93-116">This Error/Warning/Information event indicates that a value entered for a property in a row of the Batch Filter dialog box was invalid, because the operator was not Exists, but the value entered was either empty or null.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="aee93-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="aee93-117">User Action</span></span>  
 <span data-ttu-id="aee93-118">若要解決這個錯誤，開啟 [批次篩選條件] 對話方塊從內 [交換批次建立設定] 頁面的 [EDI 屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="aee93-118">To resolve this error, open the Batch Filter dialog box from within the Interchange Batch Creation Settings page of the EDI Properties dialog box.</span></span> <span data-ttu-id="aee93-119">請確定該運算子的資料列不存在，如果輸入的值是空的或 null。</span><span class="sxs-lookup"><span data-stu-id="aee93-119">Make sure that if the operator for a row is not Exists, the value entered is neither empty nor null.</span></span>