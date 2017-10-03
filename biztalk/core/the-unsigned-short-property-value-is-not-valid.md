---
title: "不帶正負號的短屬性值不是有效 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31600ed6-20bc-4382-9eb3-4d6fa9646411
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a62a37bc136f317e05db0e66cf3c2c86af97df41
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-unsigned-short-property-value-is-not-valid"></a><span data-ttu-id="017ab-102">不帶正負號的短屬性值無效</span><span class="sxs-lookup"><span data-stu-id="017ab-102">The unsigned Short property value is not valid</span></span>
## <a name="details"></a><span data-ttu-id="017ab-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="017ab-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="017ab-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="017ab-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="017ab-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="017ab-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="017ab-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="017ab-106">Event ID</span></span>|-|  
|<span data-ttu-id="017ab-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="017ab-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="017ab-108">EDI</span><span class="sxs-lookup"><span data-stu-id="017ab-108"> EDI</span></span>|  
|<span data-ttu-id="017ab-109">元件</span><span class="sxs-lookup"><span data-stu-id="017ab-109">Component</span></span>|<span data-ttu-id="017ab-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="017ab-110">EDI Engine</span></span>|  
|<span data-ttu-id="017ab-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="017ab-111">Symbolic Name</span></span>|<span data-ttu-id="017ab-112">Err_InvalidUnsignedShort</span><span class="sxs-lookup"><span data-stu-id="017ab-112">Err_InvalidUnsignedShort</span></span>|  
|<span data-ttu-id="017ab-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="017ab-113">Message Text</span></span>|<span data-ttu-id="017ab-114">不帶正負號的短屬性值無效。</span><span class="sxs-lookup"><span data-stu-id="017ab-114">The unsigned Short property value is not valid.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="017ab-115">說明</span><span class="sxs-lookup"><span data-stu-id="017ab-115">Explanation</span></span>  
 <span data-ttu-id="017ab-116">這個錯誤/警告/資訊事件表示 BizTalk Server 無法將內容屬性做比較時決定是否要批次處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="017ab-116">This Error/Warning/Information event indicates BizTalk Server was unable to compare a context property while trying to decide whether to Batch a message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="017ab-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="017ab-117">User Action</span></span>  
 <span data-ttu-id="017ab-118">若要解決這個錯誤，請在作用中批次中提供的篩選條件不會指定內容屬性具有無效的值不帶正負號的短的 XSD 類型。</span><span class="sxs-lookup"><span data-stu-id="017ab-118">To resolve this error, ensure that the filter provided in Active batches doesn’t specify a context property which has an XSD type of unsigned Short with an invalid value.</span></span>