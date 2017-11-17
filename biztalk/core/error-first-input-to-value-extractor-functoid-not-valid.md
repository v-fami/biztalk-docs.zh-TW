---
title: "錯誤-值擷取程式運算質不是有效的第一個輸入 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.firstInputValueExtractorNotValid
ms.assetid: 7703ca5f-21aa-441f-8c28-b02da72c25c1
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 68b143cea7e1d7e99c1d5b378bd9d6619270fb70
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error---first-input-to-value-extractor-functoid-not-valid"></a><span data-ttu-id="f2575-102">錯誤-值擷取程式運算質不是有效的第一個輸入</span><span class="sxs-lookup"><span data-stu-id="f2575-102">Error - First Input to Value Extractor Functoid Not Valid</span></span>
<span data-ttu-id="f2575-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="f2575-103">**Error Code**</span></span>  
  
 <span data-ttu-id="f2575-104">btm1002</span><span class="sxs-lookup"><span data-stu-id="f2575-104">btm1002</span></span>  
  
 <span data-ttu-id="f2575-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="f2575-105">**Explanation**</span></span>  
  
 <span data-ttu-id="f2575-106">第一個輸入的參數所指定**值擷取程式 」**運算質必須是輸出 （ADO 資料錄集） 從**資料庫尋查**運算質。</span><span class="sxs-lookup"><span data-stu-id="f2575-106">The first input parameter to the indicated **Value Extractor** functoid must be the output (an ADO recordset) from the **Database Lookup** functoid.</span></span>  
  
 <span data-ttu-id="f2575-107">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="f2575-107">**User Action**</span></span>  
  
 <span data-ttu-id="f2575-108">請確認所有的第一個輸入**值擷取程式 」**運算質是從連結**資料庫尋查**其左邊的地圖格線頁中的運算質。</span><span class="sxs-lookup"><span data-stu-id="f2575-108">Ensure that the first input to all **Value Extractor** functoids is a link from a **Database Lookup** functoid to their left in a map grid page.</span></span>