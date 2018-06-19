---
title: 步驟 4： 建立 Fabrikam 0 C 4 交易夥伴協議 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- double action tutorial, creating agreements
ms.assetid: a99c2cd1-0d42-4fae-a380-a53d77cd87d0
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb980ae879f06beaf468ba9b526ddc4ba83b5b06
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25966972"
---
# <a name="step-4-creating-the-fabrikam-0c4-trading-partner-agreement"></a>步驟 4： 建立 Fabrikam 0 C 4 交易夥伴協議
在此步驟中，您將使用 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 管理主控台，在 Contoso 與 Fabrikam 之間建立交易夥伴協議。 您將為 0C4 交易夥伴介面程序 (PIP) 建立新的交易夥伴協議。  
  
### <a name="to-start-the-btarn-management-console"></a>若要啟動 BTARN 管理主控台  
  
-   按一下**啟動**，指向 **所有程式**，指向  **Microsoft BizTalk\<版本\>Accelerator for RosettaNet**，然後按一下  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** 管理主控台。  
  
### <a name="to-create-the-0c4-trading-partner-agreement"></a>若要建立 0C4 交易夥伴協議  
  
1.  在 **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** 管理主控台中，展開[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，以滑鼠右鍵按一下**協議**，指向 **新增**，然後按一下 **協議**.  
  
2.  在 [新協議屬性] 對話方塊上**一般**索引標籤上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|型別**Fabrikam_To_Contoso_0C4**。|  
    |**程序組態**|選取**STD_0C4_R01.02**從下拉式清單。|  
    |**我的組織**|選取**Fabrikam**從下拉式清單。|  
    |**夥伴組織**|選取**Contoso**從下拉式清單。|  
    |**RNIF 版本**|選取**V02.00.01**從下拉式清單。|  
    |**主要角色**|選取**啟動器 （啟動者）** 從下拉式清單。|  
    |**使用方式**|選取**測試**從下拉式清單。|  
  
3.  按一下**連接埠**索引標籤，然後再執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**動作 URL**|型別**https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**。|  
    |**信號 URL**|型別**https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**。|  
    |**同步 URL**|型別**https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**。|  
  
4.  按一下 **[確定]**。  
  
5.  以滑鼠右鍵按一下**Fabrikam_To_Contoso_0C4**協議，然後再按一下**Activate**。  
  
## <a name="see-also"></a>請參閱  
 [步驟 5：建立 Fabrikam 3A2 交易夥伴協議](../../adapters-and-accelerators/accelerator-rosettanet/step-5-creating-the-fabrikam-3a2-trading-partner-agreement.md)