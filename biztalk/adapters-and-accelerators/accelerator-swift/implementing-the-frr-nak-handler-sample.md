---
title: "實作 FRR NAK 處理常式範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80fa5fb7-6864-4923-b641-e76d2b95d923
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a91c0303c9abdf6b1d8c434869445f3c84348935
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="implementing-the-frr-nak-handler-sample"></a>實作 FRR NAK 處理常式範例
若要實作範例 FRR NAK 自訂處理常式，將範例專案加入至方案、 建置和部署專案、 繫結和啟動協調流程，然後停止並重新啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  
  
### <a name="to-implement-the-frr-nak-custom-handler"></a>若要實作 FRR NAK 自訂處理常式  
  
1.  在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，開啟您的方案。 在 方案總管 中，以滑鼠右鍵按一下方案，指向**新增**，然後按一下 **現有專案**。  
  
2.  在**加入現有專案**對話方塊中，移至*\<磁碟機\>*: \Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Samples\FrrHandler。 選取**RepairSWIFTRejectedMessage.btproj**，然後按一下 **開啟**。  
  
3.  產生金鑰，並將專案中的索引鍵。  
  
4.  建置和部署 RepairSWIFTRejectedMessage.btproj 專案。  
  
5.  在 BizTalk 總管 中，展開**BizTalk 組態資料庫**，   **\<*伺服器名稱*\>，BizTalkMgmtDb.dbo** 和**協調流程**，以滑鼠右鍵按一下**RepairSWIFTRejectedMessage.Orchestration_1**，然後按一下 **繫結**。  
  
6.  在**連接埠繫結屬性**對話方塊中，選取您的主機，例如 [biztalkserverapplication]，，然後按一下**確定**。  
  
7.  在 BizTalk 總管 中，以滑鼠右鍵按一下**RepairSWIFTRejectedMessage.Orchestration_1**，然後按一下 **啟動**。  
  
8.  在**快速啟動**對話方塊中，按一下 **確定**。  
  
9. 按一下 **[開始]**，然後按一下 **[執行]**。 輸入**services.msc**，然後按一下 **確定**。 以滑鼠右鍵按一下**BizTalk 服務**，然後按一下 **重新啟動**。