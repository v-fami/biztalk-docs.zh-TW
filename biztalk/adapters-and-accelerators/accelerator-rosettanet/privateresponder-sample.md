---
title: "PrivateResponder 範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3137fadd-9582-4cc6-acfb-c44aca636950
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3de3428aa9971ba62b682494cd94c6bb74bcab53
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="privateresponder-sample"></a>PrivateResponder 範例
PrivateResponder.odx 範例包含 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 所安裝之回應者私用程序的程式碼。 這個一般私用程序會從預設 SQL 配接器架構的傳送埠和接收埠，傳送和接收 RNIF 服務內容訊息。  
  
 根據預設，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]安裝程式安裝中的範例\<*磁碟機*>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk\<版本 > Accelerator for RosettaNet\SDK\PrivateResponder。  
  
## <a name="sample-contents"></a>範例內容  
 回應者私用程序屬於回應者的內部商務程序。 私用程序能讓回應者公開程序和後端商務營運系統程式進行後端整合。 回應者私用程序會與公開程序進行通訊，以回應訊息。  
  
 回應者私用程序對於每個實作而言都是唯一的。 您可以依照您的目的自訂 PrivateResponder.odx 範例。 但是您必須小心，不要對回應者公開程序的功能造成不良影響。  
  
 如需詳細資訊，包括訊息流程的描述，請參閱[回應者私用程序](../../adapters-and-accelerators/accelerator-rosettanet/responder-private-process.md)。  
  
## <a name="see-also"></a>另請參閱  
 [協調流程範例](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md)   
 [私用程序](../../adapters-and-accelerators/accelerator-rosettanet/private-processes.md)