---
title: 必要的資料元素遺失 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 510d54b3-13de-4735-92ec-04fd4b9d460e
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b0c2d415b977c069e351d90fa5ad68b430c3f2f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262262"
---
# <a name="mandatory-data-element-missing"></a><span data-ttu-id="b1d77-102">遺失必要的資料元素</span><span class="sxs-lookup"><span data-stu-id="b1d77-102">Mandatory data element missing</span></span>
## <a name="details"></a><span data-ttu-id="b1d77-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b1d77-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b1d77-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="b1d77-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="b1d77-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="b1d77-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="b1d77-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="b1d77-106">Event ID</span></span>|-|  
|<span data-ttu-id="b1d77-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="b1d77-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="b1d77-108">EDI</span><span class="sxs-lookup"><span data-stu-id="b1d77-108"> EDI</span></span>|  
|<span data-ttu-id="b1d77-109">元件</span><span class="sxs-lookup"><span data-stu-id="b1d77-109">Component</span></span>|<span data-ttu-id="b1d77-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="b1d77-110">EDI Engine</span></span>|  
|<span data-ttu-id="b1d77-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="b1d77-111">Symbolic Name</span></span>|<span data-ttu-id="b1d77-112">X12DeMandatoryDataElementMissingDescription</span><span class="sxs-lookup"><span data-stu-id="b1d77-112">X12DeMandatoryDataElementMissingDescription</span></span>|  
|<span data-ttu-id="b1d77-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="b1d77-113">Message Text</span></span>|<span data-ttu-id="b1d77-114">遺失必要的資料元素</span><span class="sxs-lookup"><span data-stu-id="b1d77-114">Mandatory data element missing</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b1d77-115">說明</span><span class="sxs-lookup"><span data-stu-id="b1d77-115">Explanation</span></span>  
 <span data-ttu-id="b1d77-116">這個錯誤/警告/資訊事件表示，由於內送 X12 交換中不含訊息結構描述 (minOccurs 大於 0) 需要的資料元素，因此接收管線無法處理該交換。</span><span class="sxs-lookup"><span data-stu-id="b1d77-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming X12 interchange because the interchange did not contain a data element that is required by the message schema (for which minOccurs is greater than 0).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b1d77-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="b1d77-117">User Action</span></span>  
 <span data-ttu-id="b1d77-118">若要解決這個錯誤，請確定此交換包含所需的訊息結構描述中的資料元素，並再有訊息重新傳送。</span><span class="sxs-lookup"><span data-stu-id="b1d77-118">To resolve this error, make sure that the interchange contains all the data elements required by the message schema, and then have the message resent.</span></span>