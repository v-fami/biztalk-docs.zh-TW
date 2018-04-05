---
title: 錯誤-沒有任何連結或常數的對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.mapWithoutAnyLinksOrConstants
ms.assetid: 8d1cdbcd-4bd0-4ddc-9e94-746e82b6ec48
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d697d6d053f2c0a36d0f5cb45002dca28a92f005
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error---map-without-any-links-or-constants"></a><span data-ttu-id="af4d9-102">錯誤-沒有任何連結或常數的對應</span><span class="sxs-lookup"><span data-stu-id="af4d9-102">Error - Map Without Any Links or Constants</span></span>
<span data-ttu-id="af4d9-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="af4d9-103">**Error Code**</span></span>  
  
 <span data-ttu-id="af4d9-104">btm1000</span><span class="sxs-lookup"><span data-stu-id="af4d9-104">btm1000</span></span>  
  
 <span data-ttu-id="af4d9-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="af4d9-105">**Explanation**</span></span>  
  
 <span data-ttu-id="af4d9-106">對應未包含結構描述間的連結，或目的結構描述中的常數值。</span><span class="sxs-lookup"><span data-stu-id="af4d9-106">The map does not contain any links between the schemas, or constant values in the destination schema.</span></span> <span data-ttu-id="af4d9-107">因此，無法從此對應建立輸出。</span><span class="sxs-lookup"><span data-stu-id="af4d9-107">Therefore, no output can be created from this map.</span></span>  
  
 <span data-ttu-id="af4d9-108">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="af4d9-108">**User Action**</span></span>  
  
 <span data-ttu-id="af4d9-109">新增適當的連結 (若有需要，也新增運算質) 至對應格線，或新增常數至目的結構描述，以指定符合來源結構描述的執行個體訊息，如何轉換為符合目的結構描述的執行個體訊息。</span><span class="sxs-lookup"><span data-stu-id="af4d9-109">Add the appropriate links and, if appropriate, functoids to the map grid, or constants to the destination schema, to specify how instance messages conforming to the source schema should be transformed into instance messages conforming to the destination schema.</span></span>