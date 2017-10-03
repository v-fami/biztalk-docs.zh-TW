---
title: "RetractByType |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RetractByType function [Business Rules Engine], TypedXMLDocument
- RetractByType function [Business Rules Engine]
- RetractByType function [Business Rules Engine], .NET objects
- RetractByType function [Business Rules Engine], TypedData table
- RetractByType function [Business Rules Engine], DataConnection
- .NET objects
ms.assetid: e8867553-ee3c-46be-84cd-d5373eaf3337
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da8cd4581007ad2bd93ed66ebce4f5de6378280c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="retractbytype"></a>RetractByType
**RetractByType**函式會撤回工作記憶體中的指定類型的所有執行個體，而**Retract**函式會撤回只有特定類型的特定項目。 以下段落描述如何**RetractByType**函式如何使用不同類型的實體。  
  
## <a name="net-objects"></a>.NET 物件  
 特定的類別類型的所有物件會從工作記憶體都撤回。 您只需從.NET 類別事實窗格將拖曳類別**RetractByType**函式。  
  
## <a name="typedxmldocument"></a>TypedXmlDocument  
 會撤回所有執行個體。 這表示所有**TypedXmlDocument**具有相同**Typedxmldocument**不當所致。 您應該適當的節點從 XML 結構描述事實窗格拖曳到**RetractByType**函式。 與一致**Retract**函式中，如果您執行**RetractByType**的文件根節點上，不只將全部**TypedXmlDocuments**該與判斷提示**DocumentType**撤回，但所有的子**TypedXmlDocuments** (**XmlNode**樹狀結構階層架構中) 與那些父關聯**TypedXmlDocuments**也會被撤回。  
  
## <a name="typeddatatable-and-dataconnection"></a>TypedDataTable 和 DataConnection  
 **撤銷**和**RetractByType**是兩個相等**TypedDataTable**和**DataConnection**。 因為**DataSetName.DataTableName**是唯一的識別碼這兩種類型，只有一個執行個體中沒有引擎在任何時間點的時間。 如同**Retract**，拖曳到資料表**RetractByType**函式。  
  
## <a name="see-also"></a>另請參閱  
 [引擎控制函式](../core/engine-control-functions.md)