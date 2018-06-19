---
title: 如何管理 BizTalk Server 系統管理員群組 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BizTalk Administrators group, user accounts
- BizTalk Administrators group
- user accounts, BizTalk Administrators group
- Windows Management Instrumentation (WMI), administering
- BizTalk Administrators group, privileges
- security, BizTalk Administrators group
- Administration Console [BizTalk Server], security
- Administration Console [BizTalk Server], administering
- BizTalk Administrators group, about BizTalk Administrators group
ms.assetid: 60ea689b-0b93-4fcc-b49c-6436e7be473f
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2fe92c9c43ccef242d8c14b5f1aa48e0b1a8d852
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254750"
---
# <a name="how-to-manage-the-biztalk-server-administrators-group"></a>如何管理 BizTalk Server 系統管理員群組
「BizTalk Server 系統管理員」群組擁有執行管理工作所需的最低權限。 您要將使用者新增到「BizTalk Server 系統管理員」群組，以便他們可以使用 BizTalk Server 管理主控台或 WMI 提供者來執行管理工作。 當使用者不需再使用 BizTalk Server 管理主控台或 WMI 提供者執行管理工作時，您也要將他們從「BizTalk Server 系統管理員」中移除。  
  
## <a name="prerequisites"></a>必要條件  
 您必須是系統管理員或 Domain Admins 群組的成員，才能執行這個程序。  
  
### <a name="to-add-users-to-the-local-biztalk-server-administrators-group"></a>將使用者新增到本機 BizTalk Server 系統管理員群組  
  
1.  按一下**啟動**，指向 **系統管理工具**，然後按一下 **電腦管理**。  
  
2.  展開**系統工具**，依序展開**本機使用者和群組**，然後按一下 **群組**資料夾。 資料夾內容會在詳細資料窗格中出現。  
  
3.  在 [詳細資料] 窗格中，按一下**BizTalk Server 系統管理員**。  
  
4.  在**動作**功能表上，指向**所有工作**，然後按一下 **新增到群組**。  
  
5.  在**BizTalk Server 系統管理員屬性**對話方塊中，按一下 **新增**。  
  
6.  在**查看**清單中，選取您的網域或電腦名稱。  
  
7.  在包含使用者和電腦相關聯的網域或您在步驟 6 選取的電腦清單中，選取的使用者帳戶新增，請按一下 **新增**，然後按一下 **確定**。  
  
8.  按一下**確定**關閉**BizTalk Server 系統管理員屬性** 對話方塊。  
  
### <a name="to-remove-users-from-local-the-biztalk-server-administrators-group"></a>從本機 BizTalk Server 系統管理員群組移除使用者  
  
1.  按一下**啟動**，指向 **系統管理工具**，然後按一下 **電腦管理**。  
  
2.  展開**系統工具**，依序展開**本機使用者和群組**，然後按一下 **群組**資料夾。 資料夾內容會在詳細資料窗格中出現。  
  
3.  在 [詳細資料] 窗格中，按一下**BizTalk Server 系統管理員**。  
  
4.  在**動作**功能表上，按一下 **屬性**。  
  
5.  在**BizTalk Server 系統管理員屬性**對話方塊中選取的使用者帳戶您想来移除，然後再按一下**移除**。  
  
6.  按一下 **[確定]**。  
  
### <a name="to-add-users-to-the-domain-biztalk-server-administrators-group"></a>將使用者新增到網域 BizTalk Server 系統管理員群組  
  
1.  使用 Domain Admins 帳戶登入連結 SQL Server 資料庫的網域控制站。  
  
2.  按一下**啟動**，指向**所有程式**，指向 **系統管理工具**，然後按一下  **Active Directory 使用者和電腦**至啟動**Active Directory 使用者和電腦**主控台。  
  
    1.  在主控台樹狀目錄中，按一下包含您要新增成員之「BizTalk Server 系統管理員」群組的資料夾。  
  
    2.  在詳細資料窗格中，以滑鼠右鍵按一下 BizTalk Server 系統管理員群組，然後**屬性**。  
  
    3.  在**成員**索引標籤上，按一下 **新增**。  
  
    4.  在**輸入物件名稱來選取**，輸入使用者名稱，然後按一下**確定**。  
  
### <a name="to-remove-users-from-the-domain-biztalk-server-administrators-group"></a>從網域 BizTalk Server 系統管理員群組移除使用者  
  
1.  使用 Domain Admins 帳戶登入連結 SQL 資料庫的網域控制站。  
  
2.  按一下**啟動**，指向**所有程式**，指向 **系統管理工具**，然後按一下  **Active Directory 使用者和電腦**至啟動**Active Directory 使用者和電腦**主控台。  
  
    1.  在主控台樹狀目錄中，按一下包含您要新增成員之「BizTalk Server 系統管理員」群組的資料夾。  
  
    2.  在詳細資料窗格中，以滑鼠右鍵按一下 BizTalk Server 系統管理員群組，然後**屬性**。  
  
    3.  在**成員**索引標籤上，按一下您想要移除，然後按一下的成員**移除**。  
  
    4.  按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BizTalk Server 安全性](../core/managing-biztalk-server-security.md)   
 [管理主控件和服務帳戶](../core/managing-hosts-and-service-accounts.md)   
 [管理 Windows 群組和使用者帳戶的最佳作法](../core/best-practices-for-managing-windows-groups-and-user-accounts.md)   
 [Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)   
 [管理 Windows 群組和使用者帳戶](../core/managing-windows-groups-and-user-accounts.md)