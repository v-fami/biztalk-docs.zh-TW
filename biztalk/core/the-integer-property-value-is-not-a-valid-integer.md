---
title: 整數屬性值不是有效的整數 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa97f3dd-4a01-4007-b23a-820cbebbc083
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32aebb74d937bb6b57d463598e178ad4d1ca280b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278382"
---
# <a name="the-integer-property-value-is-not-a-valid-integer"></a><span data-ttu-id="ae316-102">整數屬性值不是有效的整數</span><span class="sxs-lookup"><span data-stu-id="ae316-102">The integer property value is not a valid integer</span></span>
## <a name="details"></a><span data-ttu-id="ae316-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ae316-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ae316-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ae316-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="ae316-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="ae316-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="ae316-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ae316-106">Event ID</span></span>|-|  
|<span data-ttu-id="ae316-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="ae316-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ae316-108">EDI</span><span class="sxs-lookup"><span data-stu-id="ae316-108"> EDI</span></span>|  
|<span data-ttu-id="ae316-109">元件</span><span class="sxs-lookup"><span data-stu-id="ae316-109">Component</span></span>|<span data-ttu-id="ae316-110">批次處理引擎</span><span class="sxs-lookup"><span data-stu-id="ae316-110">Batching Engine</span></span>|  
|<span data-ttu-id="ae316-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ae316-111">Symbolic Name</span></span>|<span data-ttu-id="ae316-112">InvalidIntegerPropertyValue</span><span class="sxs-lookup"><span data-stu-id="ae316-112">InvalidIntegerPropertyValue</span></span>|  
|<span data-ttu-id="ae316-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ae316-113">Message Text</span></span>|<span data-ttu-id="ae316-114">整數屬性值不是有效的整數</span><span class="sxs-lookup"><span data-stu-id="ae316-114">The integer property value is not a valid integer</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ae316-115">說明</span><span class="sxs-lookup"><span data-stu-id="ae316-115">Explanation</span></span>  
 <span data-ttu-id="ae316-116">這個錯誤/警告/資訊事件表示批次篩選條件 對話方塊中的資料列中的屬性輸入的值無效，因為屬性需要整數值，但輸入的值不是整數。</span><span class="sxs-lookup"><span data-stu-id="ae316-116">This Error/Warning/Information event indicates that a value entered for a property in a row of the Batch Filter dialog box was invalid, because the property required an integer value, but the value entered was not an integer.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ae316-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ae316-117">User Action</span></span>  
 <span data-ttu-id="ae316-118">若要解決這個錯誤，開啟 [批次篩選條件] 對話方塊從內 [交換批次建立設定] 頁面的 [EDI 屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ae316-118">To resolve this error, open the Batch Filter dialog box from within the Interchange Batch Creation Settings page of the EDI Properties dialog box.</span></span> <span data-ttu-id="ae316-119">請確定輸入的內容必須是整數的值實際上是一個整數。</span><span class="sxs-lookup"><span data-stu-id="ae316-119">Make sure that the value entered for a property that must be an integer is in fact an integer.</span></span>