---
title: 欄位位置計算 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7e315f09-f2c9-49cc-8d2f-0f4f2d48fd45
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fb167c0bf704aee869e81798116377608fde0c2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983023"
---
# <a name="field-position-calculation"></a><span data-ttu-id="22510-102">欄位位置計算</span><span class="sxs-lookup"><span data-stu-id="22510-102">Field Position Calculation</span></span>

## <a name="overview"></a><span data-ttu-id="22510-103">概觀</span><span class="sxs-lookup"><span data-stu-id="22510-103">Overview</span></span>
<span data-ttu-id="22510-104">當您使用**Positional Length**並**Positional Offset**的屬性**欄位項目**並**欄位屬性**中的節點您結構描述，以在一般檔案訊息中，定義序數記錄的版面配置**開始的位置**並**長度**的資料行**一般檔案**索引標籤BizTalk 編輯器 中的導出的起始位置和長度，分別顯示，相關的欄位和記錄。</span><span class="sxs-lookup"><span data-stu-id="22510-104">When you use the **Positional Length** and **Positional Offset** properties of the **Field Element** and **Field Attribute** nodes in your schema to define the layout of the positional records in your flat file message, the **Start Position** and **Length** columns of the **Flat File** tab in BizTalk Editor show the calculated starting positions and lengths, respectively, of the relevant fields and records.</span></span>  

> [!NOTE]
>  <span data-ttu-id="22510-105">**一般檔案**索引標籤會顯示為替代索引標籤式的檢視與 XSD 檢視在 [BizTalk 編輯器] 中，當您設定一般檔案延伸模組使用**Schema Editor Extensions**屬性**結構描述**節點。</span><span class="sxs-lookup"><span data-stu-id="22510-105">The **Flat File** tab appear as an alternate tabbed view with the XSD view in BizTalk Editor when you have configured the flat file extension using the **Schema Editor Extensions** property of the **Schema** node.</span></span> <span data-ttu-id="22510-106">這個屬性的更多有關[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="22510-106">More details on this property [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>

 <span data-ttu-id="22510-107">一般而言，特定欄位的開始位置*N*是上一個 欄位中，開始位置加上前一個欄位，再加上 （位置） 欄位指定的位移長度*N*.</span><span class="sxs-lookup"><span data-stu-id="22510-107">In general, the starting position of a particular field *N* is the starting position of the previous field, plus the length of the previous field, plus the (positional) offset you have specified for field *N*.</span></span>  

 <span data-ttu-id="22510-108">在 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的所有欄位位置計算會即時自動執行，完全不需要執行命令 (在舊版 BizTalk Server 中則需要)。</span><span class="sxs-lookup"><span data-stu-id="22510-108">All field position calculation in Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is performed automatically, on-the-fly, without any need to execute a command (as was required in previous versions of BizTalk Server).</span></span>  

## <a name="see-also"></a><span data-ttu-id="22510-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22510-109">See Also</span></span>  
- [<span data-ttu-id="22510-110">位置記錄考量</span><span class="sxs-lookup"><span data-stu-id="22510-110">Positional Record Considerations</span></span>](../core/positional-record-considerations.md)   
- <span data-ttu-id="22510-111">**Positional Length （一般檔案結構描述中的節點屬性）** 和**Positional Offset （一般檔案結構描述中的節點屬性）** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="22510-111">**Positional Length (Node Property of Flat File Schemas)** and **Positional Offset (Node Property of Flat File Schemas)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
