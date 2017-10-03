---
title: "BitwiseAnd 比較無法完成此 XSD 類型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82bc2351-c002-458a-9d35-5fdcc91c6a0e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5c0f3aa2b3ae7c60f3c104daaa885ab7ae8cc7ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="a-bitwiseand-comparison-cannot-be-done-for-this-xsd-type"></a><span data-ttu-id="4c04a-102">BitwiseAnd 比較無法完成此 XSD 類型</span><span class="sxs-lookup"><span data-stu-id="4c04a-102">A BitwiseAnd comparison cannot be done for this XSD type</span></span>
## <a name="details"></a><span data-ttu-id="4c04a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4c04a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4c04a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="4c04a-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="4c04a-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="4c04a-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="4c04a-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="4c04a-106">Event ID</span></span>|-|  
|<span data-ttu-id="4c04a-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="4c04a-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="4c04a-108">EDI</span><span class="sxs-lookup"><span data-stu-id="4c04a-108"> EDI</span></span>|  
|<span data-ttu-id="4c04a-109">元件</span><span class="sxs-lookup"><span data-stu-id="4c04a-109">Component</span></span>|<span data-ttu-id="4c04a-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="4c04a-110">EDI Engine</span></span>|  
|<span data-ttu-id="4c04a-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="4c04a-111">Symbolic Name</span></span>|<span data-ttu-id="4c04a-112">Err_InvalidBitwiseComparision</span><span class="sxs-lookup"><span data-stu-id="4c04a-112">Err_InvalidBitwiseComparision</span></span>|  
|<span data-ttu-id="4c04a-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="4c04a-113">Message Text</span></span>|<span data-ttu-id="4c04a-114">BitwiseAnd 比較無法完成此 XSD 類型。</span><span class="sxs-lookup"><span data-stu-id="4c04a-114">A BitwiseAnd comparison cannot be done for this XSD type.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4c04a-115">說明</span><span class="sxs-lookup"><span data-stu-id="4c04a-115">Explanation</span></span>  
 <span data-ttu-id="4c04a-116">這個錯誤/警告/資訊事件表示 BizTalk Server 無法將內容屬性做比較來決定訊息的批次嘗試時。</span><span class="sxs-lookup"><span data-stu-id="4c04a-116">This Error/Warning/Information event indicates BizTalk Server was unable to compare a context property while trying to decide to Batch a message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4c04a-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="4c04a-117">User Action</span></span>  
 <span data-ttu-id="4c04a-118">若要解決這個錯誤，請在作用中批次中提供的篩選條件不會指定內容屬性具有無法位元比較 CSD 類型。</span><span class="sxs-lookup"><span data-stu-id="4c04a-118">To resolve this error, ensure that the filter provided in Active batches doesn’t specify a context property which has an CSD type that can’t be bitwise compared.</span></span>