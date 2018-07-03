---
title: 端對端 Tutorial1 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- btahl7.endtoendtutorial
helpviewer_keywords:
- end-to-end tutorial, about the tutorial
- end-to-end tutorial
- tutorials, end-to-end tutorial
ms.assetid: 90625edc-70a0-42c9-a2fb-8eeb5465d766
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 264a6eee008b9b327185c931ad4e5ac60cdc995a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000735"
---
# <a name="end-to-end-tutorial"></a>端對端教學課程
本教學課程包含詳細的步驟，說明您如何使用 Microsoft[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]輔助商務程序，在 「 訂閱者 」 和 「 發行者 」 的案例。  
  
> [!IMPORTANT]
>  若要使用本教學課程中，您必須在安裝 BTAHL7 時安裝測試工具。 如果您執行一般安裝 BTAHL7 安裝，然後您必須執行自訂安裝並測試工具安裝進行本教學課程中正常運作。 在**自訂安裝**BTAHL7 自訂安裝中，選取畫面**MLLP 測試工具**從**配接器**資料夾，然後選取**測試執行個體**從**成品**資料夾。 如需詳細資訊，請參閱 <<c0> [ 安裝 BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md)。  
  
## <a name="declarative-scenario"></a>宣告式案例  
 本教學課程會使用發佈/訂閱或宣告式案例。 在宣告式案例中，商務流程是類似下圖所示。 下圖的編號的清單描述的工作流程。  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-e2e-wkflw.gif "hl7_e2e_wkflw")  
下圖顯示的宣告式案例的商務流程  
  
1.  在工作流程開始時的發行者，比方說，門診出院和傳輸系統，將訊息傳送給特定的訂閱者。 工作流程中的 「 發行者 」 是 「 Tutorial_ADTSystem"，並將訊息稱為 「**ADT ^ A103**。 」  
  
2.  訊息會路由至 BTAHL7 介面引擎，其接著接收、 處理、 驗證、 重新格式化，並再將訊息路由至訂閱者。  
  
3.  在此案例中的 「 訂閱者 」 為醫院的資訊系統 (Tutorial_HISystem) 和 Pharmacy 系統 (Tutorial_RXSystem)。 此案例使用檔案和 MLLP 配接器類型。 不需要 「 發行者 」，這是要注意的訂閱者並 BTAHL7 適當地將傳送通知給 「 發行者 」 處理訊息之後。  
  
4.  「 發行者 」 傳送 ADT ^ 將 adt^a03 訊息透過單向的 MLLP 配接器 (Tutorial_1WayReceivePort)。  
  
5.  此訊息的目的地是 BTAHL7 介面引擎，讓內送訊息包含來源訊息 (MSH3 = Tutorial_ADTSystem) 和目的訊息 (MSH5 = BTAHL7InterfaceEngine)。  
  
6.  BTAHL7 之後適當地驗證訊息，產生通知 (ACK)，然後將通知傳送至 File 配接器透過 Tutorial_ADTSystem。  
  
7.  Tutorial_HISystem 系統和 Tutorial_RXSystem 系統訂閱接收 BTAHL7 介面引擎 ADT 訊息。  
  
8.  當您使用指定的對應欄位的值時，就會發生轉換**MSH 對應**BTAHL7 設定總管中的索引標籤。  
  
     比方說，合作對象 Tutorial_RXSystem 有 MSH3 = 中指定的 BTHL7 **MSH 對應** 索引標籤。因此，「 訂閱者 」 所收到的訊息會有"BTAHL7 」 做為 MSH3 欄位的值。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [測試您的安裝](../../adapters-and-accelerators/accelerator-hl7/testing-your-installation.md)  
  
-   [準備使用教學課程](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-tutorial2.md)  
  
-   [步驟 1：建立及部署標頭和通知結構描述](../../adapters-and-accelerators/accelerator-hl7/step-1-create-and-deploy-header-and-acknowledgment-schemas.md)  
  
-   [步驟 2： 建立 v2.3.1 通用結構描述](../../adapters-and-accelerators/accelerator-hl7/step-2-create-common-schemas-for-v2-3-1.md)  
  
-   [步驟 3：建立及部署觸發程序事件 (訊息) 專案](../../adapters-and-accelerators/accelerator-hl7/step-3-create-and-deploy-a-trigger-event-message-project.md)  
  
-   [步驟 4：建立接收埠，以使用 MLLP 配接器接受來自 ADT 系統的 ADT^A03 訊息](../../adapters-and-accelerators/accelerator-hl7/step-4-create-receive-port-to-accept-adt^a03-messages-from-adt-using-mllp.md)  
  
-   [步驟 5：建立傳送埠，以使用 FILE 配接器將通知傳送到 ADT 系統](../../adapters-and-accelerators/accelerator-hl7/step-5-create-send-port-to-deliver-acknowledgments-to-adt-system-using-file.md)  
  
-   [步驟 6：建立傳送埠，以使用 FILE 配接器將 ADT^A03 訊息傳遞給 RX 系統](../../adapters-and-accelerators/accelerator-hl7/step-6-create-send-port-to-deliver-adt^a03-message-to-rx-system-using-file.md)  
  
-   [步驟 7：建立傳送埠，以使用 MLLP 配接器將 ADT^A03 訊息傳遞給 HIS](../../adapters-and-accelerators/accelerator-hl7/step-7-create-send-port-to-deliver-adt^a03-message-to-his-using-mllp-adapter.md)  
  
-   [步驟 8：設定合作對象資訊](../../adapters-and-accelerators/accelerator-hl7/step-8-configure-party-information.md)  
  
-   [步驟 9：重新啟動 BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-9-restart-biztalk-server.md)  
  
-   [步驟 10：驗證端對端案例](../../adapters-and-accelerators/accelerator-hl7/step-10-verify-the-end-to-end-scenario.md)

## <a name="see-also"></a>另請參閱
[開始使用 BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/get-started-with-the-biztalk-accelerator-for-hl7.md)