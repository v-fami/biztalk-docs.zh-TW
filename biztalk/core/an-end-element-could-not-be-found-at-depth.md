---
title: 在深度找不到結束項目 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a1edb60a-122a-4fe9-8d73-96521fe7326b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91c2727be39d3d2656e118d593b0347038657f61
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970183"
---
# <a name="an-end-element-could-not-be-found-at-depth"></a><span data-ttu-id="32917-102">在深度找不到結束項目</span><span class="sxs-lookup"><span data-stu-id="32917-102">An End Element could not be found at depth</span></span>
## <a name="details"></a><span data-ttu-id="32917-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="32917-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="32917-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="32917-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="32917-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="32917-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="32917-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="32917-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="32917-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="32917-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="32917-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="32917-108"> EDI</span></span> |
|    <span data-ttu-id="32917-109">元件</span><span class="sxs-lookup"><span data-stu-id="32917-109">Component</span></span>    |                                       <span data-ttu-id="32917-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="32917-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="32917-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="32917-111">Symbolic Name</span></span>  |                               <span data-ttu-id="32917-112">EndElementNotFoundAtDepth</span><span class="sxs-lookup"><span data-stu-id="32917-112">EndElementNotFoundAtDepth</span></span>                                |
|  <span data-ttu-id="32917-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="32917-113">Message Text</span></span>   |                     <span data-ttu-id="32917-114">結束項目深度{0}找不到</span><span class="sxs-lookup"><span data-stu-id="32917-114">An End Element at depth {0} could not be found</span></span>                     |
  
## <a name="explanation"></a><span data-ttu-id="32917-115">說明</span><span class="sxs-lookup"><span data-stu-id="32917-115">Explanation</span></span>  
 <span data-ttu-id="32917-116">這個錯誤/警告/資訊事件表示，BizTalk Server 無法處理外寄交換，因為 XML 訊息驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="32917-116">This Error/Warning/Information event indicates that BizTalk Server could not process the outgoing interchange because the XML message failed validation.</span></span> <span data-ttu-id="32917-117">XML 訊息不包含標頭或資料元素結束標記。</span><span class="sxs-lookup"><span data-stu-id="32917-117">The XML message did not contain an end tag for a header or data element.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="32917-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="32917-118">User Action</span></span>  
 <span data-ttu-id="32917-119">若要解決這個錯誤，以 XML 訊息，並新增適當的結束標記或結尾，然後再重新傳送。</span><span class="sxs-lookup"><span data-stu-id="32917-119">To resolve this error, add the appropriate end tag or trailer to the XML message, and then resend.</span></span>