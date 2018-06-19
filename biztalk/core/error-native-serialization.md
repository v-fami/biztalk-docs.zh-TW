---
title: 錯誤-原生序列化 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.nativeSerialize
ms.assetid: 48f8d460-83a0-44ce-af9b-086fcad36cb8
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c0d4a842a3f9a10703fb47bf21edb01ab92bd93c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241062"
---
# <a name="error---native-serialization"></a><span data-ttu-id="663d4-102">錯誤-原生序列化</span><span class="sxs-lookup"><span data-stu-id="663d4-102">Error - Native Serialization</span></span>
<span data-ttu-id="663d4-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="663d4-103">**Error Code**</span></span>  
  
 <span data-ttu-id="663d4-104">btm1048</span><span class="sxs-lookup"><span data-stu-id="663d4-104">btm1048</span></span>  
  
 <span data-ttu-id="663d4-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="663d4-105">**Explanation**</span></span>  
  
 <span data-ttu-id="663d4-106">嘗試將對應所產生的 XML 輸出執行個體訊息轉換為目的結構描述所指定的原生格式時，發生指出的序列化錯誤。</span><span class="sxs-lookup"><span data-stu-id="663d4-106">The indicated serialization error was encountered when attempting to convert the XML output instance message produced by the map into the native format specified by the destination schema.</span></span>  
  
 <span data-ttu-id="663d4-107">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="663d4-107">**User Action**</span></span>  
  
 <span data-ttu-id="663d4-108">根據指出的序列化錯誤，適當更正在對應中指定的轉換，或更正目的結構描述，或兩者。</span><span class="sxs-lookup"><span data-stu-id="663d4-108">Based on the indicated serialization error, make the appropriate corrections to either the transformations specified in the map, or to the destination schema, or to both.</span></span> <span data-ttu-id="663d4-109">可能會很有幫助，BizTalk 編輯器中開啟目的結構描述，並使用**驗證結構描述**，**驗證執行個體**，和**產生執行個體**可用的命令時以滑鼠右鍵按一下方案總管 中的結構描述。</span><span class="sxs-lookup"><span data-stu-id="663d4-109">It may be helpful to open the destination schema in BizTalk Editor and use the **Validate Schema**, **Validate Instance**, and **Generate Instance** commands available when you right-click a schema in Solution Explorer.</span></span>