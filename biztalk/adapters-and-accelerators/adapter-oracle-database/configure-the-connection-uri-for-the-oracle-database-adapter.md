---
title: 設定 Oracle 資料庫配接器的連線 URI |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connection URI, specifying at design time
- connection URI, specifying at run time
ms.assetid: 9f302b67-0bcc-44d1-9517-10d402873540
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 849adf16faa96726fb3d182930be8f4965eb180d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007205"
---
# <a name="configure-the-connection-uri-for-the-oracle-database-adapter"></a>設定 Oracle 資料庫配接器的連線 URI
連線 URI 會是包含參數，才能連接到 Oracle 資料庫的連接字串。 在使用時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或是[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您必須指定要連接到 Oracle 資料庫產生的中繼資料的 URI。 在設定協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您必須指定要連接到 Oracle 資料庫執行作業的 URI。  

## <a name="specifying-the-connection-uri-from-visual-studio"></a>指定連線 URI，從 Visual Studio  
 從 Visual Studio 中，您必須指定使用的認證[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。  

#### <a name="to-specify-the-connection-uri-using-consume-adapter-service-add-in"></a>若要指定使用配接器服務增益集所使用的連線 URI  

1. 以滑鼠右鍵按一下您的 BizTalk 專案，然後按**加入產生的項目**。  

2. 在 **加入產生的項目**對話方塊方塊中，執行下列動作：  


   |    使用    |             以進行此動作             |
   |----------------|------------------------------------|
   | **類別** | 按一下 **取用配接器服務**。 |
   | **範本**  | 按一下 **取用配接器服務**。 |


3. 若要啟動**取用配接器服務** 對話方塊中，按一下**新增**。  

4. 在**取用配接器服務** 對話方塊中，從**選取的繫結**清單中，選取**oracleDBBinding**，然後按一下**設定**。  

5. 中**設定介面卡** 對話方塊中，按一下**安全性** 索引標籤並從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**並指定使用者名稱和密碼來連接到 Oracle 資料庫：  

   -   若要使用的 Oracle 資料庫的認證連線，請輸入中的資料庫認證**使用者名稱**並**密碼**文字方塊。  

   -   若要使用 Windows 驗證進行連接，請輸入**/** 中**使用者名稱**文字方塊中，並保留**密碼**空白的文字方塊。  

6. 按一下  **URI 屬性**索引標籤，然後指定不同參數的值。 如需有關連線 URI 的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 <<c2> [ 建立 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)。  

7. 按一下 **繫結屬性**索引標籤，然後指定繫結的值，如果有的話，才會產生結構描述所需。 如需有關繫結屬性的詳細資訊，請參閱 < [Oracle 資料庫設定的繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。  

8. 按一下 [確定] 。  

#### <a name="to-specify-the-connection-uri-using-add-adapter-metadata-wizard"></a>若要指定連線 URI，使用 新增配接器中繼資料精靈  

1. 以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下**新增產生的項目**。  

2. 在 **加入產生的項目**對話方塊方塊中，執行下列動作：  


   |    使用    |           以進行此動作            |
   |----------------|---------------------------------|
   | **類別** |     按一下 **新增介面卡**。      |
   | **範本**  | 按一下 **新增配接器中繼資料**。 |


3. 按一下 **[加入]**。 [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。  

4. 在  [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，選取**Wcf-oracledb**。 選取的電腦上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安裝和 BizTalk 資料庫的名稱。  

   > [!IMPORTANT]
   >  如果您已經設定 biztalk Wcf-oracledb 連接埠，請選取 從連接埠**連接埠**清單。  

5. 按 [下一步] 。  

6. 在 **取用配接器服務** 對話方塊中，從**選取的繫結**清單中，選取**oracleDBBinding**，然後按一下 **設定**.  

7. 在**設定介面卡** 對話方塊中，按一下**安全性**索引標籤上，以及從**用戶端認證類型**清單中，選取**使用者名稱**和指定使用者名稱和密碼來連接到 Oracle 資料庫：  

   -   若要使用的 Oracle 資料庫的認證連線，請輸入中的資料庫認證**使用者名稱**並**密碼**文字方塊。  

   -   若要使用 Windows 驗證進行連接，請輸入**/** 中**使用者名稱**文字方塊中，並保留**密碼**空白的文字方塊。  

8. 按一下  **URI 屬性**索引標籤，然後指定不同參數的值。 如需有關連線 URI 的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 <<c2> [ 建立 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)。  

9. 按一下 **繫結屬性**索引標籤，然後指定繫結的值，如果有的話，才會產生結構描述所需。 如需有關繫結屬性的詳細資訊，請參閱 < [Oracle 資料庫設定的繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。  

10. 按一下 [確定] 。  

## <a name="specifying-the-connection-uri-from-the-biztalk-server-administration-console"></a>指定連線 URI，從 BizTalk Server 管理主控台  
 從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您必須指定認證，Wcf-custom 或 Wcf-oracledb 的連接埠組態的一部分。  

#### <a name="to-specify-the-connection-uri-for-the-wcf-custom-port"></a>若要指定 WCF 自訂連接埠的連線 URI  

1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  

2. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，然後按一下 **傳送埠**或**接收埠**。 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  

3. 在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。  

4. 傳送埠，在**Wcf-custom 傳輸屬性** 對話方塊中，按一下**認證**索引標籤，然後執行下列其中一項：  

   -   選取 **不會使用單一登入**選項，並指定使用者名稱和密碼以連接到 Oracle 資料庫。  

       -   若要使用的 Oracle 資料庫的認證連線，請輸入中的資料庫認證**使用者名稱**並**密碼**文字方塊。  

       -   若要使用 Windows 驗證進行連接，請輸入**/** 中**使用者名稱**文字方塊中，並保留**密碼**空白的文字方塊。  

   -   選取 **使用單一登入**選項，並指定分支機構應用程式企業單一登入 (SSO)。  

5. 接收埠，在**Wcf-custom 傳輸屬性** 對話方塊中，按一下**其他**索引標籤，然後執行下列其中一項：  

   -   選取 **使用者帳戶**選項，並指定使用者名稱和密碼以連接到 Oracle 資料庫。  

       -   若要使用的 Oracle 資料庫的認證連線，請輸入中的資料庫認證**使用者名稱**並**密碼**文字方塊。  

       -   若要使用 Windows 驗證進行連接，請輸入**/** 中**使用者名稱**文字方塊中，並保留**密碼**空白的文字方塊。  

   -   選取 **取得認證，從分支機構應用程式**選項，並指定分支機構應用程式。  

6. 按一下 [確定] 。  

#### <a name="to-specify-the-connection-uri-for-the-wcf-oracledb-port"></a>若要指定 Wcf-oracledb 連接埠的連線 URI  

1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  

2. 新增 Wcf-oracledb 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如需相關指示，請參閱 <<c0> [ 將 Oracle 資料庫配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md)。  

3. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，然後按一下 **傳送埠**或**接收埠**。 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  

4. 在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取**Wcf-oracledb**，然後按一下**設定**。  

   > [!NOTE]
   >  若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**索引標籤上的 [連接埠屬性] 對話方塊中，左窗格，然後按一下**新增**。  

5. 在 連接埠屬性 對話方塊中，按一下**繫結** 索引標籤。從**繫結的型別**下拉式清單中，選取**oracleDBBinding**。  

6. 如果您要建立傳送埠，在傳輸屬性對話方塊中，按一下**認證**索引標籤，然後執行下列其中一項：  

   -   選取 **不會使用單一登入**選項，並指定使用者名稱和密碼來連接到 Oracle 資料庫。  

       -   若要使用的 Oracle 資料庫的認證連線，請輸入中的資料庫認證**使用者名稱**並**密碼**文字方塊。  

       -   若要使用 Windows 驗證進行連接，請輸入**/** 中**使用者名稱**文字方塊中，並保留**密碼**空白的文字方塊。  

   -   選取 **使用單一登入**選項，並指定分支機構應用程式企業單一登入 (SSO)。  

7. 如果您要建立接收埠，在傳輸屬性對話方塊中，按一下**其他**索引標籤，然後執行下列其中一項：  

   -   選取 **使用者帳戶**選項，並指定使用者名稱和密碼來連接到 Oracle 資料庫。  

       -   若要使用的 Oracle 資料庫的認證連線，請輸入中的資料庫認證**使用者名稱**並**密碼**文字方塊。  

       -   若要使用 Windows 驗證進行連接，請輸入**/** 中**使用者名稱**文字方塊中，並保留**密碼**空白的文字方塊。  

   -   選取 **取得認證，從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。  

8. 按一下 [確定] 。  

## <a name="see-also"></a>另請參閱  
[若要開發與 Oracle 資料庫的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)   
 [連接到 Oracle 資料庫使用 Windows 驗證](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)