---
title: 使用 PIP 規格建立程序組態 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- PIPs, PIP settings
- PIPs, PIP secifications
- process configuration, PIPs
- PIPs, process configuration
ms.assetid: 64f0f5fb-f880-4ef1-95d7-2575b8d0bcff
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 777f32e5a9e035f6009f5450eb48ae8286159f05
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="using-the-pip-specification-to-create-a-process-configuration"></a>使用 PIP 規格建立程序組態
從 RosettaNet 組織 (從 RosettaNet.org) 下載交易夥伴介面程序 (PIP) 後，下載封裝包含 PIP 規格文件。 此文件可指導您在 [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] 管理主控台中建立程序組態時，要使用哪些設定。  
  
## <a name="how-pip-settings-map-to-the-pip-specification"></a>PIP 設定如何對應至 PIP 規格  
 下表描述 PIP 設定如何對應至 RosettaNet PIP 規格中的資訊。  
  
|程序組態設定|PIP 規格中的資訊|  
|-----------------------------------|------------------------------------------|  
|程序代碼|標題頁上的子標題，例如，"PIP3A4"|  
|版本|標題頁上的 PIP「版本識別碼」子標題，例如，"02.02.00"|  
|程序名稱|標題頁上的子標題，例如，"Request Purchase Order"|  
|描述 (一般索引標籤)|3.1 節，商務程序定義|  
|需要不可否認性|表 3-3：商務活動效能控制項|  
|通知時間 (秒)|表 3-3：商務活動效能控制項|  
|需要授權？|表 3-3：商務活動效能控制項|  
|需要持續的機密性|(在 PIP 規格中無參照)|  
|需要安全性傳輸？|表 4-3：訊息交換控制項|  
|單向動作|4.3 節，商務交易對話規格|  
|來源與內容的不可否認性|表 3-3：商務活動效能控制項|  
|重試計數|表 3-3：商務活動效能控制項|  
|執行時間|表 3-3：商務活動效能控制項|  
|名稱|表 3-3：商務活動效能控制項 (活動名稱)|  
|型別|(在 PIP 規格中無參照 - 供日後使用)|  
|描述 (啟動者與回應索引標籤)|表 3-4：PIP 商務文件|  
|名稱 (啟動者與回應索引標籤)|表 3-4：PIP 商務文件|  
|角色 (啟動者與回應索引標籤)|表 3-1：交易夥伴角色描述|  
|角色描述 (啟動者與回應索引標籤)|表 3-1：交易夥伴角色描述|  
|角色類型 (啟動者與回應索引標籤)|表 3-1：交易夥伴角色描述|  
|服務|表 4-1：網路元件規格|  
|服務分類|表 4-1：網路元件規格|  
  
## <a name="see-also"></a>另請參閱  
 [如何建立或編輯程序設定](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)