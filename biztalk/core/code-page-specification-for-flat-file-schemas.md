---
title: "程式碼頁規格，如一般檔案結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 825e75f1-893c-4c61-b566-f893d732a907
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64d5cfbc960346e702ed0d4a39ca74bbc4b3634c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="code-page-specification-for-flat-file-schemas"></a>一般檔案結構描述的字碼頁規格

## <a name="overview"></a>概觀
中的值**字碼頁**屬性用來建立的反組譯碼和組件的一般檔案文件期間所使用的編碼物件。 這個編碼物件允許一般檔案剖析器將輸入一般檔案文件的原生編碼主轉換為 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在內部使用的正規化 UTF-8 編碼。 這個編碼物件也允許一般檔案序列化程式將內部 UTF-8 編碼轉換回一般檔案文件的原生編碼。  
  
 設定**字碼頁**屬性扮演重要的是，但不是唯一，角色中決定一般檔案商務文件所使用的字元編碼配置。 您必須考慮由一般檔案解譯器解譯輸入一般檔案訊息的方式，以及一般檔案組合器將字元編碼為轉譯至一般檔案格式之輸出訊息的方式。  

## <a name="character-encoding"></a>字元編碼  
 在決定如何處理指定執行個體訊息之字元編碼的方式時，有多個因素扮演重要的角色，如下所示：  
  
-   當解譯一般檔案執行個體訊息時，會使用下列演算法來決定並保留編碼資訊：  
  
    1.  如果**Charset**在訊息內文部分是設定，則會使用該值。  
  
    2.  否則，如果信封 （或文件） 結構描述指定使用程式碼頁面**字碼頁**使用屬性，其值。  
  
    3.  或者，若位元順序標記存在，則會使用它的值。  
  
    4.  或者，使用 UTF-8。  
  
-   當組合一般檔案執行個體訊息時，會使用下列演算法來決定供解碼使用的字元集：  
  
-   如果**XMLNorm.TargetCharset**訊息內容屬性設定，則會使用該值。  
  
-   否則，如果**[TargetCharset**組譯工具 （設計階段） 屬性設定，則會使用該值。  
  
-   否則，如果信封 （或文件） 結構描述指定使用程式碼頁面**字碼頁**使用屬性，其值。  
  
    1.  否則，如果**SourceCharset**訊息內容屬性設定，則會使用該值。  
  
    2.  或者，使用 UTF-8。  
  
## <a name="see-also"></a>另請參閱  
 **考量當建立一般檔案訊息結構描述**和**字碼頁 （一般檔案結構描述中的節點屬性）**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]