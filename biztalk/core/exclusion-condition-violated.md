---
title: "違反排除條件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e508da6-7edc-45c0-a7ab-f23337dc1b54
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5a508c113daf628491837adee119649ac17b478
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="exclusion-condition-violated"></a><span data-ttu-id="d00f4-102">違反排除條件</span><span class="sxs-lookup"><span data-stu-id="d00f4-102">Exclusion Condition Violated</span></span>
## <a name="details"></a><span data-ttu-id="d00f4-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d00f4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d00f4-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d00f4-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="d00f4-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="d00f4-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="d00f4-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d00f4-106">Event ID</span></span>|-|  
|<span data-ttu-id="d00f4-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="d00f4-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d00f4-108">EDI</span><span class="sxs-lookup"><span data-stu-id="d00f4-108"> EDI</span></span>|  
|<span data-ttu-id="d00f4-109">元件</span><span class="sxs-lookup"><span data-stu-id="d00f4-109">Component</span></span>|<span data-ttu-id="d00f4-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="d00f4-110">EDI Engine</span></span>|  
|<span data-ttu-id="d00f4-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d00f4-111">Symbolic Name</span></span>|<span data-ttu-id="d00f4-112">X12DeExclusionConditionViolatedDescription</span><span class="sxs-lookup"><span data-stu-id="d00f4-112">X12DeExclusionConditionViolatedDescription</span></span>|  
|<span data-ttu-id="d00f4-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d00f4-113">Message Text</span></span>|<span data-ttu-id="d00f4-114">排除條件違反，如需詳細資訊的執行個體中參考欄位值</span><span class="sxs-lookup"><span data-stu-id="d00f4-114">Exclusion Condition Violated, refer to field value in instance for details</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d00f4-115">說明</span><span class="sxs-lookup"><span data-stu-id="d00f4-115">Explanation</span></span>  
 <span data-ttu-id="d00f4-116">這個錯誤/警告/資訊事件表示該驗證的 X12 交換因失敗而在設計階段 （使用 XML 驗證工具），或是在執行階段，在接收端或傳送端，執行個體中的線段失敗跨欄位驗證排除規則。</span><span class="sxs-lookup"><span data-stu-id="d00f4-116">This Error/Warning/Information event indicates that validation of an X12 interchange failed either at design time (using the XML validation tool) or at run time, on either the receive side or the send side, because a segment in the instance failed a cross-field validation exclusion rule.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d00f4-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d00f4-117">User Action</span></span>  
 <span data-ttu-id="d00f4-118">若要解決這個錯誤，請確認失敗排除規則的區段會變更，使其通過欄位交互驗證，然後執行驗證程序一次。</span><span class="sxs-lookup"><span data-stu-id="d00f4-118">To resolve this error, ensure that the segment that failed the exclusion rule is changed so that it passes cross-field validation, and then run the validation process again.</span></span>