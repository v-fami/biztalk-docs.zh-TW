---
title: "新增 A4SWIFT 使用者及更新 Windows 群組 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user accounts, Windows groups
- Windows groups, user accounts
- user accounts, creating
- Windows groups, updating
- updating Windows groups
- A4SWIFT, creating user accounts
ms.assetid: ddc54457-6499-402c-9cc2-f7b17bbc255f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce3fbf2f3b78b13205b43989c2b0c03909dec392
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="adding-a4swift-users-and-updating-windows-groups"></a>新增 A4SWIFT 使用者及更新 Windows 群組
您建立並安裝 Message Repair 和 New Submission 角色的憑證之後，您必須建立[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者並新增[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]使用者群組。  
  
 **摘要**  
  
 建立訊息修復和新送出的使用者，並新增至本機或網域帳戶[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]使用者群組，如下：  
  
-   在[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]管理主控台中，您需要建立工作流程階段 Message Repair 和 New Submission 程序中有角色的使用者數目。 將完全不同的憑證與每個這些使用者產生關聯。  
  
-   使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]電腦管理公用程式，新增正在建立修復，每個本機使用者驗證，或核准的使用者，A4SWIFT 的訊息。  
  
-   使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]電腦管理公用程式，新增 BizTalk Service BizTalk Group 服務的登入身分 欄位中所列的本機使用者[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]Users 群組。  
  
    > [!NOTE]
    >  如需有關[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者和角色，請參閱[建立部門和角色 Message Repair 和 New Submission](../../adapters-and-accelerators/accelerator-swift/creating-departments-and-roles-for-message-repair-and-new-submission.md)。  
  
### <a name="to-add-user-accounts-to-the-a4swift-users-group"></a>將使用者帳戶新增到 A4SWIFT Users 群組  
  
1.  按一下**啟動**，指向 **所有程式**，指向 **系統管理工具**，然後按一下 **電腦管理**。  
  
2.  在**電腦管理**對話方塊的左窗格中，展開 **本機使用者和群組**，然後按一下 **群組**。  
  
3.  在**電腦管理**對話方塊中的，在右窗格中，按兩下**A4SWIFT 使用者**。  
  
4.  在**A4SWIFT 使用者內容**對話方塊中，按一下 **新增**。  
  
5.  在**選取使用者、 電腦或群組**對話方塊中，於**輸入物件名稱來選取** 窗格中，輸入正在建立、 修復、 驗證，或核准訊息時，本機使用者名稱，然後按一下**確定**。  
  
6.  每個本機使用者建立、 修復、 驗證，或核准訊息重複步驟 5。  
  
7.  在 A4SWIFT 使用者屬性 對話方塊中，按一下 **確定**。  
  
8.  在 電腦管理 對話方塊的左窗格中，展開 服務及應用程式，然後按一下服務。 在右窗格中，按一下  **BizTalk Service BizTalk Group**。 請注意登入身分 一欄中所列的使用者**BizTalk Service BizTalk Group**。  
  
9. 在左窗格中**電腦管理**對話方塊方塊中，展開 **本機使用者和群組**，然後按一下 **群組**。 按兩下**A4SWIFT 使用者**。 確保登入身分 一欄中所列的使用者**BizTalk Service BizTalk Group**屬於**A4SWIFT 使用者**群組。 如果沒有，請新增該使用者**A4SWIFT 使用者**群組。  
  
10. 登出伺服器，並再登入。