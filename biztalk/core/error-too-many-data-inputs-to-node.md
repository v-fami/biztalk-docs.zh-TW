---
title: 錯誤-節點有太多資料輸入 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.tooManyDataInputsToNode
ms.assetid: 176805f0-2d6d-4072-b866-132b98c7e4b5
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c9e465f861c4048708f41ea86f04ffd52375dec9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241022"
---
# <a name="error---too-many-data-inputs-to-node"></a><span data-ttu-id="d4a92-102">錯誤-節點有太多資料輸入</span><span class="sxs-lookup"><span data-stu-id="d4a92-102">Error - Too Many Data Inputs to Node</span></span>
<span data-ttu-id="d4a92-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="d4a92-103">**Error Code**</span></span>  
  
 <span data-ttu-id="d4a92-104">btm1005</span><span class="sxs-lookup"><span data-stu-id="d4a92-104">btm1005</span></span>  
  
 <span data-ttu-id="d4a92-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="d4a92-105">**Explanation**</span></span>  
  
 <span data-ttu-id="d4a92-106">沒有連接到目的結構描述的輸入連結數目的指定節點的連結數目越大**迴圈**連接到指定節點的祖系節點的運算質。</span><span class="sxs-lookup"><span data-stu-id="d4a92-106">There are a greater number of links connected to the indicated node in the destination schema than the number of input links to the **Looping** functoid that is connected to an ancestor node of the indicated node.</span></span> <span data-ttu-id="d4a92-107">前一個與後一個類型的連結數目應該一致。</span><span class="sxs-lookup"><span data-stu-id="d4a92-107">The number of links of the former and latter types should match.</span></span>  
  
 <span data-ttu-id="d4a92-108">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="d4a92-108">**User Action**</span></span>  
  
 <span data-ttu-id="d4a92-109">重做的連結數目連接至指定的節點和**迴圈**」 運算質連接到上階節點，使其相符。</span><span class="sxs-lookup"><span data-stu-id="d4a92-109">Rework the number of links connected to the indicated node and to the **Looping** functoid connected to the ancestor node so that they match.</span></span>