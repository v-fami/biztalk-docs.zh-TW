---
title: 建立控制訊息失敗批次識別碼 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f03078e7-46b0-4082-9d66-6b892152a12d
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ba63bc570ac29f95c70b5bc6e09050e26c435b2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979799"
---
# <a name="creation-of-control-message-failed-for-batch-id"></a><span data-ttu-id="9e8c6-102">建立控制訊息失敗批次識別碼</span><span class="sxs-lookup"><span data-stu-id="9e8c6-102">Creation of Control Message failed for Batch id</span></span>
## <a name="details"></a><span data-ttu-id="9e8c6-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9e8c6-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="9e8c6-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="9e8c6-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="9e8c6-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="9e8c6-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="9e8c6-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="9e8c6-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="9e8c6-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="9e8c6-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="9e8c6-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="9e8c6-108"> EDI</span></span> |
|    <span data-ttu-id="9e8c6-109">元件</span><span class="sxs-lookup"><span data-stu-id="9e8c6-109">Component</span></span>    |                                       <span data-ttu-id="9e8c6-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="9e8c6-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="9e8c6-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="9e8c6-111">Symbolic Name</span></span>  |                               <span data-ttu-id="9e8c6-112">CreateControlMessageFailed</span><span class="sxs-lookup"><span data-stu-id="9e8c6-112">CreateControlMessageFailed</span></span>                               |
|  <span data-ttu-id="9e8c6-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="9e8c6-113">Message Text</span></span>   |                  <span data-ttu-id="9e8c6-114">建立控制訊息失敗批次識別碼{0}。</span><span class="sxs-lookup"><span data-stu-id="9e8c6-114">Creation of Control Message failed for Batch id {0}.</span></span>                  |
  
## <a name="explanation"></a><span data-ttu-id="9e8c6-115">說明</span><span class="sxs-lookup"><span data-stu-id="9e8c6-115">Explanation</span></span>  
 <span data-ttu-id="9e8c6-116">這個錯誤/警告/資訊事件表示 BizTalk Server 已啟動/停止批次。</span><span class="sxs-lookup"><span data-stu-id="9e8c6-116">This Error/Warning/Information event indicates BizTalk Server was start/stop a batch.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9e8c6-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="9e8c6-117">User Action</span></span>  
 <span data-ttu-id="9e8c6-118">若要解決這個錯誤，請確定具有指定識別碼的批次存在內含協議的協議屬性中，且資料庫已啟動。</span><span class="sxs-lookup"><span data-stu-id="9e8c6-118">To resolve this error, ensure that a batch with the given Id is present in the Agreement properties of the containing Agreement and the database is up.</span></span>