---
title: 設定使用 Wcf-oracleebs 配接器在 BizTalk 中的連接埠 |Microsoft Docs
description: 使用 Wcf-oracleebs 配接器接收或傳送訊息從 BizTalk Server 中的 Oracle EBS
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6b4c5c10-79a6-48d3-b4ee-dddf837f020b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5dc78e6bd96f69bb92018af7a68007acfe47636d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988791"
---
# <a name="configure-a-port-using-the-wcf-oracleebs-adapter"></a>設定使用 Wcf-oracleebs 配接器的連接埠
How to configure Wcf-oracleebs 如何傳送和接收連接埠，以執行傳出和傳入作業上使用 Oracle E-business Suite [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。  
  
## <a name="prerequisites"></a>必要條件  
使用成員的帳戶登入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]系統管理員 」 或 「 BizTalk 操作員群組。 如需詳細的權限的相關資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)，並[最低安全性權限](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx)。
  
## <a name="deploy-adapters-to-send-messages-to-oracle-ebs"></a>部署將訊息傳送至 Oracle EBS 配接器 
 執行下列步驟來設定 Wcf-oracleebs 傳送埠將訊息傳送至 Oracle E-business Suite 使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。    
 
1. 開啟[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2. 新增 Wcf-oracleebs 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 [將 Oracle E-business Suite 配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-ebs/add-the-oracle-ebs-adapter-to-biztalk-server-administration-console.md)列出的步驟。
  
3. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
4. 展開您要在其下部署的應用程式[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。  
  
5. 以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後指向您想要根據的模式之間的通訊設定的連接埠類型[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和 Oracle E-business Suite。  
  
6. 在 **傳送埠屬性**對話方塊的 **一般**索引標籤上，輸入傳送埠的名稱。  
  
7. 從**型別**下拉式清單中，選取 Wcf-oracleebs，，然後按一下**設定**。  
  
8. 在 [傳輸屬性] 對話方塊中，執行下列動作：  
  
   1. 按一下 **一般**索引標籤上，按一下**設定**按鈕，並提供連接參數的值。 如需連線 URI 的詳細資訊，請參閱[設定 Oracle E-business Suite 連線 URI](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-connection-uri-for-oracle-e-business-suite.md)。  
  
   2. 在 **一般**索引標籤中，於**動作**文字方塊中，輸入作業的動作。 請參閱[訊息和 Oracle EBS 配接器的訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)的每個作業的動作清單。 例如，叫用在介面資料表 (FA_BOOKS) 之資產的應用程式下的 Insert 作業的動作是：  
  
      ```  
      InterfaceTables/Insert/OFA/FA/FA_BOOKS  
      ```  
  
   3. 按一下 **繫結**索引標籤，然後指定所公開的繫結屬性的值[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。  
  
      > [!NOTE]
      >  繫結屬性會顯示根據您要設定傳送埠或接收埠。 比方說，與通知相關的繫結屬性沒有設定傳送埠，因為通知是輸入的作業，並且需要接收埠組態時。  
  
   4. 按一下 **認證**索引標籤，然後再執行下列其中一項：  
  
      -   選取 **不會使用單一登入**選項，並指定使用者名稱和密碼以連接到 Oracle E-business Suite。  
  
          |使用|以進行此動作|  
          |--------------|----------------|  
          |**使用 Oracle 資料庫的認證進行連接**|指定**ClientCredentialType**屬性來繫結**資料庫**並指定資料庫的認證**使用者名稱**和**密碼**文字方塊。|  
          |**使用 Oracle E-business Suite 認證進行連接**|指定**ClientCredentialType**屬性來繫結**EBusiness**並指定用於 Oracle E-business Suite 認證**使用者名稱**和**密碼**文字方塊。 在此情況下，您也必須指定 Oracle 資料庫認證**OracleUserName**並**OraclePassword**繫結屬性。|  
          |**若要使用 Windows 驗證，如果 ClientCredentialType 設定為 「 資料庫 」 進行連線**|指定"/"表示**使用者名**文字方塊中，並保留**密碼**空白的文字方塊。|  
          |**若要使用 Windows 驗證，如果 ClientCredentialType 設定為"EBusiness 」 進行連線**|指定 Oracle E-business Suite 認證**使用者名**並**密碼**文字方塊。 您也必須指定"/"表示**OracleUserName**繫結屬性和保持**OraclePassword**繫結屬性為空白。|  
  
      -   選取 **使用單一登入**選項，並指定分支機構應用程式企業單一登入 (SSO)。  
  
   5. 若要返回**傳送埠屬性** 對話方塊中，按一下**確定**。  
  
9. 從**傳送處理常式**清單中，選取**BizTalkServerApplication**。  
  
10. 如果您選擇**靜態單向傳送埠**在步驟 5 中，指定傳送管線。 從**傳送管線**清單中，選取對應至 XMLTransmit 管線。  
  
11. 如果您選擇**靜態請求-回應連接埠**在步驟 4 中，請指定傳送和接收管線。  
  
    1.  從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。  
  
    2.  從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。  
  
12. 按一下 [確定] 。  
  
## <a name="deploy-adapters-to-receive-messages-from-oracle-ebs"></a>部署配接器，以接收來自 Oracle EBS 的訊息  
 執行下列步驟來設定 Wcf-oracleebs 接收埠，讓接收的訊息使用 Oracle E-business Suite[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
1. 開啟[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2. 新增 Wcf-oracleebs 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如需相關指示，請參閱 < [Oracle E-business Suite 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-ebs/add-the-oracle-ebs-adapter-to-biztalk-server-administration-console.md)。  
  
3. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
4. 展開您要在其下部署的應用程式[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。  
  
5. 以滑鼠右鍵按一下**接收連接埠**，指向**新增**，然後按一下**單向接收埠**或**要求回應接收埠**，取決於之間的通訊模式[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和 Oracle E-business Suite。  
  
6. 在 **接收埠屬性**對話方塊的 **一般**索引標籤上，輸入接收埠的名稱。  
  
7. 在 **接收位置**索引標籤上，按一下**新增**。 **接收位置屬性** 對話方塊隨即出現。  
  
8. 在 **接收位置屬性**對話方塊方塊中，執行下列動作：  
  
   1.  指定接收位置的名稱。  
  
   2.  從**型別**下拉式清單中，選取 Wcf-oracleebs，，然後按一下**設定**。  
  
9. 在 [傳輸屬性] 對話方塊中，執行下列動作：  
  
   1. 按一下 **一般**索引標籤上，按一下**設定**按鈕，然後提供連接參數的值。 如需連線 URI 的詳細資訊，請參閱[設定 Oracle E-business Suite 連線 URI](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-connection-uri-for-oracle-e-business-suite.md)。  
  
   2. 按一下 **繫結**索引標籤，然後指定的繫結所公開的屬性值[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。  
  
      > [!NOTE]
      >  繫結屬性會顯示根據您要設定傳送埠或接收埠。 比方說，與通知相關的繫結屬性沒有設定傳送埠，因為通知是輸入的作業，並且需要接收埠組態時。  
  
   3. 按一下 **行為**索引標籤以設定交易隔離等級。 如需有關設定交易隔離等級的詳細資訊，請參閱 <<c0> [ 設定交易隔離等級和交易等待時間，使用 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-ebs.md)。  
  
   4. 按一下 **其他人**索引標籤，然後執行下列其中一項：  
  
      -   選取 **使用者帳戶**選項，並指定使用者名稱和密碼以連接到 Oracle E-business Suite。  
  
          |使用|以進行此動作|  
          |--------------|----------------|  
          |**使用 Oracle 資料庫的認證進行連接**|指定**ClientCredentialType**屬性來繫結**資料庫**並指定資料庫的認證**使用者名稱**和**密碼**文字方塊。|  
          |**使用 Oracle E-business Suite 認證進行連接**|指定**ClientCredentialType**屬性來繫結**EBusiness**並指定用於 Oracle E-business Suite 認證**使用者名稱**和**密碼**文字方塊。 在此情況下，您也必須指定 Oracle 資料庫認證**OracleUserName**並**OraclePassword**繫結屬性。|  
          |**若要使用 Windows 驗證，如果 ClientCredentialType 設定為 「 資料庫 」 進行連線**|指定"/"表示**使用者名**文字方塊中，並保留**密碼**空白的文字方塊。|  
          |**若要使用 Windows 驗證，如果 ClientCredentialType 設定為"EBusiness 」 進行連線**|指定 Oracle E-business Suite 認證**使用者名**並**密碼**文字方塊。 您也必須指定"/"表示**OracleUserName**繫結屬性和保持**OraclePassword**繫結屬性為空白。|  
  
      -   選取 **取得認證，從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。  
  
   5. 若要返回**接收位置屬性** 對話方塊中，按一下**確定**。  
  
10. 從**接收處理常式**下拉式清單中，選取**BizTalkServerApplication**。  
  
11. 如果您選擇**單向接收埠**在步驟 5 中，指定接收管線。 從**接收管線**清單中，選取對應至 XMLReceive 管線。  
  
12. 如果您選擇**要求回應接收埠**在步驟 5 中，請指定傳送和接收管線。  
  
    1.  從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。  
  
    2.  從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。  
  
13. 在 [**接收位置屬性**] 對話方塊中，按一下**確定**。  
  
14. 在 [**接收埠屬性**] 對話方塊中，按一下**確定**。  
  
## <a name="see-also"></a>另請參閱  
 [手動設定實體連接埠繫結至 Oracle E-business 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md)   
 [連接到 Oracle E-business Suite 使用 Windows 驗證](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-windows-authentication.md)