---
title: 如何設定 MSMQ 傳送埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, send ports
- send ports, MSMQ adapters
- configuring [MSMQ adapters], send ports
ms.assetid: 37313d45-8148-4aaf-a3f2-ea05b3b8b448
caps.latest.revision: 29
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aad4a63a11f415c57778db726af0559858eab05c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992015"
---
# <a name="how-to-configure-an-msmq-send-port"></a>如何設定 MSMQ 傳送埠
您可以設定 MSMQ 傳送埠配接器變數[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 若未設定傳送埠的屬性，會使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中所設定的預設傳送處理常式值。  

> [!IMPORTANT]
>  如果主控件執行個體與 MSMQ 傳送埠或接收位置有關聯，請確認 MSMQ 服務是否正在該電腦上執行。 如果服務不在執行中，MSMQ 接收埠會在啟動後不久即關閉，並且傳送至 MSMQ 傳送埠的訊息也將被擱置。  
>   
>  在叢集化實例中，不但叢集化 MSMQ 執行個體必須正在執行，而且叢集電腦上的本機 MSMQ 服務也應該是在執行。  

## <a name="to-configure-variables-for-an-msmq-send-port"></a>設定 MSMQ 傳送埠的變數  
 請依照下列步驟，設定 MSMQ 傳送埠的變數：  

1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中，建立新的傳送埠，或按兩下現有的傳送埠進行修改。 請參閱[如何建立傳送埠](../core/how-to-create-a-send-port2.md)如需詳細資訊。 設定所有傳送埠選項。 在上**一般**索引標籤中，於**傳輸**區段中，指定**MSMQ**如**類型**選項。  

2. 在上**一般**索引標籤**傳輸**區段中，按一下**設定**旁邊**類型**。  

3. 在  **MSMQ 傳輸屬性**對話方塊方塊中，執行下列動作：  


   |            使用此屬性            |                                                                                                                            以進行此動作                                                                                                                            |  資料類型  | 預設值 |
   |-----------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|---------------|
   |              **密碼**               |                                                                                                 指定遠端佇列的密碼。 搭配使用**使用者名**。                                                                                                 |   String    |     空白     |
   |              **使用者名稱**              |                                                             指定遠端佇列的使用者名稱。 搭配使用**密碼**。 您不能使用遠端電腦的本機使用者做為使用者名稱。                                                             |   String    |     空白     |
   |        **通知類型**         | 指定「訊息佇列」要傳回傳送應用程式的通知訊息類型。 您可以選取一個以上的通知類型。 中的任何通知類型**System.Messaging.AcknowledgeTypes**列舉型別可用。 |   String    |     無      |
   |        **管理佇列**         |                                                                                                指定接收通知訊息的佇列名稱。                                                                                                 |   String    |     空白     |
   |              **內文類型**              |                                                                               在 MSMQ 中指定訊息內文類型。 有效值是.NET 的成員**VarEnum**列舉型別。                                                                               |     int     |     8209      |
   |       **憑證指紋**        |    指定要用於訊息驗證的憑證指紋。 使用這個屬性搭配**使用驗證**以驗證訊息的屬性。 使用**使用者名**並**密碼**屬性以取得佇列的存取權。     |   String    |     空白     |
   |          **目的地佇列**          |                     指定目的地佇列。 如需有關佇列的詳細資訊，請參閱 <<c0> [ 訊息佇列的佇列](../core/message-queuing-queues.md)。 **注意：** URI 傳送埠或接收位置不能超過 256 個字元。                      |   String    |     空白     |
   |        **加密演算法**         |                                                                                                選取  **RC2**， **RC4**，或**None**加密演算法。                                                                                                |    Enum     |     無      |
   | **訊息大小上限 （以 kb 為單位）** |                                                                                       指定傳送到指定佇列的訊息之訊息大小上限。                                                                                        | UnsignedInt |     1024      |
   |          **訊息優先順序**           |                                                                                                                    設定訊息優先順序。                                                                                                                     |    Enum     |    一般     |
   |             **可復原**             |                                                                                                  指定是否保證訊息的復原能力。                                                                                                   |   布林   |     False     |
   |        **支援分割**         |                                                                                        將此布林屬性值設定為 **，則為 True**區段訊息大於 4 MB。                                                                                         |   布林   |     False     |
   |               **逾時**               |                                                                    指定等待訊息到達目的地佇列的時間上限。 僅在使用交易時適用。                                                                     |     int     |       0       |
   |            **逾時單位**             |                                                                      設定要用於單位**逾時**屬性。<br /><br /> 選取 **天**，**小時**，**分鐘**，或**秒**。                                                                      |    Enum     |     Days      |
   |            **異動**            |                                                                                               將此值設定為 **，則為 True**來傳送訊息，如果您使用的交易。                                                                                               |   布林   |     False     |
   |         **使用驗證**          |     將此布林屬性值設定為 **，則為 True**以控制驗證。 使用這個屬性搭配**憑證指紋**以驗證訊息的屬性。 使用**使用者名**並**密碼**屬性以取得佇列的存取權。      |   布林   |     False     |
   |        **使用寄不出信件佇列**        |                                                                                    將此值設定為 **，則為 True**將訊息傳送至寄不出信件佇列，如果發生失敗。                                                                                     |   布林   |     True      |
   |          **使用日誌佇列**          |                                                                                   將此值設定為 **，則為 True**只要訊息已處理就儲存訊息的複本。                                                                                    |   布林   |     False     |


4. 按一下  **確定**並**確定**以儲存設定。  

## <a name="see-also"></a>另請參閱  
 [如何設定 MSMQ 接收位置](../core/how-to-configure-an-msmq-receive-location.md)   
 [設定 MSMQ 配接器](../core/configuring-the-msmq-adapter.md)