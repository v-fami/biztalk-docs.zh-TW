---
title: 無效的控制編號值 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ac762e2-2d48-45e8-b4c4-2df246b7568c
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ce9df9724d85a3b4a2d6ebf28f94e4b9c05db05
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257222"
---
# <a name="invalid-control-number-value"></a><span data-ttu-id="c7671-102">無效的控制編號值</span><span class="sxs-lookup"><span data-stu-id="c7671-102">Invalid Control Number Value</span></span>
## <a name="details"></a><span data-ttu-id="c7671-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c7671-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c7671-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c7671-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="c7671-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="c7671-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="c7671-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c7671-106">Event ID</span></span>|-|  
|<span data-ttu-id="c7671-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="c7671-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c7671-108">EDI</span><span class="sxs-lookup"><span data-stu-id="c7671-108"> EDI</span></span>|  
|<span data-ttu-id="c7671-109">元件</span><span class="sxs-lookup"><span data-stu-id="c7671-109">Component</span></span>|<span data-ttu-id="c7671-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="c7671-110">EDI Engine</span></span>|  
|<span data-ttu-id="c7671-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c7671-111">Symbolic Name</span></span>|<span data-ttu-id="c7671-112">X12Ta1InvalidControlNumberValueDescription</span><span class="sxs-lookup"><span data-stu-id="c7671-112">X12Ta1InvalidControlNumberValueDescription</span></span>|  
|<span data-ttu-id="c7671-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c7671-113">Message Text</span></span>|<span data-ttu-id="c7671-114">無效的控制編號值</span><span class="sxs-lookup"><span data-stu-id="c7671-114">Invalid Control Number Value</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c7671-115">說明</span><span class="sxs-lookup"><span data-stu-id="c7671-115">Explanation</span></span>  
 <span data-ttu-id="c7671-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為交換中的控制編號 （交換、 群組或交易集） 的值不符合的資料類型，或沒有正確的結構描述所指定的數字的數目。</span><span class="sxs-lookup"><span data-stu-id="c7671-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the value of a control number (interchange, group, or transaction set) in the interchange did not conform to the data type or did not have the correct number of digits specified by the schema.</span></span> <span data-ttu-id="c7671-117">結構描述是 x12serviceschema EdifactServiceSchema BaseArtifacts.dll 中。</span><span class="sxs-lookup"><span data-stu-id="c7671-117">The schema is the X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c7671-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c7671-118">User Action</span></span>  
 <span data-ttu-id="c7671-119">若要解決這個錯誤，請確定控制編號是否符合的資料類型和結構描述中，所指定的數字的數目，然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="c7671-119">To resolve this error, make sure that the control number conforms to the data type and number of digits specified by the schema, and then have the interchange resent.</span></span>