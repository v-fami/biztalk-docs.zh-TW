---
title: "無效的授權辨識符號 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc2a9f83-833f-4ea0-9421-7382ee1b1a54
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dbf33e8bd42b18134bd31f02f791b306ece97272
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-authorization-qualifier"></a><span data-ttu-id="d8582-102">無效的授權辨識符號</span><span class="sxs-lookup"><span data-stu-id="d8582-102">Invalid Authorization Qualifier</span></span>
## <a name="details"></a><span data-ttu-id="d8582-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d8582-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d8582-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d8582-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="d8582-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="d8582-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="d8582-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d8582-106">Event ID</span></span>|-|  
|<span data-ttu-id="d8582-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="d8582-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d8582-108">EDI</span><span class="sxs-lookup"><span data-stu-id="d8582-108"> EDI</span></span>|  
|<span data-ttu-id="d8582-109">元件</span><span class="sxs-lookup"><span data-stu-id="d8582-109">Component</span></span>|<span data-ttu-id="d8582-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="d8582-110">EDI Engine</span></span>|  
|<span data-ttu-id="d8582-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d8582-111">Symbolic Name</span></span>|<span data-ttu-id="d8582-112">X12Ta1InvalidAuthorizationQualifierDescription</span><span class="sxs-lookup"><span data-stu-id="d8582-112">X12Ta1InvalidAuthorizationQualifierDescription</span></span>|  
|<span data-ttu-id="d8582-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d8582-113">Message Text</span></span>|<span data-ttu-id="d8582-114">無效的授權辨識符號</span><span class="sxs-lookup"><span data-stu-id="d8582-114">Invalid Authorization Qualifier</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d8582-115">說明</span><span class="sxs-lookup"><span data-stu-id="d8582-115">Explanation</span></span>  
 <span data-ttu-id="d8582-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為 ISA01 中的 授權辨識符號的值不符合任何結構描述所指定的列舉值。</span><span class="sxs-lookup"><span data-stu-id="d8582-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the value of the Authorization Qualifier in ISA01 did not match any of the enumeration values specified by the schema.</span></span> <span data-ttu-id="d8582-117">結構描述是 X12ServiceSchema BaseArtifacts.dll 中。</span><span class="sxs-lookup"><span data-stu-id="d8582-117">The schema is the X12ServiceSchema in BaseArtifacts.dll.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d8582-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d8582-118">User Action</span></span>  
 <span data-ttu-id="d8582-119">若要解決這個錯誤，請確定 ISA01 標頭中的值符合其中一個 X12ServiceSchema，所指定的列舉值，然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="d8582-119">To resolve this error, make sure that the value in the ISA01 header matches one of the enumeration values specified by the X12ServiceSchema, and then have the interchange resent.</span></span>