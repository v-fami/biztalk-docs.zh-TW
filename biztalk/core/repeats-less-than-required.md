---
title: 重複少於所需 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5bebc13-0e70-4f73-99c0-fed917d79fba
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d88fe1868a91bce7208c0da557f20211cde23109
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268526"
---
# <a name="repeats-less-than-required"></a><span data-ttu-id="22141-102">重複少於所需的次數</span><span class="sxs-lookup"><span data-stu-id="22141-102">Repeats less than required</span></span>
## <a name="details"></a><span data-ttu-id="22141-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="22141-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="22141-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="22141-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="22141-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="22141-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="22141-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="22141-106">Event ID</span></span>|-|  
|<span data-ttu-id="22141-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="22141-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="22141-108">EDI</span><span class="sxs-lookup"><span data-stu-id="22141-108"> EDI</span></span>|  
|<span data-ttu-id="22141-109">元件</span><span class="sxs-lookup"><span data-stu-id="22141-109">Component</span></span>|<span data-ttu-id="22141-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="22141-110">EDI Engine</span></span>|  
|<span data-ttu-id="22141-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="22141-111">Symbolic Name</span></span>|<span data-ttu-id="22141-112">X12FeRepeatsLessThanRequiredDescription</span><span class="sxs-lookup"><span data-stu-id="22141-112">X12FeRepeatsLessThanRequiredDescription</span></span>|  
|<span data-ttu-id="22141-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="22141-113">Message Text</span></span>|<span data-ttu-id="22141-114">重複少於所需的次數</span><span class="sxs-lookup"><span data-stu-id="22141-114">Repeats less than required</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="22141-115">說明</span><span class="sxs-lookup"><span data-stu-id="22141-115">Explanation</span></span>  
 <span data-ttu-id="22141-116">這個錯誤/警告/資訊事件表示迴圈內外之 X12 交換的區段重複次數少於文件結構描述所要求的次數。</span><span class="sxs-lookup"><span data-stu-id="22141-116">This Error/Warning/Information event indicates that segments in an X12 interchange that are either inside or outside of a loop repeated fewer times than required by the document schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="22141-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="22141-117">User Action</span></span>  
 <span data-ttu-id="22141-118">若要解決此錯誤，確定交換中迴圈內外的區段重複結構描述中所指定的次數，然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="22141-118">To resolve this error, make sure that the segments that are either inside or outside of a loop in the interchange repeat the numbers of times specified in the schema, and then resend the interchange.</span></span>