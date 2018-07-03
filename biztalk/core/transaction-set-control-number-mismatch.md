---
title: 交易集控制編號不相符 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2c4b0c3f-f3be-4c2c-8719-8e40aa7122b9
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da4c20eb6853827709731c41631a38225214424d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37021972"
---
# <a name="transaction-set-control-number-mismatch"></a><span data-ttu-id="c69e8-102">交易集控制編號不相符</span><span class="sxs-lookup"><span data-stu-id="c69e8-102">Transaction Set Control Number Mismatch</span></span>
## <a name="details"></a><span data-ttu-id="c69e8-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c69e8-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="c69e8-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c69e8-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="c69e8-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="c69e8-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="c69e8-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c69e8-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="c69e8-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="c69e8-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c69e8-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="c69e8-108"> EDI</span></span> |
|    <span data-ttu-id="c69e8-109">元件</span><span class="sxs-lookup"><span data-stu-id="c69e8-109">Component</span></span>    |                                       <span data-ttu-id="c69e8-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="c69e8-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="c69e8-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c69e8-111">Symbolic Name</span></span>  |                         <span data-ttu-id="c69e8-112">X12TsControlNumberMismatchDescription</span><span class="sxs-lookup"><span data-stu-id="c69e8-112">X12TsControlNumberMismatchDescription</span></span>                          |
|  <span data-ttu-id="c69e8-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c69e8-113">Message Text</span></span>   |                        <span data-ttu-id="c69e8-114">交易集控制編號不相符</span><span class="sxs-lookup"><span data-stu-id="c69e8-114">Transaction Set Control Number Mismatch</span></span>                         |
  
## <a name="explanation"></a><span data-ttu-id="c69e8-115">說明</span><span class="sxs-lookup"><span data-stu-id="c69e8-115">Explanation</span></span>  
 <span data-ttu-id="c69e8-116">這個錯誤/警告/資訊事件表示，由於交易集 [SE02] 欄位中的控制編號和 [ST02] 欄位中的控制編號不符，因此 EDI 接收管線拒絕內送交易集。</span><span class="sxs-lookup"><span data-stu-id="c69e8-116">This Error/Warning/Information event indicates that the EDI receive pipeline rejected the incoming transaction set because the control number contained in the SE02 field of the transaction set did not match the control number in the ST02 field.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c69e8-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c69e8-117">User Action</span></span>  
 <span data-ttu-id="c69e8-118">若要解決這個錯誤，讓傳送者交易集的變更已拒絕的交易集控制編號，在 [ST02] 欄位中，相同的控制編號，而 SE02 欄位中，然後再重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="c69e8-118">To resolve this error, have the sender of the transaction set change the control number in the SE02 field of the rejected transaction set to be the same as the control number in the ST02 field, and then resend the interchange.</span></span>