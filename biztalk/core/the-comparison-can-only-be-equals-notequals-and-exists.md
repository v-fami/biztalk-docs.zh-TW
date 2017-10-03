---
title: "比較只能 Equals、 NotEquals 和 Exists |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aad902a2-d0dc-4d91-87a7-a6305e2f40e0
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: add062aebdbabe7d5965b46c7342595f96a7b8dd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-comparison-can-only-be-equals-notequals-and-exists"></a><span data-ttu-id="234d5-102">比較只能 Equals、 NotEquals 和 Exists</span><span class="sxs-lookup"><span data-stu-id="234d5-102">The Comparison can only be Equals, NotEquals and Exists</span></span>
## <a name="details"></a><span data-ttu-id="234d5-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="234d5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="234d5-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="234d5-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="234d5-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="234d5-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="234d5-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="234d5-106">Event ID</span></span>|-|  
|<span data-ttu-id="234d5-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="234d5-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="234d5-108">EDI</span><span class="sxs-lookup"><span data-stu-id="234d5-108"> EDI</span></span>|  
|<span data-ttu-id="234d5-109">元件</span><span class="sxs-lookup"><span data-stu-id="234d5-109">Component</span></span>|<span data-ttu-id="234d5-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="234d5-110">EDI Engine</span></span>|  
|<span data-ttu-id="234d5-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="234d5-111">Symbolic Name</span></span>|<span data-ttu-id="234d5-112">Err_InvalidComparision</span><span class="sxs-lookup"><span data-stu-id="234d5-112">Err_InvalidComparision</span></span>|  
|<span data-ttu-id="234d5-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="234d5-113">Message Text</span></span>|<span data-ttu-id="234d5-114">比較只能 Equals、 NotEquals 和 Exists。</span><span class="sxs-lookup"><span data-stu-id="234d5-114">The Comparison can only be Equals, NotEquals and Exists.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="234d5-115">說明</span><span class="sxs-lookup"><span data-stu-id="234d5-115">Explanation</span></span>  
 <span data-ttu-id="234d5-116">這個錯誤/警告/資訊事件表示 BizTalk Server 無法將內容屬性做比較來決定訊息的批次嘗試時。</span><span class="sxs-lookup"><span data-stu-id="234d5-116">This Error/Warning/Information event indicates BizTalk Server was unable to compare a context property while trying to decide to Batch a message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="234d5-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="234d5-117">User Action</span></span>  
 <span data-ttu-id="234d5-118">若要解決這個錯誤，請在作用中批次中提供的篩選條件不會指定不支援其他作業的 XSD 型別等於、 NotEquals 和 Exists 以外的運算子。</span><span class="sxs-lookup"><span data-stu-id="234d5-118">To resolve this error, ensure that the filter provided in Active batches doesn’t specify an operator  other than Equals, NotEquals and Exists for XSD types that don’t support other operations.</span></span>