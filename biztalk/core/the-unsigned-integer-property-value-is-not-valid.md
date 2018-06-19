---
title: 不帶正負號的整數屬性值無效。 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 63b0398f-7848-4971-8c08-95923d80cbe3
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e5f6ac36eb2b7322a2252f4759539d721dc2e63
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278174"
---
# <a name="the-unsigned-integer-property-value-is-not-valid"></a><span data-ttu-id="eed4b-102">不帶正負號的整數屬性值無效</span><span class="sxs-lookup"><span data-stu-id="eed4b-102">The unsigned integer property value is not valid</span></span>
## <a name="details"></a><span data-ttu-id="eed4b-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="eed4b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eed4b-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="eed4b-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="eed4b-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="eed4b-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="eed4b-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="eed4b-106">Event ID</span></span>|-|  
|<span data-ttu-id="eed4b-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="eed4b-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="eed4b-108">EDI</span><span class="sxs-lookup"><span data-stu-id="eed4b-108"> EDI</span></span>|  
|<span data-ttu-id="eed4b-109">元件</span><span class="sxs-lookup"><span data-stu-id="eed4b-109">Component</span></span>|<span data-ttu-id="eed4b-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="eed4b-110">EDI Engine</span></span>|  
|<span data-ttu-id="eed4b-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="eed4b-111">Symbolic Name</span></span>|<span data-ttu-id="eed4b-112">Err_InvalidUnsignedInteger</span><span class="sxs-lookup"><span data-stu-id="eed4b-112">Err_InvalidUnsignedInteger</span></span>|  
|<span data-ttu-id="eed4b-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="eed4b-113">Message Text</span></span>|<span data-ttu-id="eed4b-114">不帶正負號的整數屬性值無效。</span><span class="sxs-lookup"><span data-stu-id="eed4b-114">The unsigned integer property value is not valid.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="eed4b-115">說明</span><span class="sxs-lookup"><span data-stu-id="eed4b-115">Explanation</span></span>  
 <span data-ttu-id="eed4b-116">這個錯誤/警告/資訊事件表示 BizTalk Server 無法將內容屬性做比較時決定是否要批次處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="eed4b-116">This Error/Warning/Information event indicates BizTalk Server was unable to compare a context property while trying to decide whether to Batch a message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="eed4b-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="eed4b-117">User Action</span></span>  
 <span data-ttu-id="eed4b-118">若要解決這個錯誤，請在作用中批次中提供的篩選條件不會指定內容屬性具有無效的值不帶正負號整數的 XSD 類型。</span><span class="sxs-lookup"><span data-stu-id="eed4b-118">To resolve this error, ensure that the filter provided in Active batches doesn’t specify a context property which has an XSD type of unsigned integer with an invalid value.</span></span>