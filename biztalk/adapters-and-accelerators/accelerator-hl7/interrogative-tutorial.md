---
title: 詢問式教學課程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interrogative tutorial
- interrogative tutorial, about the tutorial
- tutorials, interrogative tutorial
ms.assetid: 93988429-5544-4920-821f-54f0a67bda72
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 92c832de8b6572e5ac70b79db1cbcc75d3812ea6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003199"
---
# <a name="interrogative-tutorial"></a>詢問式教學課程
本教學課程包含詳細的步驟，說明您如何使用 Microsoft[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]輔助查詢/回應案例中的商務程序。  
  
> [!NOTE]
>  若要使用本教學課程中，您必須安裝 MLLP 測試工具。 典型安裝 BTAHL7 不會安裝這些工具。 您必須執行自訂安裝，並選取**MLLP 測試工具**從配接器資料夾並**測試執行個體**從 [成品] 資料夾。 如果已安裝的測試工具，您的系統將會包含資料夾\<*磁碟機*:\>\Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\MLLP 公用程式。 請參閱[安裝 BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md)。  
  
## <a name="interrogative-scenario"></a>詢問式案例  
 本教學課程使用的查詢/回應或詢問式案例。 在此案例中，商務流程是類似下圖所示。 下圖的編號的清單描述的工作流程。  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-intertutorial.gif "hl7_intertutorial")  
  
1.  在工作流程開始，當許可出院和傳輸 (ADT) 系統會將查詢傳送至醫院資訊系統。 HL7 訊息使用"**QRY ^ Q01**」 結構描述。 在本教學課程，MllpSend 公用程式可模擬 ADT 查詢訊息傳送到醫院資訊系統透過 ADT 系統接收埠，BTAHL7 整合引擎中。  
  
2.  BTAHL7 整合引擎會接收來自 ADT 系統的查詢訊息，並加以驗證。 然後，BTAHL7 管線會將通知送回 ADT。  
  
3.  BTAHL7 介面引擎會處理訊息，然後查詢訊息至 HIS 目的地合作對象透過 HIS 的路由傳送連接埠。  
  
4.  從原始的查詢中接收通知之後, ADT 系統會等候回應。 回應訊息後 HIS 醫院資訊系統會傳送接收埠。 本教學課程中，MllpSend 公用程式會模擬醫院資訊系統傳送的回應訊息。  
  
5.  BTAHL7 介面引擎會處理回應訊息，並再將其路由至目的合作對象，透過 ADT 傳送埠。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [準備使用教學課程](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-tutorial-hl7-main.md)  
  
-   [步驟 1：建立及部署通用標頭和通知結構描述](../../adapters-and-accelerators/accelerator-hl7/step-1-create-and-deploy-common-header-and-acknowledgment-schemas.md)  
  
-   [步驟 2：建立 V2.4 通用結構描述](../../adapters-and-accelerators/accelerator-hl7/step-2-create-common-schemas-for-v2-4.md)  
  
-   [步驟 3：建立及部署觸發程序事件 (訊息) 專案](../../adapters-and-accelerators/accelerator-hl7/step-3-create-and-deploy-a-trigger-event-message-project-hl7-main.md)  
  
-   [步驟 4：建立接收埠，以接受 ADT 查詢訊息](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-receive-port-for-accepting-adt-query-messages.md)  
  
-   [步驟 5：建立接收埠，以接受 HIS 訊息](../../adapters-and-accelerators/accelerator-hl7/step-5-create-the-receive-port-for-accepting-his-messages.md)  
  
-   [步驟 6：建立傳送埠以傳遞查詢訊息](../../adapters-and-accelerators/accelerator-hl7/step-6-create-a-send-port-to-deliver-query-messages.md)  
  
-   [步驟 7：建立傳送埠以傳遞回應訊息](../../adapters-and-accelerators/accelerator-hl7/step-7-create-a-send-port-to-deliver-response-messages.md)  
  
-   [步驟 8：設定合作對象資訊](../../adapters-and-accelerators/accelerator-hl7/step-8-configure-party-information-hl7-main.md)  
  
-   [步驟 9：重新啟動 BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-9-restart-biztalk-server-hl7-main.md)  
  
-   [步驟 10：驗證詢問式案例](../../adapters-and-accelerators/accelerator-hl7/step-10-verify-the-interrogative-scenario.md)  

## <a name="next-step"></a>下一步  
 [準備使用教學課程](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-tutorial-hl7-main.md)
  
## <a name="see-also"></a>另請參閱  
[開始使用 BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/get-started-with-the-biztalk-accelerator-for-hl7.md)