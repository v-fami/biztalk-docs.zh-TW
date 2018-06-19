---
title: 設定連接埠使用 wcf-custom 配接器與 SQL 配接器在 BizTalk |Microsoft 文件
description: 建立 WCF 自訂傳送和接收 BizTalk Server 中使用 SQL Server 配接器的連接埠
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d44d9932-0a5e-4072-a480-2f8dc544ca79
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0c2a47cf267bd3316600ad68a241a204090f3da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22226030"
---
# <a name="configure-a-port-using-the-wcf-custom-adapter-and-sql-adapter"></a>設定使用 wcf-custom 配接器和 SQL 配接器的連接埠
若要設定 Wcf-custom 傳送埠和接收埠來執行 SQL Server 使用的傳出和傳入作業步驟[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
## <a name="prerequisites"></a>必要條件  
使用成員的帳戶登入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]系統管理員 」 或 「 BizTalk 操作員群組。 如需詳細的權限的相關資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)，和[最低安全性權限](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx)。 
  
## <a name="deploy-adapters-to-send-messages-to-sql-server"></a>部署配接器將訊息傳送至 SQL Server  
 執行下列步驟來設定 Wcf-custom 傳送埠將訊息傳送至 SQL Server 使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。    
 
1.  啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3.  展開想要部署您的應用程式[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
4.  以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後指向您想要根據的模式之間的通訊設定的連接埠類型[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和 SQL Server。  
  
5.  在**傳送埠屬性**對話方塊**一般**索引標籤上，輸入傳送埠的名稱。  
  
6.  從**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。  
  
7.  在**Wcf-custom 傳輸屬性**對話方塊方塊中，執行下列動作：  
  
    1.  按一下**一般** 索引標籤，然後在**位址 (URI)** 欄位中，指定 SQL Server 的連線 URI。 如需連線 URI 的詳細資訊，請參閱[建立 SQL Server 連接 URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)。  
  
    2.  在**一般**索引標籤的**動作**文字方塊中，輸入作業的動作。 請參閱[訊息與訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)的每個作業的動作清單。 例如，叫用 SQL Server 資料庫中的資料表的 Insert 作業的動作是：  
  
        ```  
        TableOp/Insert/dbo/Employee  
        ```  
  
        > [!NOTE]
        >  員工有 SQL Server 資料庫中資料表的名稱。  
  
    3.  按一下**繫結** 索引標籤，並從**繫結的型別**清單中，選取**sqlBinding**。 您可以指定不同的繫結屬性所公開[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
    4.  按一下**認證**索引標籤，然後再執行下列其中一項：  
  
        -   選取**不會使用單一登入**選項，以及指定的使用者名稱和密碼來連接到 SQL Server。 請注意使用者名稱和密碼會區分大小寫。  
  
            > [!NOTE]
            >  如果您想要連接到 SQL Server 使用 Windows 驗證，請指定空白的使用者名稱和密碼。 這麼做之前，使用您登入的 Windows 使用者必須加入至 SQL Server 中所述[連接到 SQL Server 使用 Windows 驗證搭配 SQL 配接器](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。  
  
        -   選取**使用單一登入**選項，然後再指定分支機構企業單一登入 (SSO) 應用程式。  
  
             如需相對於 BizTalk Server 安全性的詳細資訊，請參閱[使用 SQL 配接器和 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md)。  
  
    5.  若要返回**傳送埠屬性**對話方塊中，按一下 **確定**。  
  
8.  從**傳送處理常式**清單中，選取**BizTalkServerApplication**。  
  
9. 如果您選擇**靜態單向傳送埠**在步驟 4 中，指定傳送管線。 從**傳送管線**清單中，選取對應至 XMLTransmit 管線。  
  
10. 如果您選擇**靜態請求-回應連接埠**在步驟 4 中，指定傳送和接收管線。  
  
    1.  從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。  
  
    2.  從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。  
  
11. 按一下 **[確定]**。  
  
## <a name="deploy-adapters-to-receive-messages-from-sql-server"></a>部署 SQL Server 從接收訊息的配接器
 執行下列步驟來設定 Wcf-custom 接收埠接收訊息，從 SQL Server 使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
1.  啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3.  展開想要部署您的應用程式[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
4.  以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下**單向接收埠**或**要求回應接收埠**，取決於之間的通訊模式[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和 SQL Server。  
  
5.  在**接收埠屬性**對話方塊**一般**索引標籤上，輸入接收埠的名稱。  
  
6.  在**接收位置**索引標籤上，按一下 **新增**。 **接收位置屬性** 對話方塊隨即出現。  
  
7.  在**接收位置屬性**對話方塊方塊中，執行下列動作：  
  
    1.  指定接收位置的名稱。  
  
    2.  從**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。  
  
8.  在**Wcf-custom 傳輸屬性**對話方塊方塊中，執行下列動作：  
  
    1.  按一下**一般** 索引標籤，然後在**位址 (URI)** 欄位中，指定 SQL Server 的連線 URI。 如需連線 URI 的詳細資訊，請參閱[建立 SQL Server 連接 URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)。  
  
    2.  按一下**繫結** 索引標籤，並從**繫結的型別**下拉式清單中，選取**sqlBinding**。 您可以指定不同的繫結屬性所公開[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
    3.  按一下**行為**索引標籤以設定交易隔離等級。 如需設定交易隔離等級的詳細資訊，請參閱[設定交易隔離等級和交易逾時，使用 SQL](../../adapters-and-accelerators/adapter-sql/configure-transaction-isolation-level-and-transaction-timeout-with-sql.md)。  
  
    4.  按一下**其他**索引標籤，然後執行下列其中一項：  
  
        -   選取**使用者帳戶**，並指定使用者名稱和密碼以連接到 SQL Server。 請注意使用者名稱和密碼會區分大小寫。  
  
            > [!NOTE]
            >  如果您想要連接到 SQL Server 使用 Windows 驗證，請指定空白的使用者名稱和密碼。 這麼做之前，使用您登入的 Windows 使用者必須加入至 SQL Server 中所述[連接到 SQL Server 使用 Windows 驗證搭配 SQL 配接器](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。  
  
        -   選取**取得認證從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。  
  
             如需有關安全性[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[使用 SQL 配接器和 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md)。  
  
    5.  若要返回**接收位置屬性**對話方塊中，按一下 **確定**。  
  
9. 從**接收處理常式**下拉式清單中，選取**BizTalkServerApplication**。  
  
10. 如果您選擇**單向接收埠**在步驟 4 中，指定接收管線。 從**接收管線**清單中，選取對應至 XMLReceive 管線。  
  
11. 如果您選擇**要求回應接收埠**在步驟 4 中，指定傳送和接收管線。  
  
    1.  從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。  
  
    2.  從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。  
  
12. 在**接收位置屬性**對話方塊中，按一下 **確定**。  
  
13. 在**接收埠屬性**對話方塊中，按一下 **確定**。  
  
## <a name="see-also"></a>另請參閱  
[手動設定 SQL 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md)