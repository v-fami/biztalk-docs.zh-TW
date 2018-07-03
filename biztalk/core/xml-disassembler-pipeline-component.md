---
title: XML 解譯器管線元件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XML Disassembler [pipeline component], about XML Disassembler
- pipeline components, XML Disassembler
- XML Disassembler [pipeline component]
ms.assetid: ef39b695-6ae7-401d-be1e-b066048c34e9
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6bdd26a8fe5f90b1fd12937d19483e25f1a1e19f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011287"
---
# <a name="xml-disassembler-pipeline-component"></a>XML 解譯器管線元件
XML 解譯器管線元件將 XML 剖析與解譯結合成一個元件。 它的主要功能為：  
  
- 移除信封。  
  
- 解譯交換。  
  
- 將內容屬性從交換和個別文件層級升級至訊息內容。  
  
  在接收信封之後，XML 解譯器元件中會發生下列動作：  
  
1. 解譯器藉由使用信封結構描述在設計階段靜態地與元件相關聯或在執行階段動態地從訊息類型決定信封結構描述，以剖析信封。 結構描述可在剖析信封期間用以驗證信封的結構。 若未定義信封結構，則會藉由使用根節點的命名空間與基底名稱查詢結構描述遞迴找尋。  
  
2. 解譯器元件會剖析信封中的每個文件。 對於每一個文件，會以它自己的內容建立 BizTalk 訊息物件，所有屬性都在此從信封與它本身複製的文件升級。 藉由使用預先定義並已編碼成與信封和訊息關聯的 XSD 結構描述中的註解之 XPath，此元件可從信封與訊息執行個體中提取內容屬性。 信封結構描述與個別文件結構描述均與管線設計師中的解譯器元件相關聯。  
  
   XML 解譯器只處理訊息內文部分中的資料。 因此，僅升級內文部分中的屬性。 在發生屬性升級時，與可升級屬性相關聯的欄位之日期時間值將轉換成 UTC。 非內文部分則未變更地複製到輸出訊息。  
  
> [!NOTE]
>  XML 解譯器管線元件目前會在所有日期時間屬性到達訊息存放區之前，強制將它們轉換成 UTC。 BizTalk Server 在內部使用 SQL 日期時間類型，其中沒有時區的相關資訊。 若您在協調流程中產生日期時間屬性，然後嘗試將它用於與後續訊息相互關聯，則可能無法正確運作，因為 XML 解譯器管線元件會回應將它轉換成 UTC，而 Microsoft SQL Server 將無法將原始與回應時間欄位識別為相同。 同樣地，您可能會遇到不一致的地方檢視訊息事件和服務執行個體追蹤資料時。  
  
 如需設定 XML 解譯器管線元件的資訊，請參閱[如何設定 XML 解譯器管線元件](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [XML 解譯器管線元件中的 XML 資訊設定項目](../core/xml-information-set-elements-in-the-xml-disassembler-pipeline-component.md)  
  
-   [XML 解譯器管線元件中無法辨識的訊息](../core/unrecognized-messages-in-the-xml-disassembler-pipeline-component.md)  
  
-   [XML 解譯器管線元件中的文件驗證](../core/document-validation-in-the-xml-disassembler-pipeline-component.md)  
  
-   [XML 解譯器管線元件中的文件結構強化](../core/document-structure-enforcement-in-the-xml-disassembler-pipeline-component.md)  
  
-   [XML 解譯器管線元件中的字元編碼](../core/character-encoding-in-xml-disassembler-pipeline-component.md)  
  
-   [逐步解說：使用 XML 信封 (基本)](../core/walkthrough-using-xml-envelopes-basic.md)