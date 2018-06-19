---
title: 在剖析期間發生錯誤。 X12 交易集包含在功能群組中處於暫停狀態，錯誤如下 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51c6fa8e-d81c-4ccb-93b4-852ab184c4e9
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6aa837fb86b34cfdd696874dd02ba26635bf7356
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241646"
---
# <a name="error-encountered-during-parsing-the-x12-transaction-set-contained-in-functional-group-is-being-suspended-with-following-errors"></a><span data-ttu-id="25070-103">在剖析期間發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="25070-103">Error encountered during parsing.</span></span> <span data-ttu-id="25070-104">X12 交易集包含在功能群組中處於暫停狀態，錯誤如下</span><span class="sxs-lookup"><span data-stu-id="25070-104">The X12 transaction set contained in functional group is being suspended with following errors</span></span>
## <a name="details"></a><span data-ttu-id="25070-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="25070-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="25070-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="25070-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="25070-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="25070-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="25070-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="25070-108">Event ID</span></span>|-|  
|<span data-ttu-id="25070-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="25070-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="25070-110">EDI</span><span class="sxs-lookup"><span data-stu-id="25070-110"> EDI</span></span>|  
|<span data-ttu-id="25070-111">元件</span><span class="sxs-lookup"><span data-stu-id="25070-111">Component</span></span>|<span data-ttu-id="25070-112">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="25070-112">EDI Engine</span></span>|  
|<span data-ttu-id="25070-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="25070-113">Symbolic Name</span></span>|<span data-ttu-id="25070-114">X12TransactionSetReceiveError</span><span class="sxs-lookup"><span data-stu-id="25070-114">X12TransactionSetReceiveError</span></span>|  
|<span data-ttu-id="25070-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="25070-115">Message Text</span></span>|<span data-ttu-id="25070-116">在剖析期間發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="25070-116">Error encountered during parsing.</span></span> <span data-ttu-id="25070-117">X12 交易集識別碼為 '{0}' 中識別碼為 '{1}'，識別碼為 '{2}'，交換中使用寄件者識別碼 '{3}'，'\ {4' 的接收者識別碼的功能群組處於暫停狀態，錯誤如下：</span><span class="sxs-lookup"><span data-stu-id="25070-117">The X12 transaction set with id '{0}' contained in functional group with id '{1}', in interchange with id '{2}', with sender id '{3}', receiver id '{4}' is being suspended with following errors:</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="25070-118">說明</span><span class="sxs-lookup"><span data-stu-id="25070-118">Explanation</span></span>  
 <span data-ttu-id="25070-119">這個錯誤/警告/資訊事件表示因為識別的交易集之敘述的錯誤，EDI 接收管線在剖析內送 X12 交換時遇到錯誤。</span><span class="sxs-lookup"><span data-stu-id="25070-119">This Error/Warning/Information event indicates that the EDI receive pipeline encountered an error when parsing an incoming X12 interchange because of the stated errors with the identified transaction set.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="25070-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="25070-120">User Action</span></span>  
 <span data-ttu-id="25070-121">若要解決這個錯誤，錯誤訊息中使用的資訊中的交易集識別錯誤，，然後決定產品說明中的問題解決方法。</span><span class="sxs-lookup"><span data-stu-id="25070-121">To resolve this error, use the information in the error message to identify the error in the transaction set and then determine the problem resolution in the product help.</span></span>