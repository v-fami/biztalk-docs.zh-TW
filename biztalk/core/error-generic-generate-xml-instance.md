---
title: 錯誤-一般產生 XML 執行個體 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.genericGenerateXmlInstance
ms.assetid: f2b42589-fd44-45d6-86e6-c2502820beee
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c859cfc775e74ab817e66dbb8b896f51458f0301
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241230"
---
# <a name="error---generic-generate-xml-instance"></a><span data-ttu-id="67068-102">錯誤-一般產生 XML 執行個體</span><span class="sxs-lookup"><span data-stu-id="67068-102">Error - Generic Generate XML Instance</span></span>
<span data-ttu-id="67068-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="67068-103">**Error Code**</span></span>  
  
 <span data-ttu-id="67068-104">btm1038</span><span class="sxs-lookup"><span data-stu-id="67068-104">btm1038</span></span>  
  
 <span data-ttu-id="67068-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="67068-105">**Explanation**</span></span>  
  
 <span data-ttu-id="67068-106">BizTalk 對應工具無法針對對應的來源結構描述產生 XML 執行個體訊息檔案。</span><span class="sxs-lookup"><span data-stu-id="67068-106">BizTalk Mapper was not able to generate an XML instance message file for the source schema of the map.</span></span> <span data-ttu-id="67068-107">這可能表示與此對應關聯的來源結構描述有問題。</span><span class="sxs-lookup"><span data-stu-id="67068-107">This suggests that there is a problem with the source schema associated with the map.</span></span>  
  
 <span data-ttu-id="67068-108">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="67068-108">**User Action**</span></span>  
  
 <span data-ttu-id="67068-109">使用 BizTalk 編輯器來開啟與對應關聯的來源結構描述，然後開始檢查來源結構描述是否有問題。</span><span class="sxs-lookup"><span data-stu-id="67068-109">Use BizTalk Editor to open the source schema associated with the map and begin investigating whether there are problems with the source schema.</span></span> <span data-ttu-id="67068-110">此外，**驗證結構描述**和**產生執行個體**可用的命令，當您以滑鼠右鍵按一下 [方案總管] 中的結構描述可用於尋找結構描述錯誤。</span><span class="sxs-lookup"><span data-stu-id="67068-110">Also, the **Validate Schema** and **Generate Instance** commands, available when you right-click a schema in Solution Explorer, are useful for finding schema errors.</span></span>