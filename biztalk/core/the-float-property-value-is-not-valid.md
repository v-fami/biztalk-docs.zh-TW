---
title: "浮點數屬性值無效。 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 79327dc6-fc5e-4290-9663-16bb64970d4b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7575bf01bbb08372f9dde8e1b352e1a3406bebe0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-float-property-value-is-not-valid"></a><span data-ttu-id="12294-102">浮點數屬性值無效</span><span class="sxs-lookup"><span data-stu-id="12294-102">The float property value is not valid</span></span>
## <a name="details"></a><span data-ttu-id="12294-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="12294-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="12294-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="12294-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="12294-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="12294-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="12294-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="12294-106">Event ID</span></span>|-|  
|<span data-ttu-id="12294-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="12294-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="12294-108">EDI</span><span class="sxs-lookup"><span data-stu-id="12294-108"> EDI</span></span>|  
|<span data-ttu-id="12294-109">元件</span><span class="sxs-lookup"><span data-stu-id="12294-109">Component</span></span>|<span data-ttu-id="12294-110">批次處理引擎</span><span class="sxs-lookup"><span data-stu-id="12294-110">Batching Engine</span></span>|  
|<span data-ttu-id="12294-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="12294-111">Symbolic Name</span></span>|<span data-ttu-id="12294-112">InvalidFloatPropertyValue</span><span class="sxs-lookup"><span data-stu-id="12294-112">InvalidFloatPropertyValue</span></span>|  
|<span data-ttu-id="12294-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="12294-113">Message Text</span></span>|<span data-ttu-id="12294-114">浮點數屬性值無效</span><span class="sxs-lookup"><span data-stu-id="12294-114">The float property value is not valid</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="12294-115">說明</span><span class="sxs-lookup"><span data-stu-id="12294-115">Explanation</span></span>  
 <span data-ttu-id="12294-116">這個錯誤/警告/資訊事件表示批次篩選條件 對話方塊中的資料列中的屬性輸入的值無效，因為屬性需要浮點值，但輸入的值不是浮點數。</span><span class="sxs-lookup"><span data-stu-id="12294-116">This Error/Warning/Information event indicates that a value entered for a property in a row of the Batch Filter dialog box was invalid, because the property required a float value, but the value entered was not a float.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="12294-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="12294-117">User Action</span></span>  
 <span data-ttu-id="12294-118">若要解決這個錯誤，開啟 [批次篩選條件] 對話方塊從內 [交換批次建立設定] 頁面的 [EDI 屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="12294-118">To resolve this error, open the Batch Filter dialog box from within the Interchange Batch Creation Settings page of the EDI Properties dialog box.</span></span> <span data-ttu-id="12294-119">請確定輸入需要浮點數屬性的值實際上是浮點數。</span><span class="sxs-lookup"><span data-stu-id="12294-119">Make sure that the value entered for a property that requires a float is in fact a float.</span></span>