---
title: "步驟 2： 建立 Fabrikam 交易夥伴組織 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, trading partners
- double action tutorial, creating partner organizations
- trading partners, partner organization
ms.assetid: 4d2ddc4c-2275-4faf-9a36-8a912cc06527
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de00977edecb97420742a6510c3290cfe3c76ea5
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-2-creating-the-fabrikam-partner-organization"></a>步驟 2： 建立 Fabrikam 交易夥伴組織
在這個步驟中，您會使用 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 管理主控台來建立新的交易夥伴。 這個教學課程中的交易夥伴是 Fabrikam 組織。  
  
### <a name="to-start-the-btarn-management-console"></a>若要啟動 BTARN 管理主控台  
  
-   在 Contoso 電腦上，按一下 **啟動**，指向 **所有程式**，指向  **Microsoft BizTalk\<版本\>Accelerator for RosettaNet**，然後按一下   **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** 管理主控台。  
  
### <a name="to-create-fabrikam-as-a-trading-partner"></a>若要建立 Fabrikam 為交易夥伴  
  
1.  在 **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** 管理主控台中，展開[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，以滑鼠右鍵按一下**夥伴**，指向 **新增**，然後按一下**夥伴**.  
  
2.  在 [新交易夥伴屬性] 對話方塊上**一般**索引標籤上，執行下列動作**:**  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|型別**FABRIKAM**。|  
    |**GBI**|型別**987654321**。 **注意：**如果您在同一部電腦上執行回送教學課程，您必須輸入"987654321"以外的 GBI 值。|  
    |**夥伴分類**|選取**購物者**從下拉式清單。|  
    |**簽章憑證**|選取**Fabrikam Signature [憑證指紋]**從下拉式清單。|  
    |**加密憑證**|選取**Fabrikam Encryption [憑證指紋]**從下拉式清單。|  
  
3.  按一下**連絡人屬性**索引標籤，然後再執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**連絡人名稱**|型別**Jane Doe**。|  
    |**E-mail Address**|型別 **jdoe@fabrikam.com** 。|  
    |**電話號碼**|型別**555-555-5555**。|  
    |**傳真號碼**|型別**555-555-5555**。|  
    |**供應鏈代碼**|型別**Electronic Components**。|  
  
4.  按一下 **[確定]**。  
  
## <a name="see-also"></a>請參閱  
 [步驟 3：建立 Contoso 0C2 交易夥伴協議](../../adapters-and-accelerators/accelerator-rosettanet/step-3-creating-the-contoso-0c2-trading-partner-agreement.md)