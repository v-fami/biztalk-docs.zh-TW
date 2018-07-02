---
title: 資料表值的通用結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 2.X schemas, common schemas
- 2.X schemas, table values
- common schemas
ms.assetid: 2421e150-1bae-43bd-aba3-6322c679b22b
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90c66ee201e5a73d8f632a8002a9a3627d1885f1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968063"
---
# <a name="table-values-common-schemas"></a><span data-ttu-id="1f7ec-102">資料表值的通用結構描述</span><span class="sxs-lookup"><span data-stu-id="1f7ec-102">Table Values Common Schemas</span></span>
<span data-ttu-id="1f7ec-103">Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 會產生**tablevalues_*\<版本\>*.xsd**檔案的每個 HL7 版本，並找出根目錄的檔案HL7 版本特定資料夾中。</span><span class="sxs-lookup"><span data-stu-id="1f7ec-103">Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) generates the **tablevalues_*\<version\>*.xsd** file for each HL7 version, and locates the file at the root of the HL7 version-specific folder.</span></span> <span data-ttu-id="1f7ec-104">資料類型通用的結構描述檔案會參考資料表值 common 結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="1f7ec-104">The data type common schema file references the table values common schema file.</span></span>  
  
 <span data-ttu-id="1f7ec-105">這些資料表中的值是列舉型別的形式。</span><span class="sxs-lookup"><span data-stu-id="1f7ec-105">Values in these tables are in the form of enumerations.</span></span> <span data-ttu-id="1f7ec-106">每個列舉會定義可接受之訊息結構描述的一或多個欄位內的值。</span><span class="sxs-lookup"><span data-stu-id="1f7ec-106">Each enumeration defines the values that are acceptable within one or more fields of the message schemas.</span></span> <span data-ttu-id="1f7ec-107">您可以查看哪些資料表適用於訊息結構描述的節點開啟結構描述在 「 BizTalk 編輯器 」 中，按一下節點，並查看**基底資料型別**屬性 窗格中的屬性。</span><span class="sxs-lookup"><span data-stu-id="1f7ec-107">You can see which table applies to a node of a message schema by opening the schema in BizTalk Editor, clicking a node, and looking at the **Base Data Type** property in the Properties pane.</span></span>  
  
 <span data-ttu-id="1f7ec-108">您無法查看有哪些可接受的值，這個節點，不過，在訊息結構描述節點的 [屬性] 窗格中檢視的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="1f7ec-108">You will not be able to see what the acceptable values for this node are, however, by viewing the enumeration in the Properties pane for the message-schema node.</span></span> <span data-ttu-id="1f7ec-109">這是因為資料表值 common 結構描述檔案定義列舉。</span><span class="sxs-lookup"><span data-stu-id="1f7ec-109">This is because the table values common schema file defines the enumeration.</span></span> <span data-ttu-id="1f7ec-110">若要檢視的列舉型別，請按一下**tablevalues_*\<版本\>*.xsd**樹狀結構描述中的 在 「 BizTalk 編輯器 」 中，然後按一下省略符號 (**...**) 列舉型別中的資料列 屬性 窗格上的按鈕。</span><span class="sxs-lookup"><span data-stu-id="1f7ec-110">To view the enumerations, click **tablevalues_*\<version\>*.xsd** in the Schema tree in BizTalk Editor, and then click the ellipsis (**...**) button on the Enumeration row in the Properties pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f7ec-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f7ec-111">See Also</span></span>  
 <span data-ttu-id="1f7ec-112">[HL7 2.X 通用結構描述檔案](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-common-schema-files.md) </span><span class="sxs-lookup"><span data-stu-id="1f7ec-112">[HL7 2.X Common Schema Files](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-common-schema-files.md) </span></span>  
 <span data-ttu-id="1f7ec-113">[資料類型的通用結構描述](../../adapters-and-accelerators/accelerator-hl7/data-types-common-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="1f7ec-113">[Data Types Common Schemas](../../adapters-and-accelerators/accelerator-hl7/data-types-common-schemas.md) </span></span>  
 [<span data-ttu-id="1f7ec-114">區段的通用結構描述</span><span class="sxs-lookup"><span data-stu-id="1f7ec-114">Segments Common Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/segments-common-schemas.md)