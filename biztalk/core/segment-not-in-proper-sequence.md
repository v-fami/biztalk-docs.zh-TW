---
title: 區段未依照正確順序排列 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f0c0fdc-10d9-4b77-a80d-b2b8571e7665
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2e90f42fdc3226827dae670daecb0e856eba156
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980359"
---
# <a name="segment-not-in-proper-sequence"></a><span data-ttu-id="2cdff-102">區段未依照正確順序排列</span><span class="sxs-lookup"><span data-stu-id="2cdff-102">Segment Not In Proper Sequence</span></span>
## <a name="details"></a><span data-ttu-id="2cdff-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2cdff-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="2cdff-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2cdff-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="2cdff-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="2cdff-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="2cdff-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2cdff-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="2cdff-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="2cdff-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="2cdff-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="2cdff-108"> EDI</span></span> |
|    <span data-ttu-id="2cdff-109">元件</span><span class="sxs-lookup"><span data-stu-id="2cdff-109">Component</span></span>    |                                       <span data-ttu-id="2cdff-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="2cdff-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="2cdff-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2cdff-111">Symbolic Name</span></span>  |                        <span data-ttu-id="2cdff-112">X12SegmentNotInProperSequenceDescription</span><span class="sxs-lookup"><span data-stu-id="2cdff-112">X12SegmentNotInProperSequenceDescription</span></span>                        |
|  <span data-ttu-id="2cdff-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2cdff-113">Message Text</span></span>   |                             <span data-ttu-id="2cdff-114">區段未依照正確順序排列</span><span class="sxs-lookup"><span data-stu-id="2cdff-114">Segment Not In Proper Sequence</span></span>                             |
  
## <a name="explanation"></a><span data-ttu-id="2cdff-115">說明</span><span class="sxs-lookup"><span data-stu-id="2cdff-115">Explanation</span></span>  
 <span data-ttu-id="2cdff-116">這個錯誤/警告/資訊事件表示，由於內送 X12 交換中的區段未依照文件結構描述指定的順序排列，因此接收管線無法處理該交換。</span><span class="sxs-lookup"><span data-stu-id="2cdff-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming X12 interchange because a segment in the interchange is out of the sequence specified by the document schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2cdff-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2cdff-117">User Action</span></span>  
 <span data-ttu-id="2cdff-118">若要解決這個錯誤，交換的傳送者必須重新排列交換中的區段，使這些區段依照文件結構描述指定的順序排列，然後再重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="2cdff-118">To resolve this error, have the sender of the interchange rearrange the segments in the interchange so they are in the order specified by the document schema, and then resend the interchange.</span></span>