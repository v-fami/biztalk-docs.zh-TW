---
title: 如何搜尋已擱置的服務執行個體 |Microsoft 文件
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
- service instances, suspended
- Query tab [Administration Console], searching
- instances, suspended
- instances, services
ms.assetid: f91b1151-d879-4aa7-afc8-4cf13d928158
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 52c0d3ad192ad2cc8f4429f78cfa38ddc97ac837
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "22255670"
---
# <a name="how-to-search-for-suspended-service-instances"></a>如何搜尋已擱置的服務執行個體
您可以使用 **查詢** 在 BizTalk Server 管理主控台中搜尋已擱置的服務執行個體 索引標籤。 您可以搜尋特定的訊息子集，以尋找與服務名稱、類型、主控件等關聯的特定訊息。  
  
> [!NOTE]
>  已中止且具有未使用訊息的執行個體，會顯示為相關的已擱置服務執行個體的錯誤碼 (「已中止且具有未使用訊息」)。 這些執行個體是不可繼續的。  
  
> [!NOTE]
>  依據 URI 或錯誤配接器名稱建立群組和篩選時，只有傳送埠和接收埠才會顯示在結果中。 URI 建立群組和篩選並不適用協調流程，因為協調流程不包含在顯示的結果內。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行此程序，您必須以「BizTalk Server 操作員」群組的成員身分登入。  
  
### <a name="to-search-for-suspended-service-instances"></a>搜尋已擱置的服務執行個體  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開 **BizTalk Server 管理**, ，然後按一下 BizTalk 群組。  
  
3.  在詳細資料窗格中，按一下 [ **新查詢** ] 索引標籤。  
  
4.  在 **查詢運算式** 群組 **值** 欄中，選取 **已擱置服務執行個體** 從下拉式清單方塊。  
  
5.  在 **欄位名稱** 欄中的空白下拉式清單方塊旁邊的星號 (**\***)，選取一或多個項目︰  
  
    |項目|Description|  
    |----------|-----------------|  
    |**應用程式名稱**|BizTalk Server 應用程式的名稱。|  
    |**建立時間**|尋找在指定日期之前或之後建立的已擱置服務執行個體。|  
    |**錯誤配接器**|您可以依據配接器類型，對已擱置服務執行個體建立群組或篩選。 例如︰ 檔案、 FTP、 HTTP、 MQSeries、 MSMQ、 POP3、 SMTP、 SOAP 或 Windows SharePoint Services。 **注意︰**  在查詢結果中，配接器才會填入欄位時 BizTalk Server 執行階段時發生錯誤執行時，會使用指定的配接。 如果執行階段在使用配接器時沒有發現錯誤，則查詢結果中的 [錯誤配接器] 欄位將是空白的。|  
    |**錯誤碼**|您可以依錯誤碼來群組或篩選已擱置的服務執行個體，以顯示所有具有該錯誤碼的已擱置服務執行個體。|  
    |**錯誤描述**|您可以群組或篩選具有指定錯誤描述的已擱置服務執行個體。|  
    |**群組結果依據**|您可以依據配接器、應用程式、錯誤碼、錯誤描述、主控件名稱、服務類別、服務執行個體狀態、服務名稱或 URI，來群組或篩選結果。|  
    |**主機名稱**|依主控件名稱來群組或篩選已擱置的服務執行個體。|  
    |**執行個體狀態**|您可以搜尋已擱置且不可繼續的執行個體，或是已擱置且可繼續的執行個體。|  
    |**最大相符項目**|要顯示的相符記錄數目。|  
    |**服務類別**|您可以搜尋外掛式配接器、傳訊、傳訊與外掛式配接器、MSMQT、協調流程，或路由失敗報告。|  
    |**服務名稱**|您可以依服務名稱來群組或篩選已擱置的服務執行個體。|  
    |**服務類型識別碼**|您可以依服務類型識別碼來群組或篩選已擱置的服務執行個體。|  
    |**擱置時間**|您可以群組或篩選在指定日期之前或之後擱置的已擱置服務執行個體。|  
    |**URI**|您可以依 URI 來群組或篩選已擱置的服務執行個體。 **注意︰**  在查詢結果中，才會填入時傳送至指定的 URI 時 BizTalk Server 執行階段執行時發生錯誤。 如果執行階段在傳送至 URI 時沒有發現錯誤，則查詢結果中的 URI 欄位會空白或顯示「URI 無法使用」。|  
  
6.  完成 **值** 適用於選取您所做的資料行 **欄位名稱** 資料行。  
  
7.  繼續新增其他行至視需要查詢，藉由完成 **欄位名稱**, ，**運算子**, ，和 **值** 資料行，然後再按一下 **執行查詢**。  
  
## <a name="see-also"></a>另請參閱  
 [使用管理主控台查詢索引標籤](../core/using-the-administration-console-query-tab.md)