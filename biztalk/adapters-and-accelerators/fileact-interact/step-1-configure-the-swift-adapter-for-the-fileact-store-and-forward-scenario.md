---
title: 步驟 1： 設定為 FileAct 存放與轉寄實例 SWIFT 的配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18653322-b748-4954-93f7-9a7a39e406f8
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3e2883bb75667d2ad2518a4b8bf0c2a90be79ec8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25964276"
---
# <a name="step-1-configure-the-swift-adapter-for-the-fileact-store-and-forward-scenario"></a>步驟 1： 設定為 FileAct 存放與轉寄實例 SWIFT 的配接器
完成[準備使用本教學課程](../../adapters-and-accelerators/fileact-interact/preparing-to-use-the-tutorial1.md)開始此步驟之前。
  
## <a name="configure-the-swift-adapter"></a>設定 SWIFT 配接器  
  
1.  啟動**BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk Server 管理**、 依序展開 BizTalk 群組、 展開**平台設定**，依序展開**配接器**，以滑鼠右鍵按一下**FILEACT**，指向 **新增**，然後按一下 **傳送處理常式**。  
  
3.  在**FILEACT – 介面卡 HandlerProperties**對話方塊**一般**索引標籤上，從**主機名稱**下拉式清單中，選取**fileacthost**，然後按一下 **屬性**。  
  
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
  
## <a name="complete-steps"></a>完成步驟
 [FileAct 存放與轉寄的案例](../../adapters-and-accelerators/fileact-interact/fileact-store-and-forward-scenario.md)   
 [步驟 2： 加入為 FileAct 存放與轉寄實例 Paramfile SWIFTNet 組態](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-fileact-store-and-forward.md)   
 [步驟 3： 建立傳送埠和接收埠為 FileAct 存放與轉寄的實例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-ports-and-receive-ports-for-the-fileact-store-and-forward.md)   
 [步驟 4：測試 FileAct 儲存和轉寄端對端案例](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-store-and-forward-end-to-end-scenario.md)