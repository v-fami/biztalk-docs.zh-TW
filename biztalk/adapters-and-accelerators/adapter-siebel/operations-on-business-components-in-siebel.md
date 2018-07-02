---
title: 在 Siebel 商務元件上的作業 |Microsoft Docs
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
ms.openlocfilehash: 2156aa058126e4029ee0002a24eca1bcedb19999
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988479"
---
# <a name="operations-on-business-components-in-siebel"></a>在 Siebel 商務元件上的作業
Siebel 商務元件是一種邏輯實體，將一或多個資料庫資料表中的資料行產生關聯成單一結構。 配接器用戶端可以執行下列作業在 Siebel 商務元件上的使用配接器：  
  
- **插入**。 配接器用戶端都可以將一或多個記錄插入商務元件。  
  
- **查詢**。 配接器用戶端可以查詢從商務元件的一或多個記錄。 這項作業會做為輸入使用下列參數：  
  
  - SearchExpr： 包含搜尋運算式。 在指定的商務元件底下的所有記錄是針對此搜尋運算式中，而相符的記錄傳回至配接器用戶端。  
  
  - SortSpec： 如果有多筆記錄符合搜尋的運算式，此規格會決定傳回記錄的順序。 這個參數是選擇性的。  
  
  - # 10： 可讓配接器用戶端，來擷取值，只傳回記錄中欄位的一部分。 這個參數是選擇性的。  
  
    > [!NOTE]
    >  [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]支援 QueryField 參數，在商務元件上的查詢作業中使用原始名稱  
  
- **更新**。 配接器用戶端可以更新商務元件中的一或多個記錄。  
  
- **刪除**。 配接器用戶端可以刪除商務元件中的一個或多筆記錄，藉由指定一組識別碼，或藉由提供的搜尋運算式。  
  
  > [!NOTE]
  >  除了其他參數的查詢、 更新和刪除作業也會採用 ViewMode 參數。 此參數接受一個整數，決定使用者的存取權限。 如需有關 ViewMode 參數和其他參數，這些作業的詳細資訊，請參閱底下的商務元件作業的要求訊息[商務元件作業的訊息結構描述](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md)。  
  
  如需詳細資訊：  
  
- 執行使用 BizTalk Server 的商務元件上的作業，請參閱[對商務元件使用 BizTalk Server 和 Siebel 配接器的 執行作業](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-using-the-siebel-adapter-in-biztalk.md)。  
  
- 執行對商務元件使用 WCF 服務模型的作業，請參閱[Siebel 配接器使用 WCF 服務模型的商務元件上的 執行作業](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-with-the-siebel-adapter-using-wcf-service.md)。  
  
- 執行對商務元件使用 WCF 通道模型的作業，請參閱[Siebel 配接器使用 WCF 服務模型的商務元件上的 執行作業](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-with-the-siebel-adapter-using-wcf-service.md)。  
  
- 執行使用訊息結構和 SOAP 動作的商務元件上的作業，請參閱[商務元件作業的訊息結構描述](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md)。  
  
## <a name="operations-on-business-components-with-mvg-fields"></a>對具有 MVG 欄位的商務元件作業  
 Siebel 商務元件也可以使用聯結或多重值的群組 (MVG) 其他商務元件從擷取的欄位。 除了會顯示所有的商務元件的插入、 查詢、 更新和刪除作業，配接器用戶端可以執行下列作業在 Siebel 商務元件上的使用配接器：  
  
- **關聯**。 配接器用戶端可以建立關聯，藉由指定搜尋運算式的父記錄和子記錄。 這是僅適用於對具有 MVG 欄位的商務元件。 搜尋運算式應該篩選父和子商務元件只有一個記錄。  
  
- **取消關聯**。 配接器用戶端可以中斷關聯，藉由指定搜尋運算式的父記錄和子記錄。 這是僅適用於對具有 MVG 欄位的商務元件。 搜尋運算式必須篩選父和子商務元件只有一個記錄。  
  
- **Query_ [MVG_Child_Business_Comp]**。 配接器用戶端可以查詢藉由指定的父記錄和 MVG 欄位名稱會與父記錄相關聯的子記錄。 這是僅適用於對具有 MVG 欄位的商務元件。  
  
  > [!NOTE]
  >  除了其他參數，這些作業也會採用 ViewMode 參數。 此參數接受一個整數，決定使用者的存取權限。 如需有關 ViewMode 參數和其他參數，這些作業的詳細資訊，請參閱底下的商務元件作業的要求訊息[商務元件作業的訊息結構描述](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md)。  
  
  如需詳細資訊：  
  
- 執行這些作業上使用的商務元件[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱 <<c2> [ 執行的作業，對具有 MVG 欄位使用 BizTalk Server 和 Siebel 配接器的商務元件](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-with-mvg-fields-using-the-siebel-adapter.md)。  
  
- 執行這些作業對商務元件使用 WCF 服務模型，請參閱[執行的作業，對具有 MVG 欄位與 Siebel 配接器使用 WCF 服務模型的商務元件](../../adapters-and-accelerators/adapter-siebel/work-with-mvp-fields-using-the-siebel-adapter-and-the-wcf-service-model.md)。  
  
- 訊息結構和這些作業的 SOAP 動作，請參閱[商務元件作業的訊息結構描述](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md)。  
  
## <a name="operations-on-business-components-with-picklist-fields"></a>在挑選清單欄位的商務元件上的作業  
 商務元件中的挑選清單欄位類型構成使用者可以從中挑選要傳遞至 Siebel 系統的特定值的值的集合。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]支援與挑選清單欄位的商務元件上的作業。 上一段所述，包含挑選清單欄位的商務元件上的作業並在任何其他商務元件上的作業相同。 不過，挑選清單的類型，根據商務元件的輸入的值可能會不同。 如需有關挑選清單和其類型的詳細資訊，請參閱 Siebel 文件。  
  
 其中一個挑選清單類型，而靜態繫結的挑選清單，顯示的配接器所列舉的挑選清單為設計階段配接器所產生的中繼資料中的型別。 這包含一組靜態的挑選清單型別必須在執行階段指定的值。  同時指定靜態繫結的挑選清單值，您一律必須指定值所屬的集合，這個值。  
  
 在挑選清單欄位的商務元件上執行作業的訊息結構是類似於任何其他商務元件作業的訊息結構中所述[的商務元件作業的訊息結構描述](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md).  
  
 如需詳細資訊：  
  
-   訊息包含挑選清單欄位的商務元件的結構，請參閱[挑選清單作業的訊息結構描述](../../adapters-and-accelerators/adapter-siebel/message-schema-for-picklist-operations.md)。  
  
-   執行包含挑選清單欄位的商務元件上的作業，請參閱[挑選清單欄位使用 BizTalk Server 與 Siebel 配接器的商務元件上的 執行作業](../../adapters-and-accelerators/adapter-siebel/run-tasks-on-business-components-with-picklist-fields-using-the-siebel-adapter.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)