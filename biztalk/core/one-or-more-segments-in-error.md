---
title: 一或多個區段發生錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4ee86667-e72a-4f1b-8d5c-15ca710dbe5d
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c364af2691767ac55a52afb52b77f09d39ef6d2d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005064"
---
# <a name="one-or-more-segments-in-error"></a><span data-ttu-id="25fd7-102">一或多個區段發生錯誤</span><span class="sxs-lookup"><span data-stu-id="25fd7-102">One or more segments in error</span></span>
## <a name="details"></a><span data-ttu-id="25fd7-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="25fd7-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="25fd7-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="25fd7-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="25fd7-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="25fd7-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="25fd7-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="25fd7-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="25fd7-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="25fd7-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="25fd7-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="25fd7-108"> EDI</span></span> |
|    <span data-ttu-id="25fd7-109">元件</span><span class="sxs-lookup"><span data-stu-id="25fd7-109">Component</span></span>    |                                       <span data-ttu-id="25fd7-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="25fd7-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="25fd7-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="25fd7-111">Symbolic Name</span></span>  |                        <span data-ttu-id="25fd7-112">X12TsOneOrMoreSegmentsInErrorDescription</span><span class="sxs-lookup"><span data-stu-id="25fd7-112">X12TsOneOrMoreSegmentsInErrorDescription</span></span>                        |
|  <span data-ttu-id="25fd7-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="25fd7-113">Message Text</span></span>   |                             <span data-ttu-id="25fd7-114">一或多個區段發生錯誤</span><span class="sxs-lookup"><span data-stu-id="25fd7-114">One or more segments in error</span></span>                              |
  
## <a name="explanation"></a><span data-ttu-id="25fd7-115">說明</span><span class="sxs-lookup"><span data-stu-id="25fd7-115">Explanation</span></span>  
 <span data-ttu-id="25fd7-116">這個錯誤/警告/資訊事件表示，來管理它們的結構描述不符合交換中的一個或多個區段。</span><span class="sxs-lookup"><span data-stu-id="25fd7-116">This Error/Warning/Information event indicates that one or more segments in the interchange did not conform to the schema governing them.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="25fd7-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="25fd7-117">User Action</span></span>  
 <span data-ttu-id="25fd7-118">若要解決這個錯誤，判斷哪一個區段中錯誤、 開啟結構描述來控管該區段中，以及判斷從該區段處於錯誤的結構描述。</span><span class="sxs-lookup"><span data-stu-id="25fd7-118">To resolve this error, determine which segment is in error, open the schema governing that segment, and determine from that schema why the segment is in error.</span></span>