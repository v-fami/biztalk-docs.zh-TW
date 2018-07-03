---
title: 步驟 10： 驗證詢問式案例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interrogative tutorial, verifying solution
ms.assetid: 1f28800b-4a1d-4f29-8123-5cdea4b4a365
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e235ceddeb251a7182975dd54a128b33b4ee2be
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990783"
---
# <a name="step-10-verify-the-interrogative-scenario"></a>步驟 10： 驗證詢問式案例
在此步驟中，您可以確認的端對端案例在本教學課程。  
  
### <a name="to-send-the-query-message"></a>傳送查詢訊息  
  
1.  開啟命令提示字元。  
  
2.  在命令提示字元中，移至 **\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>HL7\SDK\MLLP 公用程式的加速器**。  
  
3.  在命令提示字元中，輸入**MllpReceive/P 24000**，然後按**Enter**。 這會執行接聽連接埠 24000 MLLP 接聽端應用程式，並顯示螢幕收到任何訊息。 此應用程式模擬醫院資訊系統。  
  
4.  開啟額外的命令提示字元。  
  
5.  在第二個 [命令提示字元] 視窗中，移至 **\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>HL7\SDK\MLLP 公用程式加速器**.  
  
6.  在第二個命令提示字元中，輸入**MllpSend /SB 11 /EB 28 /CR 13/TWOWAY/P 22000 /F 」\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>加速器 HL7\SDK\Interrogative Tutorial\QRY^Q01.txt**，然後按下**Enter。**  
  
    > [!NOTE]
    >  此命令會傳送查詢訊息，您建立在本教學課程中 MLLP 連接埠 22000 並等候回應 （通知） 的開頭。 ADT 接收埠會拾取此訊息，並予以處理。  
  
7.  確認您有下列結果：  
  
    -   MLLP 接聽端應用程式應該會顯示訊息，以使用下列值：  
  
        ```  
        MSH|^~\&|ADT||HIS||19990303||QRY^Q01|MSG00001|P|2.4  
        QRD|200307231012|D|I|4387|||20^LI|12233|RES|ALL  
        ```  
  
    -   颾魤 ㄛ MllpSend 公用程式會建立通知檔案中的\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\名為 QRY^Q01.txt.RESPONSE 詢問式教學課程的資料夾。 此檔案包含下列資訊通知：  
  
        ```  
        MSH|^~\&|HIS||ADT||20040331154031.2222-0800||ACK^Q01^ACK|10000GSM|P|2.4  
        MSA|CA|MSG00001  
        ****END ACK****  
        ```  
  
### <a name="to-send-the-response-message"></a>若要傳送回應訊息  
  
1. 在命令提示字元中執行 MllpReceive 應用程式，請按**Ctrl + C**取消先前的作業。  
  
2. 在命令提示字元中，輸入**MllpReceive/P 25000**，然後按**Enter**。  
  
   > [!NOTE]
   >  步驟 2 執行接聽連接埠 25000 MLLP 接聽端應用程式，並顯示螢幕收到任何訊息。 此應用程式模擬 ADT 系統。  
  
3. 在第二個命令提示字元中，輸入**MllpSend /SB 11 /EB 28 /CR 13/P 23000 /F 」\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator forHL7\SDK\Interrogative Tutorial\DSR.txt 」**，然後按**Enter**。  
  
   > [!NOTE]
   >  步驟 3 中，會將傳送您 MLLP 連接埠 23000 本教學課程開頭所建立的回應訊息。 HIS 接收埠會拾取此訊息，並予以處理。  
  
4. 確認您有下列結果：  
  
   -   MLLP 接聽端應用程式應該會顯示訊息，以使用下列值：  
  
       ```  
       MSH|^~\&|HIS||ADT||19990505||DSR^Q01|ZXT23469|P|2.4  
       MSA|AA|MSG00003  
       QRD|200307231012|D|I|4387|||20^LI|12233|RES|ALL  
       DSP|||RESULTS FOR PATIENT#12233 SMITH, JOHN H. 07/23/03  
       DSP|||SPECIMEN#H85 COLLECTED 07/22/03 /07/0/0  
       DSP|||ELECTROLYTES  
       DSP||| SODIUM 136 [135-148] MEQ/L STAT  
       DSP||| POTASSIUM 4.2 [3.5-5.0] MEQ/L STAT  
       DSP||| CHLORIDE 91 [95-111] MEQ/L STAT  
       DSP||| CO2 25 [20-30] MEQ/L STAT  
       DSP|||CO2 25 [20-30] MEQ/L STAT|LB  
       ```  
  
   > [!NOTE]
   >  如果未正確顯示上述的訊息，使用 「 狀況與活動追蹤 (HAT) 工具來疑難排解錯誤。  
  
   恭喜！ 您已順利完成 BTAHL7 詢問式教學課程。  
  
## <a name="see-also"></a>另請參閱  
 [批次處理教學課程](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md)   
 [端對端教學課程](../../adapters-and-accelerators/accelerator-hl7/end-to-end-tutorial1.md)   
 [訊息擴充教學課程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)