---
title: "錯誤-XSLT 指令碼處理運算質不是有效的輸出連結 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.outputLinkForXsltNotValid
ms.assetid: cdf8e779-6cf6-4d9c-8655-f8b406498fb7
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efd597a3953db76087086c7ea9038e9fa1fd87eb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error---output-link-for-xslt-scripting-functoid-not-valid"></a><span data-ttu-id="67f92-102">錯誤-XSLT 指令碼處理運算質不是有效的輸出連結</span><span class="sxs-lookup"><span data-stu-id="67f92-102">Error - Output Link For XSLT Scripting Functoid Not Valid</span></span>
<span data-ttu-id="67f92-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="67f92-103">**Error Code**</span></span>  
  
 <span data-ttu-id="67f92-104">btm1075</span><span class="sxs-lookup"><span data-stu-id="67f92-104">btm1075</span></span>  
  
 <span data-ttu-id="67f92-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="67f92-105">**Explanation**</span></span>  
  
 <span data-ttu-id="67f92-106">相關的輸出連結**指令碼處理**運算質設定為使用內嵌 XSLT 或 「 XSLT 呼叫範本無效。</span><span class="sxs-lookup"><span data-stu-id="67f92-106">The output link of the relevant **Scripting** functoid configured to use inline XSLT or an XSLT Call Template is not valid.</span></span> <span data-ttu-id="67f92-107">這類輸出**指令碼處理**必須連接的運算質直接目的結構描述中的節點 （而非另一個運算質，例如）。</span><span class="sxs-lookup"><span data-stu-id="67f92-107">The output of such **Scripting** functoids must be connected directly to a node in the destination schema (and not to another functoid, for example).</span></span>  
  
 <span data-ttu-id="67f92-108">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="67f92-108">**User Action**</span></span>  
  
 <span data-ttu-id="67f92-109">請確定您所連線的相關輸出連結**指令碼處理**直接到目的結構描述中節點的運算質。</span><span class="sxs-lookup"><span data-stu-id="67f92-109">Ensure that you connect the output link from the relevant **Scripting** functoid directly to a node in the destination schema.</span></span>