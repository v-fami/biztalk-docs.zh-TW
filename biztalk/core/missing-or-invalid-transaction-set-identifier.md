---
title: 遺漏或無效的交易集識別項 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 282c8128-7d23-44e2-bf44-e90e52cb5fb1
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f23f44587abf67e608cff79150d9633f1707ff2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263006"
---
# <a name="missing-or-invalid-transaction-set-identifier"></a><span data-ttu-id="721d9-102">遺漏或無效的交易集識別項</span><span class="sxs-lookup"><span data-stu-id="721d9-102">Missing or invalid Transaction set identifier</span></span>
## <a name="details"></a><span data-ttu-id="721d9-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="721d9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="721d9-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="721d9-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="721d9-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="721d9-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="721d9-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="721d9-106">Event ID</span></span>|-|  
|<span data-ttu-id="721d9-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="721d9-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="721d9-108">EDI</span><span class="sxs-lookup"><span data-stu-id="721d9-108"> EDI</span></span>|  
|<span data-ttu-id="721d9-109">元件</span><span class="sxs-lookup"><span data-stu-id="721d9-109">Component</span></span>|<span data-ttu-id="721d9-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="721d9-110">EDI Engine</span></span>|  
|<span data-ttu-id="721d9-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="721d9-111">Symbolic Name</span></span>|<span data-ttu-id="721d9-112">EfactTsMissingOrInvalidTsIdentiferDescription</span><span class="sxs-lookup"><span data-stu-id="721d9-112">EfactTsMissingOrInvalidTsIdentiferDescription</span></span>|  
|<span data-ttu-id="721d9-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="721d9-113">Message Text</span></span>|<span data-ttu-id="721d9-114">遺漏或無效的交易集識別項</span><span class="sxs-lookup"><span data-stu-id="721d9-114">Missing or invalid Transaction set identifier</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="721d9-115">說明</span><span class="sxs-lookup"><span data-stu-id="721d9-115">Explanation</span></span>  
 <span data-ttu-id="721d9-116">這個錯誤/警告/資訊事件表示，接收或傳送管線無法處理 EDIFACT 交換，因為交易集識別項 （在 [UNH2.1] 欄位中） 的值已遺失或有無效的值。</span><span class="sxs-lookup"><span data-stu-id="721d9-116">This Error/Warning/Information event indicates that the receive or send pipeline could not process the EDIFACT interchange because the value of the transaction set identifier (in the UNH2.1 field) was missing or had an invalid value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="721d9-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="721d9-117">User Action</span></span>  
 <span data-ttu-id="721d9-118">若要解決這個錯誤，請確定交換已 UNH2.1 欄位的值。</span><span class="sxs-lookup"><span data-stu-id="721d9-118">To resolve this error, make sure that the interchange has a value for the UNH2.1 field.</span></span> <span data-ttu-id="721d9-119">請確認 UNH2.1 的值為有效的單位數以六位數文件類型指示項。</span><span class="sxs-lookup"><span data-stu-id="721d9-119">Verify that the value of UNH2.1 is a valid one-digit to six-digit document-type designator.</span></span>