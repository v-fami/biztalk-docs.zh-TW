---
title: 如何設定 MQSeries 配接器接收位置和傳送埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MQSeries adapters, receive ports
- receive ports, MQSeries adapters
- MQSeries adapters, send ports
- configuring [MQSeries adapters], send ports
- configuring [MQSeries adapters], receive ports
- send ports, MQSeries adapters
- configuring [MQSeries adapters], receive locations
- MQSeries adapters, receive locations
- receive locations, MQSeries adapters
ms.assetid: 552aacde-9ec0-4459-b369-073676b6f926
caps.latest.revision: 29
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78de7ee2ac88dc0c000f4227e85659e9824b62ed
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006391"
---
# <a name="how-to-configure-mqseries-adapter-receive-locations-and-send-ports"></a>如何設定 MQSeries 配接器接收位置和傳送埠
您可以同時為接收位置和傳送埠設定 MQSeries 配接器。  

## <a name="to-configure-receive-locations-and-send-ports"></a>設定接收位置和傳送埠  
 **若要建立接收埠和接收位置：**  

1. 在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**，展開**BizTalk 群組**，展開**應用程式**，然後展開您想在其中建立接收位置的應用程式。  

2. 以滑鼠右鍵按一下**接收埠**節點中，按一下**新增，** ，並指向**單向接收埠**。  

3. 輸入適當的值，在**連接埠內容** 對話方塊。 如需**連接埠內容** 對話方塊中，請參閱[如何建立接收埠](../core/how-to-create-a-receive-port.md)。  

4. 在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**接收埠**節點，您建立，然後按一下**屬性**。  

5. 在**接收埠屬性**對話方塊的左窗格中，選取**接收位置**，然後按一下**新增**右窗格中。  

6. 在 **接收位置屬性**對話方塊的 **傳輸**區段旁邊**類型**，選取**MQSeries**從下拉式清單清單，然後再按**設定**。  

7. 在  **MQSeries 傳輸屬性**對話方塊方塊中，執行下列動作：  


   |        使用        |                                                                                                                                                                                                                                                                                                                                                                                                                             以進行此動作                                                                                                                                                                                                                                                                                                                                                                                                                             |
   |------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |     **批次大小**     | 決定一個訊息批次的大小上限 (以 KB 為單位)。 **注意：** 如果**支援的交易**接收位置的屬性設定為**是**; 每個訊息批次提交到 MessageBox 資料庫是 Microsoft 的內容分散式的交易協調器 (MSDTC) 交易。 在批次中的每個訊息都保存至 MessageBox 中，並置於適當的訂閱者佇列之前，為訊息批次建立的 MSDTC 交易仍會處於開啟狀態。 因此，此 MSDTC 交易的持續時間會增加為**批次大小上限**參數會增加。 有大量的 MSDTC 交易開啟同時對造成負面影響整體效能，因為**批次大小上限**啟用交易支援時，參數應該設定為非常大的值。 |
   | **排序的處理** |                                                                                                                                                                                                                                                                                         設定 MQSeries 在接收到 MQSeries 佇列的訊息時維護訊息順序。 **注意：** 為了維護特定佇列的訊息排序，只有一個 BizTalk 主控件執行個體可接收訊息從 MQSeries 佇列。 <br /><br /> **預設值：** False                                                                                                                                                                                                                                                                                          |
   |       **佇列**        |                                                                                                                                                                                                                                                                                                                                                     從資訊填入**佇列定義** 對話方塊。 **注意：** URI 傳送埠或接收位置不能超過 256 個字元。                                                                                                                                                                                                                                                                                                                                                      |
   |   **異動**    |                                                                                                                                                                                                                                                                                                                   配接器會開始 BizTalk Server 與 MQSeries Server 之間的 Microsoft Distributed Transaction Coordinator (DTC) 交易。 當設定為**No**，不保證訊息傳遞。<br /><br /> **預設值：** False                                                                                                                                                                                                                                                                                                                   |


8. 在  **MQSeries 傳輸屬性** 對話方塊中，按一下**確定**填入**位址 (URI)** 方塊中**接收位置屬性** 對話方塊。  

