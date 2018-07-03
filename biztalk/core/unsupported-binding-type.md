---
title: 不支援的繫結類型 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5556a7d7-f092-4f69-9561-88f51ac46cc9
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a1090157a3b39dea62a3c95cb787b91e0a33bfc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004335"
---
# <a name="unsupported-binding-type"></a><span data-ttu-id="7b984-102">不支援的繫結類型</span><span class="sxs-lookup"><span data-stu-id="7b984-102">Unsupported binding type</span></span>
## <a name="details"></a><span data-ttu-id="7b984-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7b984-103">Details</span></span>  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="7b984-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="7b984-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="7b984-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="7b984-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="7b984-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="7b984-106">Event ID</span></span>     |                                         <span data-ttu-id="7b984-107">0</span><span class="sxs-lookup"><span data-stu-id="7b984-107">0</span></span>                                          |
|  <span data-ttu-id="7b984-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="7b984-108">Event Source</span></span>   |                                         <span data-ttu-id="7b984-109">0</span><span class="sxs-lookup"><span data-stu-id="7b984-109">0</span></span>                                          |
|    <span data-ttu-id="7b984-110">元件</span><span class="sxs-lookup"><span data-stu-id="7b984-110">Component</span></span>    |                                         <span data-ttu-id="7b984-111">0</span><span class="sxs-lookup"><span data-stu-id="7b984-111">0</span></span>                                          |
|  <span data-ttu-id="7b984-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="7b984-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="7b984-113">0</span><span class="sxs-lookup"><span data-stu-id="7b984-113">0</span></span>                                          |
|  <span data-ttu-id="7b984-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="7b984-114">Message Text</span></span>   |                              <span data-ttu-id="7b984-115">不支援的繫結類型</span><span class="sxs-lookup"><span data-stu-id="7b984-115">Unsupported binding type</span></span>                              |
  
## <a name="explanation"></a><span data-ttu-id="7b984-116">說明</span><span class="sxs-lookup"><span data-stu-id="7b984-116">Explanation</span></span>  
 <span data-ttu-id="7b984-117">已選擇 MsmqIntegration 繫結，但是這不受 WCF 配接卡支援。</span><span class="sxs-lookup"><span data-stu-id="7b984-117">The MsmqIntegration binding was chosen, but is not supported by the WCF adapter.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7b984-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="7b984-118">User Action</span></span>  
 <span data-ttu-id="7b984-119">使用 WCF-NetMsmq 配接器。</span><span class="sxs-lookup"><span data-stu-id="7b984-119">Use the WCF-NetMsmq adapter.</span></span> <span data-ttu-id="7b984-120">如果需要交換原生的 MSMQ 訊息，請使用 BizTalk MSMQ 配接器。</span><span class="sxs-lookup"><span data-stu-id="7b984-120">If native MSMQ messages need to be exchanged, use the BizTalk MSMQ adapter.</span></span>  
  
 <span data-ttu-id="7b984-121">如需設定配接器的詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="7b984-121">For further information on configuring adapters, see the following resource:</span></span>  
  
-   [<span data-ttu-id="7b984-122">設定 WCF-NetMsmq 配接器</span><span class="sxs-lookup"><span data-stu-id="7b984-122">Configuring the WCF-NetMsmq Adapter</span></span>](../core/configuring-the-wcf-netmsmq-adapter.md)