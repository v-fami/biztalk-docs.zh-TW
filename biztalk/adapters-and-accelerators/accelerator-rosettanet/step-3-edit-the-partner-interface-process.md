---
title: 步驟 3： 編輯交易夥伴介面程序 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- modifying, PIPs
- PIPs, modifying
- loopback tutorial, modifying PIPs
ms.assetid: 4d03c598-8ed4-4135-9748-ede101997fd0
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a3b5b6d2f6b0fcbf13ab521bc318eda54ece55f4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003607"
---
# <a name="step-3-edit-the-partner-interface-process"></a>步驟 3： 編輯交易夥伴介面程序
在此步驟中，您可以編輯交易夥伴介面程序 (PIP) 組態設定來停用安全傳輸，如果您沒有在 Microsoft® 網際網路資訊服務 (IIS) 中設定安全通訊端層 (SSL) 憑證。 由於回送實例不支援簽章內送訊息和外寄訊息，您必須變更預設設定才能繼續進行教學課程。 您將修改 STD_0C1_R01.02 PIP。  
  
### <a name="to-edit-the-std0c1r0102-pip"></a>若要編輯 STD_0C1_R01.02 PIP  
  
1. 在  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** 管理主控台中，展開**BizTalk\<版本\>Accelerator for RosettaNet**，按一下 **程序組態設定**，以滑鼠右鍵按一下**STD_0C1_R01.02**，然後按一下**屬性**。  
  
2. 在 STD_0C1_R01.02Properties 對話方塊中，在**活動**索引標籤上，設定**需要安全傳輸**選項設定為`False`。 請只在 IIS Web 伺服器沒有 SSL 憑證的情況下，才執行這個步驟。  
  
3. 設定**不可否認性所需**要`False`，將**需要授權**來`False`，將**來源與內容的不可否認**到`False`，然後按一下 **[確定]**。  
  
    這會停用不可否認性並禁止在簽章訊息中使用憑證。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 4： 建立交易協議](../../adapters-and-accelerators/accelerator-rosettanet/step-4-create-a-trade-agreement.md)   
 [授權與不可否認性屬性](../../adapters-and-accelerators/accelerator-rosettanet/authorization-and-non-repudiation-properties.md)