---
title: 步驟 10： 驗證端對端案例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- end-to-end tutorial, verifying solution
ms.assetid: 24b74ba6-e303-4ab1-8a93-25a430e4894d
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43d95e54bbcf0c7c716630305b85ba8b9bed1a52
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990343"
---
# <a name="step-10-verify-the-end-to-end-scenario"></a>步驟 10： 驗證端對端案例
在此步驟中，您可以確認的端對端案例在本教學課程。  
  
### <a name="to-verify-the-end-to-end-tutorial-scenario"></a>若要確認端對端教學課程案例  
  
1. 按一下 **開始**，指向**程式**，指向**附屬應用程式**，然後按一下**命令提示字元**。  
  
2. 在 [命令提示字元] 視窗中，移至 **\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\MLLP 公用程式**，然後按下**Enter**。  
  
   > [!NOTE]
   >  如果找不到 SDK 資料夾下的 MLLP 公用程式 資料夾，可能不會安裝 MLLP 測試工具。 開啟 [控制台] 中，然後開啟**新增或移除程式**。 選取  **Microsoft BizTalk\<版本\>Accelerator for HL7**，然後選取**變更**。 在 [BTAHL7 安裝程式精靈] 中，選取**修改**。 依序展開**配接器**資料夾，以查看是否**MLLP 測試工具**已安裝。 否則，請安裝它。  
  
3. 在 [命令提示字元] 視窗中，輸入**mllpreceive/p 14000**，然後按**Enter**。 這會執行 MLLP 接聽端應用程式接聽連接埠 14000，並指定預設 EB、 SB 和 CR 字元 MLLP 的訊息，並顯示螢幕收到任何訊息。  
  
4. 按一下 啟動額外的命令提示字元**開始**，指向**程式**，指向**附屬應用程式**，然後按一下 **命令提示字元**.  
  
5. 在第二個 [命令提示字元] 視窗中，移至 **\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>HL7\SDK\MLLP 公用程式加速器**，然後按下**Enter**。  
  
   > [!NOTE]
   >  下列步驟將訊息傳送。  
  
6. 在 [命令提示字元] 視窗中，輸入**mllpsend /SB 11 /EB 28 /CR 13 /f 」\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\端對端 Tutorial\ADT ^ A03.txt 」**，其中\<*磁碟機*\>是您的安裝磁碟機代號。 按 **Enter**鍵。  
  
7. 確認您有下列結果：  
  
   -   MLLP 接聽端應用程式應該會顯示一則訊息。 訊息的第一行應該有下列值：  
  
       ```  
       MSH|^~\&|BTAHL7^IE^UUID|MCM|HI^System^GUID||199601121005||ADT^A04|000001|P|2.4|||SU|NE  
       ```  
  
   -   訊息會出現在\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>HL7\SDK\End 端對端 Tutorial\Tutorial_sendMsg_RX 的加速器。 此訊息應該由 MLLP 接聽端應用程式所顯示的訊息相同。 確認訊息的第一行有相同的訊息值，如下所示。 請注意 MSH3 nd MSH5 下列程式碼中的值符合您指定 Tutorial_RXSystem 的值：  
  
       ```  
       MSH|^~\&|BTAHL7|MCM|Tutorial_RXSystem||199601121005||ADT^A03|000001|P|2.3.1  
       ```  
  
   -   兩個訊息都會出現在\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>HL7\SDK\End 端對端 Tutorial\Tutorial_sendAck_ADT 的加速器。 其中一個訊息是應用程式通知;另一個是認可通知。 應用程式通知應該具有下列內容：  
  
       ```  
       MSH|^~\&|BTAHL7InterfaceEngine||Tutorial_ADTSystem|MCM|<datetime>||ACK^A03^ACK|000001|P|2.3.1|||AL  
       MSA|AA|000001  
       ```  
  
   -   認可通知應該具有下列內容：  
  
       ```  
       MSH|^~\&|BTAHL7InterfaceEngine||Tutorial_ADTSystem|MCM|<datetime>||ACK^A03^ACK|100000|P|2.3.1  
       MSA|CA|000001  
       ```  
  
   > [!NOTE]
   >  如果訊息未正確顯示，使用 「 狀況與活動追蹤 (HAT) 工具來疑難排解錯誤。  
  
   恭喜！ 您已順利完成 BTAHL7 端對端教學課程。  
  
## <a name="see-also"></a>另請參閱  
 [端對端教學課程](../../adapters-and-accelerators/accelerator-hl7/end-to-end-tutorial1.md)