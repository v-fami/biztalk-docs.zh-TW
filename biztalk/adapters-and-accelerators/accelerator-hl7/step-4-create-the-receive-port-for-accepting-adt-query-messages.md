---
title: 步驟 4： 建立接收埠，以便接受 ADT 查詢訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interrogative tutorial, receive ports
ms.assetid: 8bef032f-5f43-4d36-b88f-ed81f27bb803
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 301215ea32b992516bfead3cd77ecdb009087bb8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-create-the-receive-port-for-accepting-adt-query-messages"></a>步驟 4： 建立接收埠，以便接受 ADT 查詢訊息
建立接收埠以指定許可，放電，所傳送的連入查詢訊息的位置和傳送 (ADT) 系統。 使用下列程序來建立接收埠，以便接受查詢 (QRY ^ Q01 訊息) 從 ADT 系統使用最少的較低層通訊協定 (MLLP) 配接器。  
  
## <a name="create-the-adtreceiveport-receive-port"></a>建立 ADT_ReceivePort 接收埠  
  
1.  開啟**BizTalk Server 管理**，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開**BizTalk Application 1**。  
  
2.  以滑鼠右鍵按一下**接收埠**，選取**新增**，然後選取**要求回應接收埠**。  
  
3.  如**名稱**，輸入**ADT_ReceivePort**。  
  
4.  選取**套用**連接埠，繫結，然後選取**接收位置**。  
  
5.  選取**新**。 
  
6.  如**名稱**，輸入**ADT_Receive**。  

7. 在**傳輸**區段中，選取**類型**，然後選取**MLLP**從下拉式清單。  
  
8. 選取 **[設定]**。 在**MLLP 傳輸屬性**，設定下列項目，並選取**確定**。  
  
    |使用|動作|  
    |---|---|  
    |**連接重試時間 （秒）**|新開頭[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]。 <br/><br/>若要嘗試重新連接已卸除或關閉連接之前等候的時間上限。 適用於**連線由起始**設**本機**。<br/><br/>預設值為 20 秒。|
    |**所起始的連線**| 新開頭[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]。 <br/><br/>輸入**本機**MLLP 的接收位置，以起始遠端的 LOB 伺服器的連線。 這是新的選項。<br/><br/>輸入**遠端**MLLP 的接收位置，以繼續接聽來自遠端的 LOB 伺服器連線。 這是相容的預設選項。<br/><br/>預設值為遠端。| 
    |**連接名稱**|輸入**ADT_ReceiveMLLP**。|  
    |**主機名稱**|特定[!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)]和較舊的版本。 <br/><br/>輸入**localhost**。|  
    |**本機主機名稱**|新開頭[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]。 <br/><br/>輸入的 DNS 名稱或 IP 位址的本機[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]。 您也可以輸入**localhost**。|  
    |**[通訊埠]**|特定[!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)]和較舊的版本。 <br/><br/>設定為**22000**。|  
    |**本機連接埠**|新開頭[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]。 <br/><br/>輸入 LocalHost 連接的 TCP 通訊埠編號。 時才適用**連線由起始**是**遠端**。 <br/><br/>設定為**22000**。|
    |**遠端主機**|新開頭[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]。 <br/><br/>輸入的 DNS 名稱或遠端的 LOB 伺服器 IP 位址。 適用於**連線由起始**設**本機**。|  
    |**遠端連接埠**|新開頭[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]。 <br/><br/>輸入遠端主機連接的 TCP 通訊埠編號。 適用於**連線由起始**設**本機**。<br/><br/>設定為**22000**。|  

9. 設定**接收處理常式**至**BizTalkServerApplication**。  
  
10. 設定**接收管線**至**BTAHL72XPipelines.BTAHL72XReceivePipeline**。  

11. 設定**傳送管線**至**PassThruTransmit**。
  
11. 選取 [確定] 儲存您的變更。  
  
12. 啟用您以滑鼠右鍵按一下它，建立接收位置，然後選取**啟用**。  

## <a name="next-step"></a>下一步  
[步驟 5： 建立接收埠，以便接受他的訊息](../../adapters-and-accelerators/accelerator-hl7/step-5-create-the-receive-port-for-accepting-his-messages.md)