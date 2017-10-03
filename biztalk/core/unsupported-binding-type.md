---
title: "不支援的繫結類型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5556a7d7-f092-4f69-9561-88f51ac46cc9
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 98d156f22b5e903cd704dc109f98435203bd6ba8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="unsupported-binding-type"></a><span data-ttu-id="38abf-102">不支援的繫結類型</span><span class="sxs-lookup"><span data-stu-id="38abf-102">Unsupported binding type</span></span>
## <a name="details"></a><span data-ttu-id="38abf-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="38abf-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="38abf-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="38abf-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="38abf-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="38abf-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="38abf-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="38abf-106">Event ID</span></span>|<span data-ttu-id="38abf-107">0</span><span class="sxs-lookup"><span data-stu-id="38abf-107">0</span></span>|  
|<span data-ttu-id="38abf-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="38abf-108">Event Source</span></span>|<span data-ttu-id="38abf-109">0</span><span class="sxs-lookup"><span data-stu-id="38abf-109">0</span></span>|  
|<span data-ttu-id="38abf-110">元件</span><span class="sxs-lookup"><span data-stu-id="38abf-110">Component</span></span>|<span data-ttu-id="38abf-111">0</span><span class="sxs-lookup"><span data-stu-id="38abf-111">0</span></span>|  
|<span data-ttu-id="38abf-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="38abf-112">Symbolic Name</span></span>|<span data-ttu-id="38abf-113">0</span><span class="sxs-lookup"><span data-stu-id="38abf-113">0</span></span>|  
|<span data-ttu-id="38abf-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="38abf-114">Message Text</span></span>|<span data-ttu-id="38abf-115">不支援的繫結類型</span><span class="sxs-lookup"><span data-stu-id="38abf-115">Unsupported binding type</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="38abf-116">說明</span><span class="sxs-lookup"><span data-stu-id="38abf-116">Explanation</span></span>  
 <span data-ttu-id="38abf-117">已選擇 MsmqIntegration 繫結，但是這不受 WCF 配接卡支援。</span><span class="sxs-lookup"><span data-stu-id="38abf-117">The MsmqIntegration binding was chosen, but is not supported by the WCF adapter.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="38abf-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="38abf-118">User Action</span></span>  
 <span data-ttu-id="38abf-119">使用 WCF-NetMsmq 配接器。</span><span class="sxs-lookup"><span data-stu-id="38abf-119">Use the WCF-NetMsmq adapter.</span></span> <span data-ttu-id="38abf-120">如果需要交換原生的 MSMQ 訊息，請使用 BizTalk MSMQ 配接器。</span><span class="sxs-lookup"><span data-stu-id="38abf-120">If native MSMQ messages need to be exchanged, use the BizTalk MSMQ adapter.</span></span>  
  
 <span data-ttu-id="38abf-121">如需設定配接器的詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="38abf-121">For further information on configuring adapters, see the following resource:</span></span>  
  
-   [<span data-ttu-id="38abf-122">設定 Wcf-netmsmq 配接器</span><span class="sxs-lookup"><span data-stu-id="38abf-122">Configuring the WCF-NetMsmq Adapter</span></span>](../core/configuring-the-wcf-netmsmq-adapter.md)