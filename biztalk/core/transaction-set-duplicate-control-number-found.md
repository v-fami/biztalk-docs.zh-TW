---
title: 交易集的重複控制編號找到 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1b2779a0-b365-4c4b-81c7-8f9284748b6e
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe63d3814bcce178164054ab8dcf673eeb4f395a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278558"
---
# <a name="transaction-set-duplicate-control-number-found"></a><span data-ttu-id="f4a57-102">找到的交易集重複控制編號</span><span class="sxs-lookup"><span data-stu-id="f4a57-102">Transaction Set duplicate control number found</span></span>
## <a name="details"></a><span data-ttu-id="f4a57-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f4a57-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f4a57-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f4a57-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="f4a57-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="f4a57-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="f4a57-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f4a57-106">Event ID</span></span>|-|  
|<span data-ttu-id="f4a57-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="f4a57-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f4a57-108">EDI</span><span class="sxs-lookup"><span data-stu-id="f4a57-108"> EDI</span></span>|  
|<span data-ttu-id="f4a57-109">元件</span><span class="sxs-lookup"><span data-stu-id="f4a57-109">Component</span></span>|<span data-ttu-id="f4a57-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="f4a57-110">EDI Engine</span></span>|  
|<span data-ttu-id="f4a57-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f4a57-111">Symbolic Name</span></span>|<span data-ttu-id="f4a57-112">X12TsDuplicateNumberFoundDescription</span><span class="sxs-lookup"><span data-stu-id="f4a57-112">X12TsDuplicateNumberFoundDescription</span></span>|  
|<span data-ttu-id="f4a57-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f4a57-113">Message Text</span></span>|<span data-ttu-id="f4a57-114">找到的交易集重複控制編號</span><span class="sxs-lookup"><span data-stu-id="f4a57-114">Transaction Set duplicate control number found</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f4a57-115">說明</span><span class="sxs-lookup"><span data-stu-id="f4a57-115">Explanation</span></span>  
 <span data-ttu-id="f4a57-116">這個錯誤/警告/資訊事件表示接收管線無法處理內送 X12 交換的交易集控制編號的群組中的交易集，因為已交換控制編號，另一個相同該群組中的交易集。</span><span class="sxs-lookup"><span data-stu-id="f4a57-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming X12 interchange because the transaction set control number for a transaction set in a group of that interchange was the same as the control number for another transaction set in that group.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f4a57-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f4a57-117">User Action</span></span>  
 <span data-ttu-id="f4a57-118">若要解決這個錯誤，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="f4a57-118">To resolve this error, do one of the following:</span></span>  
  
-   <span data-ttu-id="f4a57-119">群組中的交易集的控制交易的數字設定內送交換中，因此交易不重複控制編號的變更集。</span><span class="sxs-lookup"><span data-stu-id="f4a57-119">Change the transaction set control numbers of transaction sets in incoming interchange so there are no duplicate control numbers for transaction sets in a group.</span></span>  
  
-   <span data-ttu-id="f4a57-120">停用重複交易集控制編號檢查如下：</span><span class="sxs-lookup"><span data-stu-id="f4a57-120">Disable the check for duplicate transaction set control numbers as follows:</span></span>  
  
    1.  <span data-ttu-id="f4a57-121">開啟 [BizTalk Server 管理] 主控台。</span><span class="sxs-lookup"><span data-stu-id="f4a57-121">Open the BizTalk Server Administration Console.</span></span>  
  
    2.  <span data-ttu-id="f4a57-122">開啟傳送交換的合作對象 [EDI 屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f4a57-122">Open the EDI Properties dialog box for the party that sent the interchange.</span></span>  
  
    3.  <span data-ttu-id="f4a57-123">對於 X12 交換，清除 「 核取的重複項目 ST2 （交易集控制編號） 群組中 」 的 [X12 交換處理屬性] 頁面的 [EDI 屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f4a57-123">For X12 interchanges, clear the "Check for duplicate ST2 (Transaction set control number) in group" in the X12 Interchange Processing Properties Page of the EDI Properties dialog box.</span></span>  
  
    4.  <span data-ttu-id="f4a57-124">對於 EDIFACT 交換，清除 「 核取的重複 UNH1 （交易集參考編號） 群組中 「 [EDIFACT 交換處理屬性] 頁面的 [EDI 屬性] 對話方塊中的屬性。</span><span class="sxs-lookup"><span data-stu-id="f4a57-124">For EDIFACT interchanges, clear the "Check for duplicate UNH1 (Transaction set reference number) in group" property in the EDIFACT Interchange Processing Properties Page of the EDI Properties dialog box.</span></span>