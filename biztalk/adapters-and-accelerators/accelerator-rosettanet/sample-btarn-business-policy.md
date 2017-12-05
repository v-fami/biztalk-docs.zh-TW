---
title: "範例 BTARN 商務原則 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db932c17-8e8f-4f7a-b165-d1d7d749cdb6
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c85cbb7894f0d8bd1b61b7e7856865b49fd33859
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="sample-btarn-business-policy"></a>BTARN 商務原則範例
這個範例是與相關聯的 XML 程式碼[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]®[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]商務規則原則。  
  
 範例檔案是中的 samplebtarnpolicy.xml \<*磁碟機*\>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk\<版本\>Accelerator for RosettaNet\SDK\PIPAutomation\3A4。  
  
## <a name="demonstrates"></a>示範  
 本程式碼顯示具有下列規則的商務規則：  
  
 IF (內送 3A4 Purchase Order 訊息的 AccountNumber = "111111111") 和 (Order < 500 的 MonetaryAmount) THEN 會自動傳送回應訊息  
  
## <a name="see-also"></a>請參閱  
 [使用商務規則的 3A4 私用回應者協調流程](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md)