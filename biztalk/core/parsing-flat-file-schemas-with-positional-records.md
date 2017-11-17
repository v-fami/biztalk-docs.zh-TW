---
title: "剖析具有位置記錄的一般檔案結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], flat file documents
- pipeline components [custom], parsing
ms.assetid: 1ceb8c06-ac21-490e-b3d5-54e5035e5f6a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5c4a6a1d5d6c263c0f794d1b703eff256f15c43b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="parsing-flat-file-schemas-with-positional-records"></a><span data-ttu-id="75342-102">剖析具有位置記錄的一般檔案結構描述</span><span class="sxs-lookup"><span data-stu-id="75342-102">Parsing Flat File Schemas with Positional Records</span></span>
<span data-ttu-id="75342-103">當剖析具有大小不一之位置記錄的一般檔案結構描述時，您必須將標記包含在每個結構描述記錄或結尾中，以指示每個位置記錄的大小。</span><span class="sxs-lookup"><span data-stu-id="75342-103">When parsing a flat file schema with positional records of unequal size, you must include a tag within each schema record or the trailer to indicate the size of each positional record.</span></span> <span data-ttu-id="75342-104">否則，剖析引擎會傳回最長記錄的大小。</span><span class="sxs-lookup"><span data-stu-id="75342-104">Otherwise, the parsing engine returns the longest record size.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75342-105">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75342-105">See Also</span></span>  
 [<span data-ttu-id="75342-106">使用一般檔案剖析引擎</span><span class="sxs-lookup"><span data-stu-id="75342-106">Using the Flat File Parsing Engine</span></span>](../core/using-the-flat-file-parsing-engine.md)