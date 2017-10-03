---
title: "RNIF 訊息處理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RosettaNet Implementation Framework (RNIF)
- RosettaNet, about RosettaNet
- RNIF
- RNIF, non-repudiation
- RNIF, BizTalk Accelerator for RosettaNet
- non-repudiation
- RNIF, about RNIF
- BizTalk Accelerator for RosettaNet, RNIF
- RosettaNet
ms.assetid: 994f15bc-765c-4220-8ab1-176919e9e821
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 34ff8794c6dcc94571607207b4c13e9dd2bf54cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="rnif-message-processing"></a>RNIF 訊息處理
RosettaNet 組織定義 RosettaNet 實作架構 (RNIF) 規格中的訊息交換。 RNIF 定義整合系統傳輸訊息的方式。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]完整實作 RNIF 規格，將功能加入至功能[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]原生提供的方塊外。  
  
 RNIF 通訊相當複雜。 執行 RNIF 處理的公開程序包含各種不同的驗證檢查和複雜工作流程邏輯。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]原生提供這項功能。 這可讓您不需要從頭開發或維護 RNIF 邏輯，就能使用與 RosettaNet 相容的系統。  
  
## <a name="btarn-support-for-rnif"></a>BTARN 對 RNIF 的支援  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]支援兩種 RNIF 版本： RNIF 1.1 與 RNIF 2.0 (V02.00.01)。 RNIF 2.0 已在 RNIF 1.1 支援的功能上新增重要功能，包括加密、附件和同步交易。 RNIF 2.0 對 RNIF 1.1 不具有回溯相容性。  
  
> [!NOTE]
>  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 與 RosettaNet Ready RNIF 2.0 相容。  
  
 兩種版本以不同的方式定義 RosettaNet 訊息。 如需有關不同訊息容器的詳細資訊，請參閱[RNIF 標準](../../adapters-and-accelerators/accelerator-rosettanet/rnif-standard.md)。  
  
 整合系統透過 HTTP/HTTPS 及 SMTP; 執行 RNIF 傳送不過，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]實作只有 HTTP/HTTPS。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]在 RNIF 1.1 不支援附件和同步交易。  
  
### <a name="non-repudiation"></a>不可否認性  
 在 RNIF 標準中，不可否認性為必要條件。 基於此，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 所接收或傳送的任何傳輸格式訊息都會儲存到不可否認性資料庫，如此您可以證明已接收或傳送訊息。 由於此目的，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 使用 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Archive 資料庫中的 MessageStorageIn 資料表儲存內送訊息，並使用相同資料庫中的 MessageStorageOut 資料表儲存外寄訊息。  
  
 在程序組態設定檔中個別設定服務內容及通知的不可否認性需求。 如果您設定一個或兩個**來源與內容的不可否認**和**不可否認性所需**選項，以`True`，然後[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]會儲存下列資料：  
  
|data|目錄|  
|----------|--------------|  
|RecordID|所儲存訊息的專屬唯一識別碼|  
|MessageCategory|要求 (0)、回應 (1) 或信號 (2)|  
|DestinationParty|目的合作對象的名稱|  
|SourceParty|來源合作對象的名稱|  
|PIPCode|例如，PIP3A4|  
|PIPVersion|例如，V02.00|  
|MessageContent|二進位格式訊息|  
|MessageTrackingID|訊息的訊息追蹤識別碼|  
|PIPInstanceID|程序的 PIP 執行個體識別碼|  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Accelerator for RosettaNet 新增至 BizTalk Server](../../adapters-and-accelerators/accelerator-rosettanet/what-biztalk-accelerator-for-rosettanet-adds-to-biztalk-server.md)   
 [PIP 實作](../../adapters-and-accelerators/accelerator-rosettanet/pip-implementation.md)