---
title: 設定使用 wcf-custom 配接器和 Oracle 資料庫配接器的連接埠 |Microsoft Docs
description: 建立 WCF 自訂傳送和接收 BizTalk Server 中使用 Oracle DB 配接器的連接埠
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c99ff526-ad97-4095-812f-0ce88b071e7f
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 513d848d9bf95e75b8b6b983dde7019ce24ecf46
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006479"
---
# <a name="configure-a-port-using-the-wcf-custom-adapter-and-oracle-database-adapter"></a>設定使用 wcf-custom 配接器和 Oracle 資料庫配接器的連接埠
如何設定 Wcf-custom 傳送埠和接收埠，以執行傳出和傳入作業上 Oracle 資料庫使用[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]。  
  
## <a name="prerequisites"></a>必要條件  
使用成員的帳戶登入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]系統管理員 」 或 「 BizTalk 操作員群組。 請參閱[部署和管理 BizTalk 應用程式所需的權限](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)，並[最低安全性權限](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx)指導方針的權限。
  
## <a name="deploy-adapters-for-sending-messages-to-an-oracle-database"></a>部署配接器將訊息傳送至 Oracle 資料庫  
  
1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3. 展開您要在其下部署的應用程式[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
4. 以滑鼠右鍵按一下**傳送埠**，指向**新增**，並指向您想要根據的模式之間的通訊設定的連接埠類型[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和 Oracle 資料庫。  
  
5. 在 **傳送埠屬性**對話方塊的 **一般**索引標籤上，輸入傳送埠的名稱。  
  
6. 從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。  
  
7. 在  **Wcf-custom 傳輸屬性**對話方塊方塊中，執行下列動作：  
  
   1. 按一下 [**一般**] 索引標籤，然後在**位址 (URI)** 欄位中，指定 Oracle 資料庫的連線 URI。 如需連線 URI 的詳細資訊，請參閱[建立的 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)。  
  
   2. 在 **一般**索引標籤中，於**動作**文字方塊中，輸入作業的動作。 請參閱[訊息和訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)的每個作業的動作清單。 例如，叫用插入作業在 Oracle 資料庫中的 HR 結構描述下的員工資料表的動作是：  
  
      ```  
      http://Microsoft.LobServices.OracleDB/2007/03/HR/Table/EMPLOYEE/Select  
      ```  
  
   3. 按一下 **繫結**索引標籤上，以及從**繫結的型別**下拉式清單中，選取**oracleDBBinding**。 您可以指定不同的繫結屬性所公開[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。  
  
   4. 按一下 **認證**索引標籤，然後執行下列其中一項：  
  
      - 選取 **不會使用單一登入**選項，並指定使用者名稱和密碼以連接到 Oracle 資料庫。  
  
        -   若要使用的 Oracle 資料庫的認證連線，請輸入中的資料庫認證**使用者名稱**並**密碼**文字方塊。  
  
        -   若要使用 Windows 驗證進行連接，請輸入**/** 中**使用者名稱**文字方塊中，並保留**密碼**空白的文字方塊。  
  
      - 選取 **使用單一登入**選項，並指定 SSO 分支機構應用程式。  
  
        如需安全性相對於 BizTalk Server 的詳細資訊，請參閱[Oracle 資料庫配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-oracle-database/security-with-the-oracle-database-adapter-and-biztalk-server.md)。  
  
        若要返回**傳送埠屬性** 對話方塊中，按一下**確定**。  
  
8. 從**傳送處理常式**下拉式清單中，選取**BizTalkServerApplication**。  
  
9. 如果您選擇**靜態單向傳送埠**在步驟 4 中，指定傳送管線。 從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。  
  
10. 如果您選擇**靜態請求-回應連接埠**在步驟 4 中，請指定傳送和接收管線。  
  
    1.  從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。  
  
    2.  從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。  
  
11. 按一下 [確定] 。  
  
## <a name="deploy-adapters-for-receiving-messages-from-an-oracle-database"></a>部署用於從 Oracle 資料庫接收訊息的配接器  
  
1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3. 展開您要在其下部署的應用程式[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
4. 以滑鼠右鍵按一下**接收連接埠**，指向**新增**，然後按一下**單向接收埠**或**要求回應接收埠**，取決於BizTalk Server 和 Oracle 資料庫之間的通訊模式。  
  
5. 在 **接收埠屬性**對話方塊的 **一般**索引標籤上，輸入接收埠的名稱。  
  
6. 在 **接收位置**索引標籤上，按一下**新增**。 **接收位置屬性** 對話方塊隨即出現。  
  
7. 在 **接收位置屬性**對話方塊方塊中，執行下列動作：  
  
   1.  指定接收位置的名稱。  
  
   2.  從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。  
  
8. 在  **Wcf-custom 傳輸屬性**對話方塊方塊中，執行下列動作：  
  
   1. 按一下 [**一般**] 索引標籤，然後在**位址 (URI)** 欄位中，指定 Oracle 資料庫的連線 URI。 如需連線 URI 的詳細資訊，請參閱[建立的 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)。  
  
   2. 按一下 **繫結**索引標籤上，以及從**繫結的型別**下拉式清單中，選取**oracleDBBinding**。 您可以指定不同的繫結屬性所公開[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。  
  
   3. 按一下 **其他人**索引標籤，然後執行下列其中一項：  
  
      - 選取 **使用者帳戶**，並指定使用者名稱和密碼以連接到 Oracle 資料庫。  
  
        -   若要使用的 Oracle 資料庫的認證連線，請輸入中的資料庫認證**使用者名稱**並**密碼**文字方塊。  
  
        -   若要使用 Windows 驗證進行連接，請輸入**/** 中**使用者名稱**文字方塊中，並保留**密碼**空白的文字方塊。  
  
      - 選取 **取得認證，從分支機構應用程式**選項，並指定分支機構應用程式。  
  
        如需安全性相對於 BizTalk Server 的詳細資訊，請參閱[Oracle 資料庫配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-oracle-database/security-with-the-oracle-database-adapter-and-biztalk-server.md)。
  
        若要返回**接收位置屬性** 對話方塊中，按一下**確定**。  
  
9. 從**接收處理常式**下拉式清單中，選取**BizTalkServerApplication**。  
  
10. 如果您選擇**單向接收埠**在步驟 4 中，指定接收管線。 從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。  
  
11. 如果您選擇**要求回應接收埠**在步驟 4 中，請指定傳送和接收管線。  
  
    1.  從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。  
  
    2.  從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。  
  
12. 在 [**接收位置屬性**] 對話方塊中，按一下**確定**。  
  
13. 在 [**接收埠屬性**] 對話方塊中，按一下**確定**。  
  
## <a name="see-also"></a>另請參閱  
[手動設定 Oracle 資料庫配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md)   
 [連接到 Oracle 資料庫使用 Windows 驗證](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)