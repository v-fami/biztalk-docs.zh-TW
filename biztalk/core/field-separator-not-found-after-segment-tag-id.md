---
title: 區段標記識別碼後找不到欄位分隔符號 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5f6f0a74-3560-4d6d-9893-85e8426e6b17
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 82511305a9df96af2bfafe81ce41fb0eaf9ab604
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36965783"
---
# <a name="field-separator-not-found-after-segment-tag-id"></a><span data-ttu-id="40147-102">區段標記識別碼後找不到欄位分隔符號</span><span class="sxs-lookup"><span data-stu-id="40147-102">Field separator not found after segment tag id</span></span>
## <a name="details"></a><span data-ttu-id="40147-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="40147-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="40147-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="40147-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="40147-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="40147-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="40147-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="40147-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="40147-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="40147-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="40147-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="40147-108"> EDI</span></span> |
|    <span data-ttu-id="40147-109">元件</span><span class="sxs-lookup"><span data-stu-id="40147-109">Component</span></span>    |                                       <span data-ttu-id="40147-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="40147-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="40147-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="40147-111">Symbolic Name</span></span>  |                          <span data-ttu-id="40147-112">X12SeFsNotFoundAfterTagIdDescription</span><span class="sxs-lookup"><span data-stu-id="40147-112">X12SeFsNotFoundAfterTagIdDescription</span></span>                          |
|  <span data-ttu-id="40147-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="40147-113">Message Text</span></span>   |                     <span data-ttu-id="40147-114">區段標記識別碼後找不到欄位分隔符號</span><span class="sxs-lookup"><span data-stu-id="40147-114">Field separator not found after segment tag id</span></span>                     |
  
## <a name="explanation"></a><span data-ttu-id="40147-115">說明</span><span class="sxs-lookup"><span data-stu-id="40147-115">Explanation</span></span>  
 <span data-ttu-id="40147-116">這個錯誤/警告/資訊事件表示，接收管線無法處理交換，因為交換包含區段沒有緊接著資料元素分隔符號，區段識別項。</span><span class="sxs-lookup"><span data-stu-id="40147-116">This Error/Warning/Information event indicates that the receive pipeline could not process the interchange because the interchange contained a segment that had a segment identifier without a data element separator immediately following it.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="40147-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="40147-117">User Action</span></span>  
 <span data-ttu-id="40147-118">若要解決這個錯誤，確定交換中的所有區段識別項有資料元素分隔符號之後，立即就會重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="40147-118">To resolve this error, ensure that all segment identifiers in the interchange have data element separators immediately following them, and then have the interchange resent.</span></span>