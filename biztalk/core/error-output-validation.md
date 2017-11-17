---
title: "錯誤-輸出驗證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.outputValidation
ms.assetid: 18a251a9-6bd4-4fd1-a774-2ea1b7870891
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7410fba7cebbf5183a02e79aa3c179eb86cd8395
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error---output-validation"></a><span data-ttu-id="0a921-102">錯誤-輸出驗證</span><span class="sxs-lookup"><span data-stu-id="0a921-102">Error - Output Validation</span></span>
<span data-ttu-id="0a921-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="0a921-103">**Error Code**</span></span>  
  
 <span data-ttu-id="0a921-104">btm1046</span><span class="sxs-lookup"><span data-stu-id="0a921-104">btm1046</span></span>  
  
 <span data-ttu-id="0a921-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="0a921-105">**Explanation**</span></span>  
  
 <span data-ttu-id="0a921-106">由於指出的原因，無法驗證「測試對應」作業所產生的輸出執行個體訊息檔案是否符合目的結構描述。</span><span class="sxs-lookup"><span data-stu-id="0a921-106">The output instance message file created by the Test Map operation could not be validated against the destination schema for the indicated reason.</span></span>  
  
 <span data-ttu-id="0a921-107">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="0a921-107">**User Action**</span></span>  
  
 <span data-ttu-id="0a921-108">根據指出的原因，適當更正在對應中指定的轉換，或更正目的結構描述，或兩者。</span><span class="sxs-lookup"><span data-stu-id="0a921-108">Based on the indicated reason, make the appropriate corrections to either the transformations specified in the map, or to the destination schema, or to both.</span></span> <span data-ttu-id="0a921-109">可能會很有幫助，BizTalk 編輯器中開啟目的結構描述，並使用**驗證結構描述**，**驗證執行個體**，和**產生執行個體**可用的命令時以滑鼠右鍵按一下方案總管 中的結構描述。</span><span class="sxs-lookup"><span data-stu-id="0a921-109">It may be helpful to open the destination schema in BizTalk Editor and use the **Validate Schema**, **Validate Instance**, and **Generate Instance** commands available when you right-click a schema in Solution Explorer.</span></span>