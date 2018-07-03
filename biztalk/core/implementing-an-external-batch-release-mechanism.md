---
title: 實作外部批次釋放機制 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5633a448-cc29-4931-a3ad-206ae25c989b
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 298857d60662bbe2240a5cfb6cc797e4fda7abdb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010367"
---
# <a name="implementing-an-external-batch-release-mechanism"></a>實作外部批次釋放機制
您可以使用外部釋放觸發程序來觸發釋放批次。 您可讓後端的企業營運系統應用程式在達到特定的臨界值時，自動觸發釋放。 這項機制是除了會自動觸發批次釋放，由排程或交易集或字元計數，或手動觸發批次，依序按一下**覆寫**按鈕**批次設定**頁面的單向協議索引標籤。  
  
 若要實作外部釋放觸發程序，您必須設定接收埠和位置來處理 OverrideControlMessage。 接收位置必須使用 `Edi.BatchControlMessageRecvPipeline` 接收管線。 這是相同的管線，以供 BatchControlMessageRecvLoc 接收位置，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]用來處理手動覆寫的訊息。 不過，BatchControlMessageRecvLoc 是 SQL 類型的接收位置，而您為外部釋放觸發程序設定的接收位置則可使用任何配接器類型。  
  
 外部批次釋放是由 XML 控制訊息觸發的。 若要觸發批次，後端應用程式需要將控制訊息路由傳送至接收位置。 您可以修改控制訊息來啟動、覆寫或終止批次。 請參閱下面建立控制訊息的程序。  
  
 若要啟用外部釋放觸發程序，您必須選取**外部釋放觸發程序**中的屬性**批次組態**頁面**協議屬性**對話方塊針對 X12 或 EDIFACT 的方塊。 此屬性指示批次發行時必須有外部發行訊息。 **覆寫** 按鈕，**停止** 按鈕，並**啟用**範圍控制項仍然會有效如果**外部釋放觸發程序**屬性已選取。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-create-a-receive-location-for-the-external-batch-release-trigger-message"></a>若要建立外部批次釋放觸發程序訊息的接收位置  
  
1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中，建立單向接收埠。 如需有關如何建立接收埠的指示，請參閱 <<c0> [ 如何建立接收埠](../core/how-to-create-a-receive-port.md)。  
  
2. 在接收埠中建立單向接收位置。  
  
3. 選取傳輸類型。 您可以為這個接收位置選取任何類型。 一般是選取 [FILE] 類型，然後輸入接收檔案的資料夾。  
  
4. 若是接收管線，選取 `BatchControlMessageRecvPipeline`。  
  
5. 按一下 [確定] 。  
  
### <a name="to-create-the-external-batch-release-trigger-message"></a>若要建立外部批次釋放觸發程序訊息  
  
1. 在 [記事本] 中建立新檔案，命名時以 .xml 為副檔名。  
  
2. 將下列程式碼加入至此檔案中：  
  
   ```  
   <?xml version="1.0" encoding="utf-8"?>  
   <ControlMessage xmlns="http://SQLControlMessage.IssueSelect">  
     <PAM_Control xmlns="http://SQLControlMessage.IssueSelect">  
       <DestinationParty>[Party ID]</DestinationParty>  
       <EdiMessageType>[0 for X12\HIPAA|1 for Edifact]</EdiMessageType>  
       <ActionType>EdiBatchOverride</ActionType>  
       <ActionDateTime>[yyyy-mm-ddThh:mm:ss.sss]</ActionDateTime>  
       <UsedOnce>0</UsedOnce>  
       <BatchId>[Batch ID]</BatchId>  
       <BatchName>[Batch Name]</BatchName>  
       <DestinationPartyName>[Destination Party/Partner name]</DestinationPartyName>  
       <SenderPartyName>[Sender Party/Partner name]</SenderPartyName>  
       <AgreementName>[Agreement Name]</AgreementName>  
       <ReceiverPartyNameType>[Receiver Party/Partner name]</ReceiverPartyNameType>  
       <ToBeBatched>1</ToBeBatched>  
     </PAM_Control>  
   </ControlMessage>  
   ```  
  
    取代以上節錄的值，如下所示：  
  
   - 指定的動作類型。 通常**ActionType**必須設為**EdiBatchOverride**覆寫在 「 合約 」 中完成的批次設定。 您也可以將這設**EdiBatchTerminate**終止批次透過外部觸發程序。  
  
     > [!NOTE]
     >  Microsoft 建議您不要使用外部釋放觸發程序啟動批次。 因此，您不應指定**ActionType**作為**EdiBatchActivate**。  
  
   - 決定批次識別碼和批次名稱。 若要這樣做，請開啟**協議屬性**對話方塊方塊，然後在單向協議 索引標籤中，按一下**批次組態**。 按一下索引標籤，以覆寫輸入的值之批次**批次名稱**並**批次識別碼**欄位到**BatchName**並**BatchID**節點的 「 控制 」 訊息。  
  
   - 指定目的地合作對象名稱。 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下**合作對象** 節點，以及從**合作對象與商務設定檔**頁面上，取得批次接收合作對象/夥伴名稱交換。 輸入中的名稱**ReceiverPartyNameType**控制訊息的節點。  
  
   - 指定傳送者合作對象名稱。 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下**合作對象** 節點，以及從**合作對象與商務設定檔**頁面上，取得將用來傳送批次的交換的合作對象/夥伴名稱. 輸入中的名稱**SenderPartyName**控制訊息的節點。  
  
   - 指定合約名稱。 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下 **合作對象** 節點，並從**合作對象與商務設定檔**頁面上，於**協議** 區段中，以滑鼠右鍵按一下具有批次組態，必須要使用來覆寫 「 控制 」 訊息，然後按一下協議**屬性**。 在 **協議屬性**對話方塊中，於**一般**索引標籤**一般屬性**頁面上，複製的值**名稱**欄位**協議參數**區段，然後將它貼在**AgreementName**控制訊息的節點。  
  
   > [!NOTE]
   >  您不需要指定目的地合作對象識別碼。 在 「 控制 」 訊息僅為回溯相容性被必要項目。  
  
3. 儲存檔案。  
  
### <a name="to-enable-the-external-release-trigger"></a>若要啟用外部釋放觸發程序  
  
1. 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下 **合作對象** 節點，並從**合作對象與商務設定檔**頁面上，於**協議** 區段中，以滑鼠右鍵按一下具有批次組態，必須要使用來覆寫 「 控制 」 訊息，然後按一下協議**屬性**。 在 **協議屬性** 對話方塊中，於單向協議 索引標籤中，按一下**批次組態**。  
  
2. 在 **批次組態**頁面上，按一下您想要有外部釋放觸發程序，然後在批次的索引標籤**Release**區段中，選取**外部釋放觸發程序**.  
  
3. 按一下 [確定] 。  
  
## <a name="see-also"></a>另請參閱  
 [設定 EDI 批次](../core/configuring-edi-batches.md)   
 [如何建立接收位置](../core/how-to-create-a-receive-location.md)