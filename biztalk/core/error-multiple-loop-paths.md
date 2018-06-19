---
title: 錯誤-多個迴圈路徑 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.multipleLoopPaths
ms.assetid: 3f7c0c1c-5aaa-4da9-99ab-78bac536b8dd
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: afdcb1a235c71163552fd5f6b255e572feef8dc5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241086"
---
# <a name="error---multiple-loop-paths"></a><span data-ttu-id="c702f-102">錯誤-多個迴圈路徑</span><span class="sxs-lookup"><span data-stu-id="c702f-102">Error - Multiple Loop Paths</span></span>
<span data-ttu-id="c702f-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="c702f-103">**Error Code**</span></span>  
  
 <span data-ttu-id="c702f-104">btm1030</span><span class="sxs-lookup"><span data-stu-id="c702f-104">btm1030</span></span>  
  
 <span data-ttu-id="c702f-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="c702f-105">**Explanation**</span></span>  
  
 <span data-ttu-id="c702f-106">在目的結構描述中指定的節點，有多個來源迴圈路徑。</span><span class="sxs-lookup"><span data-stu-id="c702f-106">The indicated node in the destination schema has multiple source loop paths.</span></span>  
  
 <span data-ttu-id="c702f-107">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="c702f-107">**User Action**</span></span>  
  
 <span data-ttu-id="c702f-108">使用**迴圈**的迴圈會執行來源結構描述中，明確指定節點的運算質。</span><span class="sxs-lookup"><span data-stu-id="c702f-108">Use a **Looping** functoid to explicitly specify the node in the source schema over which the looping will be performed.</span></span>