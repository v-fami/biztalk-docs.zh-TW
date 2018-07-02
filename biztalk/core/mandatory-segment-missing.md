---
title: 遺失必要的區段 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8e459a22-8de5-426a-a46a-1d0ab72b532d
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e2bc9775da2fcbef756774c576074b471e808484
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977087"
---
# <a name="mandatory-segment-missing"></a><span data-ttu-id="f9735-102">遺失必要的區段</span><span class="sxs-lookup"><span data-stu-id="f9735-102">Mandatory Segment Missing</span></span>
## <a name="details"></a><span data-ttu-id="f9735-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f9735-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="f9735-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f9735-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="f9735-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="f9735-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="f9735-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f9735-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="f9735-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="f9735-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f9735-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="f9735-108"> EDI</span></span> |
|    <span data-ttu-id="f9735-109">元件</span><span class="sxs-lookup"><span data-stu-id="f9735-109">Component</span></span>    |                                       <span data-ttu-id="f9735-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="f9735-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="f9735-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f9735-111">Symbolic Name</span></span>  |                         <span data-ttu-id="f9735-112">X12MandatorySegmentMissingDescription</span><span class="sxs-lookup"><span data-stu-id="f9735-112">X12MandatorySegmentMissingDescription</span></span>                          |
|  <span data-ttu-id="f9735-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f9735-113">Message Text</span></span>   |                               <span data-ttu-id="f9735-114">遺失必要的區段</span><span class="sxs-lookup"><span data-stu-id="f9735-114">Mandatory Segment Missing</span></span>                                |
  
## <a name="explanation"></a><span data-ttu-id="f9735-115">說明</span><span class="sxs-lookup"><span data-stu-id="f9735-115">Explanation</span></span>  
 <span data-ttu-id="f9735-116">這個錯誤/警告/資訊事件表示接收管線無法處理內送 X12 交換，因為交換未包含所需的訊息結構描述 （minoccurs 大於 0） 的區段。</span><span class="sxs-lookup"><span data-stu-id="f9735-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming X12 interchange because the interchange did not contain a segment that is required by the message schema (for which minOccurs is greater than 0).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f9735-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f9735-117">User Action</span></span>  
 <span data-ttu-id="f9735-118">若要解決這個錯誤，請確定此交換包含的訊息結構描述中，所需的所有區段，然後必須將訊息重新傳送。</span><span class="sxs-lookup"><span data-stu-id="f9735-118">To resolve this error, make sure that the interchange contains all segments required by the message schema, and then have the message resent.</span></span>