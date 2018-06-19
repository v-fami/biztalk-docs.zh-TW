---
title: 使用 BizTalk 編輯器建立結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03fac91b-5b67-4baf-968c-294c525d3018
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb9e4c6496f43a9602ad56bc0e095d98f2da90d9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238934"
---
# <a name="create-schemas-using-biztalk-editor"></a>建立結構描述使用 BizTalk 編輯器

## <a name="overview"></a>概觀
BizTalk 編輯器是在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 環境中執行的工具。 您可以用它來建立、編輯和管理應用程式要使用的結構描述。 BizTalk 編輯器會使用階層式記錄與欄位的圖形系統來代表執行個體訊息的結構，並使用 XML 結構描述定義 (XSD) 語言來儲存它定義的結構描述。 不論執行個體訊息交換的格式為何，這都成立。 例如，假設您與交易夥伴交換一般檔案。 BizTalk Server 會處理這些一般檔案，它會將這些檔案轉換成 XML 格式，或是從 XML 格式轉換成一般檔案，以符合您在 BizTalk 編輯器中定義的 XSD 結構描述。  
  
 您使用 BizTalk 編輯器所建立的結構描述可用於協調的商務程序中，如下圖所示。  
  
 ![](../core/media/ebiz-dev-busprcsh.gif "ebiz_dev_busprcsh")  
  
 組合器與解譯器也會使用結構描述，將執行個體訊息從某個格式轉譯成另一個格式，例如，在一般檔案格式與 XML 之間進行轉譯。 結構描述在執行個體訊息轉換中也扮演著非常重要的角色，透過它，執行個體訊息中的資料可用以建構不同結構的執行個體訊息。 新執行個體訊息在語意上可能會一樣 (例如，不同表示法的訂單)，或是它可能是不同、但為相關類型的執行個體訊息，其需要原始執行個體訊息內容中的部分或全部資料。  
  
 將所有執行個體訊息轉譯成符合 XSD 結構描述之 XML 格式的重要理由，是為了簡化將訊息從某個結構轉換為另一個結構的程序。 一般而言，訊息結構的語法雖然不同，但其語意是一樣的。 例如，您和您的交易夥伴可能會以不同的結構來組織您們的訂單，但是它們所包含的基本資訊是相同的，可讓它們自動來回轉換。 透過先將所有的執行個體訊息轉換為對應 XSD 結構描述所決定的 XML 格式，執行個體訊息就可在 XML 與非 XML 格式之間來回轉譯，並從某個 XML 結構轉換為另一個結構。 如需有關執行個體訊息轉譯與執行個體訊息轉換之間差別的詳細資訊，請參閱[資料轉換](../core/data-transformation.md)。  
  
 在 Microsoft Visual Studio 環境中，BizTalk 編輯器的隨附工具是 BizTalk 對應工具。 在您使用 BizTalk 編輯器來建立結構描述，以定義一組相關執行個體訊息的結構與格式後，就可以使用 BizTalk 對應工具，以圖形方式定義如何將符合某個結構描述的執行個體訊息 (來源執行個體訊息與結構描述) 轉換為符合另一個結構描述的執行個體 (目的執行個體訊息與結構描述)。 這類轉換的規格是使用可延伸樣式表語言轉換 (XSLT) 來實作，並保存為稱為對應的檔案。 如需 BizTalk 對應工具 」 的概念和程序資訊，請參閱[建立對應使用 BizTalk 對應工具](../core/creating-maps-using-biztalk-mapper.md)。 如需 BizTalk 對應工具 」 屬性與運算質的參考資訊，請參閱**對應屬性參考**和**運算質參考**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
 使用 BizTalk 編輯器，您可以開啟未包含結構的空白結構描述、開啟現有 XSD 結構描述，或是從非 XSD 來源產生結構描述。 當您從非 XSD 來源產生結構描述時，BizTalk 編輯器會解譯來源的結構並產生其 XSD 表示法的結構描述。 您可以編輯出現在 BizTalk 編輯器結構描述樹狀結構檢視中的任何記錄與欄位，然後將該結構儲存為 BizTalk 結構描述。  
  
 使用鍵盤快速鍵在 「 BizTalk 編輯器 」 的相關資訊，請參閱[BizTalk 編輯器鍵盤快速鍵](../core/biztalk-editor-keyboard-shortcuts.md)。  
  
## <a name="next-steps"></a>後續的步驟
  
-   [規劃建立結構描述](../core/planning-for-schema-creation.md)  
  
-   [關於執行個體訊息](../core/about-instance-messages.md)  
  
-   [關於結構描述](../core/about-schemas.md)  
  
-   [使用 BizTalk 編輯器](../core/using-biztalk-editor.md)  
  
-   [建立結構描述](../core/creating-schemas.md)  
  
-   [使用 BizTalk 一般檔案結構描述精靈建立結構描述](../core/creating-schemas-using-biztalk-flat-file-schema-wizard.md)  
  
-   [測試結構描述](../core/testing-schemas.md)  
  
-   [延伸 BizTalk 編輯器](../core/extending-biztalk-editor.md)  
  
-   [建立結構描述時的考量](../core/considerations-when-creating-schemas.md)  
  
-   [結構描述的產生和驗證的已知的問題](../core/known-issues-with-schema-generation-and-validation.md)