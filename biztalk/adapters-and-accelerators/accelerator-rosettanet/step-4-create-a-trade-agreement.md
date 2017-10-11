---
title: "步驟 4： 建立交易協議 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, trade agreeements
- loopback tutorial, creating trade agreements
- agreements, creating
ms.assetid: 9bcb80b1-fefc-4f1c-ae03-fb736cdfd524
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b94acad2b71694223b0566f86edfcfa86610099
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-create-a-trade-agreement"></a>步驟 4： 建立交易協議
在此步驟中，您將使用 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 管理主控台，建立主要組織和夥伴組織之間的交易協議。  
  
### <a name="to-create-a-trade-agreement"></a>若要建立交易協議  
  
1.  在 **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** 管理主控台中，展開 **BizTalk\<版本 > Accelerator for RosettaNet**，以滑鼠右鍵按一下**協議**，按一下**新**，然後按一下 **協議**。  
  
2.  在**新協議屬性**對話方塊**一般**索引標籤上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|型別**交易協議**。|  
    |**程序組態**|選取**STD_0C1_R01.02**從下拉式清單。|  
    |**我的組織**|選取**首頁**從下拉式清單。|  
    |**夥伴組織**|選取**夥伴**從下拉式清單。|  
    |**主要角色**|選取**啟動器**從下拉式清單。|  
  
3.  在**新協議屬性**對話方塊**連接埠**索引標籤上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**動作 URL**|型別**http://localhost/BTARNApp/RNIFReceive.aspx**。|  
    |**信號 URL**|型別**http://localhost/BTARNApp/RNIFReceive.aspx**。|  
    |**同步 URL**|保留空白。 同步化交易夥伴介面程序 (PIP) 不需要「同步 URL」。|  
  
4.  按一下**套用**，然後按一下 **確定**。  
  
 建立交易協議之後，必須加以啟動。  
  
### <a name="to-activate-the-trade-agreement"></a>啟動交易協議  
  
-   在[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]管理主控台中，展開[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，按一下 **協議**，以滑鼠右鍵按一下**交易協議**在結果窗格中，然後按一下**Activate**.  
  
## <a name="see-also"></a>另請參閱  
 [步驟 5： 建立鏡像協議](../../adapters-and-accelerators/accelerator-rosettanet/step-5-create-a-mirror-agreement.md)