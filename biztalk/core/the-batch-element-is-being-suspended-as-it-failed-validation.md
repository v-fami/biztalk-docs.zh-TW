---
title: "因為驗證失敗處於暫停狀態的批次項目 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea5e19e8-4592-40f4-bffe-85ab27653fd5
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7022041d8d47e1bfa52eb7ef45764c17ed1a2d8d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-batch-element-is-being-suspended-as-it-failed-validation"></a><span data-ttu-id="a264d-102">批次項目已暫停驗證失敗</span><span class="sxs-lookup"><span data-stu-id="a264d-102">The batch element is being suspended as it failed validation</span></span>
## <a name="details"></a><span data-ttu-id="a264d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a264d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a264d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a264d-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="a264d-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="a264d-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="a264d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a264d-106">Event ID</span></span>|-|  
|<span data-ttu-id="a264d-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="a264d-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a264d-108">EDI</span><span class="sxs-lookup"><span data-stu-id="a264d-108"> EDI</span></span>|  
|<span data-ttu-id="a264d-109">元件</span><span class="sxs-lookup"><span data-stu-id="a264d-109">Component</span></span>|<span data-ttu-id="a264d-110">批次處理引擎</span><span class="sxs-lookup"><span data-stu-id="a264d-110">Batching Engine</span></span>|  
|<span data-ttu-id="a264d-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a264d-111">Symbolic Name</span></span>|<span data-ttu-id="a264d-112">BatchElementSuspended</span><span class="sxs-lookup"><span data-stu-id="a264d-112">BatchElementSuspended</span></span>|  
|<span data-ttu-id="a264d-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a264d-113">Message Text</span></span>|<span data-ttu-id="a264d-114">驗證失敗的批次項目是已暫停。</span><span class="sxs-lookup"><span data-stu-id="a264d-114">The batch element is being suspended as it failed validation.</span></span> <span data-ttu-id="a264d-115">錯誤： {0}</span><span class="sxs-lookup"><span data-stu-id="a264d-115">The error is : {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a264d-116">說明</span><span class="sxs-lookup"><span data-stu-id="a264d-116">Explanation</span></span>  
 <span data-ttu-id="a264d-117">這個錯誤/警告/資訊事件表示批次處理協調流程無法將交易設定為批次交換，因為交易設定失敗，批次處理協調流程所執行的驗證。</span><span class="sxs-lookup"><span data-stu-id="a264d-117">This Error/Warning/Information event indicates that the batching orchestration could not add a transaction set to a batched interchange because the transaction set failed the validation performed by the batching orchestration.</span></span> <span data-ttu-id="a264d-118">沒有交易集驗證失敗，就會產生交換。</span><span class="sxs-lookup"><span data-stu-id="a264d-118">The interchange will be generated without the transaction set that failed validation.</span></span> <span data-ttu-id="a264d-119">批次處理協調流程中設定 EDI。BatchElementValidationFailure 內容屬性為"True"。</span><span class="sxs-lookup"><span data-stu-id="a264d-119">The batching orchestration sets the EDI.BatchElementValidationFailure context property to "True".</span></span> <span data-ttu-id="a264d-120">BatchSuspend 協調流程將會根據該內容屬性收取訊息、發佈錯誤資訊，然後再擱置訊息。</span><span class="sxs-lookup"><span data-stu-id="a264d-120">The BatchSuspend orchestration picks up the message based upon that context property, posts error information, and then is suspended.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a264d-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a264d-121">User Action</span></span>  
 <span data-ttu-id="a264d-122">若要解決這個錯誤，表示寄件者的交易集發生的錯誤，錯誤訊息中所示。</span><span class="sxs-lookup"><span data-stu-id="a264d-122">To resolve this error, indicate to the sender of the transaction set what error occurred, as indicated in the error message.</span></span> <span data-ttu-id="a264d-123">已解決的問題，導致無法通過驗證，然後再重新傳送交易集合寄件者。</span><span class="sxs-lookup"><span data-stu-id="a264d-123">Have the sender resolve the issue that caused it to fail validation, and then resend the transaction set.</span></span>