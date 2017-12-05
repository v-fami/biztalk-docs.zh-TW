---
title: "Interrogative 教學課程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interrogative tutorial
- interrogative tutorial, about the tutorial
- tutorials, interrogative tutorial
ms.assetid: 93988429-5544-4920-821f-54f0a67bda72
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 642f2521917dd87b60ee43a4cd7decaeeb1f1365
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="interrogative-tutorial"></a>Interrogative 教學課程
本教學課程包含詳細的步驟，說明如何使用[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]輔助商務程序中查詢/回應實例。  
  
> [!NOTE]
>  若要使用此教學課程中，您必須安裝 MLLP 測試工具。 典型安裝 BTAHL7 不會安裝這些工具。 您必須執行自訂安裝，然後選取**MLLP 測試工具**從配接器資料夾和**測試執行個體**從 [成品] 資料夾。 如果安裝測試工具，則系統將會包含資料夾\<*磁碟機*:\>\Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\MLLP 公用程式。 請參閱[安裝 BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md)。  
  
## <a name="interrogative-scenario"></a>Interrogative 案例  
 本教學課程使用的查詢/回應或 Interrogative 案例。 在此案例中，商務流程是類似於下圖所示。 圖例之後已編號的清單描述工作流程。  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-intertutorial.gif "hl7_intertutorial")  
  
1.  當許可放電和傳輸 (ADT) 的系統會將查詢傳送至醫院資訊系統時，就會開始工作流程。 HL7 訊息使用"**QRY ^ Q01**」 結構描述。 教學課程中，MllpSend 公用程式會模擬 ADT 系統傳送查詢訊息至醫院資訊系統，透過 ADT BTAHL7 整合引擎接收埠。  
  
2.  BTAHL7 整合引擎接收 ADT 系統查詢訊息，並驗證它。 接著，BTAHL7 管線會傳送通知回 ADT。  
  
3.  BTAHL7 介面引擎處理的訊息，並再查詢訊息至 HIS 目的合作對象透過 HIS 的路由傳送連接埠。  
  
4.  從原始的查詢中接收通知之後, ADT 系統等候回應。 回應訊息回透過 HIS 醫院資訊系統傳送接收連接埠。 本教學課程，MllpSend 公用程式會模擬醫院資訊系統傳送回應訊息。  
  
5.  BTAHL7 介面引擎處理回應訊息，然後將它路由傳送至目的合作對象透過 ADT 傳送埠。  
  
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
  
## <a name="see-also"></a>請參閱  
[開始使用 BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/get-started-with-the-biztalk-accelerator-for-hl7.md)