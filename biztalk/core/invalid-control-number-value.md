---
title: 無效的控制編號值 |Microsoft Docs
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
ms.openlocfilehash: 09b274170505bf1b010d61fbefe9d43a51528aac
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37019836"
---
# <a name="invalid-control-number-value"></a><span data-ttu-id="7c0ed-102">無效的控制編號值</span><span class="sxs-lookup"><span data-stu-id="7c0ed-102">Invalid Control Number Value</span></span>
## <a name="details"></a><span data-ttu-id="7c0ed-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7c0ed-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="7c0ed-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="7c0ed-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="7c0ed-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="7c0ed-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="7c0ed-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="7c0ed-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="7c0ed-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="7c0ed-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="7c0ed-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="7c0ed-108"> EDI</span></span> |
|    <span data-ttu-id="7c0ed-109">元件</span><span class="sxs-lookup"><span data-stu-id="7c0ed-109">Component</span></span>    |                                       <span data-ttu-id="7c0ed-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="7c0ed-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="7c0ed-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="7c0ed-111">Symbolic Name</span></span>  |                       <span data-ttu-id="7c0ed-112">X12Ta1InvalidControlNumberValueDescription</span><span class="sxs-lookup"><span data-stu-id="7c0ed-112">X12Ta1InvalidControlNumberValueDescription</span></span>                       |
|  <span data-ttu-id="7c0ed-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="7c0ed-113">Message Text</span></span>   |                              <span data-ttu-id="7c0ed-114">無效的控制編號值</span><span class="sxs-lookup"><span data-stu-id="7c0ed-114">Invalid Control Number Value</span></span>                              |
  
## <a name="explanation"></a><span data-ttu-id="7c0ed-115">說明</span><span class="sxs-lookup"><span data-stu-id="7c0ed-115">Explanation</span></span>  
 <span data-ttu-id="7c0ed-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為交換中的控制編號 （交換、 群組或交易集） 的值不符合的資料類型，或沒有正確的結構描述指定的數字數目。</span><span class="sxs-lookup"><span data-stu-id="7c0ed-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the value of a control number (interchange, group, or transaction set) in the interchange did not conform to the data type or did not have the correct number of digits specified by the schema.</span></span> <span data-ttu-id="7c0ed-117">結構描述是 x12serviceschema EdifactServiceSchema BaseArtifacts.dll 中。</span><span class="sxs-lookup"><span data-stu-id="7c0ed-117">The schema is the X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7c0ed-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="7c0ed-118">User Action</span></span>  
 <span data-ttu-id="7c0ed-119">若要解決這個錯誤，請確定的控制編號是否符合的資料類型和結構描述中，指定的數字的數目，然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="7c0ed-119">To resolve this error, make sure that the control number conforms to the data type and number of digits specified by the schema, and then have the interchange resent.</span></span>