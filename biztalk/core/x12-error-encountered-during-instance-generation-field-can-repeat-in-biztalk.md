---
title: 欄位可以重複執行個體產生--期間發生錯誤，但未定義重複分隔符號 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c7a6783c-cb35-4ce8-9164-ec34ae500de1
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c6e5ed96162adac55de0bda042a12d45b4243eef
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971143"
---
# <a name="error-encountered-during-instance-generation--field-can-repeat-but-repetition-delimiter-has-not-been-defined"></a><span data-ttu-id="22cd3-102">欄位可以重複的執行個體產生--期間發生錯誤，但未定義重複分隔符號</span><span class="sxs-lookup"><span data-stu-id="22cd3-102">Error encountered during instance generation--field can repeat but repetition delimiter has not been defined</span></span>
## <a name="details"></a><span data-ttu-id="22cd3-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="22cd3-103">Details</span></span>  
  
|                 |                                                                                                                       |
|-----------------|-----------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="22cd3-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="22cd3-104">Product Name</span></span>   |                  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                   |
| <span data-ttu-id="22cd3-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="22cd3-105">Product Version</span></span> |                              [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                               |
|    <span data-ttu-id="22cd3-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="22cd3-106">Event ID</span></span>     |                                                           -                                                           |
|  <span data-ttu-id="22cd3-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="22cd3-107">Event Source</span></span>   |                [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="22cd3-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="22cd3-108"> EDI</span></span>                 |
|    <span data-ttu-id="22cd3-109">元件</span><span class="sxs-lookup"><span data-stu-id="22cd3-109">Component</span></span>    |                                                      <span data-ttu-id="22cd3-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="22cd3-110">EDI Engine</span></span>                                                       |
|  <span data-ttu-id="22cd3-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="22cd3-111">Symbolic Name</span></span>  |                                                           -                                                           |
|  <span data-ttu-id="22cd3-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="22cd3-112">Message Text</span></span>   | <span data-ttu-id="22cd3-113">執行個體產生期間發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="22cd3-113">Error encountered during instance generation.</span></span> <span data-ttu-id="22cd3-114">欄位{0}可以重複，但未定義重複分隔符號。</span><span class="sxs-lookup"><span data-stu-id="22cd3-114">The field {0} can repeat but repetition delimiter has not been defined.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="22cd3-115">說明</span><span class="sxs-lookup"><span data-stu-id="22cd3-115">Explanation</span></span>  
 <span data-ttu-id="22cd3-116">這個錯誤/警告/資訊事件表示 BizTalk Server 無法產生的 X12 訊息執行個體，因為指定的欄位可以重複 （如所指定的結構描述），但尚未定義任何重複分隔符號。</span><span class="sxs-lookup"><span data-stu-id="22cd3-116">This Error/Warning/Information event indicates that BizTalk Server could not generate an X12 message instance because the indicated field can repeat (as specified by the schema), but no repetition separator has been defined.</span></span> <span data-ttu-id="22cd3-117">會發生這種情況是當結構描述中的欄位有 minOccurs 等於 1 個以上，但已定義的標準識別項，而不是重複分隔符號。</span><span class="sxs-lookup"><span data-stu-id="22cd3-117">This occurs when a field in the schema has minOccurs equal to more than 1, but a Standard identifier has been defined, rather than a Repetition separator.</span></span> <span data-ttu-id="22cd3-118">（若為 EDIFACT 交換重複分隔符號定義預設。）</span><span class="sxs-lookup"><span data-stu-id="22cd3-118">(For EDIFACT interchanges, a repetition separator is defined by default.)</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="22cd3-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="22cd3-119">User Action</span></span>  
 <span data-ttu-id="22cd3-120">若要解決這個錯誤，請選取重複分隔符號，而不是標準的識別碼 isa11 ISA 區段定義 頁面中做為交換接收者的合作對象的輸入做為分隔符號的字元。</span><span class="sxs-lookup"><span data-stu-id="22cd3-120">To resolve this error, select Repetition separator rather than Standard identifier for ISA11 in the ISA Segment Definition page for the party as interchange receiver, and enter a character for the separator.</span></span> <span data-ttu-id="22cd3-121">如果沒有合作對象已解析的交換，定義為重複分隔符號的全域屬性的 [ISA 區段定義] 頁面中 （對於 X12 交換）。</span><span class="sxs-lookup"><span data-stu-id="22cd3-121">If no party has been resolved for the interchange, define the repetition separator in the ISA Segment Definition page of the global properties (for X12 interchanges).</span></span>