---
title: 從 SQL Server 使用 BizTalk Server 接收強型別輪詢基礎資料變更訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e6e6ba7e-9e13-4e28-b57d-d24569277bbc
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b12450e87e730e3713a89350fc2a16440e4d911
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25968052"
---
# <a name="receive-strongly-typed-polling-based-data-changed-messages-from-sql-server-using-biztalk-server"></a>從 SQL Server 使用 BizTalk Server 接收強型別輪詢基礎資料變更訊息
您可以設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]來接收 SQL Server 中的強型別輪詢訊息。 您可以指定執行以輪詢資料庫配接器的輪詢陳述式。 輪詢陳述式可以是 SELECT 陳述式或預存程序會傳回結果集。  
  
 您必須使用強型別輪詢，在案例中您要將輪詢訊息中的項目對應至任何其他結構描述。 您想要對應至結構的描述可能是 SQL Server 上的另一個作業。 比方說，您可以在其他資料表插入作業結構描述對應輪詢訊息中的特定項目。 因此，輪詢訊息中的值會做為參數的 Insert 作業。 在簡單案例中，您可以對應強型別輪詢訊息的結構描述只會儲存資訊的結構描述檔案。  
  
> [!IMPORTANT]
>  如果您想要在單一的 BizTalk 應用程式中有一個以上的輪詢作業，您必須指定**InboundID**一部分連線 URI 成為唯一的連接屬性。 使用一個唯一的連接 URI，您可以建立多個接收輪詢相同的資料庫或甚至相同資料庫的資料表中的連接埠。 如需詳細資訊，請參閱[收到輪詢訊息跨多個接收埠使用 Biztalk Server 的 sql](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-across-multiple-receive-ports-from-sql-using-biztalk.md)。  
  
 如需配接器如何支援強型別輪詢的詳細資訊，請參閱[支援輪詢](https://msdn.microsoft.com/library/dd788416.aspx)。 如需強型別輪詢的訊息結構描述的詳細資訊，請參閱[輪詢和 TypedPolling 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-the-polling-and-typedpolling-operations.md)。  
  
## <a name="how-this-topic-demonstrates-strongly-typed-polling"></a>本主題將強型別輪詢的示範  
 本主題示範如何使用強型別輪詢的輪詢訊息對應到另一個結構描述。 本主題示範如何建立 BizTalk 專案，並產生結構描述的**TypedPolling**作業。 產生結構描述之前**TypedPolling**作業，您必須執行下列動作：  
  
-   您必須指定**InboundID**連線 URI 的一部分。  
  
-   您必須指定輪詢陳述式的**PollingStatement**繫結屬性。  
  
 輪詢陳述式的一部分，執行下列作業：  
  
-   選取從 Employee 資料表的所有資料列。  
  
-   執行預存程序 (MOVE_EMP_DATA) 會將所有的記錄從 Employee 資料表 EmployeeHistory 資料表。  
  
-   執行預存程序 (ADD_EMP_DETAILS) Employee 資料表中加入新的記錄。 此程序會接受員工名稱、 指定和薪資做為參數。  
  
 若要執行這些作業，您必須指定下列**PollingStatement**繫結屬性：  
  
```  
SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000   
```  
  
 因為您產生結構描述的**TypedPolling**操作時，結構描述是強型別，包含將輪詢訊息中包含的所有項目。  
  
 相同的 BizTalk 專案的一部分，您可以加入另一個結構描述檔案，例如 EmployeeDetails.xsd。 EmployeeDetails.xsd 的結構描述如下所示：  
  
```  
<?xml version="1.0" encoding="utf-16" ?>   
<xs:schema xmlns:b="http://schemas.microsoft.com/BizTalk/2003" xmlns="http://Typed_Polling.EmployeeDetails" elementFormDefault="qualified" targetNamespace="http://Typed_Polling.EmployeeDetails" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="EmployeeDetails">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="Employee_Info" type="xs:string" />   
        <xs:element name="Employee_Profile" type="xs:string" />   
        <xs:element name="Employee_Performance" type="xs:string" />   
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
 您也會加入至專案，以將元素從 Employee 資料表 （收到的輪詢訊息） EmployeeDetails.xsd 結構描述中的項目對應的 BizTalk 對應工具。 對應的一部分，您可以結合輪詢訊息從一個或多個項目，並將它對應 EmployeeDetails 結構描述中單一項目。 您可以使用**字串串連**運算質。  
  
 最後，屬於 BizTalk 專案中，符合 EmployeeDetails.xsd 結構描述的檔案拖曳至 FILE 傳送埠。  
  
## <a name="configure-typed-polling-with-the-sql-adapter-binding-properties"></a>設定 SQL 配接器繫結屬性的型別的輪詢  
 下表摘要說明[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]繫結，您用來設定配接器來接收資料變更訊息的屬性。 除了**PollingStatement**繫結屬性，所有其他繫結屬性本節所列的是必要設定中的接收埠時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 您必須指定**PollingStatement**之前產生結構描述的繫結屬性**TypedPolling**作業。  
  
> [!NOTE]
>  針對具型別輪詢，您必須指定**PollingStatement**飛過產生結構描述時的屬性。 您可以選擇指定的其他繫結屬性以及在產生結構描述中，即使它們並非必要。 如果您指定的繫結內容，連接埠繫結檔，[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生的中繼資料產生的組件也包含您指定的繫結屬性的值。 您可以稍後匯入此繫結檔案[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台建立 wcf-custom 或 WCF SQL 接收埠以繫結已設定的屬性。 如需有關如何建立使用該繫結檔案的連接埠的詳細資訊，請參閱[設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)。  
  
|繫結屬性|Description|  
|----------------------|-----------------|  
|**InboundOperationType**|指定您是否要執行**輪詢**， **TypedPolling**，或**通知**輸入作業。 預設值是**輪詢**。 若要接收強型別輪詢訊息，將此設**TypedPolling**。|  
|**PolledDataAvailableStatement**|指定的 SQL 陳述式來判斷是否可用於輪詢的任何資料執行配接器。 SQL 陳述式必須傳回的結果集資料列和資料行所組成。 只有一個資料列是否可用，SQL 陳述式指定**PollingStatement**繫結屬性將會執行。|  
|**PollingIntervalInSeconds**|指定間隔，以秒為單位，此時[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]執行陳述式指定**PolledDataAvailableStatement**繫結屬性。 預設值是 30 秒。 輪詢間隔會決定後續輪詢間隔時間。 如果指定的間隔內執行的陳述式，則配接器就會等候剩餘的時間間隔中。|  
|**PollingStatement**|指定輪詢 SQL Server 資料庫資料表的 SQL 陳述式。 您可以指定簡單的 SELECT 陳述式或預存程序輪詢陳述式。 預設值是 null。 您必須指定的值**PollingStatement**來啟用輪詢。 輪詢陳述式在沒有進行輪詢，取決於可用的資料時，才會執行**PolledDataAvailableStatement**繫結屬性。 您可以指定任意數目的 SQL 陳述式以分號分隔。<br /><br /> **重要事項：** 如**TypedPolling**，您必須指定這個繫結屬性才能產生中繼資料。|  
|**PollWhileDataFound**|指定是否[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]忽略的輪詢間隔，並為指定的 SQL 陳述式會持續執行**PolledDataAvailableStatement**如果輪詢資料表中的資料可繫結屬性。 如果沒有資料可在資料表中，配接器會還原為執行 SQL 陳述式，在指定的輪詢間隔。 預設值是**false**。|  
  
 如需這些屬性的更完整說明，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。 如需完整的說明，如何使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]進一步來輪詢 SQL Server，請閱讀。  
  
## <a name="how-to-receive-strongly-typed-data-change-messages-from-the-sql-server-database"></a>如何接收來自 SQL Server 資料庫的強型別資料變更訊息  
 使用 SQL Server 資料庫上執行操作[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]涉及程序中所述的工作[開發 BizTalk 應用程式與 SQL 配接器的建置組塊](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)。 若要設定要接收強型別資料變更訊息的介面卡，這些工作包括：  
  
1.  建立 BizTalk 專案，然後再產生結構描述的**TypedPolling**作業。 您必須指定**InboundID**連接屬性和**PollingStatement**時產生結構描述繫結屬性。 例如，連線的 URI 指定的輸入識別碼，如下所示：  
  
    ```  
    mssql://mysqlserver//mysqldatabase?InboundID=mydatabaseId  
    ```  
  
2.  從 SQL Server 資料庫接收訊息的 BizTalk 專案中建立訊息。  
  
3.  建立協調流程接收訊息，從 SQL Server 資料庫，並將它們儲存到資料夾。  
  
4.  新增結構描述，例如 EmployeeDetails.xsd BizTalk 專案中。  
  
5.  加入至對應到 EmployeeDetails.xsd 結構描述的輪詢訊息的結構描述的 BizTalk 對應工具 」。  
  
6.  建置和部署 BizTalk 專案。  
  
7.  設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
    > [!IMPORTANT]
    >  輸入的輪詢案例對於您永遠必須設定單向的 WCF 自訂或 WCF SQL 接收埠。 雙向 Wcf-custom 或 WCF SQL 接收埠的輸入作業不支援。  
  
8.  啟動 BizTalk 應用程式。  
  
 本主題提供執行這些工作的指示。  
  
## <a name="sample-based-on-this-topic"></a>根據本主題的範例  
 基礎的範例，TypedPolling，本主題隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱[SQL 配接器範例](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md)。  
  
## <a name="generate-schema"></a>產生結構描述  
 您必須產生的結構描述**TypedPolling**作業。 請參閱[擷取中繼資料，使用 SQL 配接器的 Visual Studio 中的 SQL Server 作業的](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)如需有關如何產生結構描述。 產生結構描述時，請執行下列工作。  
  
1.  指定**InboundID**時指定連線 URI 的連接屬性。 如本主題中，您可以指定**InboundID**為**員工**。 如需連線 URI 的詳細資訊，請參閱[建立 SQL Server 連接 URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)。  
  
2.  指定的值**PollingStatement**繫結屬性。 如需此繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
     如需有關如何指定繫結屬性的指示，請參閱[設定 SQL 配接器的繫結屬性](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md)。  
  
3.  選取合約類型為**服務 （輸入作業）**。  
  
4.  產生結構描述的**TypedPolling**作業。  
  
## <a name="define-messages-and-message-types"></a>定義訊息和訊息類型  
 您先前產生的結構描述會描述 「 類型 」 所需的協調流程中的訊息。 訊息通常是為其型別由對應的結構描述所定義的變數。 一旦產生結構描述時，您必須訊息連結之協調流程檢視中的 BizTalk 專案。  
  
 本主題中，您必須建立一個從 SQL Server 資料庫接收訊息的訊息。  
  
 執行下列步驟來建立訊息，並將它們連結至結構描述。  
  
#### <a name="create-messages-and-link-to-schema"></a>建立訊息並連結到結構描述  
  
1.  BizTalk 專案中新增協調流程。 從 方案總管 中，以滑鼠右鍵按一下 BizTalk 專案名稱，指向**新增**，然後按一下 **新項目**。 輸入 BizTalk 協調流程的名稱，然後按一下**新增**。  
  
2.  如果它尚未開啟，請開啟 BizTalk 專案中，[協調流程檢視] 視窗。 按一下**檢視**，指向 **其他視窗**，然後按一下 **協調流程檢視**。  
  
3.  在**協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。  
  
4.  以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。  
  
5.  在**屬性**窗格**Message_1**，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |識別碼|型別**PollingMessage**。|  
    |訊息類型|從下拉式清單中，展開 **結構描述**，然後選取*Typed_Polling.TypedPolling_Employee.TypedPolling*，其中*Typed_Polling* BizTalk 的名稱專案。 *TypedPolling_Employee*是針對產生的結構描述**TypedPolling**作業。|  
  
## <a name="set-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]接收訊息以輪詢為基礎的資料變更從 SQL Server 資料庫。 在此協調流程中，配接器接收的輪詢訊息指定的輪詢陳述式。 BizTalk 對應工具則會對應至 EmployeeDetails.xsd 結構描述的輪詢訊息結構描述。 對應的訊息然後儲存至檔案位置。 典型的協調流程用於接收從 SQL Server 資料庫的強型別輪詢訊息就會包含：  
  
-   接收和傳送圖形，從 SQL Server 接收訊息，並分別將傳送至檔案連接埠。  
  
-   單向接收埠以接收來自 SQL Server 訊息。  
  
    > [!IMPORTANT]
    >  輸入的輪詢案例，您必須一律先設定單向接收埠。 雙向接收埠不支援的輸入操作。  
  
-   單向傳送埠以傳送輪詢回應從 SQL Server 資料庫，到資料夾。  
  
-   輪詢訊息的結構描述對應到任何結構描述的 BizTalk 對應工具 」。  
  
 範例協調流程如下。  
  
 ![協調流程的強式 &#45; 型別的輪詢](../../adapters-and-accelerators/adapter-sql/media/1db03859-b7f8-470c-9158-2be4da0b45ae.gif "1db03859-b7f8-470c-9158-2be4da0b45ae")  
  
### <a name="add-message-shapes"></a>新增訊息圖形  
 請確定您針對每個訊息圖形指定下列屬性。 圖形資料行中所列的名稱是訊息 圖形的名稱，為顯示在剛才提及的協調流程中。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ReceiveMessage|Receive|-設定**名稱**至*ReceiveMessage*<br /><br /> -設定**啟動**至 *，則為 True*|  
|SaveMessage|Send|-設定**名稱**至*SaveMessage*|  
  
### <a name="add-ports"></a>新增連接埠  
 請確定您針對每個邏輯連接埠指定下列屬性。 連接埠資料行中所列的名稱是連接埠的名稱，為顯示協調流程中。  
  
|通訊埠|屬性|  
|----------|----------------|  
|SQLReceivePort|-設定**識別碼**至*SQLReceivePort*<br /><br /> -設定**類型**至*SQLReceivePortType*<br /><br /> -設定**通訊模式**至*單向*<br /><br /> -設定**通訊方向**至*接收*|  
|SaveMessagePort|-設定**識別碼**至*SaveMessagePort*<br /><br /> -設定**類型**至*SaveMessagePortType*<br /><br /> -設定**通訊模式**至*單向*<br /><br /> -設定**通訊方向**至*傳送*|  
  
### <a name="enter-messages-for-action-shapes-and-connect-to-ports"></a>輸入動作圖形訊息並連接至連接埠  
 下表指定屬性和其值，您應該設定來指定動作圖形的訊息，以及連結至連接埠的訊息。 圖形資料行中所列的名稱是 「 訊息 」 圖形的名稱，為顯示在協調流程中先前所述。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveMessage|設定**訊息**至*PollingMessage*<br /><br /> 設定**作業**至*SQLReceivePort.TypedPolling.Request*|  
|SaveMessage|設定**訊息**至*PollingMessage*<br /><br /> 設定**作業**至*SaveMessagePort.TypedPolling.Request*|  
  
 您指定這些屬性之後，就會連接的訊息 圖形和連接埠。  
  
### <a name="add-a-biztalk-mapper"></a>新增 BizTalk 對應工具  
 您必須將 BizTalk 對應工具加入協調流程將輪詢訊息結構描述對應至 EmployeeDetails.xsd 結構描述。 在[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您將使用此對應來對應至 EmployeeDetails.xsd 架構的輪詢訊息的結構描述。  
  

1.  將 BizTalk 對應工具加入至 BizTalk 專案。 以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下**新項目**。  
  
     在**加入新項目**對話方塊的左窗格中，選取**對應檔**。 從右窗格中，選取**對應**。 指定對應名稱，例如`MapSchema.btm`。 按一下 **[加入]**。  
  
2.  從來源結構描述] 窗格中，按一下 [**開啟來源結構描述**。  
  
3.  在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，然後選取輪詢訊息的結構描述。 本主題中，選取 Typed_Polling.TypedPolling_Employee。 按一下 **[確定]**。  
  
4.  在**來源結構描述的根節點**對話方塊中，選取 TypedPolling 並按一下**確定**。  
  
5.  從 目的結構描述 窗格中，按一下 **開啟目的結構描述**。  
  
6.  在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，和 EmployeeDetails 針對選取的結構描述。 本主題中，選取 Typed_Polling.EmployeeDetails。 按一下 **[確定]**。  
  
7.  在輪詢訊息的來源結構描述中，展開 TypedPollingResultSet0 節點和後續的節點，以查看輪詢訊息中傳回的項目。 在目的結構描述中，展開 EmployeeDetails 節點以查看結構描述中的不同項目。 如本主題中，您必須將對應的方式中的結構描述的：  
  
    -   **Employee_ID**和**名稱**在來源結構描述必須對應到**Employee_Info**目的結構描述中。  
  
    -   **指定**和**Job_Description**在來源結構描述必須對應到**Employee_Profile**目的結構描述中。  
  
    -   **分級**和**薪資**在來源結構描述必須對應到**Employee_Performance**目的結構描述中。  
  
     若要結合多個來源結構描述中的節點，並將它們對應到目的結構描述中的單一節點，您必須使用**字串串連運算質**。 詳細資料[!INCLUDE[ui-guidance-developers-reference](../../includes/ui-guidance-developers-reference.md)]。
  
8.  若要使用 「 字串串連 」 運算質：  
  
    1.  從**工具箱**，拖曳**字串串連**運算質放在對應工具格線。  
  
    2.  連接**Employee_ID**和**名稱**」 運算質的來源結構描述中的項目。  
  
    3.  連接到運算質**Employee_Info**目的結構描述中的項目。  
  
    4.  您想要對應的所有項目重複這些步驟。 完成的對應會如下所示：  
  
         ![將強型別輪詢結構描述對應](../../adapters-and-accelerators/adapter-sql/media/0a4a2608-3b84-4bac-9a16-512cf42c7525.gif "0a4a2608-3b84-4bac-9a16-512cf42c7525")  
  
    5.  儲存對應。  
  
 在您建立 「 對應工具 」 之後，協調流程已完成。 您現在必須建置 BizTalk 方案，並部署到[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱[建置和執行協調流程](../../core/building-and-running-orchestrations.md)。
  
## <a name="configure-the-biztalk-application"></a>設定 BizTalk 應用程式  
 部署 BizTalk 專案之後，您稍早建立的協調流程會列在**協調流程**BizTalk Server 管理主控台 窗格。 您必須使用 BizTalk Server 管理主控台來設定應用程式。 如需逐步解說，請參閱[逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。
  
 設定應用程式包括：  
  
-   選取應用程式的主機。  
  
-   對應至 BizTalk Server 管理主控台中的實體連接埠在協調流程中建立的連接埠。 此協調流程中，您必須：  
  
    -   定義實體的 WCF 自訂或 WCF-SQL 單向接收埠。 此連接埠輪詢 SQL Server 資料庫與您指定連接埠輪詢陳述式。 如需如何建立連接埠相關資訊，請參閱[手動設定 SQL 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md)。 請確定指定接收埠的下列繫結屬性。  
  
        > [!IMPORTANT]
        >  請確定您指定**InboundID**連線 URI 的一部分。 輸入的識別碼必須是您指定在產生結構描述相同。  
  
        > [!IMPORTANT]
        >  您不需要執行這個步驟，如果您指定在設計階段的繫結屬性。 在此情況下，您可以建立 wcf-custom 或 WCF SQL 接收埠，設定必要的繫結屬性，藉由匯入所建立之繫結檔案[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 如需詳細資訊，請參閱[設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)。  
  
        |繫結屬性|值|  
        |----------------------|-----------|  
        |**InboundOperationType**|請確定您設定為**TypedPolling**。|  
        |**PolledDataAvailableStatement**|請確定您指定時產生的結構描述，也就是指定相同的 SQL 陳述式：<br /><br /> `SELECT COUNT(*) FROM Employee`|  
        |**PollingStatement**|請確定您提供您指定在產生結構描述中，也就是相同的輪詢陳述式：<br /><br /> `SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000`|  
  
         如需不同的繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
        > [!NOTE]
        >  我們建議您執行使用的輸入的操作時設定的交易隔離等級和異動逾時[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 您可以執行新增服務行為設定 Wcf-custom 或 WCF-SQL 時接收埠。 如需如何新增服務行為的指示，請參閱[設定交易隔離等級和交易逾時，使用 SQL](../../adapters-and-accelerators/adapter-sql/configure-transaction-isolation-level-and-transaction-timeout-with-sql.md)。  
  
    -   定義配接器將會卸除訊息的 FILE 傳送埠。 此傳送埠也會使用您在要對應至符合 EmployeeDetails.xsd 結構描述訊息的輪詢訊息的協調流程中建立的對應。 執行下列步驟，以設定 FILE 傳送埠，以使用對應。  
  
        1.  建立 FILE 傳送埠。  
  
        2.  從傳送埠屬性] 對話方塊的左窗格中，按一下 [**輸出對應**。 從右窗格中，按一下 下的欄位**對應**資料行中，從下拉式清單選取**MapSchema**。 按一下 **[確定]**。  
  
             ![FILE 傳送埠上設定輸出對應](../../adapters-and-accelerators/adapter-sql/media/831c9aee-fd97-466f-9270-3b04dbccd9fe.gif "831c9aee-fd97-466f-9270-3b04dbccd9fe")  
  
## <a name="start-the-application"></a>啟動應用程式  
 您必須啟動 SQL Server 資料庫從接收訊息的 BizTalk 應用程式。 如需啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。
  
 在這個階段，請確定：  
  
-   Wcf-custom 或 WCF-SQL 單向接收埠，會使用指定的陳述式的 SQL Server 資料庫的輪詢**PollingStatement**繫結屬性，正在執行。  
  
-   FILE 傳送埠，這會對應至 EmployeeDetails 結構描述的輪詢訊息，正在執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
## <a name="execute-the-operation"></a>執行作業  
 執行應用程式之後，執行下列一進行，以相同順序：  
  
-   執行配接器**PolledDataAvailableStatement** employee 資料表，並判斷資料表是否有記錄進行輪詢。  
  
-   配接器執行輪詢陳述式。 輪詢陳述式包含 SELECT 陳述式和預存程序，因為配接器的其他之後不會執行所有陳述式一個。  
  
    -   配接器會先執行 SELECT 陳述式會傳回 Employee 資料表中的所有記錄。  
  
    -   然後執行 MOVE_EMP_DATA 預存程序，會從 Employee 資料表的所有資料都移至 EmployeeHistory 資料表配接器。 這個預存程序沒有傳回任何值。  
  
    -   然後執行配接器加入 Employee 資料表中的一筆記錄的 ADD_EMP_DETAILS 預存程序。 這個預存程序傳回的員工識別碼插入記錄。  
  
     執行輪詢陳述式，並在接收訊息之後，輪詢訊息取得 FILE 傳送埠的傳送。 此處，輸出對應 (**MapSchema**) 設定 EmployeeDetails 結構描述的輪詢訊息的傳送埠對應，然後將訊息置放到檔案位置。 訊息如下所示：  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <EmployeeDetails xmlns="http://Typed_Polling.EmployeeDetails">  
      <Employee_Info>10751John</Employee_Info>   
      <Employee_Profile>TesterManagesTesting</Employee_Profile>   
      <Employee_Performance>100000</EmployeePerformance>  
    </EmployeeDetails>  
    ```  
  
     在上述的回應，您可以注意到 Employee_Info 項目包含員工識別碼 (10751) 及員工名稱 (John) 的組合。 其他項目也會包含在您建立的協調流程一部分的對應工具中對應的組合。  
  
> [!NOTE]
>  [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]將繼續輪詢直到您明確地停用接收埠從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以為 XML 檔案，稱為繫結檔案匯出組態設定。 一旦產生繫結檔案時，可以組態設定匯入檔案，使您不需要建立傳送埠和接收相同的協調流程連接埠。 如需繫結檔案的詳細資訊，請參閱[重複使用配接器繫結](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md)。
  
## <a name="see-also"></a>請參閱  
 [輪詢 SQL Server 與 BizTalk Server 使用 SQL 配接器](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-biztalk-server.md)