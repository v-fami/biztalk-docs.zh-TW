---
title: 對應元件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- file types, maps
- BizTalk Mapper, output
- maps, file type
- maps, file contents
- BizTalk Mapper, file type
- maps, components
ms.assetid: be438d21-80a8-49d8-bd08-d85618ab23de
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b1590ad1450453602b4dd5f25b2d52a4364787af
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996767"
---
# <a name="map-components"></a><span data-ttu-id="9f789-102">對應元件</span><span class="sxs-lookup"><span data-stu-id="9f789-102">Map Components</span></span>
<span data-ttu-id="9f789-103">對應檔 (具有 .btm 副檔名) 會儲存對應的大部分元件。</span><span class="sxs-lookup"><span data-stu-id="9f789-103">Map files (having a .btm extension) store most of the components of a map.</span></span> <span data-ttu-id="9f789-104">檔案中儲存的項目包含：</span><span class="sxs-lookup"><span data-stu-id="9f789-104">Items stored in the file include:</span></span>  
  
- <span data-ttu-id="9f789-105">來源與目的結構描述的參考</span><span class="sxs-lookup"><span data-stu-id="9f789-105">References to source and destination schemas</span></span>  
  
- <span data-ttu-id="9f789-106">連結，包括連結屬性</span><span class="sxs-lookup"><span data-stu-id="9f789-106">Links, including the link properties</span></span>  
  
- <span data-ttu-id="9f789-107">運算質及其屬性，例如輸入參數</span><span class="sxs-lookup"><span data-stu-id="9f789-107">Functoids with their properties such as input parameters</span></span>  
  
- <span data-ttu-id="9f789-108">其他屬性，例如與格線和對應本身相關聯的屬性。</span><span class="sxs-lookup"><span data-stu-id="9f789-108">Other miscellaneous properties such as those associated with the grid and the map itself.</span></span>  
  
  <span data-ttu-id="9f789-109">雖然 BizTalk 對應工具可將 .btm 檔案中的對應編譯至可延伸樣式表轉換 (XSLT) 檔案中，但 XSLT 並不是檔案的一部分。</span><span class="sxs-lookup"><span data-stu-id="9f789-109">Although BizTalk Mapper compiles the map in the .btm file into an Extensible Stylesheet Transformations (XSLT) file, the XSLT is not part of the file.</span></span> <span data-ttu-id="9f789-110">只有當您在編譯專案或在驗證對應時，BizTalk 對應工具才能為對應產生 XSLT。</span><span class="sxs-lookup"><span data-stu-id="9f789-110">BizTalk Mapper produces the XSLT for the map only when you compile the project or when you validate the map.</span></span> <span data-ttu-id="9f789-111">BizTalk 對應工具會將 XSLT 封裝為專案組件的一部分。</span><span class="sxs-lookup"><span data-stu-id="9f789-111">BizTalk Mapper packages the XSLT as part of the project assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f789-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f789-112">See Also</span></span>  
 <span data-ttu-id="9f789-113">[對應](../core/maps.md) </span><span class="sxs-lookup"><span data-stu-id="9f789-113">[Maps](../core/maps.md) </span></span>  
 [<span data-ttu-id="9f789-114">使用 BizTalk 對應工具建立對應</span><span class="sxs-lookup"><span data-stu-id="9f789-114">Creating Maps Using BizTalk Mapper</span></span>](../core/creating-maps-using-biztalk-mapper.md)