---
title: "設定登入認證，Oracle 資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Enter the credentials
helpviewer_keywords:
- credentials, specifying at run time
- credentials, specifying at design time
ms.assetid: d8f62829-ce77-4d82-a411-2eeefb6fe75a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eda20ad4e04a9962e471ab98eb0bc5695b391007
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-sign-in-credentials-for-the-oracle-database"></a>設定登入認證，Oracle 資料庫
[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]需要配接器用戶端提供用戶端認證。 配接器使用這些認證來驗證與 Oracle 資料庫使用者，並建立連接。  
  
 配接器用戶端可以使用時的用戶端認證同時提供[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]以及何時使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 當使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，產生的中繼資料所需的認證。 當使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，不需要的認證來執行的 Oracle 資料庫上的作業。 本主題提供有關指定在用戶端認證資訊[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]和[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
## <a name="specifying-client-credentials-from-visual-studio"></a>指定從 Visual Studio 的用戶端憑證  
 從 Visual Studio 中，您必須指定使用的認證[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。  
  
#### <a name="to-specify-credentials-using-consume-adapter-service-add-in"></a>若要指定使用配接器服務增益集所使用的認證  
  
1.  以滑鼠右鍵按一下您的 BizTalk 專案，然後選取**新增產生的項目**。  
  
2.  在**新增產生的項目**對話方塊方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**類別**|按一下**取用配接器服務**。|  
    |**範本**|按一下**取用配接器服務**。|  
  
3.  若要啟動**取用配接器服務**對話方塊中，按一下 **新增**。  
  
4.  在**取用配接器服務**對話方塊中，從**選取繫結**清單中，選取**oracleDBBinding**，然後按一下**設定**。  
  
5.  在**設定配接器**對話方塊中，按一下 [**安全性**] 索引標籤並從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**並指定使用者名稱和密碼來連接到 Oracle 資料庫：  
  
    -   若要使用的 Oracle 資料庫的認證連接，資料庫中輸入認證**使用者名**和**密碼**文字方塊。  
  
    -   若要使用 Windows 驗證進行連接，輸入 **/** 中**使用者名**文字方塊並保留**密碼**文字方塊留白。  
  
6.  按一下 **[確定]**。  
  
#### <a name="to-specify-credentials-using-add-adapter-metadata-wizard"></a>若要指定認證，使用 新增配接器中繼資料精靈  
  
1.  以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下 **新增產生的項目**。  
  
2.  在**新增產生的項目**對話方塊方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**類別**|按一下**新增介面卡**。|  
    |**範本**|按一下**新增配接器中繼資料**。|  
  
3.  按一下 **[加入]**。 [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。  
  
4.  在[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，選取**Wcf-oracledb**。 選取的電腦上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安裝和 BizTalk 資料庫的名稱。  
  
    > [!IMPORTANT]
    >  如果您已設定在 BizTalk Wcf-oracledb 連接埠，選取從連接埠**連接埠**清單。  
  
5.  按一下 **[下一步]**。  
  
6.  在**取用配接器服務**對話方塊中，從**選取繫結**清單中，選取**oracleDBBinding**，然後按一下 **設定**.  
  
7.  在**設定配接器**對話方塊中，按一下**安全性**索引標籤上，以及從**用戶端認證類型**清單中，選取**Username**和指定使用者名稱和密碼來連接到 Oracle 資料庫：  
  
    -   若要使用的 Oracle 資料庫的認證連接，資料庫中輸入認證**使用者名**和**密碼**文字方塊。  
  
    -   若要使用 Windows 驗證進行連接，輸入 **/** 中**使用者名**文字方塊並保留**密碼**文字方塊留白。  
  
8.  按一下 **[確定]**。  
  
## <a name="specifying-client-credentials-from-the-biztalk-server-administration-console"></a>指定用戶端認證從 BizTalk Server 管理主控台  
 從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您必須指定認證，Wcf-custom 或 Wcf-oracledb 的連接埠組態的一部分。  
  
#### <a name="to-specify-client-credentials-for-the-wcf-custom-port"></a>若要指定 WCF 自訂連接埠的用戶端認證  
  
1.  啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立的連接埠，並按一下**傳送埠**或**接收埠**。 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  
  
3.  在 連接埠屬性 對話方塊中，從**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。  
  
4.  傳送埠，在**Wcf-custom 傳輸屬性**對話方塊中，按一下 **認證**索引標籤，然後執行下列其中一項：  
  
    -   選取**不會使用單一登入**選項，並指定使用者名稱和密碼以連接到 Oracle 資料庫。  
  
        -   若要使用的 Oracle 資料庫的認證連接，資料庫中輸入認證**使用者名**和**密碼**文字方塊。  
  
        -   若要使用 Windows 驗證進行連接，輸入 **/** 中**使用者名**文字方塊並保留**密碼**文字方塊留白。  
  
    -   選取**使用單一登入**選項，並指定分支機構企業單一登入 (SSO) 應用程式。  
  
5.  接收埠，在**Wcf-custom 傳輸屬性**對話方塊中，按一下 **其他**索引標籤，然後執行下列其中一項：  
  
    -   選取**使用者帳戶**選項，並指定使用者名稱和密碼以連接到 Oracle 資料庫。  
  
        -   若要使用的 Oracle 資料庫的認證連接，資料庫中輸入認證**使用者名**和**密碼**文字方塊。  
  
        -   若要使用 Windows 驗證進行連接，輸入 **/** 中**使用者名**文字方塊並保留**密碼**文字方塊留白。  
  
    -   選取**取得認證從分支機構應用程式**選項，並指定分支機構應用程式。  
  
6.  按一下 **[確定]**。  
  
#### <a name="to-specify-credentials-for-the-wcf-oracledb-port"></a>若要指定認證 Wcf-oracledb 連接埠  
  
1.  啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2.  新增 Wcf-oracledb 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如需指示，請參閱[將 Oracle 資料庫配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md)。  
  
3.  在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立的連接埠，並按一下**傳送埠**或**接收埠**。 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  
  
4.  在 連接埠屬性 對話方塊中，從**類型**下拉式清單中，選取**Wcf-oracledb**，然後按一下 **設定**。  
  
    > [!NOTE]
    >  若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**在左窗格中的連接埠屬性對話方塊、 標籤，然後按一下**新增**。  
  
5.  在 連接埠屬性 對話方塊中，按一下**繫結** 索引標籤。從**繫結的型別**下拉式清單中，選取**oracleDBBinding**。  
  
6.  如果您要建立傳送埠，在 [傳輸屬性] 對話方塊中，按一下**認證**索引標籤，然後執行下列其中一項：  
  
    -   選取**不會使用單一登入**選項，並指定使用者名稱和密碼來連接到 Oracle 資料庫。  
  
        -   若要使用的 Oracle 資料庫的認證連接，資料庫中輸入認證**使用者名**和**密碼**文字方塊。  
  
        -   若要使用 Windows 驗證進行連接，輸入 **/** 中**使用者名**文字方塊並保留**密碼**文字方塊留白。  
  
    -   選取**使用單一登入**選項，並指定分支機構企業單一登入 (SSO) 應用程式。  
  
7.  如果您要建立接收埠，在 [傳輸屬性] 對話方塊中，按一下**其他**索引標籤，然後執行下列其中一項：  
  
    -   選取**使用者帳戶**選項，並指定使用者名稱和密碼來連接到 Oracle 資料庫。  
  
        -   若要使用的 Oracle 資料庫的認證連接，資料庫中輸入認證**使用者名**和**密碼**文字方塊。  
  
        -   若要使用 Windows 驗證進行連接，輸入 **/** 中**使用者名**文字方塊並保留**密碼**文字方塊留白。  
  
    -   選取**取得認證從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。  
  
8.  按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式與 Oracle 資料庫的建置組塊](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)   
 [連接到 Oracle 資料庫使用 Windows 驗證](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)