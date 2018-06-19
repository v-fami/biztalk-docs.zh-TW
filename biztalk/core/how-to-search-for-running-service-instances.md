---
title: 如何搜尋執行中服務執行個體 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- service instances, viewing
- service instances, Query tab [Administration Console]
- Query tab [Administration Console], service instances
- Query tab [Administration Console], searching
- service instances, searching
- service instances, running
ms.assetid: fc65bf33-c013-4e6a-b9fd-b4536811e7b4
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8873747b39d6fa178b813d361b72ccf24f44b54a
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "22255198"
---
# <a name="how-to-search-for-running-service-instances"></a>如何搜尋執行中的服務執行個體
您可以使用 **查詢**  索引標籤來搜尋特定 BizTalk Server 管理主控台中的已凍結、 作用中，在中斷點、 已排程，及重試服務執行個體。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行此程序，您必須以「BizTalk Server 操作員」群組的成員身分登入。  
  
### <a name="to-search-for-running-service-instances"></a>搜尋執行中的服務執行個體  
  
1.  按一下**啟動**，按一下 **程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中展開 [[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]]，然後按一下 BizTalk 群組。  
  
3.  在詳細資料窗格中，按一下 [ **新查詢** ] 索引標籤。  
  
4.  在 **查詢運算式** 群組 **值** 欄中，選取 **執行服務執行個體** 從下拉式清單方塊。  
  
5.  在 **欄位名稱** 欄中的空白下拉式清單方塊旁邊的星號 (**\***)，選取一或多個項目︰  
  
    |項目|Description|  
    |----------|-----------------|  
    |**應用程式名稱**|BizTalk Server 應用程式。|  
    |**建立時間**|尋找指定日期前後建立的執行中服務執行個體。|  
    |**群組結果依據**|您可以依據應用程式、主控件名稱、擱置作業的類型、服務類別、服務執行個體狀態或服務名稱來群組結果。|  
    |**主機名稱**|BizTalk 主控件的名稱。|  
    |**執行個體狀態**|您可以搜尋作用中的執行個體、已凍結的執行個體、準備執行的執行個體、已排程的執行個體。|  
    |**最大相符項目**|要顯示的相符記錄數目。|  
    |**暫止的作業**|您可以搜尋目前擱置或終止的執行中服務執行個體。|  
    |**服務類別**|您可以搜尋外掛式配接器、傳訊、傳訊與外掛式配接器、MSMQT、協調流程，或路由失敗報告。|  
    |**服務名稱**|您可以依服務名稱來群組或篩選執行中的服務執行個體。|  
    |**服務類型識別碼**|您可以使用服務類型識別碼來分組或篩選訊息。|  
  
6.  完成 **值** 適用於選取您所做的資料行 **欄位名稱** 資料行。  
  
7.  繼續新增其他行至視需要查詢，藉由完成 **欄位名稱**, ，**運算子**, ，和 **值** 資料行，然後再按一下 **執行查詢**。  
  
## <a name="see-also"></a>另請參閱  
 [使用管理主控台查詢索引標籤](../core/using-the-administration-console-query-tab.md)