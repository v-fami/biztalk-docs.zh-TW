---
title: "使用動態資料驗證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dynamic data validation
- validating, dynamic data
ms.assetid: 8dac7f74-92a7-447c-97bf-b1f3ce39b614
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c08393b8e6d4b2563d6fb7ccdf49559943538ce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-dynamic-data-validation"></a>使用動態資料驗證
針對動態的資料，包括驗證訊息格式和訊息內容的訊息內容驗證時動態的資料驗證很重要的一部分。 文件結構描述，其中[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] XSD 檔案中實作、 定義及驗證的訊息格式。 商務規則會定義訊息內容的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]透過商務規則引擎原則驗證。 內容驗證可以包含確認訊息執行個體中的資料符合相對頻率可能會變更的資料。 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]實作這個驗證類型以動態方式，讓您可以更新此資料在生產環境中，而不必重新編譯程式碼，或關閉服務。  
  
## <a name="validate-and-expose-data"></a>驗證和公開資料  
 在執行動態資料驗證 (DDV) 有兩個步驟：  
  
-   公開此資料。  
  
-   適用於使用該資料的驗證規則。  
  
 DDV 提供下列用於儲存、 公開，和快取動態資料支援：  
  
-   訊息類別的商務規則引擎會執行驗證。  
  
-   商務規則引擎會公開資料庫資料表資料行詞彙的資料。 商務規則引擎會實作從管線或協調流程執行的規則集來驗證訊息對此動態資料。  
  
-   現有的 SQL 介面，例如 SQL Enterprise Manager 和 Query Analyzer 中，會公開在設計階段是被動的動態資料。  
  
-   商務規則引擎資料庫資料表資料行的詞彙定義會在執行階段公開動態資料。  
  
-   商務規則引擎會在執行階段公開訊息執行個體資料。  
  
-   商務規則引擎的 XML 文件的詞彙定義會在設計階段顯示訊息執行個體資料。  
  
-   您可以撰寫規則在設計階段在商務規則編輯器 」 使用者介面或直接在 商務規則語言 」 (BRL) XML 文字編輯器中。  
  
 如需商務規則和商務規則引擎的詳細資訊，請參閱 「 開發與商務規則 」 中[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]幫助。  
  
## <a name="extending-ddv"></a>擴充 DDV  
 如果您變更 HL7 欄位交互驗證或資料類型驗證，您必須注意兩件事：  
  
-   如果您修改現有的規則，您不需要重新部署。  
  
-   如果您建立或刪除的管線元件會影響新規則，然後您必須重新編譯。  
  
## <a name="see-also"></a>另請參閱  
 [程式設計手冊](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md)   
 [訊息擴充教學課程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)