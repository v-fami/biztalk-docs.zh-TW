---
title: "無法匯入服務端點組態。 | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6dae5154-04e2-4d9b-b2b2-85313683fd9e
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4100435706ab26c0f4ab99dea4d2088ecad1c948
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-import-service-endpoint-configuration"></a><span data-ttu-id="156f8-103">無法匯入服務端點組態。</span><span class="sxs-lookup"><span data-stu-id="156f8-103">Unable to import service endpoint configuration.</span></span>
## <a name="details"></a><span data-ttu-id="156f8-104">詳細資料</span><span class="sxs-lookup"><span data-stu-id="156f8-104">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="156f8-105">產品名稱</span><span class="sxs-lookup"><span data-stu-id="156f8-105">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="156f8-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="156f8-106">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="156f8-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="156f8-107">Event ID</span></span>|<span data-ttu-id="156f8-108">0</span><span class="sxs-lookup"><span data-stu-id="156f8-108">0</span></span>|  
|<span data-ttu-id="156f8-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="156f8-109">Event Source</span></span>|<span data-ttu-id="156f8-110">0</span><span class="sxs-lookup"><span data-stu-id="156f8-110">0</span></span>|  
|<span data-ttu-id="156f8-111">元件</span><span class="sxs-lookup"><span data-stu-id="156f8-111">Component</span></span>|<span data-ttu-id="156f8-112">0</span><span class="sxs-lookup"><span data-stu-id="156f8-112">0</span></span>|  
|<span data-ttu-id="156f8-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="156f8-113">Symbolic Name</span></span>|<span data-ttu-id="156f8-114">0</span><span class="sxs-lookup"><span data-stu-id="156f8-114">0</span></span>|  
|<span data-ttu-id="156f8-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="156f8-115">Message Text</span></span>|<span data-ttu-id="156f8-116">無法匯入服務端點組態</span><span class="sxs-lookup"><span data-stu-id="156f8-116">Unable to import service endpoint configuration</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="156f8-117">說明</span><span class="sxs-lookup"><span data-stu-id="156f8-117">Explanation</span></span>  
 <span data-ttu-id="156f8-118">可能有多個說明這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="156f8-118">There could be more than one explanation for this error.</span></span> <span data-ttu-id="156f8-119">組態檔可能包含無效的字元。</span><span class="sxs-lookup"><span data-stu-id="156f8-119">The configuration file may contain invalid characters.</span></span> <span data-ttu-id="156f8-120">根項目可能已遺失。</span><span class="sxs-lookup"><span data-stu-id="156f8-120">The root element may be missing.</span></span> <span data-ttu-id="156f8-121">根層級的資料可能不正確。</span><span class="sxs-lookup"><span data-stu-id="156f8-121">The data at the root level may be invalid.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="156f8-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="156f8-122">User Action</span></span>  
 <span data-ttu-id="156f8-123">請確認組態檔的有效性。</span><span class="sxs-lookup"><span data-stu-id="156f8-123">Verify the validity of the configuration file.</span></span> <span data-ttu-id="156f8-124">嘗試使用服務組態編輯器中開啟組態檔 (**svcConfigEditor.exe**)，並確認每個屬性。</span><span class="sxs-lookup"><span data-stu-id="156f8-124">Try to open the configuration file with the Service Configuration Editor (**svcConfigEditor.exe**) and verify each property.</span></span>