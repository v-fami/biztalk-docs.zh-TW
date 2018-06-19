---
title: 警告-使用自訂 XSLT 與延伸模組 XML |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.warning.usingCustomXsltAndExtensionXML
ms.assetid: b86da5fb-6435-4e3b-89b6-d9d036b5152b
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90644aec738345e3a36286cc62aaa7a355e04348
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288582"
---
# <a name="warning---using-custom-xslt-and-extension-xml"></a><span data-ttu-id="e1111-102">警告-使用自訂 XSLT 與延伸模組 XML</span><span class="sxs-lookup"><span data-stu-id="e1111-102">Warning - Using Custom XSLT and Extension XML</span></span>
<span data-ttu-id="e1111-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="e1111-103">**Error Code**</span></span>  
  
 <span data-ttu-id="e1111-104">btm1035</span><span class="sxs-lookup"><span data-stu-id="e1111-104">btm1035</span></span>  
  
 <span data-ttu-id="e1111-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="e1111-105">**Explanation**</span></span>  
  
 <span data-ttu-id="e1111-106">值覆寫存在**自訂 XSLT 路徑**和**自訂延伸模組 XML**屬性會控制此對應中，完全略過任何對應所產生的輸出執行個體訊息指定來源和目的地結構描述之間。</span><span class="sxs-lookup"><span data-stu-id="e1111-106">The presence of override values for the **Custom XSLT Path** and **Custom Extension XML** properties is controlling the output instance messages produced by this map, completely ignoring any mappings specified between the source and destination schemas.</span></span> <span data-ttu-id="e1111-107">若您是刻意這樣做，則可以略過此警告。</span><span class="sxs-lookup"><span data-stu-id="e1111-107">If this is intentional, you can ignore this warning.</span></span>  
  
 <span data-ttu-id="e1111-108">這是有效的其中一個案例是使用 BizTalk 對應工具產生對應的基本 XSLT，修改此 XSLT 以手動方式以符合特殊需求，然後指定已修改的檔案做為值**自訂 XSLT 路徑**屬性，藉此覆寫基本 XSLT，在後續對應作業。</span><span class="sxs-lookup"><span data-stu-id="e1111-108">One scenario in which this is valid is to use BizTalk Mapper to generate preliminary XSLT for the mapping, modify this XSLT by hand to meet specific additional requirements, and then specify the modified file as the value of the **Custom XSLT Path** property, thereby overriding the preliminary XSLT during subsequent mapping operations.</span></span>  
  
 <span data-ttu-id="e1111-109">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="e1111-109">**User Action**</span></span>  
  
 <span data-ttu-id="e1111-110">如果您不想要覆寫此對應所指定的對應，會移除覆寫值**自訂 XSLT 路徑**屬性和**自訂延伸模組 XML**適當的屬性。</span><span class="sxs-lookup"><span data-stu-id="e1111-110">If you do not intend to override the mapping specified within this map, remove the override values for the **Custom XSLT Path** property and the **Custom Extension XML** property, as appropriate.</span></span>