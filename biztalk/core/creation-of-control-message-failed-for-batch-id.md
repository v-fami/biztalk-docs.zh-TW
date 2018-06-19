---
title: 建立控制訊息失敗批次識別碼 |Microsoft 文件
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
ms.openlocfilehash: 6a5650ab649e9b0957e64f3cdecc13c725d64536
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238190"
---
# <a name="creation-of-control-message-failed-for-batch-id"></a><span data-ttu-id="2862a-102">建立控制訊息失敗批次識別碼</span><span class="sxs-lookup"><span data-stu-id="2862a-102">Creation of Control Message failed for Batch id</span></span>
## <a name="details"></a><span data-ttu-id="2862a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2862a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2862a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2862a-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="2862a-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="2862a-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="2862a-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2862a-106">Event ID</span></span>|-|  
|<span data-ttu-id="2862a-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="2862a-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="2862a-108">EDI</span><span class="sxs-lookup"><span data-stu-id="2862a-108"> EDI</span></span>|  
|<span data-ttu-id="2862a-109">元件</span><span class="sxs-lookup"><span data-stu-id="2862a-109">Component</span></span>|<span data-ttu-id="2862a-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="2862a-110">EDI Engine</span></span>|  
|<span data-ttu-id="2862a-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2862a-111">Symbolic Name</span></span>|<span data-ttu-id="2862a-112">CreateControlMessageFailed</span><span class="sxs-lookup"><span data-stu-id="2862a-112">CreateControlMessageFailed</span></span>|  
|<span data-ttu-id="2862a-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2862a-113">Message Text</span></span>|<span data-ttu-id="2862a-114">建立控制訊息失敗批次識別碼 {0}。</span><span class="sxs-lookup"><span data-stu-id="2862a-114">Creation of Control Message failed for Batch id {0}.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2862a-115">說明</span><span class="sxs-lookup"><span data-stu-id="2862a-115">Explanation</span></span>  
 <span data-ttu-id="2862a-116">這個錯誤/警告/資訊事件表示 BizTalk Server 已啟動/停止批次。</span><span class="sxs-lookup"><span data-stu-id="2862a-116">This Error/Warning/Information event indicates BizTalk Server was start/stop a batch.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2862a-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2862a-117">User Action</span></span>  
 <span data-ttu-id="2862a-118">若要解決這個錯誤，請確定具有指定識別碼的批次存在內含協議的協議屬性，且資料庫已啟動。</span><span class="sxs-lookup"><span data-stu-id="2862a-118">To resolve this error, ensure that a batch with the given Id is present in the Agreement properties of the containing Agreement and the database is up.</span></span>