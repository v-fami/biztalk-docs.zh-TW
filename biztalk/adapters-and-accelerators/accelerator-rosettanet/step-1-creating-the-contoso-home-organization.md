---
title: 步驟 1： 建立 Contoso 主要組織 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- double action tutorial, creating home organizations
- creating, home organizations
- home organizations, creating
ms.assetid: 0e7a53b9-ae59-4cd1-88bd-0ada7e65acba
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 303048a06ce1acccac07d10bbe1ac53c32a08122
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000119"
---
# <a name="step-1-creating-the-contoso-home-organization"></a>步驟 1： 建立 Contoso 主要組織
在此步驟中，您可以使用 Microsoft®[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]管理主控台來建立 Contoso 主要組織。  

### <a name="to-start-the-btarn-management-console"></a>若要啟動 BTARN 管理主控台  

- 在 Contoso 電腦上，按一下**開始**，指向**所有程式**，指向**Microsoft BizTalk\<版本\>Accelerator for RosettaNet**，然後按一下  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** 管理主控台。  

### <a name="to-create-the-home-organization"></a>若要建立主要組織  

1. 在[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]管理主控台中，展開[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，以滑鼠右鍵按一下**主要組織**，指向**新增**，然後按一下**所在地組織**。  

2. 在新主要組織屬性 對話方塊中，在**一般**索引標籤上，執行下列動作：  


   |               使用               |                                                                              以進行此動作                                                                               |
   |--------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |               **名稱**               |                                                                           型別**CONTOSO**。                                                                           |
   |               **GBI**                | 型別**123456789**。 **注意：** 如果您在同一部電腦上執行 Loopback 教學課程中，您必須輸入"123456789"以外的 GBI 值。 |
   | **主要組織分類** |                                                           選取 **製造商**從下拉式清單。                                                            |


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
 [步驟 2：建立 Fabrikam 交易夥伴組織](../../adapters-and-accelerators/accelerator-rosettanet/step-2-creating-the-fabrikam-partner-organization.md)