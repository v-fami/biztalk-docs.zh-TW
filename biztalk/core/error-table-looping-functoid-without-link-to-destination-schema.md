---
title: 錯誤-表格迴圈運算質沒有目的結構描述連結 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.tableLoopingNoLinkToDestSchema
ms.assetid: cf162e6a-5c61-4adc-978b-af641db67ed2
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 329e6670288f05382acf0ea014ba9ae84c4cb645
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error---table-looping-functoid-without-link-to-destination-schema"></a><span data-ttu-id="d0029-102">錯誤-表格迴圈運算質沒有目的結構描述連結</span><span class="sxs-lookup"><span data-stu-id="d0029-102">Error - Table Looping Functoid Without Link to Destination Schema</span></span>
<span data-ttu-id="d0029-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="d0029-103">**Error Code**</span></span>  
  
 <span data-ttu-id="d0029-104">btm1077</span><span class="sxs-lookup"><span data-stu-id="d0029-104">btm1077</span></span>  
  
 <span data-ttu-id="d0029-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="d0029-105">**Explanation**</span></span>  
  
 <span data-ttu-id="d0029-106">不同於大部分的運算質**表格迴圈**運算質有多個輸出。</span><span class="sxs-lookup"><span data-stu-id="d0029-106">Unlike most functoids, the **Table Looping** functoid has multiple outputs.</span></span> <span data-ttu-id="d0029-107">所有這些輸出的其中一個必須做為第一個輸入參數個別執行個體的連接**表格抽選程式**運算質。</span><span class="sxs-lookup"><span data-stu-id="d0029-107">All but one of these outputs must be connected as the first input parameter to separate instances of the **Table Extractor** functoid.</span></span> <span data-ttu-id="d0029-108">剩餘的輸出必須連接到**記錄**目的結構描述中的節點 （具有適當的循環設定）。</span><span class="sxs-lookup"><span data-stu-id="d0029-108">The remaining output must be connected to a **Record** node (with appropriate recurrence settings) in the destination schema.</span></span> <span data-ttu-id="d0029-109">這個錯誤發生在後續輸出連結**表格迴圈**運算質遺漏。</span><span class="sxs-lookup"><span data-stu-id="d0029-109">This error occurs when this latter output link from a **Table Looping** functoid is missing.</span></span>  
  
 <span data-ttu-id="d0029-110">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="d0029-110">**User Action**</span></span>  
  
 <span data-ttu-id="d0029-111">拖曳指定**表格迴圈**記錄適當**記錄**建立遺失的連結到目的結構描述的節點。</span><span class="sxs-lookup"><span data-stu-id="d0029-111">Drag the indicated **Table Looping** record to the appropriate **Record** node in the destination schema to create the missing link.</span></span>