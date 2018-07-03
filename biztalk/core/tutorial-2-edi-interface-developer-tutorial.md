---
title: '教學課程 2: EDI 介面開發人員教學課程 |Microsoft Docs'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10fb650-cbb9-41e5-a80d-06afd0513814
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f995cc21bd94ddc00ab15d78c74679eb51d939b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37020427"
---
# <a name="tutorial-2-edi-interface-developer-tutorial"></a>教學課程 2: EDI 介面開發人員教學課程
本教學課程將示範如何在介面開發人員實例中使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的 EDI 功能。  
  
 **教學課程案例**  
  
 在此實例中，您的交易夥伴會使用 ANSI X12 版本 4010 850 交易集 (850 訊息)，傳送訂單至您的公司。 您的公司則使用內部應用程式 (「訂單系統」) 來處理訂單。  
  
 您是介面開發人員，負責設計 850 訊息 (接收自交易夥伴) 和公司內部訂單系統之間的介面。 您的交易夥伴要求其每傳送一個 850 訊息都要收到功能通知 (997)。  
  
 為方便參考，此例使用下列識別項：  
  
|實體|識別碼|  
|------------|----------------|  
|您的公司|OrderSystem|  
|您的交易夥伴|Fabrikam|  
  
 在已完成解決方案中的訊息流程如下圖所示：  
  
 ![EDI 介面開發人員教學課程訊息流程](../core/media/4944352a-dc77-47f1-a324-bf71444670c5.gif "4944352a-dc77-47f1-a324-bf71444670c5")  
  
 **訊息流程**  
  
 在此教學課程中的解決方案，將會執行下列工作：  
  
1. 從交易夥伴 Fabrikam 接收一般檔案交換。  
  
   > [!NOTE]
   >  這份清單中的事件可能不會按照所示的順序發生。  
  
2. 驗證 EDI 交換 (根據其結構描述)、將訊息解譯成 XML，並將訊息 XML 放置在 MessageBox 中。  
  
3. 產生 997 通知給接收的 EDI 交換，並將其放置在 MessageBox 中。  
  
4. 透過單向傳送埠收取 997 XML，並組合 997 EDI 交換。  
  
5. 傳送 997 交換給 Fabrikam。  
  
6. 透過單向傳送埠收取訊息 XML，並組合訊息 EDI 交換。  
  
7. 傳送 EDI 交換給 OrderSystem。  
  
   **Configuration**  
  
   在此教學課程中，您將執行下列動作：  
  
- 將 BizTalk 設定成期待來自交易夥伴的 850 訊息，以及傳回 997 通知  
  
- 使用 BizTalk 對應，將 850 訊息資料轉換為「訂單系統」所需要的格式。 此對應提供於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SDK 的教學課程檔案中。  
  
- 設定接收 850 訊息的接收埠。  
  
- 設定傳送埠，以便將 850 訊息以正確格式傳送到 OrderSystem。  
  
- 設定傳送埠，以便訂閱要路由傳回交易夥伴 Fabrikam 的由 BizTalk 產生的 997 通知。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [步驟 1：準備 EDI 介面開發人員教學課程](../core/step-1-prepare-for-the-edi-interface-developer-tutorial.md)  
  
-   [步驟 2：更新和部署教學課程解決方案](../core/step-2-update-and-deploy-the-tutorial-solution.md)  
  
-   [步驟 3：為組織設定合作對象和商務設定檔](../core/step-3-configure-a-party-and-business-profile-for-your-organization1.md)  
  
-   [步驟 4：為交易夥伴設定合作對象和商務設定檔](../core/step-4-configure-a-party-and-business-profile-for-your-trading-partner1.md)  
  
-   [步驟 5：設定接收埠和接收位置](../core/step-5-configure-a-receive-port-and-receive-location.md)  
  
-   [步驟 6：設定傳送埠將資料傳送至組織](../core/step-6-configure-a-send-port-to-send-data-to-your-organization.md)  
  
-   [步驟 7：設定傳送埠將通知傳送給交易夥伴](../core/step-7-configure-a-send-port-to-send-the-acknowledgment-to-trading-partner.md)  
  
-   [步驟 8：設定合作對象之間的交易夥伴協定](../core/step-8-configure-the-trading-partner-agreement-between-the-parties.md)  
  
-   [步驟 9：測試 EDI 解決方案](../core/step-9-test-the-edi-solution.md)  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 教學課程](../core/biztalk-server-tutorials.md)