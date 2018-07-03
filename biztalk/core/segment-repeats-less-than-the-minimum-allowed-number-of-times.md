---
title: 區段重複項目，小於允許的次數的最小。 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c8ca6c3d-f923-49bc-b5d9-65dc2d7adab1
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 29df069fefbf6e47b711d37884c00a40318e96b0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008831"
---
# <a name="segment-repeats-less-than-the-minimum-allowed-number-of-times"></a><span data-ttu-id="98c96-102">區段重複次數少於允許次數的數目下限</span><span class="sxs-lookup"><span data-stu-id="98c96-102">Segment repeats less than the minimum allowed number of times</span></span>
## <a name="details"></a><span data-ttu-id="98c96-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="98c96-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="98c96-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="98c96-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="98c96-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="98c96-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="98c96-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="98c96-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="98c96-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="98c96-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="98c96-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="98c96-108"> EDI</span></span> |
|    <span data-ttu-id="98c96-109">元件</span><span class="sxs-lookup"><span data-stu-id="98c96-109">Component</span></span>    |                                       <span data-ttu-id="98c96-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="98c96-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="98c96-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="98c96-111">Symbolic Name</span></span>  |                        <span data-ttu-id="98c96-112">X12SeSegmentRepeatsLessTimesDescription</span><span class="sxs-lookup"><span data-stu-id="98c96-112">X12SeSegmentRepeatsLessTimesDescription</span></span>                         |
|  <span data-ttu-id="98c96-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="98c96-113">Message Text</span></span>   |             <span data-ttu-id="98c96-114">區段重複次數少於允許次數的數目下限</span><span class="sxs-lookup"><span data-stu-id="98c96-114">Segment repeats less than the minimum allowed number of times</span></span>              |
  
## <a name="explanation"></a><span data-ttu-id="98c96-115">說明</span><span class="sxs-lookup"><span data-stu-id="98c96-115">Explanation</span></span>  
 <span data-ttu-id="98c96-116">這個錯誤/警告/資訊事件表示接收管線無法處理內送 X12 交換，因為交換中的區段不重複的文件結構描述所需的最小次數。</span><span class="sxs-lookup"><span data-stu-id="98c96-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming X12 interchange because a segment in the interchange does not repeat the minimum number of times required by the document schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="98c96-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="98c96-117">User Action</span></span>  
 <span data-ttu-id="98c96-118">若要解決這個錯誤，有為區段的重複交換的寄件者，讓它會至少重複文件結構描述所需的最小次數，並再重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="98c96-118">To resolve this error, have the sender of the interchange as repetition of the segment so that it repeats at least the minimum number of times required by the document schema, and then resend the interchange.</span></span>