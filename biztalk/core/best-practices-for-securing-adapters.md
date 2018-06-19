---
title: 保護配接器的最佳作法 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapters, security
- best practices, adapters
- adapters, permissions
- security, adapters
- permissions, adapters
- best practices, security
- adapters, best practices
ms.assetid: 004e1a01-b316-4eee-967f-5a806431de2b
caps.latest.revision: 25
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86abbba06e851b9b289b29cd7fbbf01b3af292a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233294"
---
# <a name="best-practices-for-securing-adapters"></a>保護配接器安全的最佳作法
本主題提供配接器安全性的最佳作法清單。  
  
 **請勿在您的電腦上安裝不受信任的配接器請只使用認證配接器開發夥伴。**  
  
 **不要將敏感的顧客資料儲存預設配接器結構描述中。**  
  
 您應該只在部署配接器後設定使用者名稱及密碼資訊。 這樣做可確保資訊會儲存在 SSO 資料庫中。 如需 SSO 資料庫的詳細資訊，請參閱[使用 SSO](../core/using-sso.md)。  
  
 **授與共用資料夾 （接收資料夾和傳送資料夾），可用來拾取及放置檔案使用 File 及 EDI 配接器上的下列權限：**  
  
-   **接收資料夾**  
  
     可以在接收位置設定 FILE 配接器的接收資料夾。 可以在接收處理常式設定 EDI 配接器的接收資料夾。 拾取檔案之 BizTalk 主控件的服務帳戶，在檔案系統層級應該具有以下權限：  
  
    -   清單資料夾 / 讀取資料  
  
    -   刪除子資料夾和檔案  
  
     若接收資料夾位於網路共用上，在檔案共用層級必須授與以下權限：  
  
    -   拾取檔案之 BizTalk 主控件的服務帳戶，必須具有「完整控制」權限。  
  
    -   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員必須具有「完整控制」權限才能進行疑難排解。  
  
    -   放置檔案至此位置的外部使用者或程式必須具有「寫入」權限。  
  
-   **傳送資料夾**  
  
     可以在傳送埠設定 FILE 及 EDI 配接器的傳送資料夾。  
  
    -   放置檔案之 BizTalk 主控件的服務帳戶，必須具有「寫入」權限。  
  
    -   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員必須具有「完整控制」權限。  
  
    -   拾取檔案的外部使用者或程式必須具有「讀取」權限。  
  
 **新增 EDI 服務執行 BTS_HOST_USERS SQL 角色的使用者帳戶。**  
  
 這是必要步驟，如此一來，您不需要管理權限也可取得 BizTalk 總管物件管理 (OM) 存取權。 若要執行這個程序，請將「EDI 子系統使用者」新增到 BizTalk 管理資料庫 (BizTalkMgmtDb) 中的 BTS_HOST_USERS 角色。  
  
 若要將 「 EDI 子系統使用者 」 加入至 SQL Server 2005 上的 BTS_HOST_USERS 角色，完成下列步驟：  
  
1.  啟動 SQL Server Management Studio 從**開始時，程式，Microsoft SQL Server 2008**。  
  
2.  連接到裝載 BizTalk 管理資料庫的 SQL Server。  
  
3.  在 [物件總管] 中展開此伺服器。  
  
4.  展開**資料庫**，然後展開 BizTalk 管理資料庫。  
  
5.  展開**安全性**，依序展開**角色**，然後按一下以選取**資料庫角色**  
  
6.  在詳細資料窗格中，以滑鼠右鍵按一下 BTS_HOST_USERS 角色，然後**屬性**。  
  
7.  在 BTS_HOST_USERS 對話方塊中，按一下**新增**，按一下 **瀏覽**，然後核取方塊，將它加入到 EDI 子系統使用者群組的旁邊。  
  
     若使用者清單中沒有可新增的「EDI 子系統使用者」群組，您必須將「EDI 子系統使用者」群組當作新資料庫使用者新增到 BizTalk 管理資料庫。 若要將「EDI 子系統使用者」群組新增成為新的資料庫使用者，請在 SQL Server Management Studio 中完成下列步驟：  
  
    1.  展開 BizTalk 管理資料庫。  
  
    2.  展開**安全性**。  
  
    3.  以滑鼠右鍵按一下**使用者**按一下**新使用者**。  
  
    4.  按一下省略符號 （...） 按鈕旁的文字方塊**登入名稱**顯示**選取登入** 對話方塊。  
  
    5.  按一下瀏覽按鈕中，輸入**EDI 子系統使用者**群組，然後再按一下 **[確定]。** 如果系統提示**找到多個物件**對話方塊中，選取**EDI 子系統使用者**登入並按一下**確定**。  
  
    6.  上**資料庫使用者-新增**對話方塊中輸入**EDI 子系統使用者**如**使用者名稱**文字方塊中，按一下 **確定**。  
  
 **新增 BizTalk 服務執行 EDI 子系統使用者群組的使用者帳戶。**  
  
 請依照下列步驟執行，新增 BizTalk 服務的使用者帳戶到「EDI 子系統使用者」群組中。  
  
-   **如果 BizTalk Server 設定為使用網域群組：**  
  
    1.  請在網域中登入 Windows Server 電腦。  
  
    2.  按一下**啟動**，按一下 **所有程式**，按一下 **系統管理工具**，然後按一下  **Active Directory 使用者和電腦**。  
  
        > [!NOTE]
        >  您必須擁有適當的網域層級權限來修改物件中的**Active Directory 使用者和電腦**介面。  
  
    3.  按一下以展開網域容器，然後按一下以展開**使用者**容器。  
  
    4.  按兩下  **EDI 子系統使用者**群組以顯示此群組的內容。  
  
    5.  按一下**成員** 索引標籤**EDI 子系統使用者**群組 對話方塊。  
  
    6.  按一下**新增** 按鈕，將 BizTalk 服務的使用者帳戶新增到此群組。  
  
    7.  按一下 **[確定]**。  
  
-   **如果 BizTalk Server 設定為使用本機群組：**  
  
    1.  請登入 BizTalk Server。  
  
    2.  按一下**啟動**，按一下 **所有程式**，按一下 **系統管理工具**，然後按一下 **電腦管理**。  
  
    3.  按一下以展開**系統工具**，按一下以展開**本機使用者和群組**，然後按一下以展開**群組**。  
  
    4.  按兩下  **EDI 子系統使用者**群組以顯示此群組的內容。  
  
    5.  按一下**新增**按鈕，將 BizTalk 服務的使用者帳戶加入到此群組。  
  
    6.  按一下 **[確定]**。