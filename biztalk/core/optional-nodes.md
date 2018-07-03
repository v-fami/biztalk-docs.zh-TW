---
title: 選擇性節點 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- testing, BizTalk Mapper
- maps, testing
- testing, maps
- BizTalk Mapper, testing
- maps, optional nodes
ms.assetid: 7dcd203e-fb23-438a-87d1-42323acd87cc
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91fe82709df36b374d8744e2060798074835b891
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994087"
---
# <a name="optional-nodes"></a><span data-ttu-id="d14fc-102">選擇性節點</span><span class="sxs-lookup"><span data-stu-id="d14fc-102">Optional Nodes</span></span>
<span data-ttu-id="d14fc-103">使用選擇性節點將會在您測試對應時產生警告。</span><span class="sxs-lookup"><span data-stu-id="d14fc-103">Using optional nodes will produce a warning when you test your map.</span></span> <span data-ttu-id="d14fc-104">有兩種情況會將來源節點視為選擇性：</span><span class="sxs-lookup"><span data-stu-id="d14fc-104">There are two conditions in which a source node may be considered optional:</span></span>  
  
- <span data-ttu-id="d14fc-105">實際的記錄或欄位為選擇性。</span><span class="sxs-lookup"><span data-stu-id="d14fc-105">The actual record or field is optional.</span></span>  
  
- <span data-ttu-id="d14fc-106">必須要有來源記錄或欄位，但是父系、祖系和更高階層為選擇性。</span><span class="sxs-lookup"><span data-stu-id="d14fc-106">The source record or field is required, but a parent, grandparent, and farther up the hierarchy is optional.</span></span>  
  
  <span data-ttu-id="d14fc-107">可能的狀況是，來源結構描述中的記錄或欄位為選擇性，但是目的結構描述需要對應的記錄或欄位。</span><span class="sxs-lookup"><span data-stu-id="d14fc-107">You may have situations when you have records and fields in a source schema that are optional, but the destination schema requires the corresponding records or fields.</span></span>  
  
  <span data-ttu-id="d14fc-108">在這兩種可能的情況中，測試您的對應中產生警告**輸出**視窗。</span><span class="sxs-lookup"><span data-stu-id="d14fc-108">In both of the possible conditions, testing your map produces a warning in the **Output** window.</span></span> <span data-ttu-id="d14fc-109">此外，輸出資料將不包含目標節點。</span><span class="sxs-lookup"><span data-stu-id="d14fc-109">In addition, the output data will not include the target node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d14fc-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d14fc-110">See Also</span></span>  
 [<span data-ttu-id="d14fc-111">測試對應</span><span class="sxs-lookup"><span data-stu-id="d14fc-111">Testing Maps</span></span>](../core/testing-maps.md)