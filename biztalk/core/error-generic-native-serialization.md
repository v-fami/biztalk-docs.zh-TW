---
title: 錯誤-一般原生序列化 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.genericNativeSerialize
ms.assetid: 3728727d-7d99-432d-844e-c956cc4635e4
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d2eacfae17d72dbb17786a1d924cfdf14be20ee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error---generic-native-serialization"></a><span data-ttu-id="c59d9-102">錯誤-一般原生序列化</span><span class="sxs-lookup"><span data-stu-id="c59d9-102">Error - Generic Native Serialization</span></span>
<span data-ttu-id="c59d9-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="c59d9-103">**Error Code**</span></span>  
  
 <span data-ttu-id="c59d9-104">btm1049</span><span class="sxs-lookup"><span data-stu-id="c59d9-104">btm1049</span></span>  
  
 <span data-ttu-id="c59d9-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="c59d9-105">**Explanation**</span></span>  
  
 <span data-ttu-id="c59d9-106">由於發生未指定的錯誤，無法將轉換 (由對應所指定) 產生的 XML 輸出執行個體訊息，轉換為目的結構描述指定的原生格式。</span><span class="sxs-lookup"><span data-stu-id="c59d9-106">The XML output instance message produced by the transformation specified by the map could not be converted to the native format specified by the destination schema due to an unspecified error.</span></span>  
  
 <span data-ttu-id="c59d9-107">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="c59d9-107">**User Action**</span></span>  
  
 <span data-ttu-id="c59d9-108">在 [BizTalk 編輯器] 中開啟目的結構描述，並使用**驗證結構描述**，**驗證執行個體**，和**產生執行個體**可用的命令，當您以滑鼠右鍵按一下在 [方案總管] 中，以隔離問題的結構描述。</span><span class="sxs-lookup"><span data-stu-id="c59d9-108">Open the destination schema in BizTalk Editor and use the **Validate Schema**, **Validate Instance**, and **Generate Instance** commands, available when you right-click a schema in Solution Explorer, to isolate the problem.</span></span>