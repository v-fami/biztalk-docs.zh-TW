---
title: 新增 A4SWIFT 使用者和更新 Windows 群組 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- user accounts, Windows groups
- Windows groups, user accounts
- user accounts, creating
- Windows groups, updating
- updating Windows groups
- A4SWIFT, creating user accounts
ms.assetid: ddc54457-6499-402c-9cc2-f7b17bbc255f
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb276c069a86d060c319f960e666210691b69056
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973327"
---
# <a name="adding-a4swift-users-and-updating-windows-groups"></a>新增 A4SWIFT 使用者和更新 Windows 群組
建立後，當您安裝 Message Repair 和 New Submission 角色的憑證時，您必須建立[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者，並新增[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]使用者群組。  
  
 **摘要**  
  
 建立 Message Repair 和 New Submission 的使用者，並將本機或網域帳戶加入[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]使用者群組，，如下所示：  
  
- 在 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]管理主控台中，您需要建立 Message Repair 和 New Submission 程序的工作流程階段中有角色的使用者數目。 將完全不同的憑證與每個這些使用者產生關聯。  
  
- 使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]電腦管理公用程式，新增建立、 修復，每個本機使用者驗證，或核准 A4SWIFT 使用者的訊息。  
  
- 使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]電腦管理公用程式，將會列在 [BizTalk Service BizTalk Group 服務的 [登入身分] 欄位的本機使用者新增[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]Users 群組。  
  
  > [!NOTE]
  >  如需詳細資訊[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者和角色，請參閱[建立部門和角色 Message Repair 和 New Submission](../../adapters-and-accelerators/accelerator-swift/creating-departments-and-roles-for-message-repair-and-new-submission.md)。  
  
### <a name="to-add-user-accounts-to-the-a4swift-users-group"></a>若要將使用者帳戶新增 A4SWIFT 使用者群組  
  
1.  按一下 **開始**，指向**所有程式**，指向**系統管理工具**，然後按一下**電腦管理**。  
  
2.  在**電腦管理**對話方塊中，在左窗格中，展開**本機使用者和群組**，然後按一下**群組**。  
  
3.  在 **電腦管理**對話方塊中，在右窗格中，按兩下**A4SWIFT 使用者**。  
  
4.  在 [ **A4SWIFT 使用者屬性**] 對話方塊中，按一下**新增**。  
  
5.  在**選取使用者、 電腦或群組**對話方塊中，於**輸入物件名稱來選取**] 窗格中，輸入本機使用者名稱建立、 修復、 驗證，或核准訊息，然後按一下 [**確定**。  
  
6.  針對每個本機使用者建立、 修復、 驗證，或核准訊息重複步驟 5。  
  
7.  在 [A4SWIFT 使用者屬性] 對話方塊中，按一下**確定**。  
  
8.  在 電腦管理 對話方塊的左窗格中，展開 服務及應用程式，然後按一下服務。 在右窗格中，按一下**BizTalk 服務 BizTalk 群組**。 請注意在的 [登入身分] 欄中所列的使用者**BizTalk 服務 BizTalk 群組**。  
  
9. 在左窗格中**電腦管理**對話方塊方塊中，展開**本機使用者和群組**，然後按一下**群組**。 按兩下**A4SWIFT 使用者**。 請確定在的 [登入身分] 欄中所列的使用者**BizTalk Service BizTalk Group**屬於**A4SWIFT 使用者**群組。 如果沒有，請加入該使用者才**A4SWIFT 使用者**群組。  
  
10. 登出伺服器，然後再次登入。