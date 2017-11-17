---
title: "遺漏或無效或重複的交易集識別項 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8580aab2-9fa4-43fb-b643-10621926591e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75251d0210be4ed34a74ba0f3f5cadf84d9941b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="missing-or-invalid-or-duplicate-transaction-set-identifier"></a><span data-ttu-id="dcf73-102">遺漏或無效或重複的交易集識別項</span><span class="sxs-lookup"><span data-stu-id="dcf73-102">Missing or invalid or duplicate Transaction set identifier</span></span>
## <a name="details"></a><span data-ttu-id="dcf73-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="dcf73-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dcf73-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="dcf73-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="dcf73-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="dcf73-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="dcf73-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="dcf73-106">Event ID</span></span>|-|  
|<span data-ttu-id="dcf73-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="dcf73-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="dcf73-108">EDI</span><span class="sxs-lookup"><span data-stu-id="dcf73-108"> EDI</span></span>|  
|<span data-ttu-id="dcf73-109">元件</span><span class="sxs-lookup"><span data-stu-id="dcf73-109">Component</span></span>|<span data-ttu-id="dcf73-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="dcf73-110">EDI Engine</span></span>|  
|<span data-ttu-id="dcf73-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="dcf73-111">Symbolic Name</span></span>|<span data-ttu-id="dcf73-112">X12TsMissingOrInvalidTsIdentiferDescription2</span><span class="sxs-lookup"><span data-stu-id="dcf73-112">X12TsMissingOrInvalidTsIdentiferDescription2</span></span>|  
|<span data-ttu-id="dcf73-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="dcf73-113">Message Text</span></span>|<span data-ttu-id="dcf73-114">遺漏或無效或重複的交易集識別項 '{0}'</span><span class="sxs-lookup"><span data-stu-id="dcf73-114">Missing or invalid or duplicate Transaction set identifier '{0}'</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="dcf73-115">說明</span><span class="sxs-lookup"><span data-stu-id="dcf73-115">Explanation</span></span>  
 <span data-ttu-id="dcf73-116">這個錯誤/警告/資訊事件表示接收或傳送管線無法處理 X12 交換交易的值設定識別碼 （ST01 欄位中），因為遺漏，重複出現，或有無效的值。</span><span class="sxs-lookup"><span data-stu-id="dcf73-116">This Error/Warning/Information event indicates that the receive or send pipeline could not process the X12 interchange because the value of the transaction set identifier (in the ST01 field) was missing, a duplicate, or had an invalid value.</span></span> <span data-ttu-id="dcf73-117">如果文件結構描述沒有 ST 標頭和 SE 結尾，也可能會發生。</span><span class="sxs-lookup"><span data-stu-id="dcf73-117">This can occur if the document schema does not have an ST header and an SE trailer.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="dcf73-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="dcf73-118">User Action</span></span>  
 <span data-ttu-id="dcf73-119">若要解決這個錯誤，請確定交換 ST01 欄位的值而結構描述擁有的 ST 標頭和 SE 結尾的項目。</span><span class="sxs-lookup"><span data-stu-id="dcf73-119">To resolve this error, make sure that the interchange has a value for the ST01 field and that the schema has an entry for the ST header and SE trailer.</span></span> <span data-ttu-id="dcf73-120">請確認的 ST01 值是有效的三位數文件類型指示項。</span><span class="sxs-lookup"><span data-stu-id="dcf73-120">Verify that the value of ST01 is a valid three-digit document-type designator.</span></span> <span data-ttu-id="dcf73-121">請確認 ST01 欄位不是重複項目與另一個交易集合的 ST01 欄位。</span><span class="sxs-lookup"><span data-stu-id="dcf73-121">Verify that the ST01 field is not a duplicate with the ST01 field of another transaction set.</span></span>