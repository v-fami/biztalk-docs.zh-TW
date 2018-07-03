---
title: 來源與目的結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- destination schemas
- source schemas, maps
- XML schemas, defining
- destination schemas, about destination schemas
- schemas, destination
- destination schemas, maps
- maps, source schemas
- schemas, Root Reference property
- Root Reference property, modifying
- source schemas
- modifying, Root Reference property
- maps, Root Reference property
- source schemas, about source schemas
- schemas, maps
- maps, schema requirements
- schemas, requirements
- schemas, source schemas
- maps, destination schemas
- Root Reference property
ms.assetid: 8c805854-9fa1-4ce3-938d-a2e61ba17fa1
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bcbb3e36122af0bae4809435b8cc1d74b46ea1ba
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011367"
---
# <a name="source-and-destination-schemas"></a>來源與目的結構描述
每一個 BizTalk 對應均使用兩個結構描述：一個來源結構描述和一個目的結構描述。 來源結構描述會定義您從中取得資料的執行個體訊息之結構。 目的結構描述則會定義對應產生的執行個體訊息之結構。 例如，若要將訂單的出貨和帳單資訊對應到發票，您需要一個結構描述以定義訂單為來源結構描述，以及另一個結構描述以定義發票為目的結構描述。  
  
 用於 BizTalk 對應的結構描述必須符合以下條件：  
  
- 來源與目的結構描述必須為目前 BizTalk 專案的一部分，或者必須將結構描述的參考包含在組件中，以便可在執行階段存取結構描述。  
  
- 用於「BizTalk 對應工具」的結構描述必須以 XML 結構描述定義 (XSD) 語言為基礎。 「BizTalk 編輯器」提供簡易的方式，以建立這類結構描述。 如需使用 「 BizTalk 編輯器建立結構描述的詳細資訊，請參閱[建立結構描述使用 BizTalk 編輯器](../core/creating-schemas-using-biztalk-editor.md)。 另請參閱[建立結構描述](../core/creating-schemas.md)。  
  
  在「BizTalk 編輯器」中，您可以建立具有多個根節點的結構描述。 但是，若您在 BizTalk 對應中使用具有多個根節點的結構描述，則必須選擇要在對應中使用哪一個根節點 (與對應的子結構)。 結構描述有**根參考**識別哪一個根屬性為主要。 如果結構描述具有多個根節點並**根參考**屬性設定結構描述是第一次開啟做為來源或目的結構描述，BizTalk 對應工具會使用指定的根目錄。 如果結構描述具有多個根節點並**根參考**未設定屬性，BizTalk 對應工具會提示您選擇的根。  
  
  如果您變更**根參考**已經在對應中，BizTalk 對應工具中使用的結構描述的屬性不會不會注意到變更，且會繼續使用原先指定的根目錄。 如果您想要建置使用相同的結構描述的不同根目錄的不同對應，則最好不要設定**根參考**屬性。 若設定該屬性，則只要結構描述用於新的對應時，您都必須明確地選擇根目錄。  
  
  如果它包含在對應之後，您可以編輯結構描述，可能會中斷模式中的連結。  
  
## <a name="see-also"></a>另請參閱  
 [對應](../core/maps.md)   
 [使用 BizTalk 對應工具建立對應](../core/creating-maps-using-biztalk-mapper.md)