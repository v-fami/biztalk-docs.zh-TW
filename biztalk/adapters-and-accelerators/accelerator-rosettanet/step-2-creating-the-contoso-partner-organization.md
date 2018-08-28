---
title: 步驟 2： 建立 Contoso 交易夥伴組織 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- double action tutorial, creating partner organizations
ms.assetid: ebb3b166-3781-40b9-89d4-2ca0c83d05f3
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 97e811493c1347bc016671469da8a0dc18483e85
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969775"
---
# <a name="step-2-creating-the-contoso-partner-organization"></a>步驟 2： 建立 Contoso 交易夥伴組織
在此步驟中，您可以使用 Microsoft®[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]管理主控台來建立新的交易夥伴。 這個教學課程中的交易夥伴是 Contoso 組織。  

### <a name="to-start-the-btarn-management-console"></a>若要啟動 BTARN 管理主控台  

- 按一下 **開始**，指向**所有程式**，指向**Microsoft BizTalk\<版本\>Accelerator for RosettaNet**，然後按一下**[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** 管理主控台。  

### <a name="to-create-fabrikam-as-a-trading-partner"></a>若要建立 Fabrikam 為交易夥伴  

1. 在**[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** 管理主控台中，展開[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，以滑鼠右鍵按一下**夥伴**，指向 **新增**，然後按一下**夥伴**.  

2. 在 [新交易夥伴屬性] 對話方塊中，在**一般**索引標籤上，執行下列<strong>:</strong>  


   |          使用          |                             以進行此動作                              |
   |----------------------------|---------------------------------------------------------------------|
   |          **名稱**          |                          型別**CONTOSO**。                          |
   |          **GBI**           |                         型別**123456789**。                         |
   | **夥伴分類** |          選取 **製造商**從下拉式清單。           |
   | **簽章憑證**  | 選取  **Contoso Signature [憑證指紋]** 從下拉式清單。  |
   | **加密憑證** | 選取  **Contoso Encryption [憑證指紋]** 從下拉式清單。 |


3. 按一下 **連絡人屬性**索引標籤，然後再執行下列動作：  


   |       使用        |               以進行此動作                |
   |-----------------------|-----------------------------------------|
   |   **連絡人名稱**    |           型別**John Doe**。            |
   |  **E-mail Address**   | 型別<strong>jdoe@contoso.com</strong>。 |
   | **電話號碼**  |         型別**555-555-5555**。          |
   |    **傳真號碼**     |         型別**555-555-5555**。          |
   | **供應鏈代碼** |     型別**Electronic Components**。     |


4. 按一下 [確定] 。  

## <a name="see-also"></a>另請參閱  
 [步驟 3：建立 Fabrikam 0C2 交易夥伴協議](../../adapters-and-accelerators/accelerator-rosettanet/step-3-creating-the-fabrikam-0c2-trading-partner-agreement.md)