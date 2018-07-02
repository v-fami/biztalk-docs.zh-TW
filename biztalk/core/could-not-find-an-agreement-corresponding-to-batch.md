---
title: 找不到與批次對應的協議 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d1c0480-9a6f-481a-9143-e5a55707c3b5
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b51fabd7aaf01d751f1a5ecff3c3a4e773e0b7b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978375"
---
# <a name="could-not-find-an-agreement-corresponding-to-batch"></a><span data-ttu-id="3bd59-102">找不到與批次對應的協議</span><span class="sxs-lookup"><span data-stu-id="3bd59-102">Could not find an Agreement corresponding to batch</span></span>
## <a name="details"></a><span data-ttu-id="3bd59-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3bd59-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="3bd59-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="3bd59-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="3bd59-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="3bd59-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="3bd59-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="3bd59-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="3bd59-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="3bd59-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="3bd59-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="3bd59-108"> EDI</span></span> |
|    <span data-ttu-id="3bd59-109">元件</span><span class="sxs-lookup"><span data-stu-id="3bd59-109">Component</span></span>    |                                       <span data-ttu-id="3bd59-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="3bd59-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="3bd59-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="3bd59-111">Symbolic Name</span></span>  |                               <span data-ttu-id="3bd59-112">AgreementNotFoundForBatch</span><span class="sxs-lookup"><span data-stu-id="3bd59-112">AgreementNotFoundForBatch</span></span>                                |
|  <span data-ttu-id="3bd59-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="3bd59-113">Message Text</span></span>   |                <span data-ttu-id="3bd59-114">找不到與批次對應的協議{0}。</span><span class="sxs-lookup"><span data-stu-id="3bd59-114">Could not find an Agreement corresponding to batch {0}.</span></span>                 |
  
## <a name="explanation"></a><span data-ttu-id="3bd59-115">說明</span><span class="sxs-lookup"><span data-stu-id="3bd59-115">Explanation</span></span>  
 <span data-ttu-id="3bd59-116">這個錯誤/警告/資訊事件表示 BizTalk Server 找不到批次對應至這個識別碼，在嘗試啟動/停止批次，或處理批次訊息。</span><span class="sxs-lookup"><span data-stu-id="3bd59-116">This Error/Warning/Information event indicates BizTalk Server was unable to find a Batch corresponding to this Id while trying to start/stop a batch or process a batch message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3bd59-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="3bd59-117">User Action</span></span>  
 <span data-ttu-id="3bd59-118">若要解決這個錯誤，請確定具有指定識別碼的批次存在內含協議的協議屬性中。</span><span class="sxs-lookup"><span data-stu-id="3bd59-118">To resolve this error, ensure that a batch with the given Id is present in the Agreement properties of the containing Agreement.</span></span>