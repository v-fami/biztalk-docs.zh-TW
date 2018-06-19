---
title: 不正確的 Doctype |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67233aae-65c0-4689-a4b3-60a48132343a
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fec7dc4f2dfed0c8e8b8fcde13593d4e29997f7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239142"
---
# <a name="doctype-is-invalid"></a><span data-ttu-id="b9802-102">文件類型不正確</span><span class="sxs-lookup"><span data-stu-id="b9802-102">Doctype is invalid</span></span>
## <a name="details"></a><span data-ttu-id="b9802-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b9802-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b9802-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="b9802-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="b9802-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="b9802-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="b9802-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="b9802-106">Event ID</span></span>|-|  
|<span data-ttu-id="b9802-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="b9802-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="b9802-108">EDI</span><span class="sxs-lookup"><span data-stu-id="b9802-108"> EDI</span></span>|  
|<span data-ttu-id="b9802-109">元件</span><span class="sxs-lookup"><span data-stu-id="b9802-109">Component</span></span>|<span data-ttu-id="b9802-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="b9802-110">EDI Engine</span></span>|  
|<span data-ttu-id="b9802-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="b9802-111">Symbolic Name</span></span>|<span data-ttu-id="b9802-112">DocTypeInvalidFormat</span><span class="sxs-lookup"><span data-stu-id="b9802-112">DocTypeInvalidFormat</span></span>|  
|<span data-ttu-id="b9802-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="b9802-113">Message Text</span></span>|<span data-ttu-id="b9802-114">Doctype {0} 無效。</span><span class="sxs-lookup"><span data-stu-id="b9802-114">Doctype {0} is invalid.</span></span> <span data-ttu-id="b9802-115">不可能決定一或多個命名空間、 版本或交易集識別碼</span><span class="sxs-lookup"><span data-stu-id="b9802-115">It is not possible to determine one or more of namespace, version or transaction set id</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b9802-116">說明</span><span class="sxs-lookup"><span data-stu-id="b9802-116">Explanation</span></span>  
 <span data-ttu-id="b9802-117">這個錯誤/警告/資訊事件表示 EDI 接收管線無法處理內送的交換，因為結構描述不正確地探索到。</span><span class="sxs-lookup"><span data-stu-id="b9802-117">This Error/Warning/Information event indicates that the EDI receive pipeline was not able to process the incoming interchange, because the schema was not discovered correctly.</span></span>  
  
 <span data-ttu-id="b9802-118">對於 X12，目標命名空間由決定在 「 啟用自訂交易集定義 方格中的 x12 交換處理屬性頁面的 EDI 屬性 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b9802-118">For X12, the target namespace is determined in the "Enable custom transaction set definitions" grid of the X12 Interchange Processing Properties page of the EDI Properties dialog box.</span></span> <span data-ttu-id="b9802-119">訊息中的 GS02 和 ST01 值必須符合資料列的方格中，為了正確識別目標命名空間中。</span><span class="sxs-lookup"><span data-stu-id="b9802-119">The GS02 and ST01 values in the message must match those in a row of the grid, to correctly identify the target namespace.</span></span> <span data-ttu-id="b9802-120">在 內送交易集識別的目標命名空間中新增的版本 （GS08 的前五個字元） 和文件類型 (ST01) 時，會建立用於交易集的結構描述名稱。</span><span class="sxs-lookup"><span data-stu-id="b9802-120">The name of the schema to be used for the transaction set is created by adding the version (the first five characters of GS08) and the doctype (ST01) in the incoming transaction set to the target namespace identified.</span></span>  
  
 <span data-ttu-id="b9802-121">對於 EDIFACT，目標命名空間是由決定在 「 啟用自訂交易集定義 方格中的 EDI 屬性 對話方塊的 EDIFACT 交換處理屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="b9802-121">For EDIFACT, the target namespace is determined in the "Enable custom transaction set definitions" grid of the EDIFACT Interchange Processing Properties page of the EDI Properties dialog box.</span></span> <span data-ttu-id="b9802-122">訊息中的 UNH2.1、 UNH2.2、 UNH2.3、 UNH2.5、 UNG2.1 和 UNG2.2 值必須符合資料列的方格中，為了正確識別目標命名空間中。</span><span class="sxs-lookup"><span data-stu-id="b9802-122">The UNH2.1, UNH2.2, UNH2.3, UNH2.5, UNG2.1, and UNG2.2 values in the message must match those in a row of the grid, to correctly identify the target namespace.</span></span> <span data-ttu-id="b9802-123">UNH2.2、 UNH2.3、 在訊息版次號碼和中的訊息類型 UNH2.1 中內送交易集識別的目標命名空間中新增訊息版本號碼會建立要用於交易集的結構描述名稱。</span><span class="sxs-lookup"><span data-stu-id="b9802-123">The name of the schema to be used for the transaction set is created by adding the message version number in UNH2.2, the message release number in UNH2.3, and the message type in UNH2.1 in the incoming transaction set to the target namespace identified.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b9802-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="b9802-124">User Action</span></span>  
 <span data-ttu-id="b9802-125">若要解決這個錯誤，執行作業，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b9802-125">To resolve this error, do as follows:</span></span>  
  
1.  <span data-ttu-id="b9802-126">請在 「 啟用自訂交易集定義 方格中的資料列，交換處理屬性頁面的 EDI 屬性 對話方塊的正確識別交易集的結構描述的命名空間。</span><span class="sxs-lookup"><span data-stu-id="b9802-126">Ensure that the namespace for the schema for the transaction set is correctly identified by a row in the "Enable custom transaction set definitions" grid of the Interchange Processing Properties page of the EDI Properties dialog box.</span></span> <span data-ttu-id="b9802-127">如果沒有，則變更方格中的值。</span><span class="sxs-lookup"><span data-stu-id="b9802-127">If not, change the values in the grid.</span></span>  
  
2.  <span data-ttu-id="b9802-128">如果已正確識別命名空間，判斷用來識別結構描述的值是否正確。</span><span class="sxs-lookup"><span data-stu-id="b9802-128">If the namespace has been correctly identified, determine whether the values that are used to identify the schema are correct.</span></span> <span data-ttu-id="b9802-129">對於 X12，它們是版本 （GS08 的前五個字元） 和內送交易集的文件類型 (ST01)。</span><span class="sxs-lookup"><span data-stu-id="b9802-129">For X12, they are the version (the first five characters of GS08) and the doctype (ST01) in the incoming transaction set.</span></span> <span data-ttu-id="b9802-130">對於 EDIFACT，它們是 UNH2.2、 UNH2.3、 在訊息版次號碼和訊息類型 UNH2.1 中內送交易集的訊息版本號碼。</span><span class="sxs-lookup"><span data-stu-id="b9802-130">For EDIFACT, they are message version number in UNH2.2, the message release number in UNH2.3, and the message type in UNH2.1 in the incoming transaction set.</span></span> <span data-ttu-id="b9802-131">如果值不正確，讓傳送者的交易集變更的值，這些欄位，然後再重新傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="b9802-131">If the values are incorrectly, have the sender of the transaction set change the values of those fields, and then resend the message.</span></span>