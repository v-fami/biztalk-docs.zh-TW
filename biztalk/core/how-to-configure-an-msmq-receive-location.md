---
title: "如何設定 MSMQ 接收位置 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, receive locations
- receive locations, MSMQ adapters
- configuring [MSMQ adapters], receive locations
ms.assetid: ba25cf43-18f1-4c19-84fb-74c7b82b95a9
caps.latest.revision: "43"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3a59e64c93e908fce7590f885fe8c38e3a51cf4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-an-msmq-receive-location"></a>如何設定 MSMQ 接收位置
您可以在 [BizTalk Server 管理] 主控台中設定 MSMQ 接收位置配接器變數。 若未在接收位置設定屬性，則會使用在 [BizTalk Server 管理] 主控台中設定的預設接收處理常式值。  
  
> [!NOTE]
>  完成下列程序之前，您必須已經新增接收埠。 如需詳細資訊，請參閱[如何建立接收埠](../core/how-to-create-a-receive-port.md)。  
  
> [!IMPORTANT]
>  如果主控件執行個體與 MSMQ 傳送埠或接收位置有關聯，請確認 MSMQ 服務是否正在該電腦上執行。 如果服務不在執行中，MSMQ 接收埠會在啟動後不久即關閉，並且傳送至 MSMQ 傳送埠的訊息也將被擱置。  
>   
>  在叢集化實例中，不但叢集化 MSMQ 執行個體必須正在執行，而且叢集電腦上的本機 MSMQ 服務也應該是在執行。  
  
## <a name="to-configure-variables-for-an-msmq-receive-location"></a>設定 MSMQ 接收位置的變數  
 請依照下列步驟，設定 MSMQ 接收位置的變數：  
  
1.  在 BizTalk Server 管理主控台中，展開  **BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開您想要在其中建立接收位置的應用程式。  
  
2.  在 BizTalk Server 管理主控台中，在左窗格中，按一下 **接收埠**節點。 然後在右窗格中，使用滑鼠右鍵按一下與現有接收位置關聯的接收埠，或是您要與新接收位置關聯的接收埠，然後按一下 **[屬性]**。  
  
3.  在**接收埠屬性**對話方塊的左窗格中，選取**接收位置**，然後在右窗格中，按兩下現有接收位置或按一下**新增**以建立新接收位置。  
  
4.  在**接收位置屬性**對話方塊中，於**傳輸**區段旁邊**類型**，選取**MSMQ**從下拉式清單中，然後按一下 **設定**。  
  
5.  在**MSMQ 傳輸屬性**對話方塊方塊中，執行下列動作：  
  
    |使用|動作|資料型別|預設值|  
    |--------------|----------------|---------------|-------------------|  
    |**密碼**|設定要用於遠端佇列的密碼。|字串|空白|  
    |**使用者名稱**|決定要用於存取遠端佇列的使用者名稱與密碼。 您不能使用遠端電腦的本機使用者做為使用者名稱。|字串|空白|  
    |**批次大小**|設定批次大小。 MSMQ 配接器以批次方式提交訊息到 MessageBox 資料庫。 預設批次大小為 20，批次大小下限為 1。 **注意：**如果**交易式**接收位置的屬性設定為**True**; 每個訊息批次提交至 MessageBox 資料庫的 Microsoft Distributed 身分交易協調器 (MSDTC) 交易。 在批次中的每個訊息都保存至 MessageBox 中，並置於適當的訂閱者佇列之前，為訊息批次建立的 MSDTC 交易仍會處於開啟狀態。 因此，此 MSDTC 交易的持續時間會增加為**批次大小**參數會增加。 同時有大量的 MSDTC 交易開啟對造成負面影響整體效能，因為**批次大小**啟用交易支援時，參數應該設定為非常大的值。|int|20|  
    |**失敗**|指定配接器如何回應錯誤。 將這個屬性設為下列其中一個值：<br /><br /> -   **停止。** 若發生錯誤狀況，則透過這個接收位置停止接收訊息。<br />-   **Suspend(non-resumable)。** 擱置訊息並標示為不可繼續。<br />-   **Suspend(resumable)。** 擱置訊息並標示為可繼續。 **重要事項：**如果**True**選項**排序的處理**屬性，**停止**選項**失敗**屬性，而**False**選項**交易式**屬性會套用在相同的時間，則不會暫止或留在來源佇列無法傳送任何訊息。 在此實例中，可能會發生訊息遺失。 若要使用時防止資料遺失，**排序的處理**功能，**停止**選項**失敗**屬性應該只會套用，如果**，則為 True**選項**交易式**屬性會套用。 接著，若發生訊息傳送失敗，原始訊息將會保留在來源 MSMQ 佇列中。 如果**排序的處理**屬性設定的值為**False**則**失敗**屬性將不會生效，且訊息傳遞失敗發生訊息將擱置狀態為**已擱置 （可繼續）**。|字串|擱置 (可繼續)|  
    |**排序的處理**|將此屬性設定為**True**或**False**。 指示是否連續處理訊息。 將屬性設定為**True**會容納已排序的訊息傳遞的 BizTalk 傳訊 」 或 「 協調流程傳送埠搭配使用時**排序的傳遞**選項設為**True**。 如需詳細資訊，請參閱[排序訊息傳遞](../core/ordered-delivery-of-messages.md)。<br /><br /> 此屬性設定為**True**藉由將配接器單一執行緒處理大型訊息時，也會最佳化資源使用狀況。 如需詳細資訊，請參閱[傳送和接收大型訊息使用 MSMQ 配接器](../core/sending-and-receiving-large-messages-using-the-msmq-adapter.md)。|布林|False|  
    |**佇列**|輸入有效的佇列路徑。 系統將根據您指定的佇列路徑執行適當的驗證。 **注意：** URI 傳送埠或接收位置不能超過 256 個字元。 **注意：** MSMQ 接收配接器來監視新訊息的指定的 MSMQ 佇列每 0.5 秒鐘使用輪詢機制。 這個 0.5 秒間隔是固定的間隔。|字串|空白|  
    |**異動**|將此屬性設定為**True**或**False**。 **注意：**配接器支援與訊息佇列 4.0 或更新版本的遠端佇列的交易式讀取。 在此案例中這兩個[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]和遠端的訊息佇列伺服器必須執行訊息佇列 4.0 或更新版本。 <br /><br /> 如需詳細資訊，請參閱[設定 MSMQ 配接器](../core/configuring-the-msmq-adapter.md)和[叢集主控件中執行配接器處理常式的考量](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)。|布林|False|  
  
    > [!NOTE]
    >  **使用者名**和**密碼**只會套用到用來存取遠端佇列的 Windows 帳戶。  
  
6.  按一下 **[確定]**。  
  
7.  在**接收位置屬性**對話方塊方塊中，輸入適當的值，以完成接收位置組態，然後按一下**確定**儲存設定。 如需有關資訊**接收位置屬性**對話方塊中，請參閱[如何建立接收位置](../core/how-to-create-a-receive-location.md)。  
  
## <a name="see-also"></a>另請參閱  
 [設定 MSMQ 配接器](../core/configuring-the-msmq-adapter.md)