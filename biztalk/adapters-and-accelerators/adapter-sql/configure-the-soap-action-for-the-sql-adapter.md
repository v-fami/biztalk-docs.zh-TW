---
title: 在 BizTalk 設定 SQL 配接器的 SOAP 動作 |Microsoft Docs
description: 在 Visual Studio 中，輸入 SOAP 動作，或使用 BizTalk 配接器組件 (BAP) 中的 WCF 自訂] 或 [WCF-SQL 配接器
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acd7f60b-c27f-4988-a67c-e56ef8d38f66
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a927740ba04a0fd1b080e73ef60892ffdc9bf385
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980519"
---
# <a name="configure-the-soap-action-for-the-sql-adapter"></a>設定 SQL 配接器的 SOAP 動作
若要使用以 WCF 為基礎的 SQL Server 上執行任何作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，您必須指定 SOAP 動作。 SOAP 動作與配接器應該執行什麼動作。 您可以從指定的 SOAP 動作[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]或從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 不過，如果您指定來自兩個位置的 SOAP 動作，您指定動作從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]將會覆寫。  
  
 如需指定 SOAP 動作的詳細資訊，請參閱[指定 WCF 傳送配接器的 SOAP 動作](../../core/specifying-soap-actions-for-wcf-send-adapters.md)。
  
## <a name="enter-the-soap-action-in-visual-studio"></a>在 Visual Studio 中，輸入 SOAP 動作  
 從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您也必須使用協調流程指定的 SOAP 動作**運算式**圖形。  
  
1.  在 BizTalk 協調流程，包括**運算式**圖形，方法是將它從**BizTalk 協調流程**工具箱。  
  
2.  按兩下**運算式**圖形以開啟 BizTalk 運算式編輯器。  
  
3.  在 [BizTalk 運算式編輯器] 中指定的動作。 例如：  
  
    ```  
    OutboundMessage(WCF.Action)="TableOp/Insert/dbo/Employee"  
    ```  
  
     如需詳細資訊**運算式**形狀 」 和 「 BizTalk 運算式編輯器，請參閱[如何建立運算式](../../core/how-to-create-expressions.md)。
  
## <a name="enter-the-soap-action-from-the-biztalk-server-administration-console"></a>從 BizTalk Server 管理主控台中輸入的 SOAP 動作  
 從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您可以指定的 SOAP 動作為 [Wcf-custom] 或 [WCF SQL 連接埠組態的一部分。  
  
### <a name="enter-a-soap-action-for-the-wcf-custom-port"></a>輸入 WCF 自訂連接埠的 SOAP 動作  
  
1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後按一下**傳送埠**。 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  
  
3. 在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。  
  
4. 在  **Wcf-custom 傳輸屬性** 對話方塊中，按一下**一般** 索引標籤。  
  
5. 在 **動作**文字方塊中，指定作業的 SOAP 動作。 您可以透過下列方式指定的動作：  
  
   -   **使用單一動作格式**。 如果 「 WCF 自訂連接埠傳送和接收訊息的單一作業，請使用此格式。 例如：  
  
       ```  
       TableOp/Insert/dbo/Employee  
       ```  
  
   -   **使用動作對應格式**。 如果單一 WCF 自訂連接埠傳送和接收多個作業的訊息，請使用此格式。 比方說，如果單一 WCF 自訂連接埠傳送或接收訊息 （若要 Employee 資料表中插入記錄） Op1 和 Op2 （若要更新 Employee 資料表中的記錄），可以指定的 SOAP 動作以下列方式：  
  
       ```  
       <BtsActionMapping>  
         <Operation Name="Op1" Action="TableOp/Insert/dbo/Employee" />  
         <Operation Name="Op2" Action="TableOp/Update/dbo/Employee" />  
       </BtsActionMapping>  
       ```  
  
        動作對應方法，提供更大的彈性以指定的一組動作，並因此啟用屬於不同的動作類型的流量通過相同的連接埠的訊息。  
  
        SOAP 動作的格式是針對每個作業不同。 如需有關每個作業的動作格式的詳細資訊，請參閱[訊息和訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)。
  
### <a name="enter-a-soap-action-for-the-wcf-sql-port"></a>輸入 WCF SQL 連接埠的 SOAP 動作  
  
1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2. 新增 WCF-SQL 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如需相關指示，請參閱 <<c0> [ 將 SQL 配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md)。  
  
3. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後按一下**傳送埠**。 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  
  
4. 在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取您稍早新增 WCF-SQL 配接器，然後按一下**設定**。  
  
5. 在 傳輸屬性 對話方塊中，按一下**一般** 索引標籤。  
  
6. 在 **動作**文字方塊中，指定作業的 SOAP 動作。 您可以透過下列方式指定的動作：  
  
   -   **使用單一動作格式**。 如果 WCF SQL 連接埠傳送和接收訊息的單一作業，請使用此格式。 例如：  
  
       ```  
       TableOp/Insert/dbo/Employee  
       ```  
  
   -   **使用動作對應格式**。 如果單一 WCF SQL 連接埠傳送和接收多個作業的訊息，請使用此格式。 比方說，如果單一 WCF SQL 連接埠傳送或接收訊息 （若要 Employee 資料表中插入記錄） Op1 和 Op2 （若要更新 Employee 資料表中的記錄），可以指定的 SOAP 動作以下列方式：  
  
       ```  
       <BtsActionMapping>  
         <Operation Name="Op1" Action="TableOp/Insert/dbo/Employee" />  
         <Operation Name="Op2" Action="TableOp/Update/dbo/Employee" />  
       </BtsActionMapping>  
       ```  
  
        動作對應方法，提供更大的彈性以指定的一組動作，並因此啟用屬於不同的動作類型的流量通過相同的連接埠的訊息。  
  
        SOAP 動作的格式是針對每個作業不同。 如需有關每個作業的動作格式的詳細資訊，請參閱[訊息和訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)。
  
## <a name="see-also"></a>另請參閱  
[若要開發使用 SQL 配接器的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)