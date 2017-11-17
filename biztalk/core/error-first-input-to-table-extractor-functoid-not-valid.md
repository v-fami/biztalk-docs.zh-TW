---
title: "錯誤-無效的表格抽選程式運算質的第一個輸入 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.firstInputToTableExtractorNotValid
ms.assetid: 5b197531-9bf4-49c6-ad3a-b3ba92d37701
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f2449f6c5572a3a29b620becdc4310f4152f2eac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error---first-input-to-table-extractor-functoid-not-valid"></a><span data-ttu-id="be255-102">錯誤-無效的表格抽選程式運算質的第一個輸入</span><span class="sxs-lookup"><span data-stu-id="be255-102">Error - First Input to Table Extractor Functoid Not Valid</span></span>
<span data-ttu-id="be255-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="be255-103">**Error Code**</span></span>  
  
 <span data-ttu-id="be255-104">btm1019</span><span class="sxs-lookup"><span data-stu-id="be255-104">btm1019</span></span>  
  
 <span data-ttu-id="be255-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="be255-105">**Explanation**</span></span>  
  
 <span data-ttu-id="be255-106">第一個輸入的參數所指定**表格抽選程式**運算質不可以從連結**表格迴圈**運算質，視需要。</span><span class="sxs-lookup"><span data-stu-id="be255-106">The first input parameter to the indicated **Table Extractor** functoid is not a link from a **Table Looping** functoid, as required.</span></span>  
  
 <span data-ttu-id="be255-107">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="be255-107">**User Action**</span></span>  
  
 <span data-ttu-id="be255-108">指定之間建立連結**表格抽選程式**運算質與適當**表格迴圈**運算質拖曳到另一個其中一個。</span><span class="sxs-lookup"><span data-stu-id="be255-108">Create a link between the indicated **Table Extractor** functoid and the appropriate **Table Looping** functoid by dragging one of them to the other.</span></span> <span data-ttu-id="be255-109">在地圖格線頁上，前一個運算質必須位於後一個運算質右邊。</span><span class="sxs-lookup"><span data-stu-id="be255-109">The former functoid must be located to the right of the latter functoid in a map grid page.</span></span> <span data-ttu-id="be255-110">此外，使用**設定\<運算質 > 運算質**對話方塊方塊中，確認新建立的連結是第一個輸入的參數所指定**表格抽選程式**運算質。</span><span class="sxs-lookup"><span data-stu-id="be255-110">Also, using the **Configure \<Functoid> Functoid** dialog box, ensure that the newly created link is the first input parameter to the indicated **Table Extractor** functoid.</span></span>