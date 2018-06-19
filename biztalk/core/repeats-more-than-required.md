---
title: 重複以上需要 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fec52b5b-e95f-479e-8922-dcf17dcefee7
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5cb8f9e324c9d09e09649719c98e3f684b0d81f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268222"
---
# <a name="repeats-more-than-required"></a><span data-ttu-id="d7f94-102">重複以上所需</span><span class="sxs-lookup"><span data-stu-id="d7f94-102">Repeats more than required</span></span>
## <a name="details"></a><span data-ttu-id="d7f94-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d7f94-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d7f94-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d7f94-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="d7f94-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="d7f94-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="d7f94-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d7f94-106">Event ID</span></span>|-|  
|<span data-ttu-id="d7f94-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="d7f94-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d7f94-108">EDI</span><span class="sxs-lookup"><span data-stu-id="d7f94-108"> EDI</span></span>|  
|<span data-ttu-id="d7f94-109">元件</span><span class="sxs-lookup"><span data-stu-id="d7f94-109">Component</span></span>|<span data-ttu-id="d7f94-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="d7f94-110">EDI Engine</span></span>|  
|<span data-ttu-id="d7f94-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d7f94-111">Symbolic Name</span></span>|<span data-ttu-id="d7f94-112">X12FeRepeatsMoreThanRequiredDescription</span><span class="sxs-lookup"><span data-stu-id="d7f94-112">X12FeRepeatsMoreThanRequiredDescription</span></span>|  
|<span data-ttu-id="d7f94-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d7f94-113">Message Text</span></span>|<span data-ttu-id="d7f94-114">重複以上所需</span><span class="sxs-lookup"><span data-stu-id="d7f94-114">Repeats more than required</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d7f94-115">說明</span><span class="sxs-lookup"><span data-stu-id="d7f94-115">Explanation</span></span>  
 <span data-ttu-id="d7f94-116">這個錯誤/警告/資訊事件表示區段中的 X12 交換的是內部或外部迴圈會重複多次的文件結構描述所要求。</span><span class="sxs-lookup"><span data-stu-id="d7f94-116">This Error/Warning/Information event indicates that segments in an X12 interchange that are either inside or outside of a loop repeated more times than required by the document schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d7f94-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d7f94-117">User Action</span></span>  
 <span data-ttu-id="d7f94-118">若要解決此錯誤，確定交換中迴圈內外的區段重複結構描述中所指定的次數，然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="d7f94-118">To resolve this error, make sure that the segments that are either inside or outside of a loop in the interchange repeat the numbers of times specified in the schema, and then resend the interchange.</span></span>