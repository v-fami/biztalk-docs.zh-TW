---
title: 錯誤-從不同的父記錄輸入累計運算質 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.inputsToCumulativeFromDiffParents
ms.assetid: a2dcfe6f-0cd4-41ed-a69f-e510a74760a9
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3c919001e05ca99383ffce72c8d450f6d04624b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error---inputs-to-cumulative-functoid-from-different-parent-records"></a><span data-ttu-id="df681-102">錯誤-從不同的父記錄輸入累計運算質</span><span class="sxs-lookup"><span data-stu-id="df681-102">Error - Inputs to Cumulative Functoid from Different Parent Records</span></span>
<span data-ttu-id="df681-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="df681-103">**Error Code**</span></span>  
  
 <span data-ttu-id="df681-104">btm1032</span><span class="sxs-lookup"><span data-stu-id="df681-104">btm1032</span></span>  
  
 <span data-ttu-id="df681-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="df681-105">**Explanation**</span></span>  
  
 <span data-ttu-id="df681-106">為指定**累計**運算質，第二個輸入的參數 （累積範圍） 是來自來源結構描述的節點做為第一個輸入參數 （要累計的節點） 的不同部分。</span><span class="sxs-lookup"><span data-stu-id="df681-106">For the indicated **Cumulative** functoid, the second input parameter (the accumulation scope) is from a different part of the source schema than the node serving as the first input parameter (the node to accumulate).</span></span>  
  
 <span data-ttu-id="df681-107">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="df681-107">**User Action**</span></span>  
  
 <span data-ttu-id="df681-108">請確定這兩個輸入參數來指定**累計**運算質會共用相同的父記錄，或您提供第二個輸入的參數 （累積範圍） 具有常數輸入的參數。</span><span class="sxs-lookup"><span data-stu-id="df681-108">Ensure that both input parameters to the indicated **Cumulative** functoid share the same parent record, or that the second input parameter (the accumulation scope) you provide has a constant input parameter.</span></span>