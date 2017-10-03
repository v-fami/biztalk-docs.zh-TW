---
title: "選擇性節點 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing, BizTalk Mapper
- maps, testing
- testing, maps
- BizTalk Mapper, testing
- maps, optional nodes
ms.assetid: 7dcd203e-fb23-438a-87d1-42323acd87cc
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 96cf7d8b22ee8469a7e52dba7bbad899209c5274
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="optional-nodes"></a><span data-ttu-id="f9acf-102">選擇性節點</span><span class="sxs-lookup"><span data-stu-id="f9acf-102">Optional Nodes</span></span>
<span data-ttu-id="f9acf-103">使用選擇性節點將會在您測試對應時產生警告。</span><span class="sxs-lookup"><span data-stu-id="f9acf-103">Using optional nodes will produce a warning when you test your map.</span></span> <span data-ttu-id="f9acf-104">有兩種情況會將來源節點視為選擇性：</span><span class="sxs-lookup"><span data-stu-id="f9acf-104">There are two conditions in which a source node may be considered optional:</span></span>  
  
-   <span data-ttu-id="f9acf-105">實際的記錄或欄位為選擇性。</span><span class="sxs-lookup"><span data-stu-id="f9acf-105">The actual record or field is optional.</span></span>  
  
-   <span data-ttu-id="f9acf-106">必須要有來源記錄或欄位，但是父系、祖系和更高階層為選擇性。</span><span class="sxs-lookup"><span data-stu-id="f9acf-106">The source record or field is required, but a parent, grandparent, and farther up the hierarchy is optional.</span></span>  
  
 <span data-ttu-id="f9acf-107">可能的狀況是，來源結構描述中的記錄或欄位為選擇性，但是目的結構描述需要對應的記錄或欄位。</span><span class="sxs-lookup"><span data-stu-id="f9acf-107">You may have situations when you have records and fields in a source schema that are optional, but the destination schema requires the corresponding records or fields.</span></span>  
  
 <span data-ttu-id="f9acf-108">在這兩種可能的情況中，測試您的對應中產生警告**輸出**視窗。</span><span class="sxs-lookup"><span data-stu-id="f9acf-108">In both of the possible conditions, testing your map produces a warning in the **Output** window.</span></span> <span data-ttu-id="f9acf-109">此外，輸出資料將不包含目標節點。</span><span class="sxs-lookup"><span data-stu-id="f9acf-109">In addition, the output data will not include the target node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9acf-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9acf-110">See Also</span></span>  
 [<span data-ttu-id="f9acf-111">測試對應</span><span class="sxs-lookup"><span data-stu-id="f9acf-111">Testing Maps</span></span>](../core/testing-maps.md)