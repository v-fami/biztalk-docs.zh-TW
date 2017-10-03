---
title: "使用 BizTalk Server 的 SQL Server 中執行具有單一 XML 參數的預存程序 |Microsoft 文件"
description: "預存程序使用中 BizTalk WCF 自訂連接埠和 SQL 配接器中傳遞單一參數"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: deb9333a-5e28-4e8d-8e0b-07b5a97a111b
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3d933b494e967184c8248d6f71ad9df113fb9b9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="execute-stored-procedures-with-a-single-xml-parameter-in-sql-server-using-biztalk-server"></a>使用 BizTalk Server 的 SQL Server 中執行具有單一 XML 參數的預存程序
執行採用單一參數的預存程序是類似於執行任何其他預存程序中所述[使用 BizTalk Server 的 SQL Server 中執行預存程序](execute-stored-procedures-in-sql-server-using-biztalk-server.md)。 不過，如上述的連結中所述的方法，您要在設計階段產生預存程序的中繼資料和建立協調流程執行階段叫用程序。  
  
 假設您只想將一個單一值傳遞給預存程序，而不進行任何處理該值。 在這種情況下，您不希望產生中繼資料、 建立協調流程、 部署協調流程，以及執行作業的額外負荷。 相反地，您可以設定 WCF 自訂或 WCF SQL 傳送埠來直接叫用預存程序。 本主題示範如何使用來執行這些工作[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
> [!NOTE]
>  本主題提供有關如何設定 Wcf-custom 傳送埠執行採用單一參數的預存程序。 您可以設定 WCF SQL 連接埠來執行相同的步驟。 如需設定 WCF SQL 連接埠的指示，請參閱[設定使用 WCF-SQL 配接器的連接埠](configure-a-port-using-the-wcf-sql-adapter.md)。  
  
## <a name="invoke-stored-procedures-without-orchestration"></a>叫用預存程序沒有協調流程  
 若要示範如何執行與不用協調流程的單一參數的預存程序，本主題會使用 ADD_LAST_EMP_XML_INFO 預存程序。 這個程序會使用 XML 做為參數值，並將它插入至**位址**資料行**員工**資料表。 您必須在您將會傳遞至預存程序的 XML 值。 不過，若要執行預存程序中使用配接器，您必須傳送要求訊息符合之結構描述的程序，和值包含 XML 的**位址**欄位中，SQL server。 因此，您必須建立該要求訊息：  
  
-   使用**範本**中使用您可以建立使用訊息範本的要求訊息的傳送埠組態選項。  
  
-   將 XML 值**位址**欄位到訊息。  
  
 在本主題中詳細說明所有這些步驟。 您必須執行下列工作集合：  
  
1.  建立檔案接收的埠，您將會卸除的 XML 檔案，就會插入到**位址**XML 欄位的**員工**資料表。 假設此連接埠稱為**MessageIn**連接埠。  
  
2.  建立 Wcf-custom 單向傳送埠取用 XML 檔案從檔案接收埠、 建構訊息使用訊息的範本，並將它傳送到 SQL Server 來執行預存程序。  
  
 這一部分的主題提供指示設定 Wcf-custom 傳送郵件範本的通訊埠。  
  
> [!NOTE]
>  雖然本主題中的資訊會示範如何執行與單一的 XML 參數的預存程序，您可以執行要執行的任何作業，使用單一參數的任何資料類型的工作。 唯一的差異會在您建立訊息的範本，針對特定作業的方式。 您可以擷取您要用於執行作業的要求訊息，藉此建立訊息範本使用協調流程與參數的值取代 BizTalk 訊息內文。  
  
##  <a name="BKMK_OneWay"></a>設定 Wcf-custom 傳送埠  
 之前建立 Wcf-custom 傳送埠時，請確定您建立檔案接收埠， **MessageIn**。  
  
1.  啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3.  展開想要部署您的應用程式[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
4.  以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後指向**靜態單向傳送埠**。  
  
5.  在**傳送埠屬性**對話方塊**一般**索引標籤上，輸入傳送埠的名稱。  
  
6.  設定連接埠接收所有檔案在卸除的訊息接收埠， **MessageIn**。  
  
    1.  在**傳送埠屬性**對話方塊中的，從左窗格中，按一下**篩選**。  
  
    2.  在右窗格中，在**屬性**資料行中，按一下方格中，然後選取**BTS。ReceivePortName**屬性。  
  
    3.  如**運算子**欄中，選取 「**==**"。  
  
    4.  如**值**資料行中，指定的檔案名稱的接收埠， `MessageIn`。  
  
7.  在**傳送埠屬性**對話方塊**一般**索引標籤上，從**類型**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。  
  
8.  在**Wcf-custom 傳輸屬性**對話方塊方塊中，執行下列動作：  
  
    1.  按一下**一般** 索引標籤，然後在**位址 (URI)**欄位中，指定 SQL Server 的連線 URI。 如需連線 URI 的詳細資訊，請參閱[建立 SQL Server 連接 URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)。  
  
    2.  在**一般**索引標籤的**動作**文字方塊中，輸入作業的動作。 請參閱[訊息與訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)的每個作業的動作清單。 例如，叫用 ADD_LAST_EMP_XML_INFO 的動作是：  
  
        ```  
        Procedure/dbo/ADD_LAST_EMP_XML_INFO  
        ```  
  
    3.  按一下**繫結** 索引標籤，並從**繫結的型別**清單中，選取**sqlBinding**。 您可以指定不同的繫結屬性所公開[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
    4.  按一下**認證**索引標籤，然後再執行下列其中一項：  
  
        -   選取**不會使用單一登入**選項，以及指定的使用者名稱和密碼來連接到 SQL Server。 請注意使用者名稱和密碼會區分大小寫。  
  
            > [!NOTE]
            >  如果您想要連接到 SQL Server 使用 Windows 驗證，請指定空白的使用者名稱和密碼。  
  
        -   選取**使用單一登入**選項，然後再指定分支機構企業單一登入 (SSO) 應用程式。  
  
             如需相對於 BizTalk Server 安全性的詳細資訊，請參閱[使用 SQL 配接器和 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md)。
  
    5.  按一下**訊息** 索引標籤，然後在**輸出 WCF 訊息內文**區段中，選擇**範本**選項。  
  
    6.  在**XML**文字方塊中，指定將用來建構 WCF 訊息的範本。 如此一來，您會建立訊息，以 WCF 為基礎的 ADD_LAST_EMP_XML_INFO 作業符合[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
         ![指定輸出 WCF 訊息的範本](../../adapters-and-accelerators/adapter-sql/media/012e9ff0-b78f-4a1d-8a3a-a7b8e3850d55.gif "012e9ff0-b78f-4a1d-8a3a-a7b8e3850d55")  
  
         ADD_LAST_EMP_XML_INFO 預存程序中，您必須指定下列範本：  
  
        ```  
        <ADD_LAST_EMP_XML_INFO xmlns="http://schemas.microsoft.com/Sql/2008/05/Procedures/dbo">  
        <xml_info>  
        \<bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="string"/>  
        </xml_info>  
        </ADD_LAST_EMP_XML_INFO>  
        ```  
  
        > [!IMPORTANT]
        >  訊息範本中的編碼方式必須一律為 「 字串 」，不論作業將會使用傳送埠時叫用參數的型別。 例如，ADD_LAST_EMP_XML_INFO 接受的參數類型的 XML，但訊息範本中的編碼方式為字串。  
  
        > [!NOTE]
        >  您可以複製預存程序的要求訊息和 < xml_info > 標記內的值取代 BizTalk 訊息內文，以建立這個郵件範本。 您也可以產生結構描述的程序使用預存程序取得要求訊息[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，然後產生取得要求 XML 結構描述的執行個體。  
  
    7.  若要返回**傳送埠屬性**對話方塊中，按一下 **確定**。  
  
9. 從**傳送處理常式**清單中，選取**BizTalkServerApplication**。  
  
10. 從**傳送管線**清單中，選取管線以對應至**PassThruTransmit**。  
  
11. 按一下 **[確定]**。  
  
## <a name="start-the-application"></a>啟動應用程式  
 若要啟動 BizTalk 應用程式，您可以啟動這兩個檔案接收位置和 WCF 自訂個別傳送埠。 您必須現在複製 XML 檔案的資料夾對應到檔案接收位置。 BizTalk 應用程式會使用檔，並在員工資料表的 [位址] 欄插入的 XML 值。 您可以驗證，請使用 SQL Server 用戶端，並選取從 Employee 資料表的記錄。  
  
## <a name="using-a-two-way-wcf-custom-send-port"></a>使用雙向 WCF 自訂傳送連接埠  
 本主題中下一節, 中的指示[如何設定 Wcf-custom 傳送埠](../../core/how-to-configure-a-wcf-custom-send-port.md)，示範如何設定單向的 WCF 自訂傳送連接埠，具有單一參數的預存程序執行而不需使用 BizTalk協調流程。 不過，在這種情況下，若要確認是否要執行預存程序成功您必須確認 SQL Server 資料庫中是否已經更新 Employee 資料表中的 [位址] 欄。  
  
 相反地，您可以建立也取得從 SQL Server 的回應，如果預存程序執行成功的雙向 Wcf-custom 傳送埠。 如果您要建立雙向 WCF 自訂連接埠，您必須執行一些額外的步驟。 請注意，您仍然需要的檔案接收位置，如前述的指示中所述。  
  
1.  例如，建立雙向 Wcf-custom 傳送埠， **ExecProcedure**。 若要設定傳送埠的步驟是類似的單向傳送埠。 唯一的差異在於，如雙向連接埠，您也必須指定接收管線。 請確定您選取**PassThruReceive**接收管線。  
  
2.  建立 FILE 傳送埠。 此連接埠會從卸除的回應訊息的 SQL Server 資料庫的資料夾。 使用**篩選** 索引標籤的 連接埠屬性 對話方塊中，設定 Wcf-custom 傳送埠從接收所有回應訊息的 FILE 傳送埠。  
  
    1.  在**傳送埠屬性**對話方塊中的，從左窗格中，按一下**篩選**。  
  
    2.  在右窗格中，在**屬性**資料行中，按一下方格中，然後選取**BTS。SPName**屬性。  
  
    3.  如**運算子**欄中，選取 「**==**"。  
  
    4.  如**值**資料行中，指定名稱的 「 WCF 自訂傳送連接埠， `ExecProcedure`。  
  
 啟動所有的三個連接埠。 複製 XML 檔案的資料夾對應到檔案接收位置。 尋找對應到檔案的資料夾中的回應傳送埠。  
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式使用 SQL 配接器](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)