---
title: 無法叫用錯誤-指令碼處理運算質的外部組件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.cannotInvokeExternalAssembly
ms.assetid: 30d97b05-2cbf-44a5-b219-3a5ae17fc597
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37f6df36a955f2f40da35368fd72fd2d1fcbb7b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22240918"
---
# <a name="error---external-assembly-for-scripting-functoid-cannot-be-invoked"></a><span data-ttu-id="309fb-102">錯誤-指令碼處理運算質的外部組件無法叫用</span><span class="sxs-lookup"><span data-stu-id="309fb-102">Error - External Assembly for Scripting Functoid Cannot Be Invoked</span></span>
<span data-ttu-id="309fb-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="309fb-103">**Error Code**</span></span>  
  
 <span data-ttu-id="309fb-104">btm1067</span><span class="sxs-lookup"><span data-stu-id="309fb-104">btm1067</span></span>  
  
 <span data-ttu-id="309fb-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="309fb-105">**Explanation**</span></span>  
  
 <span data-ttu-id="309fb-106">與相關聯的外部組件方法**指令碼處理**運算質無法叫用。</span><span class="sxs-lookup"><span data-stu-id="309fb-106">The external assembly method that is associated with the relevant **Scripting** functoid cannot be invoked.</span></span> <span data-ttu-id="309fb-107">雖然對於對應編譯而言並非必要，「測試對應」作業要求「全域組件快取」(GAC) 中必須有該類外部組件存在。</span><span class="sxs-lookup"><span data-stu-id="309fb-107">Although not required for map compilation, the Test Map operation requires that such external assemblies be present in the global assembly cache (GAC).</span></span> <span data-ttu-id="309fb-108">一般而言，執行工作階段也要求 GAC 中必須有外部組件存在。</span><span class="sxs-lookup"><span data-stu-id="309fb-108">Normal, run time operation also requires that external assemblies be present in the GAC.</span></span>  
  
 <span data-ttu-id="309fb-109">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="309fb-109">**User Action**</span></span>  
  
 <span data-ttu-id="309fb-110">請確認參考相關的外部組件**指令碼處理**運算質是在 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="309fb-110">Ensure that the external assembly referenced by the relevant **Scripting** functoid is in the GAC.</span></span>