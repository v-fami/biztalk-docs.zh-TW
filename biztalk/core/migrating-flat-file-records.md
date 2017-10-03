---
title: "移轉一般檔案記錄 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75cd5fbc-66c1-4c8b-b81a-1d028e9647b4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 28daa8426dff3d9cbe9330430e4ba3de64410e5b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="migrating-flat-file-records"></a>移轉一般檔案記錄
Microsoft [!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)] 和 Microsoft [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)] 在剖析和序列化期間，一般檔案記錄中僅支援單一字元的分隔符號。 這項限制可經由處理分隔符號的更大彈性。 [!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)]和[!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)]也支援記錄、 欄位和子欄位上設定不同的分隔符號。 相反地，Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 支援多字元的分隔符號，雖然它僅支援一種分隔符號類型—子分隔符號。 分隔符號處理的改良功能可能會影響 [!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)] 處理 [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)] 與 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 一般檔案記錄的方式。  
  
 三個結構描述註解會控制分隔符號的處理中[!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)]和[!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)]，兩個供剖析 (**skip_CR**， **skip_LF**)，一種與序列化 (**append_newline**). [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]解譯，如下所示在移轉記錄時這些註解：  
  
-   如果**skip_CR**註釋的值為**true**和目前的分隔符號不是歸位字元 (0x0D)，[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]將歸位字元新增到目前的分隔符號。 例如，若目前的分隔符號是縱線符號 (0x7C)，則產生的分隔符號是縱線符號，後面接著歸位字元 (0x7C 0x0D)。 如果目前的分隔符號是歸位字元，則維持單一的歸位的值為何**skip_CR**。  
  
-   如果**skip_LF**註釋的值為**true**，[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]將換行字元 （0x0a） 新增到目前的分隔符號。 請注意，在上述情況中，目前的分隔符號是縱線符號 (0x7C)，三個字元會產生 (0x7C 0x0D 0x0A) 如果兩個**skip_CR**和**skip_LF**是**true**.  
  
-   [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]會忽略的設定**append_newline**註解。  
  
 雖然這些註解的解譯可確保大部分的情況順利移轉，但是在某些情況下，會發生移轉失敗。 例如，如果**skip_CR**和**skip_LF**都**true**和目前的分隔符號是縱線符號 (0x7C)，[!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)]和[!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)]接受所有的下列為單一記錄集之中的有效分隔符號： 0x7C 0x0D 0x0A、 0x7C 0x0D、 0x7c 0x0a 以及 0x7C。 使用這類分隔符號集的記錄將無法移轉，且在 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 中需要自訂剖析器程式碼。  
  
 雖然 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 只有一種分隔符號類型，不過，它可解譯舊版註解，便於移轉記錄。 如果[!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)]或[!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)]結構描述具有值**def_record_delimdef_field_delim**， **def_subfield_delim**，而這些中**delimiter_type**為**inherit_record**，依此類推，[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]擷取對應的值，並將它儲存在本機。  
  
 此外，[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 會為無子系的已標記位置記錄新增欄位。  
  
## <a name="see-also"></a>另請參閱  
 [結構描述的產生和驗證的已知的問題](../core/known-issues-with-schema-generation-and-validation.md)