---
title: 在 Siebel 商務元件上的作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- business components, operations on
- operations, on business components
- operations, on business components with picklist fields
ms.assetid: 5430a8bd-88eb-4851-92e3-676ca83780c9
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc634d48d4a39e610247edbab98104bc3c6da379
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223614"
---
# <a name="operations-on-business-components-in-siebel"></a>在 Siebel 商務元件上的作業
Siebel 商務元件是將一或多個資料庫資料表中的資料行成單一結構相關聯的邏輯實體。 配接器用戶端可以執行下列作業在 Siebel 商務元件上的使用配接器：  
  
-   **插入**。 配接器用戶端可以將一個或多個記錄插入商務元件。  
  
-   **查詢**。 配接器用戶端可以查詢從商務元件的一或多個記錄。 這項作業會做為輸入使用下列參數：  
  
    -   SearchExpr： 包含搜尋運算式。 在指定的商務元件的所有記錄是對此搜尋運算式中，而相符的記錄會傳回到配接器用戶端。  
  
    -   SortSpec： 如果有多筆記錄符合搜尋運算式，此規格會決定傳回記錄的順序。 這個參數是選擇性的。  
  
    -   # 10： 可讓配接器用戶端擷取的子集傳回的記錄中欄位的值。 這個參數是選擇性的。  
  
        > [!NOTE]
        >  [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]支援 QueryField 參數在商務元件上的查詢作業中使用原始名稱  
  
-   **更新**。 配接器用戶端可以更新商務元件中的一個或多個記錄。  
  
-   **刪除**。 配接器用戶端可以刪除商務元件中的一個或多個記錄，指定一組識別碼，或藉由提供搜尋運算式。  
  
    > [!NOTE]
    >  除了其他參數的查詢、 更新和刪除作業也會採用 ViewMode 參數。 此參數採用的整數會決定使用者的存取權限。 如需 ViewMode 參數和其他參數，這些作業的詳細資訊，請參閱底下的商務元件操作的要求訊息[商務元件操作的訊息結構描述](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md)。  
  
 如需詳細資訊：  
  
-   執行使用 BizTalk Server 的商務元件上的作業時，請參閱[商務元件使用 BizTalk Server 和 Siebel 配接器上執行的作業](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-using-the-siebel-adapter-in-biztalk.md)。  
  
-   執行使用 WCF 服務模型的商務元件上的作業時，請參閱[Siebel 配接器使用 WCF 服務模型的商務元件上執行的作業](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-with-the-siebel-adapter-using-wcf-service.md)。  
  
-   執行使用 WCF 通道模型的商務元件上的作業時，請參閱[Siebel 配接器使用 WCF 服務模型的商務元件上執行的作業](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-with-the-siebel-adapter-using-wcf-service.md)。  
  
-   執行使用訊息結構和 SOAP 動作的商務元件上的作業時，請參閱[商務元件操作的訊息結構描述](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md)。  
  
## <a name="operations-on-business-components-with-mvg-fields"></a>MVG 欄位的商務元件上的作業  
 Siebel 商務元件也可以從其他使用聯結或多重值的群組 (MVG) 的商業元件擷取欄位。 所有商務元件中都顯示的 Insert、 查詢、 更新和刪除作業，除了配接器用戶端可以使用配接器執行 Siebel 商務元件的下列作業：  
  
-   **關聯**。 配接器用戶端可以建立關聯，藉由指定搜尋運算式的父記錄和子記錄。 這只適用於商務元件 MVG 欄位。 搜尋運算式應該篩選父和下層業務元件的完全一筆記錄。  
  
-   **取消關聯**。 藉由指定搜尋運算式的父記錄和子記錄，可以中斷關聯配接器用戶端。 這只適用於商務元件 MVG 欄位。 搜尋運算式必須篩選父和下層業務元件的完全一筆記錄。  
  
-   **Query_ [MVG_Child_Business_Comp]**。 配接器用戶端可以查詢藉由指定的父記錄和 MVG 欄位名稱會與父記錄相關聯之子記錄。 這只適用於商務元件 MVG 欄位。  
  
    > [!NOTE]
    >  除了其他參數，這些作業還會考慮 ViewMode 參數。 此參數採用的整數會決定使用者的存取權限。 如需 ViewMode 參數和其他參數，這些作業的詳細資訊，請參閱底下的商務元件操作的要求訊息[商務元件操作的訊息結構描述](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md)。  
  
 如需詳細資訊：  
  
-   執行這些作業使用的商務元件上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[MVG 欄位使用 BizTalk Server 和 Siebel 配接器使用的商務元件上執行的作業](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-with-mvg-fields-using-the-siebel-adapter.md)。  
  
-   執行這些作業在商務元件使用 WCF 服務模型時，請參閱[MVG 欄位使用 Siebel 配接器使用 WCF 服務模型的商務元件上執行的作業](../../adapters-and-accelerators/adapter-siebel/work-with-mvp-fields-using-the-siebel-adapter-and-the-wcf-service-model.md)。  
  
-   訊息結構和這些作業的 SOAP 動作，請參閱[商務元件操作的訊息結構描述](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md)。  
  
## <a name="operations-on-business-components-with-picklist-fields"></a>在挑選清單欄位的商務元件上的作業  
 商業元件中的挑選清單欄位型別會構成使用者可以從中挑選要傳遞至 Siebel 系統的特定值的值的集合。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]支援挑選清單欄位的商務元件上的作業。 在上一段所述，在包含挑選清單欄位的商務元件上作業會為任何其他商務元件上的作業相同。 不過，挑選清單的類型，根據商務元件的輸入的值可能會改變。 如需挑選清單和其類型的詳細資訊，請參閱 Siebel 文件。  
  
 挑選清單型別，這是靜態繫結的挑選清單，其中顯示的配接器所列舉的挑選清單為設計階段配接器所產生的中繼資料中的類型。 這包含一組靜態的挑選清單型別必須在執行階段指定的值。  靜態繫結的挑選清單的指定值，同時您一定要指定屬於集的值。  
  
 在包含挑選清單欄位的商務元件上執行作業的訊息結構類似於其他商務元件上的作業與訊息結構中所述[商務元件操作的訊息結構描述](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md).  
  
 如需詳細資訊：  
  
-   訊息結構包含挑選清單欄位的商務元件，請參閱[挑選清單作業的訊息結構描述](../../adapters-and-accelerators/adapter-siebel/message-schema-for-picklist-operations.md)。  
  
-   執行在包含挑選清單欄位的商務元件上的作業時，請參閱[商務元件中以挑選清單欄位使用 BizTalk Server 和 Siebel 配接器上執行的作業](../../adapters-and-accelerators/adapter-siebel/run-tasks-on-business-components-with-picklist-fields-using-the-siebel-adapter.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)