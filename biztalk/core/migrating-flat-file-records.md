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
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ddd43c231077f4e23efca374edbda5bf152f1415
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="migrate-flat-file-records"></a>移轉一般檔案記錄

## <a name="overview"></a>概觀
Microsoft BizTalk Server 可支援多字元的分隔符號，雖然它支援只有一種分隔符號類型 — 子分隔符號。 
  
 三個結構描述註解會控制分隔符號的 BizTalk Server 中的處理： 兩個供剖析 (**skip_CR**， **skip_LF**)，一種與序列化 (**append_newline**)。 BizTalk Server 會解譯這些註解，如下所示在移轉記錄時：  
  
-   如果**skip_CR**註釋的值為**true**和目前的分隔符號不是歸位字元 (0x0D)，BizTalk Server 會將歸位字元新增到目前的分隔符號。 例如，若目前的分隔符號是縱線符號 (0x7C)，則產生的分隔符號是縱線符號，後面接著歸位字元 (0x7C 0x0D)。 如果目前的分隔符號是歸位字元，它會保持為單一歸位字元的值為何 **skip_CR**。  
  
-   如果**skip_LF**註釋的值為**true**，BizTalk Server 會將換行字元 （0x0a） 新增到目前的分隔符號。 請注意，上述情況中，目前的分隔符號是縱線符號 (0x7C)，在三個字元會產生 (0x7C 0x0D 0x0A) 如果這兩個 **skip_CR** 和 **skip_LF** 是 **true**。  
  
-   BizTalk Server 會略過的設定**append_newline**註解。  
  
 雖然這些註解的解譯可確保大部分的情況順利移轉，但是在某些情況下，會發生移轉失敗。 例如，如果**skip_CR**和**skip_LF**都**true**和目前的分隔符號是縱線符號 (0x7C)，BizTalk Server 可接受下列為有效的所有在一組的記錄中的分隔符號： 0x7C 0x0D 0x0A、 0x7C 0x0D、 0x7c 0x0a 以及 0x7C。 使用這類分隔符號集的記錄無法移轉，且需要自訂剖析器在 BizTalk Server 中的程式碼。  
  
 雖然 BizTalk Server 只一種分隔符號類型，它可解譯舊版註解，以便輕鬆地移轉記錄。 如果 BizTalk Server 結構描述具有值**def_record_delimdef_field_delim**， **def_subfield_delim**，在中參考這些**delimiter_type**為**inherit_record**，依此類推，BizTalk Server 擷取對應的值，並將它儲存在本機。  
  
 此外，BizTalk Server 新增為子系已標記位置記錄的欄位。  
  
## <a name="see-also"></a>另請參閱  
 [產生和驗證結構描述的已知問題](../core/known-issues-with-schema-generation-and-validation.md)