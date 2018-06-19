---
title: 遺漏或無效的交易集控制編號 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6064b974-e8cd-4486-abc2-010afe0d956e
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e9448c9be2cd05c7f7d8c18c13730933c1b5824
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262990"
---
# <a name="missing-or-invalid-transaction-set-control-number"></a><span data-ttu-id="900a1-102">遺漏或無效的交易集控制編號</span><span class="sxs-lookup"><span data-stu-id="900a1-102">Missing or invalid transaction set control number</span></span>
## <a name="details"></a><span data-ttu-id="900a1-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="900a1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="900a1-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="900a1-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="900a1-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="900a1-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="900a1-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="900a1-106">Event ID</span></span>|-|  
|<span data-ttu-id="900a1-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="900a1-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="900a1-108">EDI</span><span class="sxs-lookup"><span data-stu-id="900a1-108"> EDI</span></span>|  
|<span data-ttu-id="900a1-109">元件</span><span class="sxs-lookup"><span data-stu-id="900a1-109">Component</span></span>|<span data-ttu-id="900a1-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="900a1-110">EDI Engine</span></span>|  
|<span data-ttu-id="900a1-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="900a1-111">Symbolic Name</span></span>|<span data-ttu-id="900a1-112">X12TsMissingOrInvalidTsControlNumberDescription</span><span class="sxs-lookup"><span data-stu-id="900a1-112">X12TsMissingOrInvalidTsControlNumberDescription</span></span>|  
|<span data-ttu-id="900a1-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="900a1-113">Message Text</span></span>|<span data-ttu-id="900a1-114">遺漏或無效的交易集控制編號</span><span class="sxs-lookup"><span data-stu-id="900a1-114">Missing or invalid transaction set control number</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="900a1-115">說明</span><span class="sxs-lookup"><span data-stu-id="900a1-115">Explanation</span></span>  
 <span data-ttu-id="900a1-116">這個錯誤/警告/資訊事件表示，接收管線或傳送管線無法處理交換，因為交易集控制編號 （ST02 欄位中） 的值已遺失或有無效的值。</span><span class="sxs-lookup"><span data-stu-id="900a1-116">This Error/Warning/Information event indicates that the receive or send pipeline could not process the interchange because the value of the transaction set control number (in the ST02 field) was missing or had an invalid value.</span></span> <span data-ttu-id="900a1-117">交易集控制編號必須是英數字元值。</span><span class="sxs-lookup"><span data-stu-id="900a1-117">The transaction set control number must be an alphanumeric value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="900a1-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="900a1-118">User Action</span></span>  
 <span data-ttu-id="900a1-119">若要解決這個錯誤，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="900a1-119">To resolve this error, do one of the following:</span></span>  
  
1.  <span data-ttu-id="900a1-120">請確定每個交易集的交易集控制編號。</span><span class="sxs-lookup"><span data-stu-id="900a1-120">Make sure that each transaction set has a transaction set control number.</span></span>  
  
2.  <span data-ttu-id="900a1-121">請確定每個交易集控制編號的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="900a1-121">Make sure that each transaction set control number is an alphanumeric value.</span></span>