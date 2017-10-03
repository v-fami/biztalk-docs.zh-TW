---
title: "如何搜尋追蹤的訊息事件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18df4cf7-c307-4175-926c-9be9f30b29ed
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a3d4c573b864d16362c1b12b1e293e85f139cad4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-search-for-tracked-message-events"></a>如何搜尋追蹤的訊息事件
您可以使用**新查詢**索引標籤中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台來搜尋追蹤訊息事件。  從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，您可以啟用訊息內文和追蹤訊息屬性。 在查詢結果 窗格中，您可以檢視訊息的事件，包括結構描述資訊、 事件類型、 服務執行個體識別碼，以及產生之訊息的升級的屬性的相關資訊。  
  
> [!NOTE]
>  若要檢視實際的訊息內文，您可以叫用**訊息詳細資料**操作功能表，然後移至 「 訊息部分 」 索引標籤上，或儲存訊息從結果清單檢視叫用**儲存至檔案**從內容功能表。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 操作員」群組成員的身分來登入，才能執行此程序。  
  
### <a name="to-search-for-tracked-message-items"></a>若要搜尋的項目追蹤的訊息  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，然後按一下 BizTalk 群組。  
  
3.  在 詳細資料 窗格中，按一下**新查詢** 索引標籤。  
  
4.  在**查詢運算式**群組中**值**欄中，選取**追蹤訊息事件**從下拉式清單方塊。  
  
5.  在**欄位名稱**星號旁邊的空白下拉式清單方塊中的資料行 (**\***)，選取一個或多個項目：  
  
    |項目|Description|  
    |----------|-----------------|  
    |**建立時間**|建立訊息的時間。|  
    |**事件類型**|正在追蹤的事件類型。|  
    |**最大相符項目**|要顯示的相符記錄數目。|  
    |**合作對象**|組織傳送訊息。|  
    |**[通訊埠]**|用於處理訊息的通訊埠。|  
    |**結構描述名稱**|使用訊息的結構描述的名稱。|  
    |**服務執行個體識別碼**|用於訊息的服務執行個體識別碼。|  
    |**URI**|用於訊息的 URI。|  
    |**\<選取追蹤的屬性結構描述名稱 >**|當您選取的結構描述時，該結構描述中任何升級的屬性是適合用來在查詢中。|  
  
6.  完成**值**適用於選取項目所做的資料行**欄位名稱**資料行。  
  
7.  繼續新增其他行至適當的查詢中，藉由完成**欄位名稱**，**運算子**，和**值**資料行，然後再按一下**執行查詢**。  
  
## <a name="see-also"></a>另請參閱  
 [使用管理主控台查詢索引標籤](../core/using-the-administration-console-query-tab.md)