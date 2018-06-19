---
title: 錯誤-XSLT 指令碼處理運算質的子系產生程式碼 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.xsltScriptingChildrenGenCode
ms.assetid: 9cdac362-177f-445e-904b-aa6a9b1eb46f
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 810fe9befecd9bbd1a15468ca714177900450cb7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239550"
---
# <a name="error---children-of-xslt-scripting-functoid-generate-code"></a><span data-ttu-id="e7199-102">錯誤-XSLT 指令碼處理運算質的子系產生程式碼</span><span class="sxs-lookup"><span data-stu-id="e7199-102">Error - Children of XSLT Scripting Functoid Generate Code</span></span>
<span data-ttu-id="e7199-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="e7199-103">**Error Code**</span></span>  
  
 <span data-ttu-id="e7199-104">btm1063</span><span class="sxs-lookup"><span data-stu-id="e7199-104">btm1063</span></span>  
  
 <span data-ttu-id="e7199-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="e7199-105">**Explanation**</span></span>  
  
 <span data-ttu-id="e7199-106">無法使用**指令碼處理**對應中找不到設定為使用內嵌 XSLT 或 「 XSLT 呼叫範本的運算質。</span><span class="sxs-lookup"><span data-stu-id="e7199-106">A scenario that contradicts the use of a **Scripting** functoid that is configured to use inline XSLT or an XSLT Call Template was found in the map.</span></span> <span data-ttu-id="e7199-107">在目的結構描述，會連結到這類的輸出之節點的下階節點**指令碼處理**運算質會嘗試產生其本身的 XSLT 程式碼。</span><span class="sxs-lookup"><span data-stu-id="e7199-107">In the destination schema, descendent nodes of a node that is linked to the output of such a **Scripting** functoid are attempting to generate XSLT code of their own.</span></span>  
  
 <span data-ttu-id="e7199-108">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="e7199-108">**User Action**</span></span>  
  
 <span data-ttu-id="e7199-109">藉由變更相關的使用方式，移除不相容的問題**指令碼處理**運算質或變更子節點，使其不再產生其本身的 XSLT 程式碼。</span><span class="sxs-lookup"><span data-stu-id="e7199-109">Remove the incompatibility by changing the usage of the relevant **Scripting** functoid or changing the child nodes such that they no longer generate XSLT code of their own.</span></span>