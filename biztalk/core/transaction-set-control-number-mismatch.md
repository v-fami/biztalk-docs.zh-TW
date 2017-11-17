---
title: "交易集控制編號不相符 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c4b0c3f-f3be-4c2c-8719-8e40aa7122b9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efd80bac6a5c58306a8d9ca64748ddbb8cb2bc81
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="transaction-set-control-number-mismatch"></a><span data-ttu-id="d517f-102">交易集控制編號不相符</span><span class="sxs-lookup"><span data-stu-id="d517f-102">Transaction Set Control Number Mismatch</span></span>
## <a name="details"></a><span data-ttu-id="d517f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d517f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d517f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d517f-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="d517f-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="d517f-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="d517f-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d517f-106">Event ID</span></span>|-|  
|<span data-ttu-id="d517f-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="d517f-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d517f-108">EDI</span><span class="sxs-lookup"><span data-stu-id="d517f-108"> EDI</span></span>|  
|<span data-ttu-id="d517f-109">元件</span><span class="sxs-lookup"><span data-stu-id="d517f-109">Component</span></span>|<span data-ttu-id="d517f-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="d517f-110">EDI Engine</span></span>|  
|<span data-ttu-id="d517f-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d517f-111">Symbolic Name</span></span>|<span data-ttu-id="d517f-112">X12TsControlNumberMismatchDescription</span><span class="sxs-lookup"><span data-stu-id="d517f-112">X12TsControlNumberMismatchDescription</span></span>|  
|<span data-ttu-id="d517f-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d517f-113">Message Text</span></span>|<span data-ttu-id="d517f-114">交易集控制編號不相符</span><span class="sxs-lookup"><span data-stu-id="d517f-114">Transaction Set Control Number Mismatch</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d517f-115">說明</span><span class="sxs-lookup"><span data-stu-id="d517f-115">Explanation</span></span>  
 <span data-ttu-id="d517f-116">這個錯誤/警告/資訊事件表示，由於交易集 [SE02] 欄位中的控制編號和 [ST02] 欄位中的控制編號不符，因此 EDI 接收管線拒絕內送交易集。</span><span class="sxs-lookup"><span data-stu-id="d517f-116">This Error/Warning/Information event indicates that the EDI receive pipeline rejected the incoming transaction set because the control number contained in the SE02 field of the transaction set did not match the control number in the ST02 field.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d517f-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d517f-117">User Action</span></span>  
 <span data-ttu-id="d517f-118">若要解決這個錯誤，讓傳送者交易集的變更，而 SE02 欄位中已拒絕的交易集，使 [ST02] 欄位中的控制編號與相同的控制編號，然後再重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="d517f-118">To resolve this error, have the sender of the transaction set change the control number in the SE02 field of the rejected transaction set to be the same as the control number in the ST02 field, and then resend the interchange.</span></span>