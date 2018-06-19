---
title: 範例供應鏈實例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- supply chains, examples
- examples, supply chains
ms.assetid: 1837a2c8-b1d4-4e1f-a196-a48b13b22662
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e305021e5b1206cc46ba40c2d2c4cd098c6c6e06
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22211518"
---
# <a name="sample-supply-chain-scenario"></a>範例供應鏈實例
在高科技供應鏈當中，最基本的程序之一是訂單要求及回應訊息的交換。 在雙向基礎上，購買者發出訂單，而供應者不管是接受或拒絕訂單，或是訂單尚待處理都應通知對方。  
  
 本主題描述兩位交易夥伴交換訂單訊息的範例實例，並且顯示整合與自動化加強程序的方法。  
  
## <a name="the-players"></a>交易夥伴  
 在這個範例實例中的購買者是一家大型的高科技設備製造商。 他們目前使用 EDI 架構的系統進行自動資料交換。 面對不使用 EDI 系統的供應商，他們依賴電話、傳真、試算表電子郵件及 Web 應用程式來聯繫。 即使供應商使用 EDI，購買者整合其交易夥伴通訊及後端 ERP 系統的能力也很有限。 透過 EDI 接收到訂單和資訊之後，他們必須手動重新輸入這些訂單到他們的 ERP 系統。 他們希望透過與交易夥伴自動化需求、存貨、購買和報表，改進現有的供應鏈交換程序。 他們需要可以透過網際網路與供應商及客戶聯繫，也能直接與現有的商務營運系統 (LOB) 應用程式整合的系統。  
  
 銷售商是一家中型的高效能積體電路 (IC) 供應商。 他們目前通訊與交易夥伴使用電話、 傳真、 電子郵件與附加[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsExcel](../../includes/btsexcel-md.md)]試算表、 FTP 和 Web 應用程式。 銷售商並未使用 EDI。 他們與每個交易夥伴互動的方式皆有所不同，視客戶的需要以及他們自有的技術而定。 他們希望商務程序能更有效率，以降低交易成本、加強客戶滿意度及取得競爭優勢。  
  
## <a name="the-present-business-process"></a>目前的商務程序  
 若不使用整合解決方案，製造商與供應商的訂單處理流程如下所示：  
  
1.  高科技設備製造商的客戶透過網站傳送訂單給製造商。  
  
2.  為回應原本的訂單，製造商的員工使用 LOB ERP 應用程式建立一個 IC 供應商訂單要求。  
  
3.  訂單要求在製造公司內的不同合作對象之間周遊，因為這些合作對象必須記錄、處理、檢視並授權訂單要求。 這個處理和路由的過程結合了使用者 ERP 系統的自動化程序，以及諸如附加 [!INCLUDE[btsExcel](../../includes/btsexcel-md.md)] 試算表的電子郵件等手動程序。  
  
4.  員工在電子郵件中建立訂單要求，並傳送到供應商。 其他員工重複這個程序，透過電子郵件、傳真或 EDI 與其他供應商溝通。 不同的部門使用不同的程序。 面對使用 EDI 系統的供應商，製造商的員工仍然必須手動從 ERP 系統建立訊息。  
  
5.  供應商的員工會接收訊息，然後手動將訊息輸入到 ERP 系統，變更資料的格式。 透過電子郵件，員工通知其他員工這個要求。  
  
6.  其他員工分析這個要求。 如有必要，他們會通知零件供應商有關零件方面的需求。 端視供應商的狀況，他們使用電話、傳真、電子郵件或 FTP 通知供應商。  
  
7.  在與各部門及供應商開會之後，每位員工接受或拒絕訂單的每個產品線項目，然後確認或拒絕訂單，並指示訂單尚待處理。 他們在 ERP 系統中執行這些工作。  
  
8.  不論是確認或拒絕每個要求的項目，或是建立訊息指出訂單尚待處理，供應商的員工都會以電子郵件建立訂單回應。 供應商的員工傳送回應訊息給製造商。 如果某個項目尚待處理，他們會在稍後建立另一個訊息指出等待的項目已被接受或拒絕。  
  
