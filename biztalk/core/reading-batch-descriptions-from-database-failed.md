---
title: 無法從資料庫讀取 Batchdescriptions |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f959aa35-d957-45b0-bfac-1134b5087d0c
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66a9049c9f3964b231d7c1370784bccd78fd0836
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268654"
---
# <a name="reading-batch-descriptions-from-database-failed"></a><span data-ttu-id="b8148-102">從資料庫讀取 BatchDescriptions 失敗</span><span class="sxs-lookup"><span data-stu-id="b8148-102">Reading Batch Descriptions from database failed</span></span>
## <a name="details"></a><span data-ttu-id="b8148-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b8148-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b8148-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="b8148-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="b8148-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="b8148-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="b8148-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="b8148-106">Event ID</span></span>|-|  
|<span data-ttu-id="b8148-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="b8148-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="b8148-108">EDI</span><span class="sxs-lookup"><span data-stu-id="b8148-108"> EDI</span></span>|  
|<span data-ttu-id="b8148-109">元件</span><span class="sxs-lookup"><span data-stu-id="b8148-109">Component</span></span>|<span data-ttu-id="b8148-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="b8148-110">EDI Engine</span></span>|  
|<span data-ttu-id="b8148-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="b8148-111">Symbolic Name</span></span>|<span data-ttu-id="b8148-112">LoadBatchFiltersFailed</span><span class="sxs-lookup"><span data-stu-id="b8148-112">LoadBatchFiltersFailed</span></span>|  
|<span data-ttu-id="b8148-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="b8148-113">Message Text</span></span>|<span data-ttu-id="b8148-114">從資料庫讀取 BatchDescriptions 失敗。</span><span class="sxs-lookup"><span data-stu-id="b8148-114">Reading BatchDescriptions from database failed.</span></span> <span data-ttu-id="b8148-115">錯誤：{0}。</span><span class="sxs-lookup"><span data-stu-id="b8148-115">Error: {0}.</span></span> <span data-ttu-id="b8148-116">堆疊追蹤： {1}。</span><span class="sxs-lookup"><span data-stu-id="b8148-116">Stack Trace: {1}.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b8148-117">說明</span><span class="sxs-lookup"><span data-stu-id="b8148-117">Explanation</span></span>  
 <span data-ttu-id="b8148-118">這個錯誤/警告/資訊事件表示 BizTalk Server 無法載入指定的比較連入訊息內容屬性設定的批次篩選條件。</span><span class="sxs-lookup"><span data-stu-id="b8148-118">This Error/Warning/Information event indicates BizTalk Server was unable to load the filters specified for the configured batches to compare context properties of incoming messages.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b8148-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="b8148-119">User Action</span></span>  
 <span data-ttu-id="b8148-120">若要解決這個錯誤，請確定 「 管理 」 資料庫已啟動，且可以連線。</span><span class="sxs-lookup"><span data-stu-id="b8148-120">To resolve this error, ensure that the Management database is up and can be connected.</span></span>