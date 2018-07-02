---
title: 步驟 3： 測試已移轉的應用程式，到 Oracle 資料庫配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495efc4f-9d9e-450f-a03a-628bb54e658f
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8cdd41227b8c51eae6a1f1d2e11f3b3b792482f4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970375"
---
# <a name="step-3-test-the-migrated-application-to-oracle-database-adapter"></a>步驟 3： 測試已移轉的應用程式，到 Oracle 資料庫配接器
![步驟 3 之 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")  
  
 **若要完成的時間：** 5 分鐘  
  
 **目標：** 在此步驟中，您將測試已移轉的應用程式執行插入作業上 SCOTT。CUSTOMER 資料表中。 若要這樣做，您已卸除使用 vPrev Oracle 資料庫配接器所產生的結構描述的要求訊息。  
  
## <a name="prerequisites"></a>必要條件  
  
- 將 BizTalk 協調流程中的邏輯連接埠對應至 BizTalk Server 管理主控台中的實體連接埠，以設定 BizTalk 應用程式。  
  
- 設定要用於 Wcf-custom 傳送埠以 WCF 為基礎的 BizTalk 應用程式[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
### <a name="to-test-the-migrated-application"></a>若要測試已移轉的應用程式  
  
1. 從 [Oracle_Migration] 資料夾中，複製 OracleInsert.xml 要求訊息。 此要求訊息符合 vPrev Oracle 資料庫配接器所產生的結構描述。 使用輸出對應，WCF 自訂傳送連接埠將此選項以 WCF 為基礎的結構描述符合[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]並將它傳送到 Oracle 資料庫。  
  
   ```  
   <ns0:Insert xmlns:ns0="http://schemas.microsoft.com/[OracleDb://ADAPTER/SCOTT/Tables/CUSTOMER]">  
     <ns0:Rows>  
       <ns0:InsertRecord>  
         <ns0:NAME>Customer_1</ns0:NAME>  
         <ns0:STREET>Street_1</ns0:STREET>  
         <ns0:CITY>City_1</ns0:CITY>  
       </ns0:InsertRecord>  
       <ns0:InsertRecord>  
         <ns0:NAME>Customer_2</ns0:NAME>  
         <ns0:STREET>Street_2</ns0:STREET>  
         <ns0:CITY>City_2</ns0:CITY>  
       </ns0:InsertRecord>  
     </ns0:Rows>  
   </ns0:Insert>  
   ```  
  
2. 貼上要對應至檔案的資料夾的要求訊息的接收位置。  
  
3. 協調流程會使用要求訊息，並將它傳送到 Oracle 資料庫。 在接收到回應從 Oracle 資料庫中的結構描述符合以 WCF 為基礎的結構描述[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 使用輸入的對應，Wcf-custom 傳送埠將此 vPrev Oracle 資料庫配接器的結構描述。 從 Oracle 資料庫的回應會儲存到其他的協調流程中定義的檔案位置。 上述的要求訊息的回應是：  
  
   ```  
   <?xml version="1.0" encoding="utf-8"?>  
   <ns0:InsertResponse xmlns:ns0="http://schemas.microsoft.com/[OracleDb://ADAPTER/SCOTT/Tables/CUSTOMER]"></ns0:InsertResponse>  
   ```  
  
## <a name="see-also"></a>另請參閱  
 [教學課程： 移轉 BizTalk 專案](https://msdn.microsoft.com/library/dd788186(v=bts.80).aspx)