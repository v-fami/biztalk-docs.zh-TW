---
title: 步驟 18： 測試您的新訊息擴充方案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message enrichment tutorial, testing solution
ms.assetid: 233fbf79-0ab1-4064-b828-6bbbb56cbec2
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 035925684617e74608246aed99fa98e16d0668a4
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="step-18-test-your-new-message-enrichment-solution"></a>步驟 18： 測試您的新訊息擴充方案
在此步驟中，您必須測試方案利用 WSClient 應用程式來傳送訊息給[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]以及查看 MLLPReceive 應用程式是否會如預期般收到 HL7 格式化的訊息。  
  
### <a name="to-test-your-solution"></a>若要測試您的方案  
  
1.  開啟命令提示字元。  
  
    > [!NOTE]
    >  步驟 2 需要您已安裝使用的自訂安裝程序的 MLLP 測試工具。 如果您的電腦沒有目錄包含 MllpReceive.exe 和 MllpSend.exe \MLLP 公用程式就會將其安裝藉由執行自訂安裝。 如需資訊，請參閱[執行自訂安裝](http://msdn.microsoft.com/library/e55c86e1-af63-49ba-8510-d177e1b96692)。  
  
2.  在命令提示字元中，輸入**cd \<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\MLLP 公用程式**(其中\<*磁碟機*\>是您安裝的磁碟機代號)，然後按下**Enter**。  
  
3.  在命令提示字元中，輸入**mllpreceive/p 11000 /eb 11 /sb 28 /cr 13**，然後按下**Enter**。 這會執行 MLLP 接聽應用程式接聽連接埠 11000，並指定預設 EB、 SB 和 CR 字元 MLLP 的訊息，並顯示螢幕收到任何訊息。  
  
4.  開啟第二個命令提示字元。  
  
5.  在命令提示字元中，輸入**cd \<*磁碟機*\>: \Tutorial\WSClient\bin\Debug**，然後按下**Enter**。  
  
6.  在命令提示字元中，輸入**wsclient john henry smith 123456789**，然後按下**Enter**。 這會傳送訊息至 Web 服務，其中包含範例訊息為 John Henry Smith 病患名稱，且 123456789 範例社會安全號碼號碼。  
  
7.  短暫的延遲之後 MLLPReceive 應用程式會顯示內送 MLLP 訊息。 訊息看起來應該如下所示：  
  
    ```  
    MSH|^~\&|TestTrailing^Delimiters|srcFac^srcFacUid|dstApp^dstAppUid|dstFac^dstFacUid|200307092343|sec|ADT^A04|msgid2134|P|2.2PID|||123456789||smith^john  
    ```  
  
     如果您沒有收到回應後幾分鐘的時間，您應該檢查應用程式事件記錄檔有任何錯誤，並開始進行疑難排解。  
  
## <a name="see-also"></a>另請參閱  
 [訊息擴充教學課程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)