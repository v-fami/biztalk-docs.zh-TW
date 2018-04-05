---
title: 端對端 Tutorial1 |Microsoft 文件
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
ms.openlocfilehash: 90dc31ac286f8ce1e38d9a511eb319828d8ae939
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="end-to-end-tutorial"></a>端對端教學課程
本教學課程包含詳細的步驟，說明如何使用[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]輔助商務程序在 「 訂閱者 」 和 「 發行者 」 的案例。  
  
> [!IMPORTANT]
>  若要使用此教學課程中，您必須在安裝 BTAHL7 時安裝測試工具。 如果您執行一般安裝 BTAHL7 安裝，然後您必須執行自訂安裝並測試工具安裝進行本教學課程正常運作。 在**自訂安裝**BTAHL7 自訂安裝，請選取畫面**MLLP 測試工具**從**配接器**資料夾，然後選取**測試執行個體**從**成品**資料夾。 如需詳細資訊，請參閱[安裝 BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md)。  
  
## <a name="declarative-scenario"></a>宣告式案例  
 本教學課程使用的發佈/訂閱或宣告式的案例。 在宣告式案例中，商務流程是類似於下圖所示。 圖例之後已編號的清單描述工作流程。  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-e2e-wkflw.gif "hl7_e2e_wkflw")  
下圖顯示的宣告式案例的商務流程  
  
1.  當 「 發行者 」，例如許可放電和傳輸系統會傳送訊息至特定的訂閱者時，就會開始工作流程。 工作流程中的 「 發行者 」 是 「 Tutorial_ADTSystem 」，並將訊息稱為 「**ADT ^ A103**。 」  
  
2.  在訊息傳送給 BTAHL7 介面引擎，依次接收、 處理、 驗證、 重新格式化，並再將訊息路由至訂閱者。  
  
3.  在此案例中的 「 訂閱者 」 為醫院資訊系統 (Tutorial_HISystem) 和藥局系統 (Tutorial_RXSystem)。 此案例使用檔案和 MLLP 配接器類型。 不需要 「 發行者 」，這是要注意的訂閱者並 BTAHL7 適當地將傳送通知到 「 發行者 」 在處理訊息之後。  
  
4.  「 發行者 」 傳送 ADT ^ A03 訊息透過單向 MLLP 配接器 (Tutorial_1WayReceivePort)。  
  
5.  此訊息的目的地是 BTAHL7 介面引擎，讓內送訊息包含來源訊息 (MSH3 = Tutorial_ADTSystem) 和目的訊息 (MSH5 = BTAHL7InterfaceEngine)。  
  
6.  BTAHL7 產生通知 (ACK) 之後適當地驗證訊息，並接著會通知傳送給 Tutorial_ADTSystem 透過 File 配接器。  
  
7.  Tutorial_HISystem 系統和 Tutorial_RXSystem 系統 BTAHL7 介面引擎所收到的 ADT 訊息來訂閱。  
  
8.  當您使用指定的對應欄位的值時，就會發生轉換**MSH 對應**BTAHL7 組態總管 中的索引標籤。  
  
     例如，合作對象 Tutorial_RXSystem 具有 MSH3 = BTHL7 中指定**MSH 對應** 索引標籤。因此，「 訂閱者 」 所收到的訊息會有"BTAHL7"做為 MSH3 欄位的值。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [測試您的安裝](../../adapters-and-accelerators/accelerator-hl7/testing-your-installation.md)  
  
-   [準備使用本教學課程](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-tutorial2.md)  
  
-   [步驟 1： 建立及部署標頭和通知結構描述](../../adapters-and-accelerators/accelerator-hl7/step-1-create-and-deploy-header-and-acknowledgment-schemas.md)  
  
-   [步驟 2： 建立 v2.3.1 通用結構描述](../../adapters-and-accelerators/accelerator-hl7/step-2-create-common-schemas-for-v2-3-1.md)  
  
-   [步驟 3： 建立專案並部署觸發程序事件 （訊息）](../../adapters-and-accelerators/accelerator-hl7/step-3-create-and-deploy-a-trigger-event-message-project.md)  
  
-   [步驟 4： 建立接收埠，以便接受 ADT ^ A03 訊息從 ADT 系統使用 MLLP 配接器](../../adapters-and-accelerators/accelerator-hl7/step-4-create-receive-port-to-accept-adt^a03-messages-from-adt-using-mllp.md)  
  
-   [步驟 5： 建立傳送埠，以便將通知傳送到使用 File 配接器 ADT 系統](../../adapters-and-accelerators/accelerator-hl7/step-5-create-send-port-to-deliver-acknowledgments-to-adt-system-using-file.md)  
  
-   [步驟 6： 建立傳送埠以傳送 ADT ^ A03 RX 系統使用 File 配接器的訊息](../../adapters-and-accelerators/accelerator-hl7/step-6-create-send-port-to-deliver-adt^a03-message-to-rx-system-using-file.md)  
  
-   [步驟 7： 建立傳送埠以傳送 ADT ^ A03 他使用 MLLP 配接器的訊息](../../adapters-and-accelerators/accelerator-hl7/step-7-create-send-port-to-deliver-adt^a03-message-to-his-using-mllp-adapter.md)  
  
-   [步驟 8： 設定合作對象資訊](../../adapters-and-accelerators/accelerator-hl7/step-8-configure-party-information.md)  
  
-   [步驟 9： 重新啟動 BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-9-restart-biztalk-server.md)  
  
-   [步驟 10： 確認端對端案例](../../adapters-and-accelerators/accelerator-hl7/step-10-verify-the-end-to-end-scenario.md)

## <a name="see-also"></a>另請參閱
[開始使用 BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/get-started-with-the-biztalk-accelerator-for-hl7.md)