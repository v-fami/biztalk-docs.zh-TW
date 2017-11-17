---
title: "錯誤-一般原生剖析 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.genericNativeParsing
ms.assetid: a28a4c0f-b69b-448b-b305-3b06b4f061e4
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 383c3198af290552715d51812f22c82760cb445f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error---generic-native-parsing"></a><span data-ttu-id="653a4-102">錯誤-一般原生剖析</span><span class="sxs-lookup"><span data-stu-id="653a4-102">Error - Generic Native Parsing</span></span>
<span data-ttu-id="653a4-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="653a4-103">**Error Code**</span></span>  
  
 <span data-ttu-id="653a4-104">btm1042</span><span class="sxs-lookup"><span data-stu-id="653a4-104">btm1042</span></span>  
  
 <span data-ttu-id="653a4-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="653a4-105">**Explanation**</span></span>  
  
 <span data-ttu-id="653a4-106">無法剖析針對「測試對應」作業指定的原生輸入執行個體訊息檔案，且發生一般嚴重剖析錯誤。</span><span class="sxs-lookup"><span data-stu-id="653a4-106">The native input instance message file specified for the Test Map operation could not be parsed, and generated a generic fatal parsing error.</span></span>  
  
 <span data-ttu-id="653a4-107">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="653a4-107">**User Action**</span></span>  
  
 <span data-ttu-id="653a4-108">視需要更正指定檔案中，與對應關聯的來源結構描述或原生輸入執行個體訊息，或兩者。</span><span class="sxs-lookup"><span data-stu-id="653a4-108">As appropriate, correct either the source schema associated with the map or the native input instance message in the specified file, or both.</span></span> <span data-ttu-id="653a4-109">考慮在 BizTalk 編輯器中工作以隔離問題。</span><span class="sxs-lookup"><span data-stu-id="653a4-109">Consider working within BizTalk Editor to isolate the problem.</span></span> <span data-ttu-id="653a4-110">**驗證結構描述**和**產生執行個體**可用的命令，當您以滑鼠右鍵按一下 [方案總管] 中的結構描述可用於尋找結構描述錯誤。</span><span class="sxs-lookup"><span data-stu-id="653a4-110">The **Validate Schema** and **Generate Instance** commands, available when you right-click a schema in Solution Explorer, are useful for finding schema errors.</span></span>