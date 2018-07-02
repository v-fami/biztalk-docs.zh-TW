---
title: 訊息不包含 UNA，而且分隔符號的管線屬性的格式不正確 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b761d820-e09d-4949-bb41-da9e66054c60
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 717626c6ba38d8e278ad173739c28d502c3d6e0d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967775"
---
# <a name="message-did-not-contain-una-and-pipeline-property-for-delimiters-was-incorrect-format"></a><span data-ttu-id="12544-102">訊息不包含 UNA，而且分隔符號的管線屬性的格式不正確</span><span class="sxs-lookup"><span data-stu-id="12544-102">Message did not contain UNA and pipeline property for delimiters was incorrect format</span></span>
## <a name="details"></a><span data-ttu-id="12544-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="12544-103">Details</span></span>  
  
|                 |                                                                                             |
|-----------------|---------------------------------------------------------------------------------------------|
|  <span data-ttu-id="12544-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="12544-104">Product Name</span></span>   |     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]      |
| <span data-ttu-id="12544-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="12544-105">Product Version</span></span> |                 [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                  |
|    <span data-ttu-id="12544-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="12544-106">Event ID</span></span>     |                                              -                                              |
|  <span data-ttu-id="12544-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="12544-107">Event Source</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="12544-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="12544-108"> EDI</span></span>    |
|    <span data-ttu-id="12544-109">元件</span><span class="sxs-lookup"><span data-stu-id="12544-109">Component</span></span>    |                                         <span data-ttu-id="12544-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="12544-110">EDI Engine</span></span>                                          |
|  <span data-ttu-id="12544-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="12544-111">Symbolic Name</span></span>  |                                <span data-ttu-id="12544-112">EfactDelimiterIncorrectFormat</span><span class="sxs-lookup"><span data-stu-id="12544-112">EfactDelimiterIncorrectFormat</span></span>                                |
|  <span data-ttu-id="12544-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="12544-113">Message Text</span></span>   | <span data-ttu-id="12544-114">訊息不包含 UNA，而且分隔符號的管線屬性的格式不正確 '{0}'</span><span class="sxs-lookup"><span data-stu-id="12544-114">Message did not contain UNA and pipeline property for delimiters was incorrect format '{0}'</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="12544-115">說明</span><span class="sxs-lookup"><span data-stu-id="12544-115">Explanation</span></span>  
 <span data-ttu-id="12544-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送 EDIFACT 交換因為無法判定處理交換時所需的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="12544-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming EDIFACT interchange because it could not determine the separators required to process the interchange.</span></span> <span data-ttu-id="12544-117">如果交換沒有 UNA 區段，而且 EfactDelimiters 管線屬性並未充分定義的分隔符號，這可能會發生。</span><span class="sxs-lookup"><span data-stu-id="12544-117">This can occur if the interchange does not have a UNA segment and the EfactDelimiters pipeline property does not adequately define the separators.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="12544-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="12544-118">User Action</span></span>  
 <span data-ttu-id="12544-119">若要解決這個錯誤，請執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="12544-119">To resolve this error, do one of the following:</span></span>  
  
1.  <span data-ttu-id="12544-120">請確定交換已定義的交換中，分隔符號的 UNA 區段，然後再重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="12544-120">Make sure that the interchange has a UNA segment that defines the separators for the interchange, and then resend the interchange.</span></span>  
  
2.  <span data-ttu-id="12544-121">EfactDelimiters 管線藉由開啟 BizTalk Server 管理主控台，以滑鼠右鍵按一下接收位置，可以接收的交換，內容，按一下省略符號，將管線的傳送管線 屬性的集合和然後輸入字串，包含分隔符號的值。</span><span class="sxs-lookup"><span data-stu-id="12544-121">Set the EfactDelimiters pipeline property for the send pipeline by opening the BizTalk Server Administration Console, right-clicking the receive location that will be receiving the interchange, clicking Properties, clicking the ellipsis for the pipeline, and then entering a string containing the values of the separators.</span></span>