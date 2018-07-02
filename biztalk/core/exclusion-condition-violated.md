---
title: 違反排除條件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0e508da6-7edc-45c0-a7ab-f23337dc1b54
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93e55595eaf2903ead7319b5f0269f803a3a83e5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968735"
---
# <a name="exclusion-condition-violated"></a><span data-ttu-id="f89fa-102">違反排除條件</span><span class="sxs-lookup"><span data-stu-id="f89fa-102">Exclusion Condition Violated</span></span>
## <a name="details"></a><span data-ttu-id="f89fa-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f89fa-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="f89fa-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f89fa-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="f89fa-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="f89fa-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="f89fa-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f89fa-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="f89fa-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="f89fa-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f89fa-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="f89fa-108"> EDI</span></span> |
|    <span data-ttu-id="f89fa-109">元件</span><span class="sxs-lookup"><span data-stu-id="f89fa-109">Component</span></span>    |                                       <span data-ttu-id="f89fa-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="f89fa-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="f89fa-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f89fa-111">Symbolic Name</span></span>  |                       <span data-ttu-id="f89fa-112">X12DeExclusionConditionViolatedDescription</span><span class="sxs-lookup"><span data-stu-id="f89fa-112">X12DeExclusionConditionViolatedDescription</span></span>                       |
|  <span data-ttu-id="f89fa-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f89fa-113">Message Text</span></span>   |       <span data-ttu-id="f89fa-114">違反排除條件，請參閱詳細資料的執行個體中的欄位值</span><span class="sxs-lookup"><span data-stu-id="f89fa-114">Exclusion Condition Violated, refer to field value in instance for details</span></span>       |
  
## <a name="explanation"></a><span data-ttu-id="f89fa-115">說明</span><span class="sxs-lookup"><span data-stu-id="f89fa-115">Explanation</span></span>  
 <span data-ttu-id="f89fa-116">這個錯誤/警告/資訊事件表示該驗證的 X12 交換失敗在 （使用 XML 驗證工具） 的設計階段或在執行階段，在接收端或傳送端，因為執行個體中的區段無法跨欄位驗證排除規則。</span><span class="sxs-lookup"><span data-stu-id="f89fa-116">This Error/Warning/Information event indicates that validation of an X12 interchange failed either at design time (using the XML validation tool) or at run time, on either the receive side or the send side, because a segment in the instance failed a cross-field validation exclusion rule.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f89fa-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f89fa-117">User Action</span></span>  
 <span data-ttu-id="f89fa-118">若要解決這個錯誤，請確定無法排除規則的區段已變更，讓它通過欄位交互驗證，然後再執行驗證程序一次。</span><span class="sxs-lookup"><span data-stu-id="f89fa-118">To resolve this error, ensure that the segment that failed the exclusion rule is changed so that it passes cross-field validation, and then run the validation process again.</span></span>