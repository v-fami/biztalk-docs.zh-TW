---
title: 錯誤-必要的目標有選擇節點來源 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.reqdTargetHasChoiceNodeSource
ms.assetid: 5b5af999-d100-4e5d-a959-c8b11d574d3b
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91c9ad912b03bbb475efcc9eb8207a388400b43b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22240622"
---
# <a name="error---required-target-has-choice-node-source"></a><span data-ttu-id="009fd-102">錯誤-必要的目標有選擇節點來源</span><span class="sxs-lookup"><span data-stu-id="009fd-102">Error - Required Target Has Choice Node Source</span></span>
<span data-ttu-id="009fd-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="009fd-103">**Error Code**</span></span>  
  
 <span data-ttu-id="009fd-104">btm1029</span><span class="sxs-lookup"><span data-stu-id="009fd-104">btm1029</span></span>  
  
 <span data-ttu-id="009fd-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="009fd-105">**Explanation**</span></span>  
  
 <span data-ttu-id="009fd-106">目的結構描述中指定的節點指定為必要，但連結至來源結構描述內的節點**選擇**節點。</span><span class="sxs-lookup"><span data-stu-id="009fd-106">The indicated node in the destination schema is specified as required but is linked to a node in the source schema that is within a **Choice** node.</span></span> <span data-ttu-id="009fd-107">因為來源結構描述中指定的節點可能不會出現在輸入執行個體訊息中，有可能無法用來建立必要的節點與目的結構描述的來源。</span><span class="sxs-lookup"><span data-stu-id="009fd-107">Because the indicated node in the source schema may not appear in an input instance message, there may not be a source from which to create the required node in the destination schema.</span></span>  
  
 <span data-ttu-id="009fd-108">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="009fd-108">**User Action**</span></span>  
  
 <span data-ttu-id="009fd-109">視需要，將目的結構描述中的指定節點變更為選擇性，或在目的結構描述中提供不同來源給指定的節點，此結構描述必須發生於所有有效的輸入執行個體訊息。</span><span class="sxs-lookup"><span data-stu-id="009fd-109">As appropriate, either change the indicated node in the destination schema to optional, or provide a different source for the indicated node in the destination schema that must occur in all valid input instance messages.</span></span>