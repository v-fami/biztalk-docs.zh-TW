---
title: "設定登入 SAP 系統的認證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb41106b-b673-4fcf-a56e-6208e3113469
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a6ace75f66bb7fdd4cfb3362f7d019ab99d73bf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-sign-in-credentials-for-the-sap-system"></a>設定登入 SAP 系統的認證
[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]需要配接器用戶端提供用戶端認證。 配接器使用這些認證來驗證與 SAP 系統的使用者，並建立連接。  
  
 配接器用戶端會提供用戶端認證，這兩個設計階段或執行階段。 在設計階段需要認證才能產生中繼資料。 在執行階段，認證才能執行 SAP 系統上的作業。 本節提供在設計階段和執行的階段指定用戶端認證的相關資訊。  
  
## <a name="enter-the-client-credentials-at-design-time"></a>在設計階段中輸入用戶端認證  
 設計階段，您可以指定使用的認證[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。  
  
### <a name="enter-credentials-using-consume-adapter-service-add-in"></a>輸入使用配接器服務增益集所使用的認證  
  
1.  以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下 **新增產生的項目**。  
  
2.  在**新增產生的項目**對話方塊方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**類別**|按一下**取用配接器服務**。|  
    |**範本**|按一下**取用配接器服務**。|  
  
3.  若要啟動**取用配接器服務**對話方塊中，按一下 **新增**。  
  
4.  在**取用配接器服務**對話方塊中，從**選取繫結**清單中，選取**sapBinding**，然後按一下 **設定**。  
  
5.  在**設定配接器**對話方塊中，按一下 [**安全性**] 索引標籤並從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**並指定使用者名稱和密碼以連接到 SAP 系統。  
  
6.  按一下 **[確定]**。  
  
### <a name="enter-credentials-using-add-adapter-metadata-wizard"></a>輸入認證，使用 新增配接器中繼資料精靈  
  
1.  以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下 **新增產生的項目**。  
  
2.  在**新增產生的項目**對話方塊方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**類別**|按一下**新增介面卡**。|  
    |**範本**|按一下**新增配接器中繼資料**。|  
  
3.  按一下 **[加入]**。 [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。  
  
4.  在 新增配接器精靈 中，選取  **WCF SAP**。 選取的電腦安裝 BizTalk Server 和 BizTalk 資料庫的名稱。  
  
    > [!IMPORTANT]
    >  如果您已經在 BizTalk 中設定 WCF SAP 連接埠，選取 從連接埠**連接埠**清單。  
  
5.  按一下 **[下一步]**。  
  
6.  在**取用配接器服務**對話方塊中，從**選取繫結**清單中，選取**sapBinding**，然後按一下 **設定**。  
  
7.  在**設定配接器**對話方塊中，按一下 [**安全性**] 索引標籤並從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**並指定使用者名稱和密碼以連接到 SAP 系統。  
  
8.  按一下 **[確定]**。  
  
## <a name="enter-client-credentials-at-run-time"></a>在執行階段輸入用戶端認證  
 執行階段，您可以指定用戶端認證中的 WCF 自訂 」 或 「 WCF SAP 連接埠組態的一部分[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
### <a name="enter-credentials-for-the-wcf-custom-port"></a>WCF 自訂連接埠輸入認證  
  
1.  啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立的連接埠，並按一下**傳送埠**或**接收埠**。 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  
  
3.  在 連接埠屬性 對話方塊中，從**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。  
  
    > [!NOTE]
    >  若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**在左窗格中的連接埠屬性對話方塊、 標籤，然後按一下**新增**。  
  
4.  傳送埠，在**Wcf-custom 傳輸屬性**對話方塊中，按一下 **認證**索引標籤，然後執行下列其中一項：  
  
    -   選取**不會使用單一登入**選項，並指定使用者名稱和密碼以連接到 SAP 系統。  
  
    -   選取**使用單一登入**選項，並指定分支機構企業單一登入 (SSO) 應用程式。  
  
5.  接收埠，在**Wcf-custom 傳輸屬性**對話方塊中，按一下 **其他**索引標籤，然後執行下列其中一項：  
  
    -   選取**使用者帳戶**選項，並指定使用者名稱和密碼以連接到 SAP 系統。  
  
    -   選取**取得認證從分支機構應用程式**選項，並指定分支機構應用程式。  
  
6.  按一下 **[確定]**。  
  
### <a name="enter-credentials-for-the-wcf-sap-port"></a>輸入 WCF SAP 連接埠的認證  
  
1.  啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2.  加入 WCF SAP 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如需指示，請參閱[將 SAP 配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md)。  
  
3.  在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立的連接埠，並按一下**傳送埠**或**接收埠**。 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  
  
4.  在 [連接埠屬性] 對話方塊中，從**類型**下拉式清單中，選取您之前，加入 WCF SAP 配接器，然後按一下**設定**。  
  
    > [!NOTE]
    >  若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**在左窗格中的連接埠屬性對話方塊、 標籤，然後按一下**新增**。  
  
5.  如果您要建立傳送埠，在 [傳輸屬性] 對話方塊中，按一下**認證**索引標籤，然後執行下列其中一項：  
  
    1.  選取**不會使用單一登入**選項，並指定使用者名稱和密碼以連接到 SAP 系統。  
  
    2.  選取**使用單一登入**選項，並指定分支機構企業單一登入 (SSO) 應用程式。  
  
6.  如果您要建立接收埠，在**Wcf-custom 傳輸屬性**對話方塊中，按一下 **其他**索引標籤，然後執行下列其中一項：  
  
    1.  選取**使用者帳戶**選項，並指定使用者名稱和密碼以連接到 SAP 系統。  
  
    2.  選取**取得認證從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。  
  
7.  按一下 **[確定]**。  
  
> [!NOTE]
>  [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]也支援 「 企業單一登入 (SSO) 系統。 SSO 選項只適用於 BizTalk 案例中，在其中[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]所知的 SSO 分支機構應用程式。 如需相對於 BizTalk Server 安全性的詳細資訊，請參閱[安全性與 SAP 配接器和 BizTalk Server](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md)。
  
## <a name="see-also"></a>另請參閱  
[若要建立的 SAP 應用程式的建置組塊](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)