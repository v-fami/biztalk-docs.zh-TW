---
title: "在處理交易 Set(s) 因為找不到交易集的開始項目之後發生錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5380aee-1632-4cdf-98a1-aff87574ce4f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 224b08046d1733aa8426909d7dddac4b10e48c8e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-after-processing-transaction-sets-because-the-start-element-of-a-transaction-set-could-not-be-found"></a><span data-ttu-id="5f37d-102">在處理交易 Set(s) 因為找不到交易集的開始項目之後所發生的錯誤</span><span class="sxs-lookup"><span data-stu-id="5f37d-102">Error encountered after processing Transaction Set(s) because the Start element of a Transaction set could not be found</span></span>
## <a name="details"></a><span data-ttu-id="5f37d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5f37d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5f37d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="5f37d-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="5f37d-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="5f37d-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="5f37d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="5f37d-106">Event ID</span></span>|-|  
|<span data-ttu-id="5f37d-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="5f37d-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="5f37d-108">EDI</span><span class="sxs-lookup"><span data-stu-id="5f37d-108"> EDI</span></span>|  
|<span data-ttu-id="5f37d-109">元件</span><span class="sxs-lookup"><span data-stu-id="5f37d-109">Component</span></span>|<span data-ttu-id="5f37d-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="5f37d-110">EDI Engine</span></span>|  
|<span data-ttu-id="5f37d-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="5f37d-111">Symbolic Name</span></span>|<span data-ttu-id="5f37d-112">InvalidEfactBiboXmlFormat</span><span class="sxs-lookup"><span data-stu-id="5f37d-112">InvalidEfactBiboXmlFormat</span></span>|  
|<span data-ttu-id="5f37d-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="5f37d-113">Message Text</span></span>|<span data-ttu-id="5f37d-114">在處理 {0} 交易 Set(s) 之後發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="5f37d-114">Error encountered after processing {0} Transaction Set(s).</span></span> <span data-ttu-id="5f37d-115">找不到開始交易集的項目。</span><span class="sxs-lookup"><span data-stu-id="5f37d-115">Start element of a Transaction set could not be found.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5f37d-116">說明</span><span class="sxs-lookup"><span data-stu-id="5f37d-116">Explanation</span></span>  
 <span data-ttu-id="5f37d-117">這個錯誤/警告/資訊事件表示 EDI 接收管線無法處理內送交易設定，因為接收管線找不到短期或 UNH 標頭。</span><span class="sxs-lookup"><span data-stu-id="5f37d-117">This Error/Warning/Information event indicates that the EDI receive pipeline could not process an incoming transaction set because the receive pipeline could not find the ST or UNH header.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5f37d-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="5f37d-118">User Action</span></span>  
 <span data-ttu-id="5f37d-119">若要解決這個錯誤，請連絡交換的寄件者，確保交易集發生錯誤的開頭 ST01 或 UNH1 的區段。</span><span class="sxs-lookup"><span data-stu-id="5f37d-119">To resolve this error, contact the sender of the interchange, and have them ensure that the transaction set in error begins with an ST01 or UNH1 segment.</span></span>