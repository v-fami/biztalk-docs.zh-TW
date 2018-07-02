---
title: 設定登入認證 for Oracle E-business Suite |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 743ced51-706b-4788-b5a8-e0ed8ffb3b48
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 08081cc1e59181f3cd6aad0dfa532b060287d2ea
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978943"
---
# <a name="configure-the-sign-in-credentials-for-the-oracle-e-business-suite"></a>For Oracle E-business Suite 中設定的登入認證
[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]需要配接器用戶端，以提供用戶端認證。 配接器會使用這些認證來驗證 Oracle E-business Suite 的使用者，並建立連線。  

 配接器用戶端可以提供使用時的用戶端認證兩者[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]以及何時使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 當使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，產生中繼資料所需的認證。 當使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，就需要認證 Oracle E-business Suite 上執行作業。  

> [!IMPORTANT]
>  您可以指定 Oracle E-business Suite 或基礎的 Oracle 資料庫的認證。 若要連接並產生中繼資料中，您可以指定任何認證。 不過，在執行作業，以叫用 Oracle E-business Suite 成品，您必須指定 Oracle E-business Suite 認證因為他們就必須設定您想要叫用 Oracle E-business Suite 應用程式的應用程式內容。 如需有關設定應用程式內容的詳細資訊，請參閱 <<c0> [ 設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  

 本節提供有關指定在用戶端認證的詳細資訊[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]而[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  

## <a name="specifying-credentials-from-visual-studio"></a>指定的認證，從 Visual Studio  
 從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您必須指定使用的認證[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。  

#### <a name="to-specify-credentials-using-consume-adapter-service-add-in"></a>若要指定使用配接器服務增益集所使用的認證  

1.  以滑鼠右鍵按一下您的 BizTalk 專案，然後按**加入產生的項目**。  

2.  在 **加入產生的項目**對話方塊方塊中，執行下列動作：  

    |使用|以進行此動作|  
    |--------------|----------------|  
    |**類別**|按一下 **取用配接器服務**。|  
    |**範本**|按一下 **取用配接器服務**。|  

3.  若要啟動**取用配接器服務** 對話方塊中，按一下**新增**。  

4.  在 **取用配接器服務** 對話方塊中，從**選取的繫結**清單中，選取**oracleEBSBinding**，然後按一下 **設定**.  

5.  在**設定介面卡** 對話方塊中，按一下**安全性**索引標籤上，以及從**用戶端認證類型**清單中，選取**使用者名稱**和指定的使用者名稱和密碼以連接到 Oracle E-business Suite。  

    |使用|以進行此動作|  
    |--------------|----------------|  
    |**使用 Oracle 資料庫的認證進行連接**|指定**ClientCredentialType**屬性來繫結**資料庫**並指定資料庫的認證**使用者名稱**和**密碼**文字方塊。|  
    |**使用 Oracle E-business Suite 認證進行連接**|指定**ClientCredentialType**屬性來繫結**EBusiness**並指定用於 Oracle E-business Suite 認證**使用者名稱**和**密碼**文字方塊。 在此情況下，您也必須指定 Oracle 資料庫認證**OracleUserName**並**OraclePassword**繫結屬性。|  
    |**若要使用 Windows 驗證，如果 ClientCredentialType 設定為 「 資料庫 」 進行連線**|指定"/"表示**使用者名**文字方塊中，並保留**密碼**空白的文字方塊。|  
    |**若要使用 Windows 驗證，如果 ClientCredentialType 設定為"EBusiness 」 進行連線**|指定 Oracle E-business Suite 認證**使用者名**並**密碼**文字方塊。 您也必須指定"/"表示**OracleUserName**繫結屬性和保持**OraclePassword**繫結屬性為空白。|  

6.  按一下 [確定] 。  

#### <a name="to-specify-credentials-using-add-adapter-metadata-wizard"></a>若要指定認證，使用 新增配接器中繼資料精靈  

1. 以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下**新增產生的項目**。  

2. 在 **加入產生的項目**對話方塊方塊中，執行下列動作：  


   |    使用    |           以進行此動作            |
   |----------------|---------------------------------|
   | **類別** |     按一下 **新增介面卡**。      |
   | **範本**  | 按一下 **新增配接器中繼資料**。 |


3. 按一下 **[加入]**。 [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。  

4. 在  [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，選取**Wcf-oracleebs**。 選取的電腦安裝 BizTalk Server 和 BizTalk 資料庫的名稱。  

   > [!IMPORTANT]
   >  如果您已經在 BizTalk 設定 Wcf-oracleebs 連接埠，請從連接埠清單中選取連接埠。  

5. 按 [下一步] 。  

6. 在 **取用配接器服務** 對話方塊中，從**選取的繫結**清單中，選取**oracleEBSBinding**，然後按一下 **設定**.  

7. 在**設定介面卡** 對話方塊中，按一下**安全性**索引標籤上，以及從**用戶端認證類型**清單中，選取**使用者名稱**和指定的使用者名稱和密碼以連接到 Oracle E-business Suite。  


   |                                         使用                                          |                                                                                                                                               以進行此動作                                                                                                                                                |
   |-------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                     **使用 Oracle 資料庫的認證進行連接**                      |                                                                          指定**ClientCredentialType**屬性來繫結**資料庫**並指定資料庫的認證**使用者名稱**和**密碼**文字方塊。                                                                          |
   |                 **使用 Oracle E-business Suite 認證進行連接**                  | 指定**ClientCredentialType**屬性來繫結**EBusiness**並指定用於 Oracle E-business Suite 認證**使用者名稱**和**密碼**文字方塊。 在此情況下，您也必須指定 Oracle 資料庫認證**OracleUserName**並**OraclePassword**繫結屬性。 |
   | **若要使用 Windows 驗證，如果 ClientCredentialType 設定為 「 資料庫 」 進行連線**  |                                                                                                         指定"/"表示**使用者名**文字方塊中，並保留**密碼**空白的文字方塊。                                                                                                         |
   | **若要使用 Windows 驗證，如果 ClientCredentialType 設定為"EBusiness 」 進行連線** |                                       指定 Oracle E-business Suite 認證**使用者名**並**密碼**文字方塊。 您也必須指定"/"表示**OracleUserName**繫結屬性和保持**OraclePassword**繫結屬性為空白。                                       |


8. 按一下 [確定] 。  

## <a name="specifying-credentials-from-the-biztalk-server-administration-console"></a>指定認證，從 BizTalk Server 管理主控台  
 從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您必須指定認證，Wcf-custom 或 Wcf-oracleebs 的連接埠組態的一部分。  

#### <a name="to-specify-credentials-for-the-wcf-custom-port"></a>若要指定認證的 WCF 自訂連接埠  

1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  

2. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，然後按一下 **傳送埠**或**接收埠**。 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  

3. 在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。  

   > [!NOTE]
   >  若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**索引標籤上的 [連接埠屬性] 對話方塊中，左窗格，然後按一下**新增**。  

4. 在  **Wcf-custom 傳輸屬性** 對話方塊中，按一下**繫結** 索引標籤。從**繫結的型別**下拉式清單中，選取**oracleEBSBinding**。  

5. 如果您要建立傳送埠，在**Wcf-custom 傳輸屬性** 對話方塊中，按一下**認證**索引標籤，然後執行下列其中一項：  

   -   選取 **不會使用單一登入**選項，並指定使用者名稱和密碼以連接到 Oracle E-business Suite。  

       |使用|以進行此動作|  
       |--------------|----------------|  
       |**使用 Oracle 資料庫的認證進行連接**|指定**ClientCredentialType**屬性來繫結**資料庫**並指定資料庫的認證**使用者名稱**和**密碼**文字方塊。|  
       |**使用 Oracle E-business Suite 認證進行連接**|指定**ClientCredentialType**屬性來繫結**EBusiness**並指定用於 Oracle E-business Suite 認證**使用者名稱**和**密碼**文字方塊。 在此情況下，您也必須指定 Oracle 資料庫認證**OracleUserName**並**OraclePassword**繫結屬性。|  
       |**若要使用 Windows 驗證，如果 ClientCredentialType 設定為 「 資料庫 」 進行連線**|指定"/"表示**使用者名**文字方塊中，並保留**密碼**空白的文字方塊。|  
       |**若要使用 Windows 驗證，如果 ClientCredentialType 設定為"EBusiness 」 進行連線**|指定 Oracle E-business Suite 認證**使用者名**並**密碼**文字方塊。 您也必須指定"/"表示**OracleUserName**繫結屬性和保持**OraclePassword**繫結屬性為空白。|  

   -   選取 **使用單一登入**選項，並指定分支機構應用程式企業單一登入 (SSO)。  

6. 如果您要建立接收埠，在**Wcf-custom 傳輸屬性** 對話方塊中，按一下**其他**索引標籤，然後執行下列其中一項：  

   -   選取 **使用者帳戶**選項，並指定使用者名稱和密碼以連接到 Oracle E-business Suite。  

       |使用|以進行此動作|  
       |--------------|----------------|  
       |**使用 Oracle 資料庫的認證進行連接**|指定**ClientCredentialType**屬性來繫結**資料庫**並指定資料庫的認證**使用者名稱**和**密碼**文字方塊。|  
       |**使用 Oracle E-business Suite 認證進行連接**|指定**ClientCredentialType**屬性來繫結**EBusiness**並指定用於 Oracle E-business Suite 認證**使用者名稱**和**密碼**文字方塊。 在此情況下，您也必須指定 Oracle 資料庫認證**OracleUserName**並**OraclePassword**繫結屬性。|  
       |**若要使用 Windows 驗證，如果 ClientCredentialType 設定為 「 資料庫 」 進行連線**|指定"/"表示**使用者名**文字方塊中，並保留**密碼**空白的文字方塊。|  
       |**若要使用 Windows 驗證，如果 ClientCredentialType 設定為"EBusiness 」 進行連線**|指定 Oracle E-business Suite 認證**使用者名**並**密碼**文字方塊。 您也必須指定"/"表示**OracleUserName**繫結屬性和保持**OraclePassword**繫結屬性為空白。|  

   -   選取 **取得認證，從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。  

7. 按一下 [確定] 。  

#### <a name="to-specify-credentials-for-the-wcf-oracleebs-port"></a>若要指定認證 Wcf-oracleebs 連接埠  

1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  

2. 新增 Wcf-oracleebs 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如需相關指示，請參閱 < [Oracle E-business Suite 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-ebs/add-the-oracle-ebs-adapter-to-biztalk-server-administration-console.md)。  

3. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，然後按一下 **傳送埠**或**接收埠**。 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  

4. 在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取**Wcf-oracleebs**，然後按一下**設定**。  

   > [!NOTE]
   >  若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**索引標籤上的 [連接埠屬性] 對話方塊中，左窗格，然後按一下**新增**。  

5. 在 連接埠屬性 對話方塊中，按一下**繫結** 索引標籤。從**繫結的型別**下拉式清單中，選取**oracleEBSBinding**。  

6. 如果您要建立傳送埠，在傳輸屬性對話方塊中，按一下**認證**索引標籤，然後執行下列其中一項：  

   -   選取 **不會使用單一登入**選項，並指定使用者名稱和密碼以連接到 Oracle E-business Suite。  

       |使用|以進行此動作|  
       |--------------|----------------|  
       |**使用 Oracle 資料庫的認證進行連接**|指定**ClientCredentialType**屬性來繫結**資料庫**並指定資料庫的認證**使用者名稱**和**密碼**文字方塊。|  
       |**使用 Oracle E-business Suite 認證進行連接**|指定**ClientCredentialType**屬性來繫結**EBusiness**並指定用於 Oracle E-business Suite 認證**使用者名稱**和**密碼**文字方塊。 在此情況下，您也必須指定 Oracle 資料庫認證**OracleUserName**並**OraclePassword**繫結屬性。|  
       |**若要使用 Windows 驗證，如果 ClientCredentialType 設定為 「 資料庫 」 進行連線**|指定"/"表示**使用者名**文字方塊中，並保留**密碼**空白的文字方塊。|  
       |**若要使用 Windows 驗證，如果 ClientCredentialType 設定為"EBusiness 」 進行連線**|指定 Oracle E-business Suite 認證**使用者名**並**密碼**文字方塊。 您也必須指定"/"表示**OracleUserName**繫結屬性和保持**OraclePassword**繫結屬性為空白。|  

   -   選取 **使用單一登入**選項，並指定分支機構應用程式企業單一登入 (SSO)。  

7. 如果您要建立接收埠，在傳輸屬性對話方塊中，按一下**其他**索引標籤，然後執行下列其中一項：  

   -   選取 **使用者帳戶**選項，並指定使用者名稱和密碼以連接到 Oracle E-business Suite。  

       |使用|以進行此動作|  
       |--------------|----------------|  
       |**使用 Oracle 資料庫的認證進行連接**|指定**ClientCredentialType**屬性來繫結**資料庫**並指定資料庫的認證**使用者名稱**和**密碼**文字方塊。|  
       |**使用 Oracle E-business Suite 認證進行連接**|指定**ClientCredentialType**屬性來繫結**EBusiness**並指定用於 Oracle E-business Suite 認證**使用者名稱**和**密碼**文字方塊。 在此情況下，您也必須指定 Oracle 資料庫認證**OracleUserName**並**OraclePassword**繫結屬性。|  
       |**若要使用 Windows 驗證，如果 ClientCredentialType 設定為 「 資料庫 」 進行連線**|指定"/"表示**使用者名**文字方塊中，並保留**密碼**空白的文字方塊。|  
       |**若要使用 Windows 驗證，如果 ClientCredentialType 設定為"EBusiness 」 進行連線**|指定 Oracle E-business Suite 認證**使用者名**並**密碼**文字方塊。 您也必須指定"/"表示**OracleUserName**繫結屬性和保持**OraclePassword**繫結屬性為空白。|  

   -   選取 **取得認證，從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。  

8. 按一下 [確定] 。  

## <a name="see-also"></a>另請參閱  
 [若要建立 Oracle E-business Suite 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)   
 [連接到 Oracle E-business Suite 使用 Windows 驗證](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-windows-authentication.md)