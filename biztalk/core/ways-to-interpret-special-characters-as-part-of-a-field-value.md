---
title: "將特殊字元解譯為欄位值的一部分的方式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e19a202-4e4d-42e0-ba1e-fddc52792b21
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b96a3c7502a47541e8e58ec3df3eccf6098e3abc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="ways-to-interpret-special-characters-as-part-of-a-field-value"></a>如何將特殊字元解譯為欄位值的一部分
位置及分隔記錄中的欄位可以包含不同類型的特殊字元，例如填補、換行及逸出字元。 分隔記錄還能包含一或多個不同的分隔符號字元，用來區隔記錄中的欄位或用來區隔不同的記錄。 有時候這些字元本身就是資料的一部分，而不應解譯為上述狀況的特殊字元。  
  
 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 所使用的一般檔案結構描述支援兩種不同的技術，可將這種用法的特殊字元標幟為僅是欄位所含資料的一部分。 這兩種技術分別採用逸出字元和換行字元。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [逸出字元](../core/escape-characters.md)  
  
-   [換行字元](../core/wrap-characters.md)