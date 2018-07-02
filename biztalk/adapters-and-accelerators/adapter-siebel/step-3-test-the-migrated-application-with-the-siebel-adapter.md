---
title: 步驟 3： 測試移轉應用程式與 Siebel 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 651ee1b2-52da-497a-84a5-67f1436cc3e6
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1669ed459dffbd8746936ffa1ba8c23677173e5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989583"
---
# <a name="step-3-test-the-migrated-application-with-the-siebel-adapter"></a>步驟 3： 測試移轉應用程式與 Siebel 配接器
![步驟 3 之 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")  
  
 **若要完成的時間：** 5 分鐘  
  
 **目標：** 在此步驟中，您將測試已移轉的應用程式執行插入作業帳戶商務元件上的。 若要這樣做，您已卸除使用 vPrev Siebel 配接器所產生的結構描述的要求訊息。  
  
## <a name="prerequisites"></a>必要條件  
  
- 將 BizTalk 協調流程中的邏輯連接埠對應至 BizTalk Server 管理主控台中的實體連接埠，以設定 BizTalk 應用程式。  
  
- 設定要用於 Wcf-custom 傳送埠以 WCF 為基礎的 BizTalk 應用程式[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
### <a name="to-test-the-migrated-application"></a>若要測試已移轉的應用程式  
  
1. 從 [Siebel_BussComp_Migration] 資料夾中，複製 AccountInsert.xml 要求訊息。 此要求訊息符合 vPrev Siebel 配接器所產生的結構描述。 使用輸出對應，WCF 自訂傳送連接埠將此選項以 WCF 為基礎的結構描述符合[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]並將它傳送至 Siebel 系統。  
  
   ```  
   <Insert xmlns="http://schemas.microsoft.com/[Siebel://Business Objects/Account/Account]">  
     <AccountInsertRecordSet>  
       <AccountInsertRecord xmlns="http://schemas.microsoft.com/Business_Objects">  
         <Currency_Code>USD</Currency_Code>  
         <Customer_Account_Group>Sold-To-Party</Customer_Account_Group>  
         <Location>Location_1</Location>  
         <Main_Phone_Number>012345678</Main_Phone_Number>  
         <Name>John_Smith</Name>  
         <Party_Name>Party_Name_1</Party_Name>  
         <Primary_Address_Id></Primary_Address_Id>  
       </AccountInsertRecord>  
     </AccountInsertRecordSet>  
   </Insert>  
   ```  
  
2. 貼上要對應至檔案的資料夾的要求訊息的接收位置。  
  
3. 協調流程會使用要求訊息，並將它傳送至 Siebel 系統。 在接收到回應來自 Siebel 系統中的結構描述符合以 WCF 為基礎的結構描述[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。 使用輸入的對應，Wcf-custom 傳送埠將此 vPrev Siebel 配接器的結構描述。 來自 Siebel 系統的回應會儲存到其他的協調流程中定義的檔案位置。 上述的要求訊息的回應是：  
  
   ```  
   <?xml version="1.0" encoding="utf-8"?>  
   <ns0:InsertResponse xmlns:ns0="http://schemas.microsoft.com/[Siebel://Business Objects/Account/Account]" xmlns:exposed="http://schemas.microsoft.com" xmlns:Business_Objects="http://schemas.microsoft.com/Business_Objects">  
     <ns0:RowIDList>  
       <exposed:String>1-8EWWZ</exposed:String>  
     </ns0:RowIDList>  
   </ns0:InsertResponse>  
   ```  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 2： 移轉 BizTalk 專案中 Siebel](../../adapters-and-accelerators/adapter-siebel/tutorial-2-migrating-biztalk-projects-in-siebel.md)