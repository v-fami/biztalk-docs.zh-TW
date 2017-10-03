---
title: "使用管線設計師 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Pipeline Designer, how to
- pipelines, Pipeline Designer
ms.assetid: bdb2f5c7-f8a2-4bd6-a8d8-8b7a64f97bd0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce7a8bc7c7943ff96f0d70a802a2756f8d8c4783
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-pipeline-designer"></a>使用管線設計師
管線設計師是一套裝載於 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 的圖形化編輯器，可讓您建立新管線、檢視 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 隨附的管線範本、移動管線內的管線元件，還可以設定管線、階段以及管線元件。  
  
 管線設計師會使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 殼層的三項主要工具，作為設計經驗的一部分：  
  
-   [屬性] 視窗，可在其中檢視和修改管線物件的大部分特性。  
  
-   [工具箱]，作為設計介面的來源。  
  
-   設計介面，[工具箱] 的元件可拖放至此。  
  
 下圖顯示管線設計師的環境。  
  
 ![管線設計師編輯環境](../core/media/ebiz-prog-usepipe.gif "ebiz_prog_usepipe")  
描述管線設計師的環境。  
  
 為了增強您的開發經驗，管線設計師已和 BizTalk 專案範本進行整合。 若要建立新的 BizTalk 專案中使用專案系統之後, 您可以使用**加入新項目**命令**檔案**功能表來新增管線到您的方案。 如需 BizTalk 專案範本的詳細資訊，請參閱[使用 BizTalk 專案系統](../core/using-the-biztalk-project-system.md)。  
  
> [!NOTE]
>  在舊版 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，管線的概念封裝在訊息通道和連接埠中，而這些通道和連接埠為套用至文件的特定元件定義了設定順序。 在這個版本中，管線變的更有彈性，因為您可以自由地重新排列管線各階段的元件，也可以輕易地在管線中插入多個自訂元件。  
  
 管線設計師的設計介面可讓您繪製管線的圖形表示。 設計介面佔據了 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 視窗的主要區段，可讓您編輯屬於 BizTalk 專案的管線。 您可以按一下設計介面上方的索引標籤，在管線之間瀏覽。  
  
 每個管線都由階段組成，而每個階段都包含了一個或多個元件。 若階段中沒有元件，則浮水印文字即表示可以從 [工具箱] 插入圖形。 當插入第一個圖形到階段中時，這段初始文字就會消失。 設計介面會以垂直方式顯示管線，從頂端 (開始) 到底端 (結束)。  
  
 和其他一般的 Microsoft Windows 程式，您可以在執行數個工作，例如**開啟**和**儲存**從**檔案**功能表。  
  
## <a name="see-also"></a>另請參閱  
 [使用管線設計師建立管線](../core/creating-pipelines-with-pipeline-designer.md)   
 [建立管線使用管線設計師](../core/creating-pipelines-using-pipeline-designer.md)