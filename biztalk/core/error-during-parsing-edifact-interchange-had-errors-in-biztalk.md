---
title: "在剖析期間發生錯誤。 Edifact 交換發生下列錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fa8f9d5-5b7c-47c9-96d3-77be280b78e9
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4585966de7ecb410f8f46fa675fa4eae0c6715a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-during-parsing-the-edifact-interchange-had-the-following-errors"></a><span data-ttu-id="58144-103">在剖析期間發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="58144-103">Error encountered during parsing.</span></span> <span data-ttu-id="58144-104">Edifact 交換發生下列錯誤</span><span class="sxs-lookup"><span data-stu-id="58144-104">The Edifact interchange had the following errors</span></span>
## <a name="details"></a><span data-ttu-id="58144-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="58144-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="58144-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="58144-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="58144-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="58144-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="58144-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="58144-108">Event ID</span></span>|-|  
|<span data-ttu-id="58144-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="58144-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="58144-110">EDI</span><span class="sxs-lookup"><span data-stu-id="58144-110"> EDI</span></span>|  
|<span data-ttu-id="58144-111">元件</span><span class="sxs-lookup"><span data-stu-id="58144-111">Component</span></span>|<span data-ttu-id="58144-112">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="58144-112">EDI Engine</span></span>|  
|<span data-ttu-id="58144-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="58144-113">Symbolic Name</span></span>|<span data-ttu-id="58144-114">EfactInterchangeReceiveError</span><span class="sxs-lookup"><span data-stu-id="58144-114">EfactInterchangeReceiveError</span></span>|  
|<span data-ttu-id="58144-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="58144-115">Message Text</span></span>|<span data-ttu-id="58144-116">在剖析期間發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="58144-116">Error encountered during parsing.</span></span> <span data-ttu-id="58144-117">寄件者識別碼 '{1}' 識別碼為 '{0}'，Edifact 交換接收者識別碼 '{2}' 發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="58144-117">The Edifact interchange with id '{0}', with sender id '{1}', receiver id '{2}' had the following errors:</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="58144-118">說明</span><span class="sxs-lookup"><span data-stu-id="58144-118">Explanation</span></span>  
 <span data-ttu-id="58144-119">這個錯誤/警告/資訊事件表示 EDI 接收管線在剖析內送 EDIFACT 交換，因為交換中敘述的錯誤時遇到錯誤。</span><span class="sxs-lookup"><span data-stu-id="58144-119">This Error/Warning/Information event indicates that the EDI receive pipeline encountered an error when parsing an incoming EDIFACT interchange because of the stated errors in the interchange.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="58144-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="58144-120">User Action</span></span>  
 <span data-ttu-id="58144-121">若要解決這個錯誤，找出交換中的錯誤，，然後決定產品說明中的問題解決方法需要使用錯誤訊息中的資訊。</span><span class="sxs-lookup"><span data-stu-id="58144-121">To resolve this error, use the information in the error message to identify the error in the interchange and then determine the problem resolution in the product help.</span></span>