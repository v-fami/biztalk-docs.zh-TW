---
title: "巢狀位置和分隔記錄 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1688f04-d3c7-492c-82f7-a734bec0e409
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ccc3d994a3561f26df1bdffa7b547b1f647936a6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="nested-positional-and-delimited-records"></a>巢狀位置和分隔記錄
在 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 支援的一般檔案格式中，允許某些位置和分隔記錄的組合，但其他組合則不允許。 下列組合是允許的：  
  
-   在一般檔案中，會使用分隔符號決定所有記錄及其附屬記錄彼此之間的界限，其中 (有可能不同) 會使用分隔符號分隔這些記錄中的欄位。  
  
-   在一般檔案中，所有記錄、其附屬記錄以及其欄位是根據預先定義的記錄與欄位長度指示它們在檔案中的位置，來決定彼此之間的界限。  
  
-   在一般檔案中，會使用分隔符號決定檔案中最外層的記錄組之間的界限，而且還會使用混合的分隔和位置附屬記錄。 分隔或位置附屬記錄中的欄位之間的界限，分別是以分隔符號或是固定欄位長度來決定。 位置 (附屬) 記錄的附屬記錄必須也是位置記錄；換句話說，一旦檔案的某部分從分隔記錄切換到位置記錄，則檔案的整個附屬部分必須是位置記錄。  
  
 由於剖析的模稜兩可會產生位置記錄，所以不論它們在何處發生，都會禁止包含分隔的附屬記錄。  
  
## <a name="see-also"></a>另請參閱  
 [考量當建立一般檔案訊息結構描述](../core/considerations-when-creating-flat-file-message-schemas.md)