---
title: 步驟 4： 建立 Fabrikam 0c 4 個交易夥伴協議 |Microsoft Docs
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
ms.openlocfilehash: 435f1568ab32769e0f44d8829a0114ca1805dd0a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007831"
---
# <a name="step-4-creating-the-fabrikam-0c4-trading-partner-agreement"></a>步驟 4： 建立 Fabrikam 0c 4 個交易夥伴協議
在此步驟中，您會建立 Contoso 與 Fabrikam 使用 Microsoft® 之間的交易夥伴協議[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]管理主控台。 您將為 0C4 交易夥伴介面程序 (PIP) 建立新的交易夥伴協議。  

### <a name="to-start-the-btarn-management-console"></a>若要啟動 BTARN 管理主控台  

- 按一下 **開始**，指向**所有程式**，指向**Microsoft BizTalk\<版本\>Accelerator for RosettaNet**，然後按一下**[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** 管理主控台。  

### <a name="to-create-the-0c4-trading-partner-agreement"></a>若要建立 0C4 交易夥伴協議  

1. 在**[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** 管理主控台中，展開[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，以滑鼠右鍵按一下**協議**，指向 **新增**，然後按一下 **協議**.  

2. 在 [新協議屬性] 對話方塊中，在**一般**索引標籤上，執行下列動作：  


   |         使用          |                        以進行此動作                         |
   |---------------------------|-----------------------------------------------------------|
   |         **名稱**          |             型別**Fabrikam_To_Contoso_0C4**。             |
   | **程序組態** |    選取  **STD_0C4_R01.02**從下拉式清單。     |
   |    **我的組織**    |       選取  **Fabrikam**從下拉式清單。        |
   | **夥伴組織**  |        選取  **Contoso**從下拉式清單。        |
   |     **RNIF 版本**      |       選取  **V02.00.01**從下拉式清單。       |
   |       **主要角色**       | 選取 **啟動器 （啟動者）** 從下拉式清單。 |
   |         **Usage**         |         選取 **測試**從下拉式清單。          |


3. 按一下 **連接埠**索引標籤，然後再執行下列動作：  


   |    使用    |                          以進行此動作                           |
   |----------------|---------------------------------------------------------------|
   | **動作 URL** | 型別**https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**。 |
   | **信號 URL** | 型別**https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**。 |
   |  **同步 URL**  | 型別**https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**。 |


4. 按一下 [確定] 。  

5. 以滑鼠右鍵按一下**Fabrikam_To_Contoso_0C4**協議，然後再按一下**Activate**。  

## <a name="see-also"></a>另請參閱  
 [步驟 5：建立 Fabrikam 3A2 交易夥伴協議](../../adapters-and-accelerators/accelerator-rosettanet/step-5-creating-the-fabrikam-3a2-trading-partner-agreement.md)