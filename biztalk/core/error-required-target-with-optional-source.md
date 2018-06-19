---
title: 錯誤-必要的目標具有選擇性來源 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.reqdTargetWithOptionalSource
ms.assetid: 3f342011-4577-4682-8324-8296615d5194
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 76dd96f61766a475db6385e306bc64bc36db4fcf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241398"
---
# <a name="error---required-target-with-optional-source"></a><span data-ttu-id="4bcde-102">錯誤-必要的目標具有選擇性來源</span><span class="sxs-lookup"><span data-stu-id="4bcde-102">Error - Required Target with Optional Source</span></span>
<span data-ttu-id="4bcde-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="4bcde-103">**Error Code**</span></span>  
  
 <span data-ttu-id="4bcde-104">btm1001</span><span class="sxs-lookup"><span data-stu-id="4bcde-104">btm1001</span></span>  
  
 <span data-ttu-id="4bcde-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="4bcde-105">**Explanation**</span></span>  
  
 <span data-ttu-id="4bcde-106">目的結構描述中指定必要節點的資料，是來自於來源結構描述中的選擇性節點。</span><span class="sxs-lookup"><span data-stu-id="4bcde-106">The data for the indicated required node in the destination schema comes from an optional node in the source schema.</span></span> <span data-ttu-id="4bcde-107">因此，有效的執行個體訊息可能會導致對應失敗。</span><span class="sxs-lookup"><span data-stu-id="4bcde-107">Therefore, there may be valid instance messages for which mapping will fail.</span></span>  
  
 <span data-ttu-id="4bcde-108">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="4bcde-108">**User Action**</span></span>  
  
 <span data-ttu-id="4bcde-109">分別確認所指定來源與目的結構描述的選擇性與必要特性，並考慮使這些特性一致。</span><span class="sxs-lookup"><span data-stu-id="4bcde-109">Confirm the optional and required characteristics of the specified source and destination nodes, respectively, and consider making these characteristics match.</span></span>