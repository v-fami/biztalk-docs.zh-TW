---
title: 使用 BizTalk Server 的 SQL Server 中執行具有單一 XML 參數的預存程序 |Microsoft Docs
description: 使用 WCF 自訂連接埠與 SQL 配接器在 BizTalk 中的預存程序傳遞單一參數
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: deb9333a-5e28-4e8d-8e0b-07b5a97a111b
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a71ee5be554393db10e65adb49694e7104bb011b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976921"
---
# <a name="execute-stored-procedures-with-a-single-xml-parameter-in-sql-server-using-biztalk-server"></a>使用 BizTalk Server 的 SQL Server 中執行具有單一 XML 參數的預存程序
執行預存程序接受單一參數是類似於執行任何其他預存程序中所述[使用 BizTalk Server 的 SQL Server 中執行預存程序](execute-stored-procedures-in-sql-server-using-biztalk-server.md)。 不過，如上述連結內所述的方法，您需要在設計階段產生預存程序的中繼資料和建立協調流程叫用在執行階段的程序。  
  
 假設您只想將一個單一值傳遞至預存程序，而不進行任何處理數值。 在此情況下，您不想產生中繼資料、 建立協調流程、 部署協調流程，以及執行作業的額外負荷。 相反地，您可以設定 Wcf-custom 或 WCF SQL 傳送埠直接叫用預存程序。 本主題示範如何使用執行這些工作[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
> [!NOTE]
>  本主題提供有關如何設定 Wcf-custom 傳送埠執行採用單一參數的預存程序。 您可以藉由設定 WCF SQL 連接埠來執行相同的步驟。 如需設定 WCF SQL 連接埠的指示，請參閱[設定使用 WCF-SQL 配接器的連接埠](configure-a-port-using-the-wcf-sql-adapter.md)。  
  
## <a name="invoke-stored-procedures-without-orchestration"></a>叫用預存程序，而不需要協調流程  
 為了示範如何執行而不需要協調流程的單一參數的預存程序，本主題會使用 ADD_LAST_EMP_XML_INFO 預存程序。 此程序會採用 XML 值做為參數，並將它插入至**地址**資料行**員工**資料表。 您必須具有您將會傳遞至預存程序的 XML 值。 不過，若要執行預存程序中使用配接器，您必須傳送要求訊息符合之結構描述的程序中，而且包含的 XML 值**地址**欄位中，SQL server。 因此，您必須建立該要求訊息：  
  
- 使用**範本**中使用您可以建立使用訊息範本的要求訊息的傳送埠組態選項。  
  
- 將 XML 值**地址**欄位到訊息。  
  
  本主題中的詳細說明所有這些步驟。 您必須執行下列一組工作：  
  
1. 建立檔案接收的埠會放置會插入到 XML 檔案的位置**地址**XML 欄位**員工**資料表。 假設此連接埠稱為**MessageIn**連接埠。  
  
2. 建立 Wcf-custom 單向傳送埠來挑選 XML 檔案從檔案接收埠、 建構訊息使用訊息的範本，並將它傳送到 SQL Server 以執行預存程序。  
  
   本主題的這個部分提供有關設定 Wcf-custom 傳送埠時的訊息範本。  
  
> [!NOTE]
>  雖然本主題中的資訊會示範如何執行具有單一 XML 參數的預存程序，您可以執行的工作執行任何作業，會採用單一參數的任何資料類型。 唯一的差異會在您建立的特定作業的訊息範本的方式。 您可以建立的訊息範本依照您用來執行作業的要求訊息使用協調流程和參數的值取代為 BizTalk 訊息內文。  
  
##  <a name="BKMK_OneWay"></a> 設定 Wcf-custom 傳送埠  
 然後再建立 Wcf-custom 傳送埠時，請確定您在建立檔案接收埠**MessageIn**。  
  
1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3. 展開您要在其下部署的應用程式[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
4. 以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後指向**靜態單向傳送埠**。  
  
5. 在 **傳送埠屬性**對話方塊的 **一般**索引標籤上，輸入傳送埠的名稱。  
  
6. 設定連接埠接收所有檔案在卸除的訊息接收連接埠**MessageIn**。  
  
   1.  在 **傳送埠屬性**對話方塊中，從左窗格中，按一下**篩選**。  
  
   2.  在右窗格中，在**屬性**資料行中，按一下方格中，然後選取**BTS。ReceivePortName**屬性。  
  
   3.  針對**運算子**欄中，選取 「**==**"。  
  
   4.  針對**值**資料行中，指定的檔案名稱的接收埠， `MessageIn`。  
  
7. 在 **傳送埠屬性**對話方塊的 **一般**索引標籤上，從**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。  
  
8. 在  **Wcf-custom 傳輸屬性**對話方塊方塊中，執行下列動作：  
  
   1. 按一下 [**一般**] 索引標籤，然後在**位址 (URI)** 欄位中，指定 SQL Server 的連線 URI。 如需連線 URI 的詳細資訊，請參閱[建立 SQL Server 連接 URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)。  
  
   2. 在 **一般**索引標籤中，於**動作**文字方塊中，輸入作業的動作。 請參閱[訊息和訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)的每個作業的動作清單。 例如，叫用 ADD_LAST_EMP_XML_INFO 的動作是：  
  
      ```  
      Procedure/dbo/ADD_LAST_EMP_XML_INFO  
      ```  
  
   3. 按一下 **繫結**索引標籤上，以及從**繫結的型別**清單中，選取**sqlBinding**。 您可以指定不同的繫結屬性所公開[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
   4. 按一下 **認證**索引標籤，然後再執行下列其中一項：  
  
      -   選取 **不會使用單一登入**選項，以及指定的使用者名稱和密碼來連接到 SQL Server。 請注意，使用者名稱和密碼會區分大小寫。  
  
          > [!NOTE]
          >  如果您想要連接到 SQL Server 使用 Windows 驗證，請指定空白的使用者名稱和密碼。  
  
      -   選取 **使用單一登入**選項，然後再指定分支機構應用程式企業單一登入 (SSO)。  
  
           如需安全性相對於 BizTalk Server 的詳細資訊，請參閱[SQL 配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md)。
  
   5. 按一下 [**訊息**] 索引標籤，然後在**輸出 WCF 訊息內文**區段中，選擇**範本**選項。  
  
   6. 在  **XML**文字方塊中，指定將用來建構 WCF 訊息的範本。 這樣做，您建立符合以 WCF 為基礎的 ADD_LAST_EMP_XML_INFO 作業訊息[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
       ![指定輸出 WCF 訊息的範本](../../adapters-and-accelerators/adapter-sql/media/012e9ff0-b78f-4a1d-8a3a-a7b8e3850d55.gif "012e9ff0-b78f-4a1d-8a3a-a7b8e3850d55")  
  
       ADD_LAST_EMP_XML_INFO 預存程序中，您必須指定下列範本：  
  
      ```  
      <ADD_LAST_EMP_XML_INFO xmlns="http://schemas.microsoft.com/Sql/2008/05/Procedures/dbo">  
      <xml_info>  
      <bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="string"/>  
      </xml_info>  
      </ADD_LAST_EMP_XML_INFO>  
      ```  
  
      > [!IMPORTANT]
      >  訊息範本中的編碼方式必須一律為 「 字串 」 類型的作業，並使用傳送埠時叫用的參數。 比方說，ADD_LAST_EMP_XML_INFO 採用 XML 類型，類型參數，但訊息範本中的編碼方式為字串。  
      > 
      > [!NOTE]
      >  您可以複製預存程序的要求訊息，並將 < xml_info > 標記內的值取代為 BizTalk 訊息內文，以建立此訊息範本。 您也可以產生程序使用的結構描述的預存程序取得要求訊息[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，然後產生取得要求 XML 結構描述的執行個體。  
  
   7. 若要返回**傳送埠屬性** 對話方塊中，按一下**確定**。  
  
9. 從**傳送處理常式**清單中，選取**BizTalkServerApplication**。  
  
10. 從**傳送管線**清單中，選取管線以對應至**PassThruTransmit**。  
  
11. 按一下 [確定] 。  
  
## <a name="start-the-application"></a>啟動應用程式  
 若要啟動的 BizTalk 應用程式，您可以啟動這兩個檔案接收位置，然後個別 「 WCF 自訂傳送連接埠。 您必須現在複製資料夾對應至檔案的 XML 檔案接收位置。 BizTalk 應用程式使用的檔案，並插入員工資料表的 [位址] 欄位中的 XML 值。 您可以驗證，請使用 SQL Server 用戶端，並選取從 Employee 資料表的記錄。  
  
## <a name="using-a-two-way-wcf-custom-send-port"></a>使用雙向 WCF 自訂傳送連接埠  
 本主題中下一節, 中的指示[如何設定 Wcf-custom 傳送埠](../../core/how-to-configure-a-wcf-custom-send-port.md)，示範如何設定單向的 WCF 自訂傳送連接埠，來執行具有單一參數的預存程序，而不需使用 BizTalk協調流程。 不過，在此情況下，若要確認是否要執行預存程序已成功您必須確認 SQL Server 資料庫中是否已更新 Employee 資料表中的 [位址] 欄。  
  
 相反地，您可以建立也取得從 SQL Server 的回應，如果預存程序執行成功的雙向 Wcf-custom 傳送埠。 如果您要建立雙向的 WCF 自訂連接埠，您必須執行一些額外的步驟。 請注意，您仍然需要的檔案接收位置，如先前的指示中所述。  
  
1. 建立雙向的 Wcf-custom 傳送埠，例如**ExecProcedure**。 若要設定傳送埠的步驟會類似於單向傳送埠。 唯一的差別是，如雙向連接埠，您也必須指定接收管線。 請確定您選取**PassThruReceive**接收管線。  
  
2. 建立 FILE 傳送埠。 此連接埠會從卸除的回應訊息的 SQL Server 資料庫的資料夾。 使用**篩選器** 索引標籤的 連接埠屬性 對話方塊中，設定 Wcf-custom 傳送埠從接收所有回應訊息的 FILE 傳送埠。  
  
   1.  在 **傳送埠屬性**對話方塊中，從左窗格中，按一下**篩選**。  
  
   2.  在右窗格中，在**屬性**資料行中，按一下方格中，然後選取**BTS。SPName**屬性。  
  
   3.  針對**運算子**欄中，選取 「**==**"。  
  
   4.  針對**值**資料行中，指定名稱的 Wcf-custom 傳送埠， `ExecProcedure`。  
  
   啟動所有三個連接埠。 複製 XML 檔案，才能對應至檔案的資料夾接收位置。 尋找對應至檔案的資料夾中的回應傳送埠。  
  
## <a name="see-also"></a>另請參閱  
[使用 SQL 配接器開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)