---
title: 步驟 1： 設定 FileAct 即時案例 SWIFT 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: afc52c63-9f83-4e90-9269-e90834b792bf
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 991d3d37bab70e07eb21b21a040e3479fc2658df
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25966077"
---
# <a name="step-1-configure-the-swift-adapter-for-the-fileact-real-time-scenario"></a>步驟 1： 設定 FileAct 即時案例 SWIFT 配接器
在開始此步驟之前，必須先完成[準備使用本教學課程](../../adapters-and-accelerators/fileact-interact/preparing-to-use-the-tutorial1.md)。  
  
### <a name="to-configure-the-swift-adapter"></a>若要設定 SWIFT 配接器  
  
1.  啟動**BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk Server 管理**、 依序展開 BizTalk 群組、 展開**平台設定**，依序展開**配接器**，以滑鼠右鍵按一下**FILEACT**，指向 **新增**，然後按一下 **傳送處理常式**。  
  
3.  在**FILEACT – 配接器處理常式屬性**對話方塊**一般**索引標籤上，從**主機名稱**下拉式清單中，選取**fileacthost**，然後按一下 **屬性**。  
  
4.  在**FILEACT 傳輸屬性**對話方塊**屬性**索引標籤上，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**引數**|輸入下列引數:-SagMessagePartner \<Fileact 用戶端訊息的夥伴建立 SAG\> **附註：** 引數中的用戶端是 MessagePartner SAG 中進行設定。|  
    |**密碼編譯模式**|從下拉式清單選取**進階**。|  
    |**FACryptoMode**|從下拉式清單選取**進階**。|  
    |**記錄訊息**|從下拉式清單選取**TRUE**。 這可讓要擷取，並在 BAM 入口網站中追蹤的訊息事件。|  
    |**啟用**|False|  
    |**事件端點**|輸入適當的 SAG 端點。|  
    |**PhysicalFolderName**|在伺服器上，輸入資料夾的名稱。 例如，C:\Fileact\ServerLocation。|  
    |**PollingInterval**|輸入適當的間隔 （以秒為單位） 之後，配接器會檢查的檔案傳輸的狀態。|  
    |**密碼**|輸入您用來連接到 SAG 的密碼。 如需詳細資訊，請參閱 SAG 說明。|  
    |**使用者名稱**|輸入您用來連接到 SAG 的使用者名稱。|  
  
5.  按一下**確定**關閉 FILEACT 傳輸屬性 對話方塊。  
  
6.  按一下**確定**關閉 FILEACT – 配接器處理常式屬性 對話方塊。  
  
7.  在訊息方塊中，按一下**確定**，然後重新啟動 FileAct 主控件執行個體。  
  
## <a name="see-also"></a>請參閱  
 [FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/fileact-real-time-scenario.md)   
 [步驟 2： 將 SWIFTNet 組態新增至 Paramfile FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-fileact-real-time-scenario.md)   
 [步驟 3： 建立傳送埠和接收埠以進行 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-3-create-the-send-ports-and-receive-ports-for-fileact-real-time-scenario.md)   
 [步驟 4：測試 FileAct 即時端對端案例](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-real-time-end-to-end-scenario.md)