9. 製造商的員工接收訂單回應。 他們會重新輸入訂單到後端 ERP 系統中。  
  
10. 另一位員工分析訂單確認狀況，然後建立回應給原本的客戶以確認訂單。 他們透過電子郵件傳送這個回應。  
  
## <a name="the-rosettanet-solution"></a>RosettaNet 解決方案  
 Microsoft BizTalk Server 和 [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 會將訂單要求和回應程序自動化及標準化。 使用整合的系統可將人工介入的程度、處理過程中的紙張用量以及電話和傳真機的使用率降至最低。 大多數的程序都是在整合的伺服器電腦之間自動交易。 當員工必須手動執行操作時，他們通常都是在後端的 ERP 系統上作業。 下圖顯示整合的系統。  
  
 ![&#60;沒有變更 &#62;] (../../adapters-and-accelerators/accelerator-rosettanet/media/rn3-integrated-supply-chain-scenario.gif "RN3_Integrated_Supply_Chain_Scenario")  
  
 在這個實例中，整合的系統變更下列程序：  
  
-   RosettaNet 實作架構 (RNIF) 連線取代原本在製造商與 IC 供應商之間的日常人工互動。 系統自動傳送和接收訊息、路由資料到後端的系統，並確認及回應訊息。 製造商和供應商雙方都使用 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 實作 RNIF 連線。  
  
-   RNIF 連線取代在製造商、IC 供應商及其他交易夥伴之間的 EDI 連線。 這讓整合系統自動路由資料到交易夥伴的後端系統中。 某些交易夥伴使用 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 實作 RNIF 連線，而其他交易夥伴則使用不同的 RosettaNet 相容解決方案。  
  
-   對於那些 RosettaNet 相容解決方案的小型交易夥伴，製造商及 IC 供應商會建立可讓交易夥伴使用 Web 瀏覽器存取的 Web 服務。 Web 服務使用標準的 RNIF 連線，與製造商或 IC 供應商端的 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 系統通訊。  
  
-   製造商和供應商之間交換的訊息遵循標準 RosettaNet 交易夥伴介面程序 (PIP) 制訂的結構描述。 這些結構描述取代 EDI 和 FTP 中使用的格式。 所有的交易夥伴都會使用相同的結構描述，因此，他們不需要對應各種訊息之間的資料。  
  
-   [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會自動驗證所有的訊息是否符合結構描述，以降低資料錯誤的風險。  
  
-   管理員可以使用系統管理軟體工具介入 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 伺服器。 用戶端電腦的商務決策制訂者可以使用 Microsoft Office 架構的應用程式或工具中的商務監視工具。 這些都是高效率的程序，可使系統有效率地運作並讓系統或企業的運作有更高的透明度。  
  
### <a name="message-flow"></a>訊息流程  
 商務程序現在包括下列步驟：  
  
1.  高科技設備製造商的客戶透過網站傳送訂單給製造商。  
  
2.  為回應原本的訂單，製造商的員工使用公司的訂單和存貨管理系統產生訂單要求。 這個 LOB 應用程式屬於 ERP 系統，擁有 Web 架構的使用者介面。  
  
3.  系統仍以 ERP 系統原生格式傳送訂單要求到 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]。  
  
4.  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會自動產生訂單要求訊息，遵循 RosettaNet 組織所定義的 3A4 PIP 標準。 此訂單要求採用 XML 格式。 PIP 定義訊息的內容。  
  
    > [!NOTE]
    >  3A4 PIP 確定所有的訂單要求和回應都是相同的格式。 這個 PIP 是 RosettaNet 定義之 PIP 的部分集合，組成完整的互相連接訊息系統。 例如，在傳送 3A4 訊息之前，購買者可能尋找價格與可用性 (PIP 3A2)、要求報價 (PIP 3A1) 或傳送購物車 (PIP 3A3)。 在傳送訂單要求之後，購買者可能變更訂單 (PIP 3A8)、取消訂單 (PIP 3A9)、查詢訂單狀態 (PIP 3A5) 或散佈訂單狀態 (PIP 3A6)。 RosettaNet 組織已經標準化這些訊息。  
  
5.  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 使用 RNIF 標頭包裝要求訊息 (亦即服務內容)，RNIF 標頭讓 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 可透過網際網路將訊息傳送至供應商網站的其他 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 電腦。 RNIF 定義交易夥伴透過網際網路交換訊息的方式。  
  
6.  製造商的 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 系統傳送訂單要求至 IC 供應商的 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 系統。  
  
7.  供應商的 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] N 系統接收訂單要求。 如果這是單向動作要求 (沒有相對回應)，供應商的 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 系統將傳回信號訊息，表示已經收到訊息。 然而，由於這是雙向動作訊息，供應商的 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 系統會傳回回條確認信號訊息，隨後傳回回應訊息。  
  
8.  供應商的 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 系統從訂單要求訊息中移除 RNIF 標頭，並處理訊息的服務內容，然後將要求路由傳送至供應商的 ERP 系統。  
  
9. 供應商的員工會在 ERP 系統中處理訂單。 如果他們需要傳送訊息給零件供應商，也會使用相同的 BizTalk 及 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 系統執行操作。 IT 部門可以自訂系統以自動回應製造商。  
  
10. 員工使用供應商的 ERP 系統產生訂單回應訊息，然後將回應訊息路由傳送至供應商的 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 系統。  
  
11. 供應商的 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 系統產生 PIP 3A4 訂單回應訊息，以 RNIF 標頭包裝回應訊息的服務內容，然後將訂單回應傳送至製造商的 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 系統。  
  
12. 製造商的 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 系統接收訂單回應，然後將回條確認訊息傳送至供應商的 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]。 供應商的 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 系統將確認路由傳送至供應商的 ERP 系統。  
  
