---
title: "記錄和欄位的順序 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Mapper, sorting
- XSLT, sorting
ms.assetid: 7fa9b5cd-73bc-496f-a081-4a45da3afe42
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5826d46fef73400a5d54e2d1154a1647af85294e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="order-of-records-and-fields"></a><span data-ttu-id="4bcad-102">記錄和欄位的順序</span><span class="sxs-lookup"><span data-stu-id="4bcad-102">Order of Records and Fields</span></span>
<span data-ttu-id="4bcad-103">BizTalk 對應工具所使用的「可延伸樣式表語言轉換」(XSLT) 並不保證輸出項目和屬性的輸出順序。</span><span class="sxs-lookup"><span data-stu-id="4bcad-103">Extensible Stylesheet Language Transformations (XSLT), as used by BizTalk Mapper, do not guarantee the output order of output elements and attributes.</span></span> <span data-ttu-id="4bcad-104">這是因為 BizTalk 對應工具透過檢查目的結構描述之結構，然後經由格線頁將項目傳回，從來源結構描述的結構擷取值以產生 XSLT。</span><span class="sxs-lookup"><span data-stu-id="4bcad-104">This is because BizTalk Mapper generates XSLT by examining the destination schema structure, and then propagating elements back through the grid pages to extract values from the source schema structure.</span></span> <span data-ttu-id="4bcad-105">例如，若您要建立一個輸出檔案，將 BillTo Address 記錄列在 ShipTo Address 記錄之前，您必須確保在目的結構描述中，BillTo Address 位在 ShipTo Address 記錄之前。</span><span class="sxs-lookup"><span data-stu-id="4bcad-105">For example, if you want to create an output file that has the BillTo Address record listed before the ShipTo Address record, you must ensure that the BillTo Address precedes the ShipTo Address record in the destination schema.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4bcad-106">項目和屬性出現在輸出執行個體訊息中的順序相依於記錄和欄位在對應的目的結構描述中的順序。</span><span class="sxs-lookup"><span data-stu-id="4bcad-106">The order in which elements and attributes appear in an output instance message depends on the order of the records and fields of the corresponding destination schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bcad-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4bcad-107">See Also</span></span>  
 <span data-ttu-id="4bcad-108">[對應](../core/maps.md) </span><span class="sxs-lookup"><span data-stu-id="4bcad-108">[Maps](../core/maps.md) </span></span>  
 [<span data-ttu-id="4bcad-109">使用 BizTalk 對應工具建立對應</span><span class="sxs-lookup"><span data-stu-id="4bcad-109">Creating Maps Using BizTalk Mapper</span></span>](../core/creating-maps-using-biztalk-mapper.md)