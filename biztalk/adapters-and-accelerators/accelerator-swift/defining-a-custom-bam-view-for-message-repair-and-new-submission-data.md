---
title: 訊息修復和新送出資料中定義自訂 BAM 檢視 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BAM views
- Message Repair and New Submission, BAM views
ms.assetid: 76a6e78d-9b11-4b43-a500-a9d7666ee468
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e88ec7506a299476dccb6ef9f9d0125768ea80b6
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26006815"
---
# <a name="defining-a-custom-bam-view-for-message-repair-and-new-submission-data"></a>訊息修復和新送出資料中定義自訂 BAM 檢視
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]安裝程式會提供定義商務活動和商務檢視 BAM 定義檔案。 您可以部署 BAM 定義檔案，若要使用該檢視，或您可以建立自訂檢視，您可以加入 BAM 定義檔案。  
  
 BAM 定義檔案是在 MrsrActivities.xml *\<磁碟機\>*: \Program Files\Microsoft BizTalk Accelerator for SWIFT\BAMTracking。 它會定義訊息活動和 RepairView 檢視。 如需有關使用 bm 部署 MrsrActivities.xml 部署公用程式，請參閱 BizTalk Server 說明。  
  
 在 商務活動監控檢視精靈從 BAM 活頁簿中建立自訂檢視。 如需建立自訂檢視的詳細資訊，請參閱 「 建立 BAM 檢視 」 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Server 資訊工作者說明。  
  
 訊息中的活動 MrsrActivities.xml 包含下列項目，您可以加入自訂的檢視：  
  
> [!NOTE]
>  當持續時間會計算在 BAM 中時，它們會測量單位的一天 （14.4 分鐘 = 0.1 天）。  
  
|項目|使用|項目類型|  
|----------|---------|---------------|  
|目的地 BIC|訊息的接收者的 LT 位址 (從應用程式標頭區塊的輸入訊息 SWIFT，或訊息的區塊 1 取自 SWIFT 其中[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]機構是目的地)。<br /><br /> 這項資料，則一律存在 （從應用程式標頭輸入目的地 LT SWIFTBound 訊息，或從基本的標頭 LT 接收來自 SWIFT 的訊息）。|商務資料 - TEXT|  
|結束時間|完成日期和時間時 MRSRRepair 協調流程處理訊息 （MRSR_Completed 或 MRSR_Failed）。<br /><br /> 只會針對已完成 MRSR 工作流程，也就是訊息已結束，此資料是否都出現**BTS。作業** == **A4SWIFT_MRSRCompleted**或**A4SWIFT_MRSRFailed**。|商務里程碑|  
|參考|此訊息或傳送的機構; 所指派的交易的唯一參考識別碼取自欄位 20 或 20C(SEME)|商務資料 - TEXT|  
|訊息類型|FIN 或 GPA 訊息類型。<br /><br /> 這項資料，則一律存在 （應用程式標頭輸入或應用程式標頭輸出）。|商務資料 - TEXT|  
|New Submission|指標，指出是否這是新的項目 (Y) 或來自另一個系統或 SWIFT (N) 的訊息。<br /><br /> 這項資料的才會顯示建立功能與角色所源自的訊息。|商務資料 - TEXT|  
|優先權|SWIFT 訊息的優先順序 (N = 正常，U = 緊急 S = 系統)。<br /><br /> 這項資料，則一律存在。|商務資料 - TEXT|  
|接收的時間|MRSRRepair 協調流程前次收到訊息的時間與日期 （從上一個階段 – 請參閱下方的階段）。<br /><br /> 這項資料，則一律存在。|商務里程碑|  
|寄件者 BIC|訊息的訂閱者的 LT 位址 (取自區塊 1 的訊息至 SWIFT 其中[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]機構是寄件者，或從應用程式標頭輸出來自 SWIFT 的訊息)。<br /><br /> 這項資料，則一律存在 （從基本 SWIFTBound 訊息的標頭 LT 地址，或從應用程式接收來自 SWIFT 的訊息的標頭輸出）。|商務資料 - TEXT|  
|傳送時間|日期和時間時 MRSRRepair 協調流程最後傳送訊息至 MRSR 網站 （適用於目前的階段）。<br /><br /> 除非訊息是協調流程中的程序中，則一律存在這項資料。|商務里程碑|  
|Start Time|日期和時間時 MRSRRepair 協調流程開始收到訊息新提交，或是為從介面 （內部系統或 SWIFT） 訊息。<br /><br /> 這項資料，則一律存在。|商務里程碑|  
|最後一個階段|上次完成的工作流程 （一律之前是現在的階段） 中的步驟|商務資料 - TEXT|  
|狀態|可為以下項目：<br /><br /> 完成 （如果成功的話）<br />-重設及說明 （適用於重設如果重新啟動工作流程的工作流程）<br />-失敗，原因 （如果未順利，完成的訊息也就是已拒絕或已逾時）。<br /><br /> 這項資料，則一律存在。|商務資料 - TEXT|  
|部門|選取由 MRSRRepair 協調流程根據部門原則的部門 (取決於[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]機構)|商務資料 - TEXT|  
|使用者名稱|與上一個階段相關聯的使用者名稱 （請參閱上述的階段）|商務資料 - TEXT|  
|目前的階段|MRSRRepair 協調流程已傳送訊息 （例如，收件匣） 工作流程步驟。<br /><br /> 這項資料會出現，除非該訊息已完成訊息修復。|商務資料 - TEXT|