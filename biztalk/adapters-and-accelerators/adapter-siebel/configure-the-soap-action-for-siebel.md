---
title: "在 BizTalk 中設定 Siebel 配接器的 SOAP 動作 |Microsoft 文件"
description: "在 Visual Studio 中，輸入 SOAP 動作，或使用 Wcf-custom 或 Wcf-siebel 配接器在 BizTalk 配接器組件 (BAP)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f22a4691-0355-4f08-a14e-e90a3c987ac0
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b851aa0b26d80a43f5a839232298ace5507f471b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-soap-action-for-siebel"></a>設定 Siebel 的 SOAP 動作
若要執行使用 WCF 型 Siebel 系統中的任何作業[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，配接器使用者必須指定 SOAP 動作。 SOAP 動作與外界溝通的配接器應該執行哪些動作。 您可以指定在設計階段或執行階段的 SOAP 動作。 不過，如果您指定的 SOAP 動作這兩個設計階段和執行階段，則會覆寫您在設計階段指定的動作。  
  
 如需指定 SOAP 動作的詳細資訊，請參閱[指定 WCF 傳送配接器的 SOAP 動作](../../core/specifying-soap-actions-for-wcf-send-adapters.md)。
  
## <a name="enter-soap-action-at-design-time"></a>輸入在設計階段的 SOAP 動作  
 設計階段，您必須指定的 SOAP 動作協調流程包括 「 運算式 」 圖形。  
  
1.  在 BizTalk 協調流程 「 運算式 」 圖形，藉以加入將它從**BizTalk 協調流程**工具箱。  
  
2.  按兩下**運算式**圖形以開啟 BizTalk 運算式編輯器。  
  
3.  在 BizTalk 運算式編輯器 」 中指定的動作。 例如：  
  
    ```  
    OutboundMessage(WCF.Action)="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert"  
    ```  
  
     如需有關**運算式**圖形和 BizTalk 運算式編輯器，請參閱[如何建立運算式](../../core/how-to-create-expressions.md)。  
  
## <a name="enter-soap-action-at-run-time"></a>在執行階段輸入 SOAP 動作  
 執行階段，您必須指定 Wcf-custom 或 Wcf-siebel 連接埠屬性 對話方塊的一部分的 SOAP 動作。  
  
#### <a name="enter-a-soap-action-for-the-wcf-custom-port"></a>輸入 WCF 自訂連接埠的 SOAP 動作  
  
1.  啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後按一下 **傳送埠**。 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  
  
3.  在 連接埠屬性 對話方塊中，從**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。  
  
4.  在**Wcf-custom 傳輸屬性**對話方塊中，按一下 [**一般**] 索引標籤。  
  
5.  在**動作**文字方塊中，指定作業的 SOAP 動作。 您可以下列方式指定的動作：  
  
    -   **使用單一動作格式**。 如果 WCF 自訂連接埠傳送和接收訊息的單一作業，請使用此格式。 例如：  
  
        ```  
        http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert  
        ```  
  
    -   **使用動作對應格式**。 如果單一 WCF 自訂連接埠傳送和接收多個作業的訊息，請使用此格式。 例如，如果單一 WCF 自訂連接埠傳送與接收訊息 （若要執行插入作業帳戶商務元件上的） Op1 和 Op2 （於執行帳戶商務元件上的更新作業），SOAP 動作可以指定下列方式：  
  
        ```  
        <BtsActionMapping>  
          <Operation Name="Op1" Action="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert " />  
          <Operation Name="Op2" Action="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Update " />  
        </BtsActionMapping>  
        ```  
  
         此方法提供更大彈性，以指定的一組動作，因此啟用流經的相同連接埠屬於不同的動作類型的訊息。  
  
         SOAP 動作的格式是不同的每一項作業。 如需每個作業的動作格式的詳細資訊，請參閱[訊息與訊息結構描述](messages-and-message-schemas-for-siebel-adapter-in-biztalk.md)。
  
#### <a name="enter-a-soap-action-for-the-wcf-siebel-port"></a>輸入 Wcf-siebel 連接埠的 SOAP 動作  
  
1.  啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2.  新增 Wcf-siebel 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如需指示，請參閱[新增 Siebel 配接器至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md)。  
  
3.  在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後按一下 **傳送埠**。 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  
  
4.  在 [連接埠屬性] 對話方塊中，從**類型**下拉式清單中，選取 Wcf-siebel 配接器，您將較舊版本，然後再按一下**設定**。  
  
5.  在 連接埠屬性 對話方塊中，按一下**一般** 索引標籤。  
  
6.  在**動作**文字方塊中，指定作業的 SOAP 動作。 您可以下列方式指定的動作：  
  
    -   **使用單一動作格式**。 如果 WCF 自訂連接埠傳送和接收訊息的單一作業，請使用此格式。 例如：  
  
        ```  
        http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert  
        ```  
  
    -   **使用動作對應格式**。 如果單一 WCF 自訂連接埠傳送和接收多個作業的訊息，請使用此格式。 例如，如果單一 WCF 自訂連接埠傳送與接收訊息 （若要執行插入作業帳戶商務元件上的） Op1 和 Op2 （於執行帳戶商務元件上的更新作業），SOAP 動作可以指定下列方式：  
  
        ```  
        <BtsActionMapping>  
          <Operation Name="Op1" Action="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert " />  
          <Operation Name="Op2" Action="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Update " />  
        </BtsActionMapping>  
        ```  
  
         此方法提供更大彈性，以指定的一組動作，因此啟用流經的相同連接埠屬於不同的動作類型的訊息。  
  
         SOAP 動作的格式是不同的每一項作業。 如需每個作業的動作格式的詳細資訊，請參閱[訊息與訊息結構描述](messages-and-message-schemas-for-siebel-adapter-in-biztalk.md)。
  
## <a name="see-also"></a>另請參閱  
[若要建立 Siebel 配接器的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)