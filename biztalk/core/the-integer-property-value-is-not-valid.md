---
title: 整數屬性值無效。 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 31d4e9a7-4336-40f1-997a-9f79d86b26d2
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: acbb350d9dd8fe77e42bb7e8b3cdf4617c87a2f7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278902"
---
# <a name="the-integer-property-value-is-not-valid"></a><span data-ttu-id="f3ceb-102">整數屬性值無效</span><span class="sxs-lookup"><span data-stu-id="f3ceb-102">The integer property value is not valid</span></span>
## <a name="details"></a><span data-ttu-id="f3ceb-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f3ceb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f3ceb-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f3ceb-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="f3ceb-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="f3ceb-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="f3ceb-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f3ceb-106">Event ID</span></span>|-|  
|<span data-ttu-id="f3ceb-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="f3ceb-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f3ceb-108">EDI</span><span class="sxs-lookup"><span data-stu-id="f3ceb-108"> EDI</span></span>|  
|<span data-ttu-id="f3ceb-109">元件</span><span class="sxs-lookup"><span data-stu-id="f3ceb-109">Component</span></span>|<span data-ttu-id="f3ceb-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="f3ceb-110">EDI Engine</span></span>|  
|<span data-ttu-id="f3ceb-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f3ceb-111">Symbolic Name</span></span>|<span data-ttu-id="f3ceb-112">Err_InvalidInteger</span><span class="sxs-lookup"><span data-stu-id="f3ceb-112">Err_InvalidInteger</span></span>|  
|<span data-ttu-id="f3ceb-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f3ceb-113">Message Text</span></span>|<span data-ttu-id="f3ceb-114">整數屬性值無效。</span><span class="sxs-lookup"><span data-stu-id="f3ceb-114">The integer property value is not valid.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f3ceb-115">說明</span><span class="sxs-lookup"><span data-stu-id="f3ceb-115">Explanation</span></span>  
 <span data-ttu-id="f3ceb-116">這個錯誤/警告/資訊事件表示 BizTalk Server 無法將內容屬性做比較時決定是否要批次處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="f3ceb-116">This Error/Warning/Information event indicates BizTalk Server was unable to compare a context property while trying to decide whether to Batch a message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f3ceb-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f3ceb-117">User Action</span></span>  
 <span data-ttu-id="f3ceb-118">若要解決這個錯誤，請在作用中批次中提供的篩選條件不會指定內容屬性的 XSD 類型的整數值無效。</span><span class="sxs-lookup"><span data-stu-id="f3ceb-118">To resolve this error, ensure that the filter provided in Active batches doesn’t specify a context property which has an XSD type of integer with an invalid value.</span></span>