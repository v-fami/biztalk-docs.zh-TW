---
title: 無效的授權值 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70d0dd75-b045-4b67-ba23-78551493f074
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 674585daa50f0adc0708a792b318bc0b736eca49
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974431"
---
# <a name="invalid-authorization-value"></a><span data-ttu-id="99002-102">無效的授權值</span><span class="sxs-lookup"><span data-stu-id="99002-102">Invalid Authorization Value</span></span>
## <a name="details"></a><span data-ttu-id="99002-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="99002-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="99002-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="99002-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="99002-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="99002-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="99002-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="99002-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="99002-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="99002-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="99002-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="99002-108"> EDI</span></span> |
|    <span data-ttu-id="99002-109">元件</span><span class="sxs-lookup"><span data-stu-id="99002-109">Component</span></span>    |                                       <span data-ttu-id="99002-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="99002-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="99002-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="99002-111">Symbolic Name</span></span>  |                       <span data-ttu-id="99002-112">X12Ta1InvalidAuthorizationValueDescription</span><span class="sxs-lookup"><span data-stu-id="99002-112">X12Ta1InvalidAuthorizationValueDescription</span></span>                       |
|  <span data-ttu-id="99002-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="99002-113">Message Text</span></span>   |                              <span data-ttu-id="99002-114">無效的授權值</span><span class="sxs-lookup"><span data-stu-id="99002-114">Invalid Authorization Value</span></span>                               |
  
## <a name="explanation"></a><span data-ttu-id="99002-115">說明</span><span class="sxs-lookup"><span data-stu-id="99002-115">Explanation</span></span>  
 <span data-ttu-id="99002-116">這個錯誤/警告/資訊事件表示接收管線無法處理內送交換，因為在 ISA02 授權資訊的值不符合結構描述 （如果是 X12_AN)，所指定的資料類型，或沒有結構描述 (10) 所需的數字數目。</span><span class="sxs-lookup"><span data-stu-id="99002-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the value of the Authorization Information in ISA02 did not conform to the data type specified by the schema (X12_AN), or did not have the number of digits required by the schema (10).</span></span> <span data-ttu-id="99002-117">結構描述是 X12ServiceSchema BaseArtifacts.dll 中。</span><span class="sxs-lookup"><span data-stu-id="99002-117">The schema is the X12ServiceSchema in BaseArtifacts.dll.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="99002-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="99002-118">User Action</span></span>  
 <span data-ttu-id="99002-119">若要解決這個錯誤，請確定 ISA02 標頭中的值是否符合 X12： 資料型別和有 10 位數 （使用尾端空格），然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="99002-119">To resolve this error, make sure that the value in the ISA02 header conforms to the X12:AN data type and has 10 digits (with trailing spaces), and then have the interchange resent.</span></span>