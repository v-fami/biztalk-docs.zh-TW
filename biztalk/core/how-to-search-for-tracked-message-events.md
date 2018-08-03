---
title: 如何搜尋追蹤的訊息事件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18df4cf7-c307-4175-926c-9be9f30b29ed
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a49ae9793c38746d965c75dc9da902cfe6b6da3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989287"
---
# <a name="how-to-search-for-tracked-message-events"></a>如何搜尋追蹤的訊息事件
您可以使用**新的查詢**索引標籤中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]来搜尋的管理主控台追蹤訊息事件。  從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，您可以啟用訊息內文和訊息屬性追蹤。 在查詢結果 窗格中，您可以檢視訊息事件，包括結構描述資訊、 事件類型、 服務執行個體識別碼和所有產生之訊息的升級的屬性的相關資訊。  

> [!NOTE]
>  若要檢視實際的訊息本文，您可以叫用**訊息的詳細資料**操作功能表，然後移至 「 訊息組件 」 索引標籤上，或將訊息儲存從結果清單檢視叫用**儲存至檔案**從操作功能表。  

## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 操作員」群組成員的身分來登入，才能執行此程序。  

### <a name="to-search-for-tracked-message-items"></a>搜尋追蹤的訊息項目  

1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]。  

2. 在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，然後按一下 BizTalk 群組。  

3. 在 詳細資料 窗格中，按一下**新的查詢** 索引標籤。  

4. 在 **查詢運算式**群組中**值**欄中，選取**追蹤的訊息事件**從下拉式清單方塊。  

5. 在 **欄位名稱**星號旁邊的空白下拉式清單方塊中的資料行 (* *\\* * *)，選取一或多個項目：  


   |                        項目                         |                                              描述                                               |
   |-----------------------------------------------------|--------------------------------------------------------------------------------------------------------|
   |                  **建立時間**                  |                                   建立訊息的時間。                                    |
   |                   **事件類型**                    |                                    正在追蹤的事件類型。                                    |
   |                 **最大相符項目**                 |                                   要顯示的相符記錄數目。                                    |
   |                      **合作對象**                      |                                傳送訊息的組織。                                 |
   |                      **通訊埠**                       |                                 用來處理訊息的連接埠。                                  |
   |                   **結構描述名稱**                   |                                訊息使用的結構描述名稱。                                 |
   |               **服務執行個體識別碼**               |                             訊息所用的服務執行個體識別碼。                              |
   |                       **URI**                       |                                     用來將訊息的 URI。                                      |
   | **\<選取 追蹤屬性的結構描述名稱\>** | 當您選取的結構描述時，該結構描述中任何升級的屬性是適合用來在查詢中。 |


6. 完成**值**適當選取您在中所做的資料行**欄位名**資料行。  

7. 繼續新增其他行至適當的查詢中，藉由完成**欄位名**，**運算子**，並**值**資料行，然後再按一下**執行查詢**。  

## <a name="see-also"></a>另請參閱  
 [使用管理主控台查詢索引標籤](../core/using-the-administration-console-query-tab.md)