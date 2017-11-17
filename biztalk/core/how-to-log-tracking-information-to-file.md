---
title: "如何追蹤資訊記錄至檔案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Business Rules Framework, tracking
- DebugTrackingInterceptor
- Business Rules Framework, code samples
ms.assetid: c832b763-aa08-4a0e-9086-776dccb0a6ef
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6cdaae8e727cedc784ecaade83178cf50f863f99
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-log-tracking-information-to-file"></a><span data-ttu-id="86bb3-102">如何將追蹤資訊記錄至檔案</span><span class="sxs-lookup"><span data-stu-id="86bb3-102">How to Log Tracking Information to File</span></span>
<span data-ttu-id="86bb3-103">當商務規則引擎在執行時，它會將執行追蹤資訊傳送到攔截器。</span><span class="sxs-lookup"><span data-stu-id="86bb3-103">When the Business Rule Engine executes, it passes execution tracking information to an interceptor.</span></span> <span data-ttu-id="86bb3-104">引擎會設定為使用 BizTalk 攔截器追蹤訊息事件和服務執行個體資料時使用。</span><span class="sxs-lookup"><span data-stu-id="86bb3-104">The engine is configured to use the BizTalk interceptor which is used when tracking message events and service instance data.</span></span> <span data-ttu-id="86bb3-105">當您呼叫 BizTalk 協調流程外部的引擎時，您可以在執行原則時傳送想使用的攔截器。</span><span class="sxs-lookup"><span data-stu-id="86bb3-105">If you are calling the engine outside of BizTalk orchestration, you can pass the interceptor you want to use when you execute the policy.</span></span> <span data-ttu-id="86bb3-106">除了 BizTalk 攔截器，您也可以使用**DebugTrackingInterceptor**來追蹤資訊輸出到檔案。</span><span class="sxs-lookup"><span data-stu-id="86bb3-106">In addition to the BizTalk interceptor, you can also use the **DebugTrackingInterceptor** to output the tracking information to file.</span></span> <span data-ttu-id="86bb3-107">下列程式碼範例示範如何使用**DebugTrackingInterceptor**。</span><span class="sxs-lookup"><span data-stu-id="86bb3-107">The following code example demonstrates how to use **DebugTrackingInterceptor**.</span></span>  
  
```  
DebugTrackingInterceptor tracker = new DebugTrackingInterceptor("TrackingOutput.txt");  
policy.Execute(shortTermFacts,tracker);  
```