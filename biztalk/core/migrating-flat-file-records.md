---
title: 移轉一般檔案記錄 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 75cd5fbc-66c1-4c8b-b81a-1d028e9647b4
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f055b6a572e357a520b9679796ad0288dda19f3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994071"
---
# <a name="migrate-flat-file-records"></a>移轉一般檔案記錄

## <a name="overview"></a>概觀
Microsoft BizTalk Server 支援多字元的分隔符號，雖然它支援只有一種分隔符號類型 — 子分隔符號。 
  
 三個結構描述註解會控制處理 BizTalk Server 中的分隔符號： 剖析的兩個 (**skip_CR**， **skip_LF**)，一個供序列化 (**append_newline**)。 BizTalk Server 會解譯這些註解，如下所示在移轉記錄時：  
  
- 如果**skip_CR**註釋的值為 **，則為 true**和目前的分隔符號不是歸位字元 (0x0D)，BizTalk Server 會將歸位字元新增到目前的分隔符號。 例如，若目前的分隔符號是縱線符號 (0x7C)，則產生的分隔符號是縱線符號，後面接著歸位字元 (0x7C 0x0D)。 如果目前的分隔符號是歸位字元，就會保持為單一歸位字元的值為何**skip_CR**。  
  
- 如果**skip_LF**註釋的值為 **，則為 true**，BizTalk Server 會將換行字元 (0x0A) 到目前的分隔符號。 請注意，在上面的案例，其中目前的分隔符號是縱線符號 (0x7C)，三個字元產生 (0x7C 0x0D 0x0A) 如果兩個**skip_CR**並**skip_LF**是**true**.  
  
- BizTalk Server 會略過的設定**append_newline**註釋。  
  
  雖然這些註解的解譯可確保大部分的情況順利移轉，但是在某些情況下，會發生移轉失敗。 比方說，如果**skip_CR**並**skip_LF**兩者都是**true**和目前的分隔符號是縱線符號 (0x7C)，BizTalk Server 會接受為有效下列所有項目單一的資料錄集內的分隔符號： 0x7C 0x0D 0x0A 0x7C 0x0D、 0x7C 0x0A，以及 0x7C。 使用這類分隔符號集的記錄無法移轉，且需要自訂剖析器在 BizTalk Server 中的程式碼。  
  
  雖然 BizTalk Server 只一種分隔符號類型，它可解譯舊版註解，以便輕鬆地移轉記錄。 如果 BizTalk Server 結構描述具有值**def_record_delimdef_field_delim**， **def_subfield_delim**，而這些中**delimiter_type**作為**inherit_record**，依此類推，BizTalk Server 會擷取對應的值，並將它儲存到本機。  
  
  此外，BizTalk Server 會新增為子系的標記位置記錄的欄位。  
  
## <a name="see-also"></a>另請參閱  
 [產生和驗證結構描述的已知問題](../core/known-issues-with-schema-generation-and-validation.md)