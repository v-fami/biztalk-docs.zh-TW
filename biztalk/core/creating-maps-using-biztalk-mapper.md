---
title: 使用 BizTalk 對應工具建立對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, maps
- maps, creating
- orchestrations, maps
- translations [maps]
- maps, about maps
- transformations [maps]
- maps
ms.assetid: 265e61d8-8cff-44c9-a717-8e895cb4b9bf
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c12da6732729052119bfcc7841424db6d0dcaff9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238334"
---
# <a name="creating-maps-using-biztalk-mapper"></a>使用 BizTalk 對應工具建立對應
「BizTalk 對應工具」是在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 環境中執行的工具。 您可以使用 BizTalk 對應工具建立和編輯對應，以轉譯或轉換 XML 訊息。 對應可以用於協調流程 (如下圖所示)，也可以用於處理接收埠所接收的訊息，接著加以轉換然後透過傳送埠傳送出去。  
  
 ![當對應的商務處理圖表。] (../core/media/ebiz-dev-busprcsg.gif "ebiz_dev_busprcsg")  
商務處理中的對應  
  
 對應可讓您轉譯和轉換訊息。 轉譯是將訊息從一種格式轉換為另一種格式的程序，例如將一般檔案轉換為 XML 檔案。 轉換則是擷取某個訊息中的資訊，並將該資訊插入另一個訊息的程序。 例如，您可以擷取採購單中的送貨和帳單地址，並將這些地址插入發票文件。  
  
 「BizTalk 對應工具」使用專屬的圖示和連結圖形系統，代表從輸入執行個體訊息到輸出執行個體訊息的轉譯和轉換關係。 對應工具使用與 BizTalk 編輯器相同的結構描述圖形表示法。 「BizTalk 對應工具」會將其對應儲存為「可延伸樣式表語言轉換」(XSLT) 樣式表。  
  
> [!NOTE]
>  BizTalk 對應工具支援 XSLT 1.0。 在 [BizTalk 對應工具] 中不支援使用 XSLT 2.0。  
  
 如需建立結構描述資訊，請參閱[建立結構描述使用 BizTalk 編輯器](../core/creating-schemas-using-biztalk-editor.md)。 如需使用協調流程中的對應資訊，請參閱[協調流程使用協調流程設計師建立](../core/creating-orchestrations-using-orchestration-designer.md)。  
  
> [!NOTE]
>  對應的效能視對應的複雜度 (運算質的數目和類型)、輸入和輸出結構描述的大小、輸入訊息的大小以及您的硬體而異。  
  
 使用 BizTalk 對應工具鍵盤快速鍵的相關資訊，請參閱[BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [規劃建立對應](../core/planning-to-create-maps.md)  
  
-   [關於對應](../core/about-maps.md)  
  
-   [使用 BizTalk 對應工具](../core/using-biztalk-mapper.md)  
  
-   [建立對應](../core/creating-maps.md)  
  
-   [編譯和測試對應](../core/compiling-and-testing-maps.md)  
  
-   [地圖疑難排解](../core/troubleshooting-maps.md)