13. 製造商的 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 系統從回應訊息中移除 RNIF 標頭，再處理服務內容，然後將訂單回應路由傳送至製造商的 ERP 應用程式。  
  
14. 製造商的員工分析所有的訂單確認訊息，然後建立回應傳送給原本的客戶以確認訂單。 然後，員工會透過電子郵件傳送這個回應。  
  
## <a name="advantages-of-the-btarn-solution"></a>BTARN 解決方案的優點  
 BizTalk Server 及 [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] 會將大多數的訂單要求與回應程序自動化。 這兩者不僅會為製造商和 IC 供應商自動化程序，也會為所有採用 RosettaNet 相容解決方案做為供應鏈管理的其他交易夥伴進行自動化。  
  
 整合的系統可將人工介入的程度及處理過程中的紙張用量降至最低。 大多數的程序都需要整合的伺服器電腦之間的自動化互動。 製造商和 IC 供應商兩者對他們的程序都具有高度的可控制性和透明度。 他們會自動接收確認，並且可以保存不可否認性證據。  
  
 使用 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 的自動化系統可以讓製造商和供應商執行下列作業：  
  
-   縮短訂單完成的週期時間  
  
-   降低程序的不可確定性，以及提高程序的可信賴程度  
  
-   縮短完成時間以及報價回應時間  
  
-   減少用在人工重新處理資訊、取得遺漏資訊或校正錯誤的時間  
  
-   提高程序透明度並允許監視程序及追蹤訊息  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 如何解決商務需求](../../adapters-and-accelerators/accelerator-rosettanet/how-biztalk-server-solves-the-business-need1.md)   
 [交易夥伴整合需求](../../adapters-and-accelerators/accelerator-rosettanet/the-need-for-trading-partner-integration.md)   
 [供應鏈面臨的挑戰](../../adapters-and-accelerators/accelerator-rosettanet/the-supply-chain-challenge.md)   
 [供應鏈方案](../../adapters-and-accelerators/accelerator-rosettanet/the-supply-chain-solution.md)   
 [範例中樞架構實例](../../adapters-and-accelerators/accelerator-rosettanet/sample-hub-based-scenario.md)