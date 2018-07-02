---
title: 此排程器無法排程批次 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4146124c-1eb0-4c1e-843b-b19c687a56b7
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a7be725a96f00c3d27db71db7748aff512ad960
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974359"
---
# <a name="this-scheduler-was-unable-to-schedule-the-batch"></a><span data-ttu-id="d5836-102">此排程器無法排程批次</span><span class="sxs-lookup"><span data-stu-id="d5836-102">This scheduler was unable to schedule the batch</span></span>
## <a name="details"></a><span data-ttu-id="d5836-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d5836-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="d5836-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d5836-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="d5836-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="d5836-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="d5836-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d5836-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="d5836-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="d5836-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d5836-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="d5836-108"> EDI</span></span> |
|    <span data-ttu-id="d5836-109">元件</span><span class="sxs-lookup"><span data-stu-id="d5836-109">Component</span></span>    |                                    <span data-ttu-id="d5836-110">批次引擎</span><span class="sxs-lookup"><span data-stu-id="d5836-110">Batching Engine</span></span>                                     |
|  <span data-ttu-id="d5836-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d5836-111">Symbolic Name</span></span>  |                                 <span data-ttu-id="d5836-112">UnableToScheduleBatch</span><span class="sxs-lookup"><span data-stu-id="d5836-112">UnableToScheduleBatch</span></span>                                  |
|  <span data-ttu-id="d5836-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d5836-113">Message Text</span></span>   |                    <span data-ttu-id="d5836-114">此排程器無法排程批次</span><span class="sxs-lookup"><span data-stu-id="d5836-114">This scheduler was unable to schedule the batch</span></span>                     |
  
## <a name="explanation"></a><span data-ttu-id="d5836-115">說明</span><span class="sxs-lookup"><span data-stu-id="d5836-115">Explanation</span></span>  
 <span data-ttu-id="d5836-116">此錯誤表示排程器無法判斷下一個出現的批次釋放。</span><span class="sxs-lookup"><span data-stu-id="d5836-116">This error indicates the scheduler could not determine the next occurrence of a batch release.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d5836-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d5836-117">User Action</span></span>  
 <span data-ttu-id="d5836-118">若要解決這個錯誤，請確定有效的批次發行排程。</span><span class="sxs-lookup"><span data-stu-id="d5836-118">To resolve this error, make sure the batch release schedule is valid.</span></span>