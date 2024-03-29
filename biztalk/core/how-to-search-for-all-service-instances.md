---
title: 如何搜尋所有服務執行個體 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- service instances, Query tab [Administration Console]
- Query tab [Administration Console], service instances
- Query tab [Administration Console], searching
- service instances, searching
- instances, services
ms.assetid: 48cb885c-aaf1-44e8-9810-2e70cf63db81
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c2a9193633b111d9a75e2c695017c880e924058e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013751"
---
# <a name="how-to-search-for-all-service-instances"></a>如何搜尋所有服務執行個體
您可以使用**查詢** 索引標籤，在 BizTalk Server 管理主控台，來搜尋所有服務執行個體。 若有任何執行中或擱置的執行個體，就無法取消登錄特定服務類型。 例如，取消登錄特定服務類型之前，可以搜尋所有的服務執行個體，以確保沒有執行中或擱置的執行個體。  

> [!NOTE]
>  URI 建立群組和篩選時，結果中僅會顯示傳送埠和接收埠。 URI 建立群組和篩選並不適用協調流程，因為協調流程不包含在顯示的結果內。  

## <a name="prerequisites"></a>必要條件  
 若要執行此程序，您必須以「BizTalk Server 操作員」群組的成員身分登入。  

### <a name="to-search-for-all-service-instances"></a>搜尋所有服務執行個體  

1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  

2. 在主控台樹狀目錄中展開 [[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]]，然後按一下 BizTalk 群組。  

3. 在 詳細資料 窗格中，按一下**新的查詢** 索引標籤。  

4. 在 **查詢運算式**群組中**值**欄中，選取**所有進行中服務執行個體**從下拉式清單方塊。  

5. 在 **欄位名稱**星號旁邊的空白下拉式清單方塊中的資料行 (* *\\* * *)，選取一或多個項目：  


   |        使用         |                                                                                                              以進行此動作                                                                                                              |
   |-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |  **Application Name**   |                                                                                                   BizTalk Server 應用程式。                                                                                                    |
   |    **建立時間**    |                                                                                尋找指定日期前後建立的所有服務執行個體。                                                                                |
   |  **將結果分組**   |                                                              您可以依據應用程式、主控件名稱、服務類別、服務執行個體狀態或服務名稱來群組結果。                                                               |
   |      **Host Name**      |                                                                                                    BizTalk 主控件的名稱。                                                                                                     |
   |   **執行個體狀態**   | 您可以搜尋所有正在執行的執行個體、所有擱置的執行個體、作用中的執行個體、凍結的執行個體、準備執行的執行個體、已排程的執行個體、已擱置但不可繼續的執行個體，或是已擱置但可以繼續的執行個體。 |
   |   **最大相符項目**   |               要顯示的相符記錄數目 (必要)。 依預設，通常設定為 50。<br /><br /> 當您也使用 [群組結果依據] 時，會顯示群組的數目而非記錄的總數。               |
   |    **服務類別**    |                                                 您可以搜尋外掛式配接器、傳訊、傳訊與外掛式配接器、MSMQT、協調流程，或路由失敗報告。                                                  |
   | **服務執行個體識別碼** |                                                                                  您可以依據服務執行個體識別碼來群組或篩選服務執行個體。                                                                                   |
   |    **服務名稱**     |                                                                                      您可以依據服務名稱來群組或篩選服務執行個體。                                                                                      |
   |   **服務類型識別碼**   |                                                                                    您可以依據服務類型識別碼來群組或篩選服務執行個體。                                                                                     |


6. 完成**值**適當選取您在中所做的資料行**欄位名**資料行。  

7. 繼續新增其他行至視需要查詢中，藉由完成**欄位名**，**運算子**，和**值**資料行，然後再按一下**執行查詢**。  

## <a name="see-also"></a>另請參閱  
 [使用管理主控台查詢索引標籤](../core/using-the-administration-console-query-tab.md)