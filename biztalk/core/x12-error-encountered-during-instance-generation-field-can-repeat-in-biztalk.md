---
title: 欄位可以重複執行個體產生-期間發生錯誤，但尚未定義重複分隔符號 |Microsoft 文件
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
ms.openlocfilehash: 366caec69fd84b91cf815a58e4975e8e5d7b4d06
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22290102"
---
# <a name="error-encountered-during-instance-generation--field-can-repeat-but-repetition-delimiter-has-not-been-defined"></a><span data-ttu-id="00f37-102">欄位可以重複執行個體產生-期間發生錯誤，但尚未定義重複分隔符號</span><span class="sxs-lookup"><span data-stu-id="00f37-102">Error encountered during instance generation--field can repeat but repetition delimiter has not been defined</span></span>
## <a name="details"></a><span data-ttu-id="00f37-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="00f37-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="00f37-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="00f37-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="00f37-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="00f37-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="00f37-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="00f37-106">Event ID</span></span>|-|  
|<span data-ttu-id="00f37-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="00f37-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="00f37-108">EDI</span><span class="sxs-lookup"><span data-stu-id="00f37-108"> EDI</span></span>|  
|<span data-ttu-id="00f37-109">元件</span><span class="sxs-lookup"><span data-stu-id="00f37-109">Component</span></span>|<span data-ttu-id="00f37-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="00f37-110">EDI Engine</span></span>|  
|<span data-ttu-id="00f37-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="00f37-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="00f37-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="00f37-112">Message Text</span></span>|<span data-ttu-id="00f37-113">執行個體產生期間發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="00f37-113">Error encountered during instance generation.</span></span> <span data-ttu-id="00f37-114">欄位 {0} 可以重複，但尚未定義重複分隔符號。</span><span class="sxs-lookup"><span data-stu-id="00f37-114">The field {0} can repeat but repetition delimiter has not been defined.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="00f37-115">說明</span><span class="sxs-lookup"><span data-stu-id="00f37-115">Explanation</span></span>  
 <span data-ttu-id="00f37-116">這個錯誤/警告/資訊事件表示 BizTalk Server 無法產生的 X12 訊息執行個體，因為指定的欄位可以重複 （如指定結構描述），但尚未定義任何重複分隔符號。</span><span class="sxs-lookup"><span data-stu-id="00f37-116">This Error/Warning/Information event indicates that BizTalk Server could not generate an X12 message instance because the indicated field can repeat (as specified by the schema), but no repetition separator has been defined.</span></span> <span data-ttu-id="00f37-117">發生這種情況的欄位結構描述中的有 minOccurs 等於超過 1，但已定義標準識別項，而非重複分隔符號。</span><span class="sxs-lookup"><span data-stu-id="00f37-117">This occurs when a field in the schema has minOccurs equal to more than 1, but a Standard identifier has been defined, rather than a Repetition separator.</span></span> <span data-ttu-id="00f37-118">（若為 EDIFACT 交換重複分隔符號定義預設。）</span><span class="sxs-lookup"><span data-stu-id="00f37-118">(For EDIFACT interchanges, a repetition separator is defined by default.)</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="00f37-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="00f37-119">User Action</span></span>  
 <span data-ttu-id="00f37-120">若要解決這個錯誤，選取 重複分隔符號而非標準識別項 ISA11 ISA 區段定義 頁面中做為交換接收者的合作對象和輸入字元的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="00f37-120">To resolve this error, select Repetition separator rather than Standard identifier for ISA11 in the ISA Segment Definition page for the party as interchange receiver, and enter a character for the separator.</span></span> <span data-ttu-id="00f37-121">如果沒有合作對象已解析的交換，定義為重複分隔符號的全域屬性 [ISA 區段定義] 頁面中 （對於 X12 交換）。</span><span class="sxs-lookup"><span data-stu-id="00f37-121">If no party has been resolved for the interchange, define the repetition separator in the ISA Segment Definition page of the global properties (for X12 interchanges).</span></span>