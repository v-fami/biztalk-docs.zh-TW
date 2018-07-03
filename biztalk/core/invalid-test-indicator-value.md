---
title: 無效的測試指示器值 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d81d501-4020-4ff9-955c-5674a99d250b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 89245453e7b1b7d8c40e33bf25a3ab3aac1933db
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991023"
---
# <a name="invalid-test-indicator-value"></a><span data-ttu-id="e010f-102">無效的測試指示符號值</span><span class="sxs-lookup"><span data-stu-id="e010f-102">Invalid Test Indicator Value</span></span>
## <a name="details"></a><span data-ttu-id="e010f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e010f-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="e010f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e010f-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="e010f-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="e010f-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="e010f-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e010f-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="e010f-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="e010f-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="e010f-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="e010f-108"> EDI</span></span> |
|    <span data-ttu-id="e010f-109">元件</span><span class="sxs-lookup"><span data-stu-id="e010f-109">Component</span></span>    |                                       <span data-ttu-id="e010f-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="e010f-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="e010f-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e010f-111">Symbolic Name</span></span>  |                       <span data-ttu-id="e010f-112">X12Ta1InvalidTestIndicatorValueDescription</span><span class="sxs-lookup"><span data-stu-id="e010f-112">X12Ta1InvalidTestIndicatorValueDescription</span></span>                       |
|  <span data-ttu-id="e010f-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e010f-113">Message Text</span></span>   |                              <span data-ttu-id="e010f-114">無效的測試指示符號值</span><span class="sxs-lookup"><span data-stu-id="e010f-114">Invalid Test Indicator Value</span></span>                              |
  
## <a name="explanation"></a><span data-ttu-id="e010f-115">說明</span><span class="sxs-lookup"><span data-stu-id="e010f-115">Explanation</span></span>  
 <span data-ttu-id="e010f-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為 UNB11 欄位中的測試指示符號不符合的資料類型和服務結構描述 （建立方法的數字數目X12serviceschema BaseArtifacts.dll 中的 EdifactServiceSchema)。</span><span class="sxs-lookup"><span data-stu-id="e010f-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the Test Indicator in the UNB11 field did not conform to the data type and number of digits established by the service schema (X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e010f-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e010f-117">User Action</span></span>  
 <span data-ttu-id="e010f-118">若要解決這個錯誤，請確定 UNB11 欄位是 EDIFACT_N 資料型別，並且是 1 個字元的長度。</span><span class="sxs-lookup"><span data-stu-id="e010f-118">To resolve this error, make sure that the UNB11 field is of the EDIFACT_N data type and is 1 character in length.</span></span> <span data-ttu-id="e010f-119">重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="e010f-119">Have the interchange resent.</span></span>