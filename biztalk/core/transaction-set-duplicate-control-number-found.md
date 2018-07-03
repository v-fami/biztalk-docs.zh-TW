---
title: 發現交易集重複的控制編號 |Microsoft Docs
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
ms.openlocfilehash: d6b9b55dc5cd61bc4c8c806f2dc42259cadf2f69
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977704"
---
# <a name="transaction-set-duplicate-control-number-found"></a><span data-ttu-id="cd810-102">發現交易集重複的控制編號</span><span class="sxs-lookup"><span data-stu-id="cd810-102">Transaction Set duplicate control number found</span></span>
## <a name="details"></a><span data-ttu-id="cd810-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="cd810-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="cd810-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="cd810-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="cd810-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="cd810-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="cd810-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="cd810-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="cd810-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="cd810-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="cd810-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="cd810-108"> EDI</span></span> |
|    <span data-ttu-id="cd810-109">元件</span><span class="sxs-lookup"><span data-stu-id="cd810-109">Component</span></span>    |                                       <span data-ttu-id="cd810-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="cd810-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="cd810-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="cd810-111">Symbolic Name</span></span>  |                          <span data-ttu-id="cd810-112">X12TsDuplicateNumberFoundDescription</span><span class="sxs-lookup"><span data-stu-id="cd810-112">X12TsDuplicateNumberFoundDescription</span></span>                          |
|  <span data-ttu-id="cd810-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="cd810-113">Message Text</span></span>   |                     <span data-ttu-id="cd810-114">發現交易集重複的控制編號</span><span class="sxs-lookup"><span data-stu-id="cd810-114">Transaction Set duplicate control number found</span></span>                     |
  
## <a name="explanation"></a><span data-ttu-id="cd810-115">說明</span><span class="sxs-lookup"><span data-stu-id="cd810-115">Explanation</span></span>  
 <span data-ttu-id="cd810-116">這個錯誤/警告/資訊事件表示接收管線無法處理內送 X12 交換的交易集控制編號的群組中的交易集因為交換已與另一個的控制編號相同交易集在該群組中。</span><span class="sxs-lookup"><span data-stu-id="cd810-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming X12 interchange because the transaction set control number for a transaction set in a group of that interchange was the same as the control number for another transaction set in that group.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cd810-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="cd810-117">User Action</span></span>  
 <span data-ttu-id="cd810-118">若要解決這個錯誤，請執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="cd810-118">To resolve this error, do one of the following:</span></span>  
  
-   <span data-ttu-id="cd810-119">群組中的交易集的控制交易的數目會設定內送交換中，因此會不有任何重複的控制編號，交易的變更集。</span><span class="sxs-lookup"><span data-stu-id="cd810-119">Change the transaction set control numbers of transaction sets in incoming interchange so there are no duplicate control numbers for transaction sets in a group.</span></span>  
  
-   <span data-ttu-id="cd810-120">如下所示停用檢查重複的交易集控制編號：</span><span class="sxs-lookup"><span data-stu-id="cd810-120">Disable the check for duplicate transaction set control numbers as follows:</span></span>  
  
    1.  <span data-ttu-id="cd810-121">開啟 [BizTalk Server 管理] 主控台。</span><span class="sxs-lookup"><span data-stu-id="cd810-121">Open the BizTalk Server Administration Console.</span></span>  
  
    2.  <span data-ttu-id="cd810-122">開啟傳送交換的合作對象 [EDI 屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="cd810-122">Open the EDI Properties dialog box for the party that sent the interchange.</span></span>  
  
    3.  <span data-ttu-id="cd810-123">對於 X12 交換，清除 「 檢查重複項目 ST2 （交易集控制編號） 群組中 」 的 X12 交換處理屬性頁面的 EDI 屬性 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="cd810-123">For X12 interchanges, clear the "Check for duplicate ST2 (Transaction set control number) in group" in the X12 Interchange Processing Properties Page of the EDI Properties dialog box.</span></span>  
  
    4.  <span data-ttu-id="cd810-124">對於 EDIFACT 交換，清除 「 檢查重複項目 UNH1 （交易集參考編號） 群組中"[EDIFACT 交換處理屬性] 頁面的 [EDI 屬性] 對話方塊中的屬性。</span><span class="sxs-lookup"><span data-stu-id="cd810-124">For EDIFACT interchanges, clear the "Check for duplicate UNH1 (Transaction set reference number) in group" property in the EDIFACT Interchange Processing Properties Page of the EDI Properties dialog box.</span></span>