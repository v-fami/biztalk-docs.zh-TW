---
title: 設定使用 WCF-SQL 配接器在 BizTalk 中的連接埠 |Microsoft Docs
description: 建立 WCF SQL 傳送和接收 BizTalk Server 中使用 SQL Server 配接器的連接埠
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f8cdc032-3160-43de-9510-7ca69506083e
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f6a2484c23d4abf8fbe489c3b2fed3ced25b9313
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992071"
---
# <a name="configure-a-port-using-the-wcf-sql-adapter"></a>設定使用 WCF-SQL 配接器的連接埠
本主題提供有關如何設定 WCF SQL 傳送和接收連接埠，以執行 SQL Server 使用的傳出和傳入作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
## <a name="prerequisites"></a>必要條件  
使用成員的帳戶登入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]系統管理員 」 或 「 BizTalk 操作員群組。 如需詳細的權限的相關資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)，並[最低安全性權限](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx)。
  
## <a name="deploy-adapters-to-send-messages-to-sql-server"></a>部署配接器將訊息傳送至 SQL Server  
 執行下列步驟來設定 WCF SQL 傳送埠將訊息傳送至 SQL Server 使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2. 新增 WCF-SQL 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如需相關指示，請參閱 <<c0> [ 將 SQL 配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md)。  
  
3. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
4. 展開您要在其下部署的應用程式[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
5. 以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後指向您想要根據的模式之間的通訊設定的連接埠類型[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和 SQL Server。  
  
6. 在 **傳送埠屬性**對話方塊的 **一般**索引標籤上，輸入傳送埠的名稱。  
  
7. 從**型別**下拉式清單中，選取您稍早新增 WCF-SQL 配接器，然後按一下**設定**。  
  
8. 在 [傳輸屬性] 對話方塊中，執行下列動作：  
  
   1. 按一下 **一般**索引標籤上，按一下**設定**按鈕，然後提供連接參數的值。 如需有關連線 URI 的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱 <<c2> [ 建立 SQL Server 連接 URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)。  
  
   2. 在 **一般**索引標籤中，於**動作**文字方塊中，輸入作業的動作。 請參閱[訊息和訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)的每個作業的動作清單。 例如，叫用 SQL Server 資料庫中的資料表的 Insert 作業的動作是：  
  
      ```  
      TableOp/Insert/dbo/Employee  
      ```  
  
      > [!NOTE]
      >  員工是 SQL Server 資料庫中資料表的名稱。  
  
   3. 按一下 **繫結**索引標籤，然後指定的繫結所公開的屬性值[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
      > [!NOTE]
      >  繫結屬性會顯示根據您要設定傳送埠或接收埠。 比方說，與通知相關的繫結屬性沒有設定傳送埠，因為通知是輸入的作業，並且需要接收埠組態時。  
  
   4. 按一下 **認證**索引標籤，然後再執行下列其中一項：  
  
      -   選取 **不會使用單一登入**選項，以及指定的使用者名稱和密碼來連接到 SQL Server。 請注意，使用者名稱和密碼會區分大小寫。  
  
          > [!NOTE]
          >  如果您想要連接到 SQL Server 使用 Windows 驗證，請指定空白的使用者名稱和密碼。 這麼做之前，Windows 您登入，必須將的使用者加入到 SQL Server 中所述[連接到 SQL Server 使用 Windows 驗證與 SQL 配接器](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。  
  
      -   選取 **使用單一登入**選項，然後再指定分支機構應用程式企業單一登入 (SSO)。  
  
           如需安全性相對於 BizTalk Server 的詳細資訊，請參閱[SQL 配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md)。  
  
   5. 若要返回**傳送埠屬性** 對話方塊中，按一下**確定**。  
  
9. 從**傳送處理常式**清單中，選取**BizTalkServerApplication**。  
  
10. 如果您選擇要建立**靜態單向傳送埠**在步驟 5 中，指定傳送管線。 從**傳送管線**清單中，選取對應至 XMLTransmit 管線。  
  
11. 如果您選擇要建立**靜態請求-回應連接埠**在步驟 5 中，請指定傳送和接收管線。  
  
    1.  從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。  
  
    2.  從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。  
  
12. 按一下 [確定] 。  
  
## <a name="deploy-adapters-to-receive-messages-from-sql-server"></a>部署 SQL Server 從接收訊息的配接器  
 執行下列步驟來設定 WCF SQL 接收埠接收訊息，從 SQL Server 使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2. 新增 WCF-SQL 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如需相關指示，請參閱 <<c0> [ 將 SQL 配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md)。  
  
3. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
4. 展開您要在其下部署的應用程式[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
5. 以滑鼠右鍵按一下**接收連接埠**，指向**新增**，然後按一下**單向接收埠**或**要求回應接收埠**，取決於之間的通訊模式[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和 SQL Server。  
  
6. 在 **接收埠屬性**對話方塊的 **一般**索引標籤上，輸入接收埠的名稱。  
  
7. 在 **接收位置**索引標籤上，按一下**新增**。 **接收位置屬性** 對話方塊隨即出現。  
  
8. 在 **接收位置屬性**對話方塊方塊中，執行下列動作：  
  
   1.  指定接收位置的名稱。  
  
   2.  從**型別**下拉式清單中，選取您稍早新增 WCF-SQL 配接器，然後按一下**設定**。  
  
9. 在 [傳輸屬性] 對話方塊中，執行下列動作：  
  
   1. 按一下 **一般**索引標籤上，按一下**設定**按鈕，然後提供連接參數的值。 如需有關連線 URI 的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱 <<c2> [ 建立 SQL Server 連接 URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)。  
  
   2. 按一下 **繫結**索引標籤，然後指定的繫結所公開的屬性值[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
      > [!NOTE]
      >  繫結屬性會顯示根據您要設定傳送埠或接收埠。 比方說，與通知相關的繫結屬性沒有設定傳送埠，因為通知是輸入的作業，並且需要接收埠組態時。  
  
   3. 按一下 **行為**索引標籤以設定交易隔離等級。 如需有關設定交易隔離等級的詳細資訊，請參閱 <<c0> [ 設定交易隔離等級和交易等待時間，使用 SQL](../../adapters-and-accelerators/adapter-sql/configure-transaction-isolation-level-and-transaction-timeout-with-sql.md)。  
  
   4. 按一下 **其他**索引標籤，然後執行下列其中一項：  
  
      - 選取 **使用者帳戶**，並指定使用者名稱和密碼來連線到 SQL Server。 請注意，使用者名稱和密碼會區分大小寫。  
  
        > [!NOTE]
        >  如果您想要連接到 SQL Server 使用 Windows 驗證，請指定空白的使用者名稱和密碼。 這麼做之前，Windows 您登入，必須將的使用者加入到 SQL Server 中所述[連接到 SQL Server 使用 Windows 驗證與 SQL 配接器](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。  
  
      - 選取 **取得認證，從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。  
  
         如需有關安全性相對於[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱 < [SQL 配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md)。  
  
   5. 若要返回**接收位置屬性** 對話方塊中，按一下**確定**。  
  
10. 從**接收處理常式**下拉式清單中，選取**BizTalkServerApplication**。  
  
11. 如果您選擇要建立**單向接收埠**在步驟 5 中，指定接收管線。 從**接收管線**清單中，選取對應至 XMLReceive 管線。  
  
12. 如果您選擇要建立**要求回應接收埠**在步驟 5 中，請指定傳送和接收管線。  
  
    1.  從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。  
  
    2.  從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。  
  
13. 在 [**接收位置屬性**] 對話方塊中，按一下**確定**。  
  
14. 在 [**接收埠屬性**] 對話方塊中，按一下**確定**。  
  
## <a name="see-also"></a>另請參閱  
[手動設定 SQL 配接器的實體連接埠繫結 ](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md)