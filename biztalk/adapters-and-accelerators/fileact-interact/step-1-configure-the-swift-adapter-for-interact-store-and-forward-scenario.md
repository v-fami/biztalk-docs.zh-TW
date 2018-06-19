---
title: 步驟 1： 設定 SWIFT 配接器互動存放區和轉送 （提取） 案例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4182021c-36c9-4c96-b2fa-e23c87862cfe
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9de8c569744c5bbf750ef2aa804efbc456cd74a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25965868"
---
# <a name="step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-pull-scenario"></a>步驟 1： 設定 SWIFT 配接器互動存放區和轉送 （提取） 案例
在開始此步驟之前，必須先完成[準備使用本教學課程](../../adapters-and-accelerators/fileact-interact/preparing-to-use-the-tutorial1.md)。  
  
### <a name="to-configure-the-swift-adapter"></a>若要設定 SWIFT 配接器  
  
1.  啟動**BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，展開 BizTalk Server 管理、 BizTalk 群組、 展開**平台設定**，依序展開**配接器**，以滑鼠右鍵按一下**互動**，指向**新增**，然後按一下 **傳送處理常式**。  
  
3.  在**互動 – 配接器處理常式屬性**對話方塊**一般**索引標籤上，從**主機名稱**下拉式清單中，選取**interacthost**，然後按一下 **屬性**。  
  
4.  在**互動傳輸屬性**對話方塊**屬性**索引標籤上，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**引數**|輸入下列引數: – SagMessagePartner\<互動的用戶端訊息夥伴建立 SAG\> **附註：** 引數中的用戶端是 MessagePartner SAG 中進行設定。|  
    |**密碼編譯模式**|從下拉式清單選取**進階**。|  
    |**LogMessageBody**|從下拉式清單選取**FALSE**。 **注意：** 如果設為 TRUE 時，它會保留的訊息本文的 「 BizTalk 追蹤資料庫。 不過，基於安全性理由，訊息本文可以永遠不會在檢視 BAM 入口網站。|  
    |**記錄訊息**|從下拉式清單選取**TRUE**。 這可讓要擷取，並在 BAM 入口網站中追蹤的訊息事件。|  
    |**啟用**|False。|  
    |**密碼**|輸入您用來連接到 SAG 的密碼。 如需詳細資訊，請參閱 SAG 說明。|  
    |**使用者名稱**|輸入您用來連接到 SAG 的使用者名稱。|  
  
5.  按一下**確定**關閉互動傳輸屬性 對話方塊。  
  
6.  按一下**確定**關閉互動 – 配接器處理常式屬性 對話方塊。  
  
7.  在訊息方塊中，按一下**確定**，然後重新啟動互動的主控件執行個體。  
  
8.  重複步驟 1。  
  
9. 在主控台樹狀目錄中，展開 BizTalk Server 管理 中，展開**BizTalk**群組中，展開**平台設定**，依序展開**配接器**選取互動，開啟**Biztalkserverapplication** ，然後按一下 **屬性**。  
  
10. 在**互動傳輸屬性**對話方塊**屬性**索引標籤上，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**引數**|輸入下列引數: – SagMessagePartner\<互動的用戶端訊息夥伴建立 SAG\> **附註：** 引數中的用戶端是 MessagePartner SAG 中進行設定。|  
    |**密碼編譯模式**|從下拉式清單選取**進階**。|  
    |**LogMessageBody**|從下拉式清單選取**FALSE**。 **注意：** 如果設為 TRUE 時，它會保留的訊息本文的 「 BizTalk 追蹤資料庫。 不過，基於安全性理由，訊息本文可以永遠不會在檢視 BAM 入口網站。|  
    |**記錄訊息**|從下拉式清單選取**TRUE**。 這可讓要擷取，並在 BAM 入口網站中追蹤的訊息事件。|  
    |**啟用**|True|  
    |**密碼**|輸入您用來連接到 SAG 的密碼。 如需詳細資訊，請參閱 SAG 說明。|  
    |**使用者名稱**|輸入您用來連接到 SAG 的使用者名稱。|  
  
11. 按一下**確定**關閉互動傳輸屬性 對話方塊。  
  
12. 選取**設預設處理常式**選項。  
  
13. 按一下**確定**關閉互動 – 配接器處理常式屬性 對話方塊。  
  
14. 在訊息方塊中，按一下**確定**，然後重新啟動**BizTalkServerApplication**主控件執行個體。  
  
## <a name="see-also"></a>請參閱  
 [步驟 2： 建立傳送埠和接收埠以進行互動的存放區和轉送 （提取） 案例](../../adapters-and-accelerators/fileact-interact/step-2-create-send-ports-and-receive-ports-for-the-interact-store-and-forward.md)   
 [步驟 3： 建立協調流程互動的存放區和轉送 （提取） 案例的動態傳送埠](../../adapters-and-accelerators/fileact-interact/step-3-create-orchestration-with-dynamic-send-for-interact-store-and-forward.md)   
 [步驟 4：測試 InterAct 儲存和轉寄 (提取) 端對端案例](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-store-and-forward-pull-end-to-end-scenario.md)