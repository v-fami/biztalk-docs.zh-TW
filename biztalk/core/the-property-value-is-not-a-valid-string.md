---
title: "屬性值不是有效的字串 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78df6aca-26b5-4d49-93b0-71de19f5c9dd
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7dfcceba7944226f801101818c2bf8c96ac42ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-property-value-is-not-a-valid-string"></a><span data-ttu-id="b8004-102">不是有效的字串屬性值。</span><span class="sxs-lookup"><span data-stu-id="b8004-102">The property value is not a valid string</span></span>
## <a name="details"></a><span data-ttu-id="b8004-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b8004-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b8004-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="b8004-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="b8004-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="b8004-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="b8004-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="b8004-106">Event ID</span></span>|-|  
|<span data-ttu-id="b8004-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="b8004-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="b8004-108">EDI</span><span class="sxs-lookup"><span data-stu-id="b8004-108"> EDI</span></span>|  
|<span data-ttu-id="b8004-109">元件</span><span class="sxs-lookup"><span data-stu-id="b8004-109">Component</span></span>|<span data-ttu-id="b8004-110">批次處理引擎</span><span class="sxs-lookup"><span data-stu-id="b8004-110">Batching Engine</span></span>|  
|<span data-ttu-id="b8004-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="b8004-111">Symbolic Name</span></span>|<span data-ttu-id="b8004-112">InvalidPropertyValue</span><span class="sxs-lookup"><span data-stu-id="b8004-112">InvalidPropertyValue</span></span>|  
|<span data-ttu-id="b8004-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="b8004-113">Message Text</span></span>|<span data-ttu-id="b8004-114">不是有效的字串屬性值。</span><span class="sxs-lookup"><span data-stu-id="b8004-114">The property value is not a valid string</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b8004-115">說明</span><span class="sxs-lookup"><span data-stu-id="b8004-115">Explanation</span></span>  
 <span data-ttu-id="b8004-116">這個錯誤/警告/資訊事件表示批次篩選條件 對話方塊中的資料列中的屬性輸入的值無效，因為屬性需要字串值，但輸入的值並不是 string。</span><span class="sxs-lookup"><span data-stu-id="b8004-116">This Error/Warning/Information event indicates that a value entered for a property in a row of the Batch Filter dialog box was invalid, because the property required a string value, but the value entered was not a string.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b8004-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="b8004-117">User Action</span></span>  
 <span data-ttu-id="b8004-118">若要解決這個錯誤，開啟 [批次篩選條件] 對話方塊從內 [交換批次建立設定] 頁面的 [EDI 屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b8004-118">To resolve this error, open the Batch Filter dialog box from within the Interchange Batch Creation Settings page of the EDI Properties dialog box.</span></span> <span data-ttu-id="b8004-119">請確定輸入為字串屬性的值是字串。</span><span class="sxs-lookup"><span data-stu-id="b8004-119">Make sure that the value entered for a string property is a string.</span></span>