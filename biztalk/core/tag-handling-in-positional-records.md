---
title: "處理標記位置記錄中 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c85d695-6dc9-4200-a453-dc576832adca
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 804647b3cf43b9b6747b2e5f50e05e38313b03d9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="tag-handling-in-positional-records"></a>位置記錄中處理標記

## <a name="overview"></a>概觀
位置記錄可包含熟知的字元順序 (稱為標記)，可用來區別記錄中的不同類型。 這可讓一般檔案解譯器適當地識別適當**記錄**包含正確剖析一般檔案記錄所需的資訊的結構描述中節點。  
  
 您可以使用**[標記識別項**和**標記位移**一起指定標記和其位置在位置記錄中的屬性。 請注意，這可以讓標記取決於您設定的任何位置出現在位置記錄， **Positional Length**和**Positional Offset**內各個欄位的屬性記錄中，標記可解譯為與其中一個相關聯的資料的一部分，或多個這些欄位。  
  
 **Positional Offset**屬性也可讓您將標記分開從記錄中的資料。 例如，如果標記就會發生在記錄開頭且四個字元的長度，您可以設定的值**Positional Offset**到四個，進而有效地略過記錄中的第一個欄位的屬性位置記錄標記時記錄的對等的 XML 格式轉譯的第一個欄位的值。  

這些屬性的詳細[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。 
  
## <a name="see-also"></a>另請參閱  
 [位置記錄的考量](../core/positional-record-considerations.md)   
