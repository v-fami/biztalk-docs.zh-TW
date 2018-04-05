---
title: 錯誤-輸入驗證 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.inputValidation
ms.assetid: 3529481d-11ae-4334-9ff7-24342cb2bab4
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b7f6392c6f5aad85442659beb9f6f1e3ef989299
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error---input-validation"></a><span data-ttu-id="6ac6e-102">錯誤-輸入驗證</span><span class="sxs-lookup"><span data-stu-id="6ac6e-102">Error - Input Validation</span></span>
<span data-ttu-id="6ac6e-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="6ac6e-103">**Error Code**</span></span>  
  
 <span data-ttu-id="6ac6e-104">btm1044</span><span class="sxs-lookup"><span data-stu-id="6ac6e-104">btm1044</span></span>  
  
 <span data-ttu-id="6ac6e-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="6ac6e-105">**Explanation**</span></span>  
  
 <span data-ttu-id="6ac6e-106">由於指出的原因，無法驗證「測試對應」作業指定的輸入執行個體訊息檔案是否符合來源結構描述。</span><span class="sxs-lookup"><span data-stu-id="6ac6e-106">The input instance message file specified for the Test Map operation could not be validated against the source schema for the indicated reason.</span></span>  
  
 <span data-ttu-id="6ac6e-107">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="6ac6e-107">**User Action**</span></span>  
  
 <span data-ttu-id="6ac6e-108">根據指出的原因，適當更正輸入執行個體訊息檔案或來源結構描述，或兩者。</span><span class="sxs-lookup"><span data-stu-id="6ac6e-108">Based on the indicated reason, make the appropriate corrections to either the input instance message file or to the source schema, or to both.</span></span> <span data-ttu-id="6ac6e-109">可能會很有幫助，BizTalk 編輯器中開啟來源結構描述，並使用**驗證結構描述**和**產生執行個體**可用，當您以滑鼠右鍵按一下 [方案總管] 中的結構描述的命令。</span><span class="sxs-lookup"><span data-stu-id="6ac6e-109">It may be helpful to open the source schema in BizTalk Editor and use the **Validate Schema** and **Generate Instance** commands available when you right-click a schema in Solution Explorer.</span></span>