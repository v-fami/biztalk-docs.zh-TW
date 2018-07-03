---
title: 定義 Message Repair 和 New Submission 資料的自訂 BAM 檢視 |Microsoft Docs
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
ms.openlocfilehash: 490c1244b8ea63dda255220569f3ccee4e0f70c5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007839"
---
# <a name="defining-a-custom-bam-view-for-message-repair-and-new-submission-data"></a>定義 Message Repair 和 New Submission 資料的自訂 BAM 檢視
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] 安裝程式會提供定義商務活動和商務檢視 BAM 定義檔案。 您可以部署 BAM 定義檔案，以使用該檢視，或您可以建立自訂檢視，您可以加入 BAM 定義檔案。  

 BAM 定義檔案是在 MrsrActivities.xml *\<磁碟機\>*: \Program Files\Microsoft BizTalk Accelerator for SWIFT\BAMTracking。 它會定義訊息活動和 RepairView 檢視。 如需有關使用 bm 部署 MrsrActivities.xml 部署公用程式，請參閱 BizTalk Server 說明。  

 在 [商務活動監控檢視精靈] 從 BAM 活頁簿中建立自訂檢視。 如需建立自訂檢視的詳細資訊，請參閱 「 建立 BAM 檢視 」 MicrosoftBizTalk 伺服器資訊背景工作協助。  

 MrsrActivities.xml 中的訊息活動會包含下列項目，您可以加入自訂的檢視：  

> [!NOTE]
>  持續時間會計算在 BAM 中，當它們被測量單位的一天 （14.4 分鐘 = 0.1 天）。  

|      項目       |                                                                                                                                                                                                                                  使用                                                                                                                                                                                                                                   |      項目類型       |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------|
| 目的地 BIC | 訊息接收者的 l 位址 (從應用程式標頭區塊輸入訊息至 SWIFT，或從訊息的區塊 1 取自 SWIFT 其中[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]機構是目的地)。<br /><br /> 這項資料，則一律存在 （從應用程式標頭輸入目的地 L SWIFTBound 訊息，或從基本的標頭 l，接收來自 SWIFT 的訊息）。 | 商務資料 - TEXT |
|    結束時間     |                                                                            完成日期和時間時 MRSRRepair 協調流程處理訊息 （MRSR_Completed 或 MRSR_Failed）。<br /><br /> 這項資料是存在，只針對已完成 MRSR 工作流程，也就是訊息已結束， **BTS。作業** == **A4SWIFT_MRSRCompleted**或是**A4SWIFT_MRSRFailed**。                                                                             |  商務里程碑  |
|    參考    |                                                                                                                                                                此訊息或傳送的機構; 所指派的交易的唯一參考識別碼取自欄位 20 或 20C(SEME)                                                                                                                                                                | 商務資料 - TEXT |
|  訊息類型   |                                                                                                                                                                    FIN 或 GPA 的訊息類型。<br /><br /> 這項資料，則一律存在 （應用程式標頭輸入或應用程式標頭的輸出）。                                                                                                                                                                    | 商務資料 - TEXT |
| New Submission  |                                                                                                                       指標，指出是否這是新的項目 (Y) 或來自另一個系統或 SWIFT (N) 的訊息。<br /><br /> 僅針對建立功能與角色所源自的訊息有這項資料。                                                                                                                        | 商務資料 - TEXT |
|    優先權     |                                                                                                                                                                            SWIFT 訊息的優先權 (N = 正常，U = 緊急，S = 系統)。<br /><br /> 這項資料一律會出現。                                                                                                                                                                            | 商務資料 - TEXT |
|  接收的時間  |                                                                                                                                                  MRSRRepair 協調流程前次收到訊息的時間與日期 （上一個階段 – 請參閱下方的階段）。<br /><br /> 這項資料一律會出現。                                                                                                                                                   |  商務里程碑  |
|   寄件者 BIC    |        訊息的建立者的 l 位址 (取自區塊 1 的訊息至 SWIFT 其中[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]機構是傳送者，或從應用程式標頭輸出來自 SWIFT 的訊息)。<br /><br /> 這項資料，則一律存在 （從基本 SWIFTBound 訊息的標頭 l 地址或應用程式接收來自 SWIFT 的訊息的標頭輸出）。        | 商務資料 - TEXT |
|    傳送時間    |                                                                                                                             日期和時間時 MRSRRepair 協調流程最後將訊息傳送至 MRSR 網站 （適用於目前的階段）。<br /><br /> 這項資料一律會出現，除非是在協調流程中的程序中的訊息。                                                                                                                             |  商務里程碑  |
|   Start Time    |                                                                                                                          時間與日期時 MRSRRepair 協調流程一開始接收訊息作為新送出或介面 （內部系統或 SWIFT） 中的訊息。<br /><br /> 這項資料一律會出現。                                                                                                                          |  商務里程碑  |
|   最後一個階段    |                                                                                                                                                                                       上次完成的工作流程 （一律之前訊息所在現在階段） 中的步驟                                                                                                                                                                                       | 商務資料 - TEXT |
|     [狀態]      |                                                                                               可為以下項目：<br /><br /> 完成 （如果成功）<br />-重設和原因 （適用於工作流程重新啟動時重設的工作流程）<br />失敗及原因 （如果未順利，完成的訊息也就是已拒絕或已逾時）。<br /><br /> 這項資料一律會出現。                                                                                                | 商務資料 - TEXT |
|   部門    |                                                                                                                          部門原則根據 MRSRRepair 協調流程所選科系 (取決於[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]機構)                                                                                                                           | 商務資料 - TEXT |
|    使用者名稱     |                                                                                                                                                                                               與前一個階段相關聯的使用者名稱 （請參閱上述的階段）                                                                                                                                                                                                | 商務資料 - TEXT |
|  目前的階段  |                                                                                                                                     工作流程步驟的 MRSRRepair 協調流程已傳送的訊息 （例如，收件匣）。<br /><br /> 這項資料會出現，除非該訊息已完成訊息修復。                                                                                                                                      | 商務資料 - TEXT |

