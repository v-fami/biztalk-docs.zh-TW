---
title: "欄位位置計算 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e315f09-f2c9-49cc-8d2f-0f4f2d48fd45
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 55c58f532ea64300518667d677d2248f5c1c2b6b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="field-position-calculation"></a><span data-ttu-id="0a9a2-102">欄位位置計算</span><span class="sxs-lookup"><span data-stu-id="0a9a2-102">Field Position Calculation</span></span>

## <a name="overview"></a><span data-ttu-id="0a9a2-103">概觀</span><span class="sxs-lookup"><span data-stu-id="0a9a2-103">Overview</span></span>
<span data-ttu-id="0a9a2-104">當您使用**Positional Length**和**Positional Offset**屬性**欄位項目**和**欄位屬性**節點中的您結構描述以定義在一般檔案訊息中，序數記錄的版面配置**開始位置**和**長度**的資料行**一般檔案** 索引標籤BizTalk 編輯器 中顯示的導出的起始位置和長度，分別相關欄位及記錄。</span><span class="sxs-lookup"><span data-stu-id="0a9a2-104">When you use the **Positional Length** and **Positional Offset** properties of the **Field Element** and **Field Attribute** nodes in your schema to define the layout of the positional records in your flat file message, the **Start Position** and **Length** columns of the **Flat File** tab in BizTalk Editor show the calculated starting positions and lengths, respectively, of the relevant fields and records.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0a9a2-105">**一般檔案** 索引標籤會顯示為替代索引標籤式檢視與 XSD 檢視在 BizTalk 編輯器 中，當您完成設定一般檔案延伸模組使用**Schema Editor Extensions**屬性**結構描述**節點。</span><span class="sxs-lookup"><span data-stu-id="0a9a2-105">The **Flat File** tab appear as an alternate tabbed view with the XSD view in BizTalk Editor when you have configured the flat file extension using the **Schema Editor Extensions** property of the **Schema** node.</span></span> <span data-ttu-id="0a9a2-106">這個屬性的詳細[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="0a9a2-106">More details on this property [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
 <span data-ttu-id="0a9a2-107">一般而言，特定欄位的開始位置*N*是前一個欄位中，開始位置，加上前一個欄位中，加上您指定的欄位 （位置） 位移的長度*N*.</span><span class="sxs-lookup"><span data-stu-id="0a9a2-107">In general, the starting position of a particular field *N* is the starting position of the previous field, plus the length of the previous field, plus the (positional) offset you have specified for field *N*.</span></span>  
  
 <span data-ttu-id="0a9a2-108">在 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的所有欄位位置計算會即時自動執行，完全不需要執行命令 (在舊版 BizTalk Server 中則需要)。</span><span class="sxs-lookup"><span data-stu-id="0a9a2-108">All field position calculation in Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is performed automatically, on-the-fly, without any need to execute a command (as was required in previous versions of BizTalk Server).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a9a2-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a9a2-109">See Also</span></span>  
-  [<span data-ttu-id="0a9a2-110">位置記錄的考量</span><span class="sxs-lookup"><span data-stu-id="0a9a2-110">Positional Record Considerations</span></span>](../core/positional-record-considerations.md)   
-  <span data-ttu-id="0a9a2-111">**Positional Length （一般檔案結構描述中的節點屬性）**和**Positional Offset （一般檔案結構描述中的節點屬性）**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="0a9a2-111">**Positional Length (Node Property of Flat File Schemas)** and **Positional Offset (Node Property of Flat File Schemas)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>