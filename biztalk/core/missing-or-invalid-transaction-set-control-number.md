---
title: 遺漏或無效的交易集控制編號 |Microsoft Docs
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
ms.openlocfilehash: 14b8a05a636be08e605d8d2a5bae98748fd3dbb7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971679"
---
# <a name="missing-or-invalid-transaction-set-control-number"></a><span data-ttu-id="040ac-102">遺漏或無效的交易集控制編號</span><span class="sxs-lookup"><span data-stu-id="040ac-102">Missing or invalid transaction set control number</span></span>
## <a name="details"></a><span data-ttu-id="040ac-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="040ac-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="040ac-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="040ac-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="040ac-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="040ac-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="040ac-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="040ac-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="040ac-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="040ac-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="040ac-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="040ac-108"> EDI</span></span> |
|    <span data-ttu-id="040ac-109">元件</span><span class="sxs-lookup"><span data-stu-id="040ac-109">Component</span></span>    |                                       <span data-ttu-id="040ac-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="040ac-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="040ac-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="040ac-111">Symbolic Name</span></span>  |                    <span data-ttu-id="040ac-112">X12TsMissingOrInvalidTsControlNumberDescription</span><span class="sxs-lookup"><span data-stu-id="040ac-112">X12TsMissingOrInvalidTsControlNumberDescription</span></span>                     |
|  <span data-ttu-id="040ac-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="040ac-113">Message Text</span></span>   |                   <span data-ttu-id="040ac-114">遺漏或無效的交易集控制編號</span><span class="sxs-lookup"><span data-stu-id="040ac-114">Missing or invalid transaction set control number</span></span>                    |
  
## <a name="explanation"></a><span data-ttu-id="040ac-115">說明</span><span class="sxs-lookup"><span data-stu-id="040ac-115">Explanation</span></span>  
 <span data-ttu-id="040ac-116">這個錯誤/警告/資訊事件表示，接收管線或傳送管線無法處理交換，因為交易集控制編號 （ST02 欄位中） 的值遺漏或具有無效的值。</span><span class="sxs-lookup"><span data-stu-id="040ac-116">This Error/Warning/Information event indicates that the receive or send pipeline could not process the interchange because the value of the transaction set control number (in the ST02 field) was missing or had an invalid value.</span></span> <span data-ttu-id="040ac-117">交易集控制編號必須是英數字元值。</span><span class="sxs-lookup"><span data-stu-id="040ac-117">The transaction set control number must be an alphanumeric value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="040ac-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="040ac-118">User Action</span></span>  
 <span data-ttu-id="040ac-119">若要解決這個錯誤，請執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="040ac-119">To resolve this error, do one of the following:</span></span>  
  
1.  <span data-ttu-id="040ac-120">請確定每個交易集具有交易集控制編號。</span><span class="sxs-lookup"><span data-stu-id="040ac-120">Make sure that each transaction set has a transaction set control number.</span></span>  
  
2.  <span data-ttu-id="040ac-121">請確定每個交易集控制編號的英數字元值。</span><span class="sxs-lookup"><span data-stu-id="040ac-121">Make sure that each transaction set control number is an alphanumeric value.</span></span>