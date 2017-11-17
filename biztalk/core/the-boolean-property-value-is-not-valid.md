---
title: "布林屬性值無效。 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62b6c178-f8ea-451a-b2dc-9396c24c0f5b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6aa8d79c2c3b4ce9033a164a664e27effdd2b63
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-boolean-property-value-is-not-valid"></a><span data-ttu-id="f619e-102">不是有效的布林屬性值</span><span class="sxs-lookup"><span data-stu-id="f619e-102">The boolean property value is not valid</span></span>
## <a name="details"></a><span data-ttu-id="f619e-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f619e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f619e-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f619e-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="f619e-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="f619e-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="f619e-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f619e-106">Event ID</span></span>|-|  
|<span data-ttu-id="f619e-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="f619e-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f619e-108">EDI</span><span class="sxs-lookup"><span data-stu-id="f619e-108"> EDI</span></span>|  
|<span data-ttu-id="f619e-109">元件</span><span class="sxs-lookup"><span data-stu-id="f619e-109">Component</span></span>|<span data-ttu-id="f619e-110">批次處理引擎</span><span class="sxs-lookup"><span data-stu-id="f619e-110">Batching Engine</span></span>|  
|<span data-ttu-id="f619e-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f619e-111">Symbolic Name</span></span>|<span data-ttu-id="f619e-112">InvalidBooleanPropertyValue</span><span class="sxs-lookup"><span data-stu-id="f619e-112">InvalidBooleanPropertyValue</span></span>|  
|<span data-ttu-id="f619e-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f619e-113">Message Text</span></span>|<span data-ttu-id="f619e-114">不是有效的布林屬性值</span><span class="sxs-lookup"><span data-stu-id="f619e-114">The boolean property value is not valid</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f619e-115">說明</span><span class="sxs-lookup"><span data-stu-id="f619e-115">Explanation</span></span>  
 <span data-ttu-id="f619e-116">這個錯誤/警告/資訊事件表示批次篩選條件 對話方塊中的資料列中的屬性輸入的值無效，因為屬性需要布林值，但輸入的值不是布林值。</span><span class="sxs-lookup"><span data-stu-id="f619e-116">This Error/Warning/Information event indicates that a value entered for a property in a row of the Batch Filter dialog box was invalid, because the property required a boolean value, but the value entered was not a boolean.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f619e-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f619e-117">User Action</span></span>  
 <span data-ttu-id="f619e-118">若要解決這個錯誤，開啟 [批次篩選條件] 對話方塊從內 [交換批次建立設定] 頁面的 [EDI 屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f619e-118">To resolve this error, open the Batch Filter dialog box from within the Interchange Batch Creation Settings page of the EDI Properties dialog box.</span></span> <span data-ttu-id="f619e-119">請確定輸入需要的布林值屬性的值實際上是布林值。</span><span class="sxs-lookup"><span data-stu-id="f619e-119">Make sure that the value entered for a property that requires a boolean value is in fact a boolean.</span></span>