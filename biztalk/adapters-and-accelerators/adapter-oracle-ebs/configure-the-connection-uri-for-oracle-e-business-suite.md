---
title: 設定 Oracle E-business Suite 連線 URI |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2bb02b4-4ad6-4b07-b48a-8f9a47967ffc
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6638e91616cb0e5134108aac0ed18ee844196ba7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991711"
---
# <a name="configure-the-connection-uri-for-oracle-e-business-suite"></a>設定 Oracle E-business Suite 連線 URI
連接字串，其中包含參數，才能連接到 Oracle E-business Suite 連線 URI。 在使用時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或是[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您必須指定要連接到 Oracle E-business Suite，產生的中繼資料的 URI。 在設定協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您必須指定要連接到 Oracle E-business Suite 來執行作業的 URI。  

## <a name="specifying-the-connection-uri-from-visual-studio"></a>指定連線 URI，從 Visual Studio  
 從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您必須指定連線 URI 使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。  

#### <a name="to-specify-the-connection-uri-using-consume-adapter-service-add-in"></a>若要指定連線 URI 使用取用配接器服務增益集  

1. 以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下**新增產生的項目**。  

2. 在 **加入產生的項目**對話方塊方塊中，執行下列動作：  


   |    使用    |             以進行此動作             |
   |----------------|------------------------------------|
   | **類別** | 按一下 **取用配接器服務**。 |
   | **範本**  | 按一下 **取用配接器服務**。 |


3. 若要啟動**取用配接器服務** 對話方塊中，按一下**新增**。  

4. 在 **取用配接器服務** 對話方塊中，從**選取的繫結**清單中，選取**oracleEBSBinding**，然後按一下 **設定**.  

5. 在 **設定介面卡** 對話方塊中，按一下**安全性** 索引標籤。從**用戶端認證類型**清單中，選取**Username**和指定的使用者名稱和密碼以連接到 Oracle E-business Suite。  


   |                                         使用                                          |                                                                                                                                               以進行此動作                                                                                                                                                |
   |-------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                     **使用 Oracle 資料庫的認證進行連接**                      |                                                                          指定**ClientCredentialType**屬性來繫結**資料庫**並指定資料庫的認證**使用者名稱**和**密碼**文字方塊。                                                                          |
   |                 **使用 Oracle E-business Suite 認證進行連接**                  | 指定**ClientCredentialType**屬性來繫結**EBusiness**並指定用於 Oracle E-business Suite 認證**使用者名稱**和**密碼**文字方塊。 在此情況下，您也必須指定 Oracle 資料庫認證**OracleUserName**並**OraclePassword**繫結屬性。 |
   | **若要使用 Windows 驗證，如果 ClientCredentialType 設定為 「 資料庫 」 進行連線**  |                                                                                                         指定"/"表示**使用者名**文字方塊中，並保留**密碼**空白的文字方塊。                                                                                                         |
   | **若要使用 Windows 驗證，如果 ClientCredentialType 設定為"EBusiness 」 進行連線** |                                       指定 Oracle E-business Suite 認證**使用者名**並**密碼**文字方塊。 您也必須指定"/"表示**OracleUserName**繫結屬性和保持**OraclePassword**繫結屬性為空白。                                       |


6. 按一下  **URI 屬性**索引標籤，然後指定不同參數的值。 如需有關連線 URI 的[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱 <<c2> [ 設定 Oracle E-business Suite 連線 URI](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-connection-uri-for-oracle-e-business-suite.md)。  

7. 按一下 **繫結屬性**索引標籤，然後指定繫結的值，如果有的話，才會產生結構描述所需。 如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。  

8. 按一下 [確定] 。  

#### <a name="to-specify-the-connection-uri-using-add-adapter-metadata-wizard"></a>若要指定連線 URI，使用 新增配接器中繼資料精靈  

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

7. 在 **設定介面卡** 對話方塊中，按一下**安全性** 索引標籤。從**用戶端認證類型**清單中，選取**Username**和指定的使用者名稱和密碼以連接到 Oracle E-business Suite。  


   |                                         使用                                          |                                                                                                                                               以進行此動作                                                                                                                                                |
   |-------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                     **使用 Oracle 資料庫的認證進行連接**                      |                                                                          指定**ClientCredentialType**屬性來繫結**資料庫**並指定資料庫的認證**使用者名稱**和**密碼**文字方塊。                                                                          |
   |                 **使用 Oracle E-business Suite 認證進行連接**                  | 指定**ClientCredentialType**屬性來繫結**EBusiness**並指定用於 Oracle E-business Suite 認證**使用者名稱**和**密碼**文字方塊。 在此情況下，您也必須指定 Oracle 資料庫認證**OracleUserName**並**OraclePassword**繫結屬性。 |
   | **若要使用 Windows 驗證，如果 ClientCredentialType 設定為 「 資料庫 」 進行連線**  |                                                                                                         指定"/"表示**使用者名**文字方塊中，並保留**密碼**空白的文字方塊。                                                                                                         |
   | **若要使用 Windows 驗證，如果 ClientCredentialType 設定為"EBusiness 」 進行連線** |                                       指定 Oracle E-business Suite 認證**使用者名**並**密碼**文字方塊。 您也必須指定"/"表示**OracleUserName**繫結屬性和保持**OraclePassword**繫結屬性為空白。                                       |


8. 按一下  **URI 屬性**索引標籤，然後指定不同參數的值。 如需有關連線 URI 的[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱 <<c2> [ 設定 Oracle E-business Suite 連線 URI](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-connection-uri-for-oracle-e-business-suite.md)。  

9. 按一下 **繫結屬性**索引標籤，然後指定繫結的值，如果有的話，才會產生結構描述所需。 如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。  

    > [!NOTE]
    >  如果您選取的現有 Wcf-oracleebs 傳送埠時，您需要指定繫結屬性。 從傳送埠組態，會挑選繫結屬性。 不過，您可以選擇指定繫結所需屬性在設計階段，如果有的話。 在此情況下，繫結屬性的新值將用於在設計階段時產生的中繼資料。 不過，在執行階段針對屬性繫結的傳送埠組態中指定的值將會適用。  

10. 按一下 [確定] 。  

## <a name="specifying-the-connection-uri-from-the-biztalk-server-administration-console"></a>指定連線 URI，從 BizTalk Server 管理主控台  
 從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您必須指定連線 URI Wcf-custom 或 Wcf-oracleebs 的連接埠組態的一部分。  

#### <a name="to-specify-the-connection-uri-for-the-wcf-custom-port"></a>若要指定 WCF 自訂連接埠的連線 URI  

1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  

2. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，然後按一下 **傳送埠**或**接收埠**。 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  

3. 在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。  

   > [!NOTE]
   >  若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**索引標籤上的 [連接埠屬性] 對話方塊中，左窗格，然後按一下**新增**。  

4. 在  **Wcf-custom 傳輸屬性** 對話方塊中，按一下**一般** 索引標籤。  

5. 在 **位址 (URI)** 文字方塊中，指定連接到 Oracle E-business Suite 連線 URI。 如需有關連線 URI 的[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱 <<c2> [ 設定 Oracle E-business Suite 連線 URI](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-connection-uri-for-oracle-e-business-suite.md)。  

6. 在  **Wcf-custom 傳輸屬性** 對話方塊中，按一下**繫結** 索引標籤。從**繫結的型別**下拉式清單中，選取**oracleEBSBinding**。  

7. 如果您要建立傳送埠，在**Wcf-custom 傳輸屬性** 對話方塊中，按一下**認證**索引標籤，然後執行下列其中一項：  

   -   選取 **不會使用單一登入**選項，並指定使用者名稱和密碼以連接到 Oracle E-business Suite。  

       |使用|以進行此動作|  
       |--------------|----------------|  
       |**使用 Oracle 資料庫的認證進行連接**|指定**ClientCredentialType**屬性來繫結**資料庫**並指定資料庫的認證**使用者名稱**和**密碼**文字方塊。|  
       |**使用 Oracle E-business Suite 認證進行連接**|指定**ClientCredentialType**屬性來繫結**EBusiness**並指定用於 Oracle E-business Suite 認證**使用者名稱**和**密碼**文字方塊。 在此情況下，您也必須指定 Oracle 資料庫認證**OracleUserName**並**OraclePassword**繫結屬性。|  
       |**若要使用 Windows 驗證，如果 ClientCredentialType 設定為 「 資料庫 」 進行連線**|指定"/"表示**使用者名**文字方塊中，並保留**密碼**空白的文字方塊。|  
       |**若要使用 Windows 驗證，如果 ClientCredentialType 設定為"EBusiness 」 進行連線**|指定 Oracle E-business Suite 認證**使用者名**並**密碼**文字方塊。 您也必須指定"/"表示**OracleUserName**繫結屬性和保持**OraclePassword**繫結屬性為空白。|  

   -   選取 **使用單一登入**選項，並指定分支機構應用程式企業單一登入 (SSO)。  

8. 如果您要建立接收埠，在**Wcf-custom 傳輸屬性** 對話方塊中，按一下**其他**索引標籤，然後執行下列其中一項：  

   -   選取 **使用者帳戶**選項，並指定使用者名稱和密碼以連接到 Oracle E-business Suite。  

       |使用|以進行此動作|  
       |--------------|----------------|  
       |**使用 Oracle 資料庫的認證進行連接**|指定**ClientCredentialType**屬性來繫結**資料庫**並指定資料庫的認證**使用者名稱**和**密碼**文字方塊。|  
       |**使用 Oracle E-business Suite 認證進行連接**|指定**ClientCredentialType**屬性來繫結**EBusiness**並指定用於 Oracle E-business Suite 認證**使用者名稱**和**密碼**文字方塊。 在此情況下，您也必須指定 Oracle 資料庫認證**OracleUserName**並**OraclePassword**繫結屬性。|  
       |**若要使用 Windows 驗證，如果 ClientCredentialType 設定為 「 資料庫 」 進行連線**|指定"/"表示**使用者名**文字方塊中，並保留**密碼**空白的文字方塊。|  
       |**若要使用 Windows 驗證，如果 ClientCredentialType 設定為"EBusiness 」 進行連線**|指定 Oracle E-business Suite 認證**使用者名**並**密碼**文字方塊。 您也必須指定"/"表示**OracleUserName**繫結屬性和保持**OraclePassword**繫結屬性為空白。|  

   -   選取 **取得認證，從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。  

9. 按一下 [確定] 。  

#### <a name="to-specify-the-connection-uri-for-the-wcf-oracleebs-port"></a>若要指定 Wcf-oracleebs 連接埠的連線 URI  

1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  

2. 新增 Wcf-oracleebs 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如需相關指示，請參閱 < [Oracle E-business Suite 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-ebs/add-the-oracle-ebs-adapter-to-biztalk-server-administration-console.md)。  

3. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，然後按一下 **傳送埠**或**接收埠**。 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  

4. 在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取 Wcf-oracleebs 配接器中，使用您稍早新增，然後按一下**設定**。  

   > [!NOTE]
   >  若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**索引標籤上的 [連接埠屬性] 對話方塊中，左窗格，然後按一下**新增**。  

5. 在 傳輸屬性 對話方塊中，按一下**一般** 索引標籤。  

6. 按一下 **設定**按鈕，並提供連接參數的值。 如需有關連線 URI 的[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱 <<c2> [ 設定 Oracle E-business Suite 連線 URI](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-connection-uri-for-oracle-e-business-suite.md)。  

7. 在 [傳輸屬性] 對話方塊中，按一下**繫結**索引標籤，然後指定繫結屬性的值。  

   > [!NOTE]
   >  繫結屬性會顯示根據您要設定傳送埠或接收埠。 比方說，與通知相關的繫結屬性沒有設定傳送埠，因為通知是輸入的作業，並且需要接收埠組態時。  

8. 如果您要建立傳送埠，在傳輸屬性對話方塊中，按一下**認證**索引標籤，然後執行下列其中一項：  

   -   選取 **不會使用單一登入**選項，並指定使用者名稱和密碼以連接到 Oracle E-business Suite。  

       |使用|以進行此動作|  
       |--------------|----------------|  
       |**使用 Oracle 資料庫的認證進行連接**|指定**ClientCredentialType**屬性來繫結**資料庫**並指定資料庫的認證**使用者名稱**和**密碼**文字方塊。|  
       |**使用 Oracle E-business Suite 認證進行連接**|指定**ClientCredentialType**屬性來繫結**EBusiness**並指定用於 Oracle E-business Suite 認證**使用者名稱**和**密碼**文字方塊。 在此情況下，您也必須指定 Oracle 資料庫認證**OracleUserName**並**OraclePassword**繫結屬性。|  
       |**若要使用 Windows 驗證，如果 ClientCredentialType 設定為 「 資料庫 」 進行連線**|指定"/"表示**使用者名**文字方塊中，並保留**密碼**空白的文字方塊。|  
       |**若要使用 Windows 驗證，如果 ClientCredentialType 設定為"EBusiness 」 進行連線**|指定 Oracle E-business Suite 認證**使用者名**並**密碼**文字方塊。 您也必須指定"/"表示**OracleUserName**繫結屬性和保持**OraclePassword**繫結屬性為空白。|  

   -   選取 **使用單一登入**選項，並指定分支機構應用程式企業單一登入 (SSO)。  

9. 如果您要建立接收埠，在傳輸屬性對話方塊中，按一下**其他**索引標籤，然後執行下列其中一項：  

    -   選取 **使用者帳戶**選項，並指定使用者名稱和密碼以連接到 Oracle E-business Suite。  

        |使用|以進行此動作|  
        |--------------|----------------|  
        |**使用 Oracle 資料庫的認證進行連接**|指定**ClientCredentialType**屬性來繫結**資料庫**並指定資料庫的認證**使用者名稱**和**密碼**文字方塊。|  
        |**使用 Oracle E-business Suite 認證進行連接**|指定**ClientCredentialType**屬性來繫結**EBusiness**並指定用於 Oracle E-business Suite 認證**使用者名稱**和**密碼**文字方塊。 在此情況下，您也必須指定 Oracle 資料庫認證**OracleUserName**並**OraclePassword**繫結屬性。|  
        |**若要使用 Windows 驗證，如果 ClientCredentialType 設定為 「 資料庫 」 進行連線**|指定"/"表示**使用者名**文字方塊中，並保留**密碼**空白的文字方塊。|  
        |**若要使用 Windows 驗證，如果 ClientCredentialType 設定為"EBusiness 」 進行連線**|指定 Oracle E-business Suite 認證**使用者名**並**密碼**文字方塊。 您也必須指定"/"表示**OracleUserName**繫結屬性和保持**OraclePassword**繫結屬性為空白。|  

    -   選取 **取得認證，從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。  

10. 按一下 [確定] 。  

## <a name="see-also"></a>另請參閱  
 [若要建立 Oracle E-business Suite 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)   
 [連接到 Oracle E-business Suite 使用 Windows 驗證](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-windows-authentication.md)