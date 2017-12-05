---
title: "步驟 2： 設定的連接埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e804da96-26ae-482d-b6e1-67af24d639d9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c9aaefe0cff41365a587079d0c82629ddddc586
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-2-configure-the-ports"></a>步驟 2： 設定的連接埠
![步驟 4 之 2](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")  
  
 **若要完成的時間：** 15 分鐘  
  
 **目標：**在此步驟中，您建立的實體連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 您建立每個邏輯連接埠在協調流程中所建立的實體連接埠。 您將建立下列連接埠：  
  
-   單向 WCF 自訂接收埠以接收通知訊息變更**員工**SQL Server 資料庫中的資料表。  
  
-   要求-回應 WCF 自訂傳送埠以傳送要求訊息並接收回應叫用**UPDATE_EMPLOYEE**預存程序，在上執行插入作業的**Purchase_Order**資料表。 在協調流程中，您可以使用相同的傳送埠來執行這兩個作業。 同樣地，在[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您將這兩個作業使用單一傳送埠。  
  
-   單向傳送埠以傳送插入作業的回應。 在本教學課程中，您必須通知採購部門，透過電子郵件，因為您建立此傳送埠做為 SMTP 連接埠。  
  
## <a name="prerequisites"></a>必要條件  
 您必須先完成[步驟 1： 部署的協調流程](../../adapters-and-accelerators/adapter-sql/step-1-deploy-the-orchestration.md))。  
  
### <a name="to-create-a-physical-one-way-receive-port"></a>若要建立單向的實體接收埠  
  
1.  啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2.  在左邊主控台樹狀目錄中，依序展開**BizTalk Server 管理**，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下 **重新整理**。  
  
3.  展開**BizTalk 群組**，依序展開**應用程式**，然後展開**SampleApplication**。 此教學課程中，您可以建立所有的連接埠和 SampleApplication 應用程式中的應用程式。  
  
4.  請遵循底下的 < 部署配接器的接收訊息從 SQL Server > 一節的指示[設定使用 wcf-custom 配接器和 SQL 配接器的連接埠](../../adapters-and-accelerators/adapter-sql/configure-a-port-using-the-wcf-custom-adapter-and-sql-adapter.md)。 埠命名為**NotifyReceivePort**。  
  
5.  請確定您設定下列繫結屬性設定配接器接收的變更通知**員工**資料表。  
  
    |繫結屬性|值|  
    |----------------------|-----------|  
    |**InboundOperationType**|將此設**通知**。|  
    |**NotificationStatement**|將此值設定為：<br /><br /> `SELECT Employee_ID, Name FROM dbo.Employee WHERE Status=0`<br /><br /> **注意：**您必須明確指定資料行名稱的陳述式中這個 Select 陳述式中所示。 此外，您必須一律指定資料表名稱，以及結構描述名稱，例如`dbo.Employee`。|  
    |**NotifyOnListenerStart**|將此設**True**。|  
  
     如需不同的繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
### <a name="to-create-a-request-response-send-port-for-two-operations"></a>建立要求-回應傳送埠的兩個作業  
  
1.  請遵循底下的 < 部署配接器的傳送訊息至 SQL Server > 一節的指示[設定使用 wcf-custom 配接器和 SQL 配接器的連接埠](../../adapters-and-accelerators/adapter-sql/configure-a-port-using-the-wcf-custom-adapter-and-sql-adapter.md)。 埠命名為**SQLOutboundPort**。  
  
2.  因為您正在執行兩項作業使用相同的傳送埠時，您必須使用動態動作對應來指定作業的動作。 在設定連接埠時**動作**方塊中，以下列方式指定動作對應：  
  
    ```  
    <BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
      <Operation Name="UpdateEmp" Action="TypedProcedure/dbo/UPDATE_EMPLOYEE" />  
      <Operation Name="InsertPO" Action="TableOp/Insert/dbo/Purchase_Order" />  
    </BtsActionMapping>  
    ```  
  
     請注意，在協調流程，您建立要求-回應傳送埠的兩個作業： **UpdateEmp**和**InsertPO**。 因此，實體連接埠組態中您會提供相同的作業名稱動態動作對應中。 在以上摘錄中，為動作**UpdateEmp**作業`TypedProcedure/dbo/UPDATE_EMPLOYEE`。 同樣地，針對動作**InsertPO**作業`TableOp/Insert/dbo/Purchase_Order`。  
  
3.  您也必須設定傳送埠，使用您在對應的回應訊息的協調流程中建立的對應工具**UPDATE_EMPLOYEE**預存程序來插入作業的要求訊息**Purchase_順序**資料表。 若要這樣做：  
  
    1.  以滑鼠右鍵按一下在 SQLOutboundPort[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台，然後按一下**屬性**。  
  
    2.  從**SQLOutboundPort-傳送埠屬性**對話方塊中的，從左窗格中，按一下**輸出對應**。  
  
    3.  從右窗格中，在**輸出對應**方塊中，按一下下方的儲存格**對應**資料行，然後從下拉式清單中，選取**[transform_1]**。 這是您建立 BizTalk 協調流程中之對應的名稱[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。  
  
         按一下 **[確定]**。  
  
         ![設定輸出對應](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-010-map-ports.gif "sql_adap_tut_010_map_ports")  
  
### <a name="to-create-an-smtp-send-port"></a>若要建立 SMTP 傳送埠  
  
1.  依照 「 如何設定 SMTP 傳送埠與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台 」 區段在[http://go.microsoft.com/fwlink/?LinkId=141549](http://go.microsoft.com/fwlink/?LinkId=141549)。 埠命名為**EmailResponse**。  
  
2.  連接埠組態的一部分，指定 電子郵件地址，如採購部門**至**屬性。  
  
## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 在此步驟中您建立 WCF 自訂接收 SQL Server 從接收通知的連接埠、 Wcf-custom 傳送埠執行 SQL Server 上的作業和採購部門為以電子郵件傳送回應從 SQL Server 的 SMTP 連接埠。  
  
## <a name="next-steps"></a>後續步驟  
 您設定和啟動 BizTalk 應用程式中所述[步驟 3： 設定並啟動應用程式](../../adapters-and-accelerators/adapter-sql/step-3-configure-and-start-the-application.md)。  
  
## <a name="see-also"></a>請參閱  
 [步驟 1： 部署的協調流程](../../adapters-and-accelerators/adapter-sql/step-1-deploy-the-orchestration.md)   
 [步驟 3： 設定並啟動應用程式](../../adapters-and-accelerators/adapter-sql/step-3-configure-and-start-the-application.md)   
 [第 5 課：部署方案](../../adapters-and-accelerators/adapter-sql/lesson-5-deploy-the-solution.md)