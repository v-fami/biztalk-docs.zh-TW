---
title: 在 BizTalk 設定 Oracle 資料庫的 SOAP 動作 |Microsoft Docs
description: 在 Visual Studio 中，輸入 SOAP 動作，或使用 Wcf-custom 或 Wcf-oracledb 配接器在 BizTalk 配接器組件 (BAP)
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0d21cca-3907-4f99-af76-c1e7286e1bcf
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe8b1b2c1043551b692530dcff4b8fdf49a44b54
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994671"
---
# <a name="configure-the-soap-action-for-oracle-database"></a>設定 Oracle 資料庫的 SOAP 動作
若要完成使用 WCF 為基礎的 Oracle 資料庫上的任何作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，配接器使用者必須輸入 SOAP 動作。 SOAP 動作與配接器應該完成哪些動作。 您可以輸入在設計階段或在執行階段的 SOAP 動作。 不過，如果您輸入的 SOAP 動作這兩個設計階段，然後執行階段，就會覆寫您在設計階段輸入的動作。  
  
 如需指定 SOAP 動作的詳細資訊，請參閱[指定 WCF 傳送配接器的 SOAP 動作](../../core/specifying-soap-actions-for-wcf-send-adapters.md)。  
  
## <a name="enter-soap-action-from-visual-studio"></a>輸入 SOAP 動作，從 Visual Studio  
 從 Visual Studio 中，您必須指定的 SOAP 動作的協調流程使用**運算式**圖形。  
  
1.  在 BizTalk 協調流程，包括**運算式**圖形，方法是將它從**BizTalk 協調流程**工具箱。  
  
2.  按兩下**運算式**圖形以開啟 BizTalk 運算式編輯器。  
  
3.  在 BizTalk 運算式編輯器 」 中指定的動作。 例如：  
  
    ```
    OutboundMessage(WCF.Action)="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert"  
    ```  
  
     如需詳細資訊**運算式**圖形和 BizTalk 運算式編輯器，請參閱[如何建立運算式](../../core/how-to-create-expressions.md)。  
  
## <a name="enter-soap-action-from-biztalk-server-administration"></a>從 BizTalk Server 管理 中輸入 SOAP 動作  
 從 BizTalk Server 管理主控台中，您必須指定 Wcf-custom 或 Wcf-oracledb 的連接埠組態的一部分的 SOAP 動作。 

#### <a name="enter-a-soap-action-for-the-wcf-custom-port"></a>輸入 WCF 自訂連接埠的 SOAP 動作  
 
  
1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用的程式在其下您想要建立連接埠，並按一下 **傳送埠**。 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  
  
3. 在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。  
  
4. 在  **Wcf-custom 傳輸屬性** 對話方塊中，按一下**一般** 索引標籤。  
  
5. 在 **動作**文字方塊中，指定作業的 SOAP 動作。 您可以透過下列方式指定的動作：  
  
   -   **使用單一動作格式**。 如果 「 WCF 自訂連接埠傳送和接收訊息的單一作業，請使用此格式。 例如：  
  
       ```  
       http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert  
       ```  
  
   -   **使用動作對應格式**。 如果單一 WCF 自訂連接埠傳送和接收多個作業的訊息，請使用此格式。 比方說，如果單一 WCF 自訂連接埠傳送或接收訊息 （若要將記錄插入的 EMP 資料表） 的 Op1 和 Op2 （若要更新的 EMP 資料表中的記錄），可以指定的 SOAP 動作以下列方式：  
  
       ```  
       <BtsActionMapping>  
         <Operation Name="Op1" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert" />  
         <Operation Name="Op2" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Update " />  
       </BtsActionMapping>  
       ```  
  
        此方法提供更大的彈性以指定的一組動作，並因此啟用訊息屬於不同的動作類型的流量通過相同的連接埠。  
  
        SOAP 動作的格式是針對每個作業不同。 如需有關每個作業的動作格式的詳細資訊，請參閱[訊息和訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)。  
  
#### <a name="enter-a-soap-action-for-the-wcf-oracledb-port"></a>輸入 Wcf-oracledb 連接埠的 SOAP 動作  
  
1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2. 新增 Wcf-oracledb 配接器至 BizTalk Server 管理主控台。 如需相關指示，請參閱 <<c0> [ 將 Oracle 資料庫配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md)。  
  
3. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用的程式在其下您想要建立連接埠，並按一下 **傳送埠**。 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  
  
4. 在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取您稍早新增 Wcf-oracledb 連接埠，然後按一下**設定**。  
  
5. 在  **Wcf-custom 傳輸屬性** 對話方塊中，按一下**一般** 索引標籤。  
  
6. 在 **動作**文字方塊中，指定作業的 SOAP 動作。 您可以透過下列方式指定的動作：  
  
   -   **使用單一動作格式**。 如果 Wcf-oracledb 連接埠傳送和接收訊息的單一作業，請使用此格式。 例如：  
  
       ```  
       http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert  
       ```  
  
   -   **使用動作對應格式**。 如果單一 Wcf-oracledb 連接埠傳送和接收多個作業的訊息，請使用此格式。 比方說，如果單一 Wcf-oracledb 連接埠傳送或接收訊息 （若要將記錄插入的 EMP 資料表） 的 Op1 和 Op2 （若要更新的 EMP 資料表中的記錄），可以指定的 SOAP 動作以下列方式：  
  
       ```  
       <BtsActionMapping>  
         <Operation Name="Op1" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert" />  
         <Operation Name="Op2" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Update " />  
       </BtsActionMapping>  
       ```  
  
        此方法提供更大的彈性以指定的一組動作，並因此啟用訊息屬於不同的動作類型的流量通過相同的連接埠。  
  
        SOAP 動作的格式是針對每個作業不同。 如需有關每個作業的動作格式的詳細資訊，請參閱[訊息和訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)。
  
## <a name="see-also"></a>另請參閱  
[若要開發與 Oracle 資料庫的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)