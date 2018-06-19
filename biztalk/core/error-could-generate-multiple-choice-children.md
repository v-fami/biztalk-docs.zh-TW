---
title: 錯誤-可能產生多個 Choice 子系 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.couldGenMultipleChoiceChildren
ms.assetid: 64e69ebb-781f-4ecb-9d91-6fdcca949d4b
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9322897f6fab9bc4b9c3e098214c19fb339b58d2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22240686"
---
# <a name="error---could-generate-multiple-choice-children"></a><span data-ttu-id="cc0cb-102">錯誤-可能產生多個 Choice 子系</span><span class="sxs-lookup"><span data-stu-id="cc0cb-102">Error - Could Generate Multiple Choice Children</span></span>
<span data-ttu-id="cc0cb-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="cc0cb-103">**Error Code**</span></span>  
  
 <span data-ttu-id="cc0cb-104">btm1027</span><span class="sxs-lookup"><span data-stu-id="cc0cb-104">btm1027</span></span>  
  
 <span data-ttu-id="cc0cb-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="cc0cb-105">**Explanation**</span></span>  
  
 <span data-ttu-id="cc0cb-106">目的結構描述的連結，不適當地啟用多個節點**選擇**要產生的群組節點。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-106">Links to the destination schema inappropriately enable multiple nodes within a **Choice** group node to be generated.</span></span>  
  
 <span data-ttu-id="cc0cb-107">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="cc0cb-107">**User Action**</span></span>  
  
 <span data-ttu-id="cc0cb-108">重新設定連結至目的結構描述，因此，只有單一節點內**選擇**產生群組節點。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-108">Rework the links into the destination schema so that only a single node within the **Choice** group node can be generated.</span></span>