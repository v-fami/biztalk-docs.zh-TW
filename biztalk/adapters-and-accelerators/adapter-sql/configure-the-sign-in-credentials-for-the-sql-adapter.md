---
title: 設定登入認證 SQL 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c20e177-0e64-4df3-a3dd-dca3fcf314db
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f07a3840524988e5f643ca89799b7c7f23ff0fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22226238"
---
# <a name="configure-the-sign-in-credentials-for-the-sql-adapter"></a>設定登入認證 SQL 配接器
[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]需要配接器用戶端提供用戶端認證。 配接器使用這些認證來驗證與 SQL Server 使用者並建立連接。  
  
 配接器用戶端可以使用時的用戶端認證同時提供[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]以及何時使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 當使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，產生的中繼資料所需的認證。 當使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，不需要的認證來執行 SQL Server 上的作業。  
  
 本節提供有關指定在用戶端認證的詳細資訊[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]和[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
## <a name="enter-credentials-from-visual-studio"></a>從 Visual Studio 中輸入認證  
 從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您可以指定使用的認證[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。  
  
### <a name="using-consume-adapter-service-add-in"></a>使用會耗用配接器服務增益集  
  
1.  以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後選取**新增產生的項目**。  
  
2.  在**新增產生的項目**對話方塊方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**類別**|按一下**取用配接器服務**。|  
    |**範本**|按一下**取用配接器服務**。|  
  
3.  若要啟動**取用配接器服務**對話方塊中，按一下 **新增**。  
  
4.  在**取用配接器服務**對話方塊中，從**選取繫結**清單中，選取**sqlBinding**，然後按一下 **設定**。  
  
5.  在**設定配接器**對話方塊中，按一下**安全性** 索引標籤，並從**用戶端認證類型**清單中，執行下列其中一項：  
  
    > [!NOTE]
    >  如果您要連接到 SQL Server 使用 Windows 驗證，使用您登入的 Windows 使用者必須加入至 SQL Server 中所述[連接到 SQL Server 使用 Windows 驗證與 SQL 配接器](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。  
  
    |按一下此選項|動作|  
    |----------------|----------------|  
    |**無**|使用 Windows 驗證連接到 SQL Server。|  
    |**視窗**|使用 Windows 驗證連接到 SQL Server。|  
    |**使用者名稱**|指定的使用者名稱和密碼來連接到 SQL Server 藉由指定使用者在 SQL Server 資料庫中定義的認證。 請注意使用者名稱和密碼會區分大小寫。 **注意：** 如果您離開**使用者名**和**密碼**空白欄位，配接器連接至 SQL Server 使用 Windows 驗證。|  
  
6.  按一下 **[確定]**。  
  
### <a name="using-add-adapter-metadata-wizard"></a>使用新增配接器中繼資料精靈  
  
1.  以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後選取**新增產生的項目**。  
  
2.  在**新增產生的項目**對話方塊方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**類別**|按一下**新增介面卡**。|  
    |**範本**|按一下**新增配接器中繼資料**。|  
  
3.  按一下 **[加入]**。 [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。  
  
4.  在 新增配接器精靈 中，選取  **WCF-SQL**。 選取的電腦安裝 BizTalk Server 和 BizTalk 資料庫的名稱。  
  
    > [!IMPORTANT]
    >  如果您已經在 BizTalk 中設定 WCF SQL 連接埠，選取 從連接埠**連接埠**清單。  
  
5.  按一下 **[下一步]**。  
  
6.  在**取用配接器服務**對話方塊中，從**選取繫結**清單中，選取**sqlBinding**，然後按一下 **設定**。  
  
7.  在**設定配接器**對話方塊中，按一下**安全性** 索引標籤，並從**用戶端認證類型**清單中，執行下列其中一項：  
  
    > [!NOTE]
    >  如果您要連接到 SQL Server 使用 Windows 驗證，使用您登入的 Windows 使用者必須加入至 SQL Server 中所述[連接到 SQL Server 使用 Windows 驗證與 SQL 配接器](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。  
  
    |按一下此選項|動作|  
    |----------------|----------------|  
    |**無**|使用 Windows 驗證連接到 SQL Server。|  
    |**視窗**|使用 Windows 驗證連接到 SQL Server。|  
    |**使用者名稱**|指定的使用者名稱和密碼來連接到 SQL Server 藉由指定使用者在 SQL Server 資料庫中定義的認證。 請注意使用者名稱和密碼會區分大小寫。 **注意：** 如果您離開**使用者名**和**密碼**空白欄位，配接器連接至 SQL Server 使用 Windows 驗證。|  
  
8.  按一下 **[確定]**。  
  
## <a name="enter-credentials-from-the-biztalk-server-administration-console"></a>從 BizTalk Server 管理主控台中輸入認證  
 從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您可以指定的認證，Wcf-custom 或 WCF SQL 連接埠組態的一部分。  
  
### <a name="enter-credentials-for-the-wcf-custom-port"></a>WCF 自訂連接埠輸入認證  
  
1.  啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立的連接埠，並按一下**傳送埠**或**接收埠**。 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  
  
3.  在 連接埠屬性 對話方塊中，從**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。  
  
    > [!NOTE]
    >  若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**在左窗格中的連接埠屬性對話方塊、 標籤，然後按一下**新增**。  
  
4.  如果您要建立傳送埠，在**Wcf-custom 傳輸屬性**對話方塊中，按一下 **認證**索引標籤，然後執行下列其中一項：  
  
    -   選取**不會使用單一登入**選項，並指定使用者名稱和密碼以連接到 SQL Server。 請注意使用者名稱和密碼會區分大小寫。  
  
        > [!NOTE]
        >  如果您想要連接到 SQL Server 使用 Windows 驗證，請指定空白的使用者名稱和密碼。 這麼做之前，使用您登入的 Windows 使用者必須加入至 SQL Server 中所述[連接到 SQL Server 使用 Windows 驗證與 SQL 配接器](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。  
  
    -   選取**使用單一登入**選項，並指定分支機構企業單一登入 (SSO) 應用程式。  
  
5.  如果您要建立接收埠，在**Wcf-custom 傳輸屬性**對話方塊中，按一下 **其他**索引標籤，然後執行下列其中一項：  
  
    -   選取**使用者帳戶**選項，並指定使用者名稱和密碼以連接到 SQL Server。 請注意使用者名稱和密碼會區分大小寫。  
  
        > [!NOTE]
        >  如果您想要連接到 SQL Server 使用 Windows 驗證，請指定空白的使用者名稱和密碼。 這麼做之前，使用您登入的 Windows 使用者必須加入至 SQL Server 中所述[連接到 SQL Server 使用 Windows 驗證與 SQL 配接器](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。  
  
    -   選取**取得認證從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。  
  
6.  按一下 **[確定]**。  
  
### <a name="enter-credentials-for-the-wcf-sql-port"></a>輸入 WCF SQL 連接埠的認證  
  
1.  啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2.  新增 WCF-SQL 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如需指示，請參閱[SQL 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md)。  
  
3.  在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立的連接埠，並按一下**傳送埠**或**接收埠**。 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  
  
4.  在 [連接埠屬性] 對話方塊中，從**類型**下拉式清單中，選取您稍早，新增 WCF-SQL 配接器，然後按一下**設定**。  
  
    > [!NOTE]
    >  若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**在左窗格中的連接埠屬性對話方塊、 標籤，然後按一下**新增**。  
  
5.  如果您要建立傳送埠，在 [傳輸屬性] 對話方塊中，按一下**認證**索引標籤，然後執行下列其中一項：  
  
    -   選取**不會使用單一登入**選項，並指定使用者名稱和密碼以連接到 SQL Server。 請注意使用者名稱和密碼會區分大小寫。  
  
        > [!NOTE]
        >  如果您想要連接到 SQL Server 使用 Windows 驗證，請指定空白的使用者名稱和密碼。 這麼做之前，使用您登入的 Windows 使用者必須加入至 SQL Server 中所述[連接到 SQL Server 使用 Windows 驗證與 SQL 配接器](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。  
  
    -   選取**使用單一登入**選項，並指定分支機構企業單一登入 (SSO) 應用程式。  
  
6.  如果您要建立接收埠，在 [傳輸屬性] 對話方塊中，按一下**其他**索引標籤，然後執行下列其中一項：  
  
    -   選取**使用者帳戶**選項，並指定使用者名稱和密碼以連接到 SQL Server。 請注意使用者名稱和密碼會區分大小寫。  
  
        > [!NOTE]
        >  如果您想要連接到 SQL Server 使用 Windows 驗證，請指定空白的使用者名稱和密碼。 這麼做之前，使用您登入的 Windows 使用者必須加入至 SQL Server 中所述[連接到 SQL Server 使用 Windows 驗證與 SQL 配接器](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。  
  
    -   選取**取得認證從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。  
  
7.  按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式與 SQL 配接器的建置組塊](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)