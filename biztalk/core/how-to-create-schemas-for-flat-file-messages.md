---
title: 如何建立一般檔案訊息的結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 48f2747b-7f26-4fb2-a855-523e093f3813
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58583037b8fae945dea07aa8af62e969b96e073f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249406"
---
# <a name="create-schemas-for-flat-file-messages"></a>建立一般檔案訊息的結構描述

## <a name="overview"></a>概觀
建立 XML 訊息結構描述中所述之後[建立 XML 訊息的結構](../core/how-to-create-schemas-for-xml-messages.md)，使用**Schema Editor Extensions**屬性**結構描述**節點，以啟用一般檔案延伸模組。 啟用一般檔案延伸模組會在結構描述中的許多節點類型加入相當多的屬性。 這些屬性通常用來控制如何將一般檔案商務文件轉譯為對等的 XML 商務文件，以及從 XML 商務文件轉譯為對等的一般檔案商務文件，屬性值以 XML 結構描述定義 (XSD) 語言註解儲存在結構描述檔案中。 要正確地使用這些屬性需要多加練習，並全盤瞭解每個一般檔案格式分別管理哪些方面。 

針對概念和參考的一般檔案屬性的相關資訊，請參閱[考量當建立一般檔案訊息結構描述](../core/considerations-when-creating-flat-file-message-schemas.md)和**一般檔案結構描述的增補節點屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
## <a name="see-also"></a>另請參閱  
-  [管理專案中的結構描述](../core/managing-schemas-within-projects.md)
-  這些屬性的更多詳細資料[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]