---
title: 通訊模式錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06656073-9bae-4d6f-98ae-2714a72ee79c
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef9f7f4419d6c95b9b11343f395ab8e3d17c7c34
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37021081"
---
# <a name="communication-pattern-errors"></a><span data-ttu-id="dbb4a-102">通訊模式錯誤</span><span class="sxs-lookup"><span data-stu-id="dbb4a-102">Communication Pattern Errors</span></span>
<span data-ttu-id="dbb4a-103">診斷及解決 WCF 通訊模式錯誤的資訊。</span><span class="sxs-lookup"><span data-stu-id="dbb4a-103">Information for diagnosing and resolving WCF Communication Pattern errors.</span></span>  

## <a name="fault-messages-are-not-supported-on-one-way-ports"></a><span data-ttu-id="dbb4a-104">單向連接埠上不支援將錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="dbb4a-104">Fault messages are not supported on one-way ports</span></span>
  
|                 |                                                       <span data-ttu-id="dbb4a-105">錯誤詳細資料</span><span class="sxs-lookup"><span data-stu-id="dbb4a-105">Error details</span></span>                                                       |
|-----------------|---------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="dbb4a-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="dbb4a-106">Product Name</span></span>   |                    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                     |
| <span data-ttu-id="dbb4a-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="dbb4a-107">Product Version</span></span> |                                [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                 |
|    <span data-ttu-id="dbb4a-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="dbb4a-108">Event ID</span></span>     |                                                             <span data-ttu-id="dbb4a-109">0</span><span class="sxs-lookup"><span data-stu-id="dbb4a-109">0</span></span>                                                             |
|  <span data-ttu-id="dbb4a-110">事件來源</span><span class="sxs-lookup"><span data-stu-id="dbb4a-110">Event Source</span></span>   |                                                             <span data-ttu-id="dbb4a-111">0</span><span class="sxs-lookup"><span data-stu-id="dbb4a-111">0</span></span>                                                             |
|    <span data-ttu-id="dbb4a-112">元件</span><span class="sxs-lookup"><span data-stu-id="dbb4a-112">Component</span></span>    |                                                             <span data-ttu-id="dbb4a-113">0</span><span class="sxs-lookup"><span data-stu-id="dbb4a-113">0</span></span>                                                             |
|  <span data-ttu-id="dbb4a-114">符號名稱</span><span class="sxs-lookup"><span data-stu-id="dbb4a-114">Symbolic Name</span></span>  |                                                             <span data-ttu-id="dbb4a-115">0</span><span class="sxs-lookup"><span data-stu-id="dbb4a-115">0</span></span>                                                             |
|  <span data-ttu-id="dbb4a-116">訊息文字</span><span class="sxs-lookup"><span data-stu-id="dbb4a-116">Message Text</span></span>   | <span data-ttu-id="dbb4a-117">單向連接埠上不支援將錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="dbb4a-117">Fault messages are not supported on one-way ports.</span></span> <span data-ttu-id="dbb4a-118">更正服務描述"{0}「 連接埠類型 」{1}"，然後重新執行精靈</span><span class="sxs-lookup"><span data-stu-id="dbb4a-118">Correct service description "{0}" port type "{1}" and rerun the wizard</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="dbb4a-119">說明</span><span class="sxs-lookup"><span data-stu-id="dbb4a-119">Explanation</span></span>  
 <span data-ttu-id="dbb4a-120">此錯誤表示嘗試取用的服務是單向服務，而且具有指定的錯誤。</span><span class="sxs-lookup"><span data-stu-id="dbb4a-120">This error indicates the service trying to be consumed is a one-way service and has the fault specified.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="dbb4a-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="dbb4a-121">User Action</span></span>  
 <span data-ttu-id="dbb4a-122">請更正服務藉由切換至要求-回應從單向通訊模式。</span><span class="sxs-lookup"><span data-stu-id="dbb4a-122">Correct the service by switching the communication pattern from one-way to request-response.</span></span> <span data-ttu-id="dbb4a-123">或在程式碼中移除錯誤。</span><span class="sxs-lookup"><span data-stu-id="dbb4a-123">Or remove the fault in the code.</span></span>
 
 