---
title: "移除命名空間範例的運作方式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf5834b4-e0fd-4180-9d15-4cdd99f0f353
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e82e4f369d8db2230b44586cbb928ea57b27f462
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-the-remove-namespace-sample-works"></a><span data-ttu-id="b7a43-102">移除命名空間範例的運作方式</span><span class="sxs-lookup"><span data-stu-id="b7a43-102">How the Remove Namespace Sample Works</span></span>
<span data-ttu-id="b7a43-103">第二個和第三個測試使用**移除命名空間**元件位於**NamespaceSampleSendPipeline**管線。</span><span class="sxs-lookup"><span data-stu-id="b7a43-103">The second and third tests use the **Remove Namespace** component located in the **NamespaceSampleSendPipeline** pipeline.</span></span> <span data-ttu-id="b7a43-104">它會採用做為輸入文件與命名空間的根節點上，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b7a43-104">It takes as input a document with a namespace on the root node, such as the following:</span></span>  
  
```  
<ns0:CanonicalOrder OrderID="OrderID_0" OrderDate="OrderDate_1"   
    Status="Status_2"   
    xmlns:ns0="http://schemas.microsoft.biztalk.esb.test.com/test">  
```  
  
 <span data-ttu-id="b7a43-105">**移除命名空間**元件只會移除此命名空間，並傳回文件沒有根節點的命名空間，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b7a43-105">The **Remove Namespace** component simply removes this namespace and returns a document that does not have a root node namespace, as shown here:</span></span>  
  
```  
<CanonicalOrder OrderID="OrderID_0" OrderDate="OrderDate_1" Status="Status_2">  
```