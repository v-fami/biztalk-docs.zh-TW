---
title: "無效的控制標準識別項 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d2b5a54-7f29-49c9-8bcf-a5b4b6d07ad3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94975e63d5781200ee1bfd9d14896c1e5fe722a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-control-standard-identifier"></a><span data-ttu-id="d3d1e-102">無效的控制標準識別項</span><span class="sxs-lookup"><span data-stu-id="d3d1e-102">Invalid Control Standard Identifier</span></span>
## <a name="details"></a><span data-ttu-id="d3d1e-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d3d1e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d3d1e-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d3d1e-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="d3d1e-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="d3d1e-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="d3d1e-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d3d1e-106">Event ID</span></span>|-|  
|<span data-ttu-id="d3d1e-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="d3d1e-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d3d1e-108">EDI</span><span class="sxs-lookup"><span data-stu-id="d3d1e-108"> EDI</span></span>|  
|<span data-ttu-id="d3d1e-109">元件</span><span class="sxs-lookup"><span data-stu-id="d3d1e-109">Component</span></span>|<span data-ttu-id="d3d1e-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="d3d1e-110">EDI Engine</span></span>|  
|<span data-ttu-id="d3d1e-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d3d1e-111">Symbolic Name</span></span>|<span data-ttu-id="d3d1e-112">X12Ta1InvalidControlStandardIdentifierDescription</span><span class="sxs-lookup"><span data-stu-id="d3d1e-112">X12Ta1InvalidControlStandardIdentifierDescription</span></span>|  
|<span data-ttu-id="d3d1e-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d3d1e-113">Message Text</span></span>|<span data-ttu-id="d3d1e-114">無效的控制標準識別項</span><span class="sxs-lookup"><span data-stu-id="d3d1e-114">Invalid Control Standard Identifier</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d3d1e-115">說明</span><span class="sxs-lookup"><span data-stu-id="d3d1e-115">Explanation</span></span>  
 <span data-ttu-id="d3d1e-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為交換控制標準識別項 （欄位 ISA11） 交換中的值不符合在列舉中的項目指定由結構描述。</span><span class="sxs-lookup"><span data-stu-id="d3d1e-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the value of the interchange control standards identifier (field ISA11) in the interchange did not match an entry in the enumeration specified by the schema.</span></span> <span data-ttu-id="d3d1e-117">結構描述是 x12serviceschema EdifactServiceSchema BaseArtifacts.dll 中。</span><span class="sxs-lookup"><span data-stu-id="d3d1e-117">The schema is the X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d3d1e-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d3d1e-118">User Action</span></span>  
 <span data-ttu-id="d3d1e-119">若要解決這個錯誤，請確定交換中使用的交換控制標準識別項符合 ISA11 的欄位列舉中的項目，然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="d3d1e-119">To resolve this error, make sure that the interchange control standards identifier used in the interchange matches an entry in the enumeration for the ISA11 field, and then have the interchange resent.</span></span>