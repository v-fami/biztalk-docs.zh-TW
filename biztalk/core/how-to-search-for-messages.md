---
title: "如何搜尋訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, viewing
- messages, searching
- Query tab [Administration Console], searching
- Query tab [Administration Console], messages
ms.assetid: c751d23f-913a-4325-81da-a36d61c07e8b
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5443cc021bd5f97621f44d295432c99834bdaed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-search-for-messages"></a>如何搜尋訊息
您可以使用**查詢**中要搜尋特定類別的訊息 [BizTalk Server 管理主控台] 索引標籤。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行此程序，您必須以「BizTalk Server 操作員」群組的成員身分登入。  
  
### <a name="to-search-for-messages"></a>搜尋訊息  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中展開 [[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]]，然後按一下 BizTalk 群組。  
  
3.  在 詳細資料 窗格中，按一下**新查詢** 索引標籤。  
  
4.  在**查詢運算式**群組中**值**欄中，選取**訊息**從下拉式清單方塊。  
  
5.  在**欄位名稱**星號旁邊的空白下拉式清單方塊中的資料行 (**\***)，選取一個或多個項目：  
  
    |項目|Description|  
    |----------|-----------------|  
    |**建立時間**|尋找在指定的日期之前或之後建立的訊息。|  
    |**錯誤配接器**|您可以分組或篩選訊息，配接器類型： 檔案、 FTP、 HTTP、 MQSeries、 MSMQ、 POP3、 SMTP、 SOAP 或 Windows SharePoint Services。|  
    |**錯誤碼**|您可以使用錯誤碼來分組或篩選訊息。|  
    |**錯誤描述**|您可以使用錯誤描述來分組或篩選訊息。|  
    |**Host Name**|您可以使用主控件名稱來分組或篩選訊息。|  
    |**執行個體狀態**|參考訊息的服務執行個體的狀態。 您可以搜尋下列所有類型的執行個體：所有執行中的執行個體、所有擱置的執行個體、作用中的執行個體、已凍結的執行個體、準備執行的執行個體、已排程的執行個體、已擱置但不可繼續的執行個體，或已擱置但可以繼續的執行個體。|  
    |**最大相符項目**|要顯示的相符記錄數目。|  
    |**訊息識別碼**|您可以使用訊息識別碼來分組或篩選訊息。|  
    |**訊息狀態**|您可以搜尋狀態為已使用、進行中、已擱置、已擱置但不可繼續、已擱置且可以繼續、已佇列、已佇列但等候處理、已佇列但已排程稍後傳遞，以及已佇列但等候重試的訊息。|  
    |**訊息類型**|您可以使用訊息類型來分組或篩選訊息。|  
    |**服務類別**|您可以搜尋外掛式配接器、傳訊、傳訊與外掛式配接器、MSMQT、協調流程，或路由失敗報告。|  
    |**服務執行個體識別碼**|您可以使用服務執行個體識別碼來分組或篩選訊息。|  
    |**服務名稱**|您可以使用服務名稱來分組或篩選訊息。|  
    |**服務類型識別碼**|您可以使用服務類型識別碼來分組或篩選訊息。|  
    |**URI**|您可以使用 URI 來分組或篩選訊息。|  
  
6.  完成**值**適用於選取項目所做的資料行**欄位名稱**資料行。  
  
7.  繼續新增其他行至視需要查詢，藉由完成**欄位名稱**，**運算子**，和**值**資料行，然後再按一下**執行查詢**。  
  
## <a name="see-also"></a>另請參閱  
 [使用管理主控台查詢索引標籤](../core/using-the-administration-console-query-tab.md)