9. 在 **接收位置屬性**對話方塊方塊中，輸入適當的值，以完成接收位置的組態，然後按一下**確定**儲存設定。 如需**接收位置屬性** 對話方塊中，請參閱[如何建立接收位置](../core/how-to-create-a-receive-location.md)。  

   **若要建立傳送埠：**  

10. 在 [BizTalk Server 管理] 主控台中，建立新的靜態傳送埠。 請參閱[如何建立傳送埠](../core/how-to-create-a-send-port2.md)如需詳細資訊。 設定所有傳送埠選項，並指定**MQSeries** for**型別**選項**傳輸**一節**一般** 索引標籤。  

11. 在上**一般**索引標籤**傳輸**區段中，按一下**設定**旁邊**類型**。  

12. 在  **MQSeries 傳輸屬性**對話方塊方塊中，執行下列動作：  

    |屬性|描述|  
    |--------------|-----------------|  
    |**分割大小**|設定在配接器與 MQSAgent 之間傳送的訊息之訊息區塊大小 (以 KB 為單位)|  
    |**SSO 分支機構應用程式**|設定單一登入 (SSO) 分支機構應用程式。 使用者識別碼和密碼 sso 來**MQMD_UserIdentifier**，而**MQIIH_Authenticator** (或**MQCIH_Authenticator**) 屬性分別。<br /><br /> **預設值：** 空白|  
    |**資料轉換**|將訊息轉換為 MQSeries for Windows Server 的 ANSI 字碼頁。<br /><br /> 選取 **是**執行從 Unicode 轉換成 ANSI。<br /><br /> **預設值：** 否|  
    |**排序**|設定 MQSeries 在訊息傳送到 MQSeries 佇列時保持訊息的順序。<br /><br /> 選取 **是**以保持訊息順序。 **注意：** 您必須設定**Delivery Notification**您的協調流程中的屬性**傳輸**傳送埠。 <br /><br /> **預設值：** 否|  
    |**佇列定義**|來自資訊填入**佇列定義** 對話方塊中或直接在欄位中。 **注意：** URI 傳送埠或接收位置不能超過 256 個字元。|  
    |**允許的分割**|若個別訊息超過 MQSeries 佇列的訊息最大長度，則使用「MQSeries 佇列管理員」分割。 如果您選取**是**，MQSeries 會將分割的訊息放入佇列。<br /><br /> **預設值：** 否|  
    |**支援的交易**|配接器會開始 BizTalk Server 與 MQSeries Server 之間的 DTC (分散式交易協調器) 交易。 當設定為**No**，不保證訊息傳遞。<br /><br /> **預設值：** [是]**附註：** 並未使用不同設定傳送埠**交易支援**將訊息傳送至相同的 MQSeries 佇列的設定。 **注意︰** 除了測試案例，此屬性應一律設為預設值**是**。 設定這個屬性的值**No**在生產環境可能會導致無法預期的問題。|  

     下表顯示如何設定這些屬性。  

     ![MQSeries 傳輸屬性 對話方塊](../core/media/bts-dev-mqsendtransportprops.gif "BTS_Dev_MQSendTransportProps")  

13. 按一下省略符號 (**...**) 按鈕右邊**佇列定義**方塊，以定義佇列。 您可以使用**匯出**對話方塊中，就像您可能與接收位置，立即建立佇列，或將匯出定義佇列的指令碼。  

14. 按一下 **確定**在每個對話方塊中，以關閉對話方塊並儲存設定。  

    **若要登錄的傳送埠、 啟動傳送埠，並啟用接收位置：**  

15. 以滑鼠右鍵按一下傳送埠，然後按一下 **登錄**登錄傳送埠。  

16. 以滑鼠右鍵按一下傳送埠，然後按一下 **啟動**啟動傳送埠。  

17. 以滑鼠右鍵按一下接收位置，然後按一下 **啟用**來啟用接收位置。  

18. 檢視事件記錄檔，以確認沒有 BizTalk Server 錯誤。  

## <a name="see-also"></a>另請參閱  
 [如何設定 MQSeries 配接器傳送和接收處理常式](../core/how-to-configure-mqseries-adapter-send-and-receive-handlers.md)   
 [設定 MQSeries 配接器](../core/configuring-the-mqseries-adapter.md)