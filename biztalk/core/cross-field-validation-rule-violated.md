---
title: 跨欄位驗證規則違規 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d606a80-9046-4572-9cfb-a3434ed8073e
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d590fc318e7d833a067f4275986bef88da10364
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976655"
---
# <a name="cross-field-validation-rule-violated"></a><span data-ttu-id="d8a7c-102">違反欄位交互驗證規則</span><span class="sxs-lookup"><span data-stu-id="d8a7c-102">Cross field validation rule violated</span></span>
## <a name="details"></a><span data-ttu-id="d8a7c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d8a7c-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="d8a7c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d8a7c-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="d8a7c-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="d8a7c-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="d8a7c-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d8a7c-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="d8a7c-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="d8a7c-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d8a7c-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="d8a7c-108"> EDI</span></span> |
|    <span data-ttu-id="d8a7c-109">元件</span><span class="sxs-lookup"><span data-stu-id="d8a7c-109">Component</span></span>    |                                       <span data-ttu-id="d8a7c-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="d8a7c-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="d8a7c-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d8a7c-111">Symbolic Name</span></span>  |                                           -                                            |
|  <span data-ttu-id="d8a7c-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d8a7c-112">Message Text</span></span>   |                          <span data-ttu-id="d8a7c-113">違反欄位交互驗證規則</span><span class="sxs-lookup"><span data-stu-id="d8a7c-113">Cross field validation rule violated</span></span>                          |
  
## <a name="explanation"></a><span data-ttu-id="d8a7c-114">說明</span><span class="sxs-lookup"><span data-stu-id="d8a7c-114">Explanation</span></span>  
 <span data-ttu-id="d8a7c-115">這個錯誤/警告/資訊事件表示，接收管線或傳送管線中的 X12 交換無法通過欄位交互驗證。</span><span class="sxs-lookup"><span data-stu-id="d8a7c-115">This Error/Warning/Information event indicates that the X12 interchange failed cross-field validation in the receive pipeline or the send pipeline.</span></span> <span data-ttu-id="d8a7c-116">這代表 X12ConditionDesignator_Check 旗標已設為 [是]，且交換中至少有一個元素無法通過依首碼 "X12ConditionDesignatorX" 識別的規則。</span><span class="sxs-lookup"><span data-stu-id="d8a7c-116">This indicates that the X12ConditionDesignator_Check flag is set to "Yes", and that at least one element in the interchange failed a rule identified by the prefix "X12ConditionDesignatorX".</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d8a7c-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d8a7c-117">User Action</span></span>  
 <span data-ttu-id="d8a7c-118">若要解決這個錯誤，請執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="d8a7c-118">To resolve this error, do one of the following:</span></span>  
  
-   <span data-ttu-id="d8a7c-119">找出無法通過欄位交互驗證規則的資料元素。</span><span class="sxs-lookup"><span data-stu-id="d8a7c-119">Identify which data element failed a cross-field validation rule.</span></span> <span data-ttu-id="d8a7c-120">請連絡交換的寄件者，並指出建立交換時，必須遵循的規則。</span><span class="sxs-lookup"><span data-stu-id="d8a7c-120">Contact the sender of the interchange and indicate that the rule must be followed when creating the interchange.</span></span>  
  
-   <span data-ttu-id="d8a7c-121">開啟結構描述的交換，並設定為 [否] 的驗證失敗的資料元素的 X12ConditionDesignator_Check 旗標。</span><span class="sxs-lookup"><span data-stu-id="d8a7c-121">Open the schema for the interchange, and set the X12ConditionDesignator_Check flag for the data element that failed validation to "No".</span></span>