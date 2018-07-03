---
title: 設定使用 WCF-SAP 配接器在 BizTalk 中的連接埠 |Microsoft Docs
description: 建立 WCF SAP 連接埠來傳送或接收訊息，從使用 mySAP 配接器的 BizTalk 配接器組件 (BAP) 中的 SAP
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 420683f8-2516-4c65-895d-fe535824d450
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a80c778e34505755a147dccf48e50ea9ea3a18d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992671"
---
# <a name="configure-a-port-using-the-wcf-sap-adapter"></a>設定使用 WCF-SAP 配接器的連接埠
本主題提供有關如何設定 WCF SAP 傳送和接收埠來執行 SAP 系統使用的傳出和傳入作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
## <a name="prerequisites"></a>必要條件  
使用成員的帳戶登入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]系統管理員 」 或 「 BizTalk 操作員群組。 如需詳細的權限的相關資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)，並[最低安全性權限](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx)。
  
## <a name="deploy-adapters-to-send-messages-to-sap"></a>部署配接器將訊息傳送至 SAP  
完成下列步驟來設定 WCF SAP 的傳送埠將訊息傳送至 SAP 系統使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2. 新增 WCF SAP 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如需相關指示，請參閱 < [SAP 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md)。  
  
3. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
4. 展開您要在其下部署的應用程式[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
5. 以滑鼠右鍵按一下**傳送埠**，指向**新增**，並指向您想要根據 BizTalk Server 與 SAP 系統之間的通訊模式所設定的連接埠類型。  
  
6. 在 **傳送埠屬性**對話方塊的 **一般**索引標籤上，輸入傳送埠的名稱。  
  
7. 從**型別**下拉式清單中，選取您稍早新增的 WCF SAP 配接器，然後按一下**設定**。  
  
8. 在 [傳輸屬性] 對話方塊中，執行下列動作：  
  
   1. 按一下 **一般**索引標籤上，按一下**設定**按鈕，然後提供連接參數的值。 如需連線 URI 的詳細資訊，請參閱[建立 SAP 系統連線 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。  
  
   2. 在 **一般**索引標籤中，於**動作**文字方塊中，輸入作業的動作。 請參閱[訊息和訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)的每個作業的動作清單。 比方說，是叫用 RFC_CUSTOMER_GET 的動作：  
  
      ```  
      http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET  
      ```  
  
   3. 按一下 **繫結**索引標籤，然後指定的繫結所公開的屬性值[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
      > [!NOTE]
      >  繫結屬性會顯示根據您要設定傳送埠或接收埠。 比方說，繫結屬性與輸入相關的作業無法使用。 在設定傳送埠，因為輸入的作業需要接收埠組態  
  
   4. 按一下 **認證**索引標籤，然後執行下列其中一項：  
  
   -   選取 **不會使用單一登入**選項，並指定使用者名稱和密碼來連線到 SAP 系統。  
  
   -   選取 **使用單一登入**選項，並指定 SSO 分支機構應用程式。  
  
        如需安全性相對於 BizTalk Server 的詳細資訊，請參閱[SAP 配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md)。  
  
        若要返回**傳送埠屬性** 對話方塊中，按一下**確定**。  
  
9. 從**傳送處理常式**下拉式清單中，選取**BizTalkServerApplication**。  
  
10. 如果您選擇要建立**靜態單向傳送埠**在步驟 5 中，指定傳送管線。 從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。  
  
11. 如果您選擇要建立**靜態請求-回應連接埠**在步驟 5 中，請指定傳送和接收管線。  
  
    1.  從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。  
  
    2.  從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。  
  
12. 按一下 [確定] 。  
  
## <a name="deploy-adapters-to-receive-messages-from-sap"></a>部署至從 SAP 接收訊息的配接器  
完成下列步驟來設定 WCF SAP 接收埠接收訊息，從 SAP 系統使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2. 新增 WCF SAP 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如需相關指示，請參閱 < [SAP 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md)。  
  
3. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
4. 展開您要在其下部署的應用程式[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
5. 以滑鼠右鍵按一下**接收連接埠**，指向**新增**，然後按一下**單向接收埠**或**要求回應接收埠**取決於BizTalk Server 與 SAP 系統之間的通訊模式。  
  
6. 在 **接收埠屬性**對話方塊的 **一般**索引標籤上，輸入接收埠的名稱。  
  
7. 在 **接收位置**索引標籤上，按一下**新增**。 **接收位置屬性** 對話方塊隨即出現。  
  
8. 在 **接收位置屬性**對話方塊方塊中，執行下列動作：  
  
   1.  指定接收位置的名稱。  
  
   2.  從**型別**下拉式清單中，選取您稍早新增的 WCF SAP 配接器，然後按一下**設定**。  
  
9. 在 [傳輸屬性] 對話方塊中，執行下列動作：  
  
   1. 按一下 **一般**索引標籤上，按一下**設定**按鈕，然後提供連接參數的值。 如需連線 URI 的詳細資訊，請參閱[建立 SAP 系統連線 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。  
  
   2. 按一下 **繫結**索引標籤上，以及從**繫結的型別**下拉式清單中，選取**sapBinding**。 如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
      > [!NOTE]
      >  繫結屬性會顯示根據您要設定傳送埠或接收埠。 比方說，繫結屬性與輸入相關的作業無法使用。 在設定傳送埠，因為輸入的作業需要接收埠組態  
  
   3. 按一下 **其他**索引標籤，然後執行下列其中一項：  
  
   4. 選取 **使用者帳戶**，並指定使用者名稱和密碼來連線到 SAP 系統。  
  
   5. 選取 **取得認證，從分支機構應用程式**選項，並指定分支機構應用程式。  
  
       如需安全性相對於 BizTalk Server 的詳細資訊，請參閱[SAP 配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md)。  
  
       按一下 [ **[確定]** 以返回**接收位置屬性**] 對話方塊。  
  
10. 從**接收處理常式**下拉式清單中，選取**BizTalkServerApplication**。  
  
11. 如果您選擇要建立**單向接收埠**在步驟 5 中，指定接收管線。 從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。  
  
12. 如果您選擇要建立**要求回應接收埠**在步驟 5 中，請指定傳送和接收管線。  
  
    1.  從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。  
  
    2.  從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。  
  
13. 按一下 [ **[確定]** 中**接收位置屬性**] 對話方塊。  
  
14. 按一下 [ **[確定]** 中**接收埠屬性**] 對話方塊。

## <a name="see-also"></a>另請參閱
[以手動方式設定 SAP 配接器的實體連接埠繫結](manually-configure-a-physical-port-binding-to-the-sap-adapter.md)