---
title: WCF 執行階段錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5591bd4-aa15-4c7a-903e-fc73b880692f
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df75d019b9af36f4ef7fce21ea17dc1e9a8e7aac
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999927"
---
# <a name="wcf-run-time-errors"></a><span data-ttu-id="da90c-102">WCF 執行階段錯誤</span><span class="sxs-lookup"><span data-stu-id="da90c-102">WCF Run-Time Errors</span></span>
<span data-ttu-id="da90c-103">診斷及解決 WCF 執行階段事件的資訊。</span><span class="sxs-lookup"><span data-stu-id="da90c-103">Information for diagnosing and resolving WCF run-time events.</span></span>  
  
## <a name="wcf-service-host-restarted"></a><span data-ttu-id="da90c-104">WCF 服務主控件已重新啟動</span><span class="sxs-lookup"><span data-stu-id="da90c-104">WCF service host restarted</span></span>
  
|                 |                                   <span data-ttu-id="da90c-105">錯誤詳細資料</span><span class="sxs-lookup"><span data-stu-id="da90c-105">Error details</span></span>                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="da90c-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="da90c-106">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="da90c-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="da90c-107">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="da90c-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="da90c-108">Event ID</span></span>     |                                       <span data-ttu-id="da90c-109">0x1FB0</span><span class="sxs-lookup"><span data-stu-id="da90c-109">0x1FB0</span></span>                                       |
|  <span data-ttu-id="da90c-110">事件來源</span><span class="sxs-lookup"><span data-stu-id="da90c-110">Event Source</span></span>   |                                         <span data-ttu-id="da90c-111">0</span><span class="sxs-lookup"><span data-stu-id="da90c-111">0</span></span>                                          |
|    <span data-ttu-id="da90c-112">元件</span><span class="sxs-lookup"><span data-stu-id="da90c-112">Component</span></span>    |                                         <span data-ttu-id="da90c-113">0</span><span class="sxs-lookup"><span data-stu-id="da90c-113">0</span></span>                                          |
|  <span data-ttu-id="da90c-114">符號名稱</span><span class="sxs-lookup"><span data-stu-id="da90c-114">Symbolic Name</span></span>  |                          <span data-ttu-id="da90c-115">BTS_I_WCF_SERVICE_HOST_RESTARTED</span><span class="sxs-lookup"><span data-stu-id="da90c-115">BTS_I_WCF_SERVICE_HOST_RESTARTED</span></span>                          |
|  <span data-ttu-id="da90c-116">訊息文字</span><span class="sxs-lookup"><span data-stu-id="da90c-116">Message Text</span></span>   |                                         <span data-ttu-id="da90c-117">0</span><span class="sxs-lookup"><span data-stu-id="da90c-117">0</span></span>                                          |
  
## <a name="explanation"></a><span data-ttu-id="da90c-118">說明</span><span class="sxs-lookup"><span data-stu-id="da90c-118">Explanation</span></span>  
 <span data-ttu-id="da90c-119">此訊息提供一個方式，讓 WCF 配接器寫入「資訊性」事件日誌項目 (針對配接器提供的 API 可用來建立警告或錯誤，但無法建立資訊)。</span><span class="sxs-lookup"><span data-stu-id="da90c-119">This message provides a way for the WCF adapter to write an “informational” event log entry (the provided APIs for adapters allow the creation of warnings or errors, not information).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="da90c-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="da90c-120">User Action</span></span>  
 <span data-ttu-id="da90c-121">如果您在事件日誌中看到此資訊事件，表示自動復原已成功。</span><span class="sxs-lookup"><span data-stu-id="da90c-121">If you see this informational event in the event log, it indicates that the auto-recovery has succeeded.</span></span> <span data-ttu-id="da90c-122">不需要針對此訊息採取任何進一步動作。</span><span class="sxs-lookup"><span data-stu-id="da90c-122">No further action in regard to this message is necessary.</span></span>