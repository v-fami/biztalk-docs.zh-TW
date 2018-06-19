---
title: 建立結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 20b88194-b400-4ebc-8882-d493fbf30e0f
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac019276923467fe2d95f5a0a0b4a7b53513e9c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238534"
---
# <a name="creating-schemas"></a>建立結構描述
您可以使用 BizTalk 編輯器來建立兩種類型的結構描述： 訊息結構描述與屬性結構描述。  
  
> [!NOTE]
>  訊息結構描述有數種類型，包括 XML 訊息結構描述、一般檔案訊息結構描述和信封結構描述。  
  
 訊息結構描述會定義您預期要對您的交易夥伴或應用程式傳送及接收之訊息內容的結構與條件約束。 訊息結構描述是最常見類型的結構描述，您將使用與 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可以建立的商務文件和用來包含它們，信封的 XML 訊息結構描述，並透過使用 「 一般檔案延伸模組至 「 BizTalk 編輯器，它可以建立一般檔案訊息結構描述，包括標頭、 內文和結尾結構描述。  
  
 屬性結構描述為特殊類型的結構描述。 屬性結構描述會提供欄位和 (或) 記錄資料的驗證範本，在執行個體訊息中升級為所謂的訊息內容。 屬性結構描述的用途為提供正式的強型別資料定義，以便在執行階段升級。  
  
 屬性升級提供從執行個體訊息中提取主要資訊部分 (由您定義) 的集中機制，並使處理通過 BizTalk Server 之訊息的 BizTalk Server 元件更容易存取。 升級屬性的最常用用途是比對訊息執行個體與訂閱，讓訊息可正確地傳遞以進行處理。  
  
 本節將描述在 BizTalk Server 中建立不同類型結構描述的方式，並呈現多種結構描述類型的相關主題。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [管理專案中的結構描述](../core/managing-schemas-within-projects.md)  
  
-   [管理結構描述中的節點](../core/managing-the-nodes-within-a-schema.md)  
  
-   [升級屬性](../core/promoting-properties.md)