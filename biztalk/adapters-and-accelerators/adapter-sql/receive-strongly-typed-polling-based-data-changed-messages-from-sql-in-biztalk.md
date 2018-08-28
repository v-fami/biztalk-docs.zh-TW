---
title: 使用 BizTalk Server 從 SQL Server 接收強型別輪詢為基礎的資料變更訊息 |Microsoft Docs
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
ms.openlocfilehash: 5454a20e087a643acb6f2b0bc9735eae6d29b996
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976255"
---
# <a name="receive-strongly-typed-polling-based-data-changed-messages-from-sql-server-using-biztalk-server"></a>使用 BizTalk Server 從 SQL Server 接收強型別輪詢為基礎的資料變更訊息
您可以設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]來接收 SQL Server 中的強型別輪詢訊息。 您可以指定要輪詢的資料庫執行的配接器的輪詢陳述式。 輪詢陳述式可以是 SELECT 陳述式或預存程序會傳回結果集。  
  
 您必須使用強型別輪詢，在案例中您要將輪詢訊息中的項目對應至任何其他的結構描述。 SQL Server 上的另一個作業，可能是您想要對應至結構的描述。 例如，您可以將輪詢訊息中的特定項目對應至另一個資料表上的 [插入] 作業的結構描述。 因此，輪詢訊息中的值會做為參數的 Insert 作業。 在簡單的案例中，您可以將強型別輪詢訊息的結構描述對應至結構描述檔案，只會儲存資訊。  
  
> [!IMPORTANT]
>  如果您想要在單一的 BizTalk 應用程式中有一個以上的輪詢作業，您必須指定**InboundID**一部分的連線 URI，使其成為唯一的連接屬性。 使用唯一連線 URI，您可以建立多個接收輪詢相同的資料庫或甚至是相同的資料表在資料庫中的連接埠。 如需詳細資訊，請參閱 <<c0> [ 接收輪詢訊息跨多個接收埠從使用 Biztalk Server 的 SQL](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-across-multiple-receive-ports-from-sql-using-biztalk.md)。  
  
 如需配接器如何支援強型別輪詢的詳細資訊，請參閱[輪詢支援](https://msdn.microsoft.com/library/dd788416.aspx)。 如需有關強型別輪詢的訊息結構描述的詳細資訊，請參閱[輪詢和 TypedPolling 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-the-polling-and-typedpolling-operations.md)。  
  
## <a name="how-this-topic-demonstrates-strongly-typed-polling"></a>本主題將強型別輪詢的示範  
 本主題示範如何使用強型別輪詢的輪詢訊息對應到另一個結構描述。 本主題說明如何建立 BizTalk 專案，並產生結構描述**TypedPolling**作業。 產生結構描述之前**TypedPolling**作業中，您必須執行下列動作：  
  
- 您必須指定**InboundID**連線 URI 的一部分。  
  
- 您必須指定輪詢陳述式**PollingStatement**繫結屬性。  
  
  輪詢陳述式的一部分，執行下列作業：  
  
- 從 [員工] 資料表中選取所有資料列。  
  
- 執行預存程序 (MOVE_EMP_DATA) 將從 Employee 資料表的所有記錄都移至 EmployeeHistory 資料表。  
  
- 執行預存程序 (ADD_EMP_DETAILS)，將新記錄新增至 [員工] 資料表。 此程序會接受員工名稱、 指定和薪資做為參數。  
  
  若要執行這些作業，您必須指定下列**PollingStatement**繫結屬性：  
  
```  
SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000   
```  
  
 因為您產生結構描述**TypedPolling**操作時，結構描述為強型別，包含將輪詢訊息中包含的所有項目。  
  
 相同的 BizTalk 專案的一部分，您可以新增另一個結構描述檔案，例如 EmployeeDetails.xsd。 EmployeeDetails.xsd 的結構描述如下所示：  
  
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
  
 您也會加入至專案，以對應 EmployeeDetails.xsd 結構描述中的項目從 [員工] 資料表 （收到的輪詢訊息） 之項目的的 BizTalk 對應工具。 隨著對應的詳細資訊，您可以結合一或多個項目從輪詢訊息，並將它對應 EmployeeDetails 結構描述中的單一項目。 您可以使用來進行這**字串串連**運算質。  
  
 最後，屬於 BizTalk 專案中，符合 EmployeeDetails.xsd 結構描述檔案拖放至 FILE 傳送埠。  
  
## <a name="configure-typed-polling-with-the-sql-adapter-binding-properties"></a>設定 SQL 配接器繫結屬性的型別的輪詢  
 下表摘要說明[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]繫結屬性，您用來設定配接器接收資料變更訊息。 以外**PollingStatement**繫結屬性，所有其他繫結屬性列出這一節則需要設定中的接收埠時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 您必須指定**PollingStatement**才會產生結構描述繫結屬性**TypedPolling**作業。  
  
> [!NOTE]
>  針對具型別輪詢，您必須指定**PollingStatement**飛過產生結構描述時的屬性。 您可以選擇指定的其他繫結屬性以及產生結構描述時，即使它們並非必要。 如果您指定的繫結屬性，連接埠繫結檔案，[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生的中繼資料產生的組件也包含您指定的繫結屬性的值。 您可以稍後匯入此繫結檔案中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來建立 WCF 自訂或 WCF-SQL 與繫結屬性已設定接收埠。 如需建立使用該繫結檔案的連接埠的詳細資訊，請參閱 <<c0> [ 設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)。  
  
|         繫結屬性         |                                                                                                                                                                                                                                                                                                   描述                                                                                                                                                                                                                                                                                                    |
|----------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     **InboundOperationType**     |                                                                                                                                                                                                  指定是否要執行**輪詢**， **TypedPolling**，或**通知**輸入作業。 預設值是**輪詢**。 若要接收強型別輪詢訊息，將此設**TypedPolling**。                                                                                                                                                                                                   |
| **PolledDataAvailableStatement** |                                                                                                                                                 指定配接器執行，以判斷是否有任何資料可供輪詢 SQL 陳述式。 SQL 陳述式必須傳回的結果集資料列和資料行所組成。 如果可用的資料列，為指定的 SQL 陳述式僅**PollingStatement**屬性繫結將會執行。                                                                                                                                                 |
|   **PollingIntervalInSeconds**   |                                                                                   指定間隔 （秒），此時[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]執行陳述式指定**PolledDataAvailableStatement**繫結屬性。 預設值是 30 秒。 輪詢間隔會決定後續輪詢間隔的時間間隔。 如果指定的間隔內執行的陳述式，則配接器會等候剩餘的時間間隔中。                                                                                    |
|       **PollingStatement**       | 指定輪詢 SQL Server 資料庫資料表的 SQL 陳述式。 您可以指定簡單的 SELECT 陳述式或輪詢陳述式的預存程序。 預設值是 null。 您必須指定的值**PollingStatement**啟用輪詢。 輪詢陳述式在沒有可供輪詢，取決於使用的資料時，才會執行**PolledDataAvailableStatement**繫結屬性。 您可以指定任意數目的 SQL 陳述式以分號分隔。<br /><br /> **重要事項︰** For **TypedPolling**，您必須指定這個繫結屬性才能產生中繼資料。 |
|      **PollWhileDataFound**      |                                                                                      指定是否[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]忽略的輪詢間隔，並持續執行 SQL 陳述式指定**PolledDataAvailableStatement**繫結屬性，如果資料可在所輪詢的資料表。 如果沒有資料可在資料表中，配接器會還原為執行 SQL 陳述式，在指定的輪詢間隔。 預設值是**false**。                                                                                       |
  
 如需這些屬性的更完整說明，請參閱[了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。 如需完整的說明，如何使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]輪詢 SQL Server，可深入閱讀。  
  
## <a name="how-to-receive-strongly-typed-data-change-messages-from-the-sql-server-database"></a>如何接收從 SQL Server 資料庫的強型別資料變更訊息  
 執行 SQL Server 資料庫使用運算[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]具有[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]牽涉到程序中所述的工作[開發使用 SQL 配接器的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)。 若要設定要接收的強型別資料變更訊息的介面卡，這些工作如下：  
  
1. 建立 BizTalk 專案，然後再產生結構描述**TypedPolling**作業。 您必須指定**InboundID**連接屬性和**PollingStatement**時產生結構描述繫結屬性。 例如，連接 URI，連同指定的輸入識別碼，如下所示：  
  
   ```  
   mssql://mysqlserver//mysqldatabase?InboundID=mydatabaseId  
   ```  
  
2. 從 SQL Server 資料庫接收訊息的 BizTalk 專案中建立訊息。  
  
3. 建立協調流程接收的 SQL Server 資料庫中的訊息，並將它們儲存到資料夾。  
  
4. 新增結構描述，例如 EmployeeDetails.xsd BizTalk 專案中。  
  
5. 新增對應至 EmployeeDetails.xsd 結構描述的輪詢訊息的結構描述的 BizTalk 對應工具 」。  
  
6. 建置和部署 BizTalk 專案。  
  
7. 設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
   > [!IMPORTANT]
   >  輸入的輪詢案例一律必須設定單向的 WCF 自訂或 WCF SQL 接收埠。 雙向 WCF 自訂] 或 [WCF-SQL 接收埠不支援的輸入作業。  
  
8. 啟動 BizTalk 應用程式。  
  
   本主題提供執行這些工作的指示。  
  
## <a name="sample-based-on-this-topic"></a>根據本主題的範例  
 ，TypedPolling，根據本主題提供了範例[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱 < [SQL 配接器的範例](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md)。  
  
## <a name="generate-schema"></a>產生結構描述  
 您必須產生的結構描述**TypedPolling**作業。 請參閱[擷取使用 SQL 配接器的 Visual Studio 中的 SQL Server 作業的中繼資料](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)如需有關如何產生結構描述。 產生結構描述時，請執行下列工作。  
  
1.  指定**InboundID**時指定連線 URI 的連接屬性。 本主題中，您可以指定**InboundID**作為**員工**。 如需連線 URI 的詳細資訊，請參閱[建立 SQL Server 連接 URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)。  
  
2.  指定的值**PollingStatement**繫結屬性。 如需有關這個繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
     如需有關如何指定繫結屬性的指示，請參閱 <<c0> [ 設定 SQL 配接器的繫結屬性](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md)。  
  
3.  選取合約類型作為**服務 （輸入作業）**。  
  
4.  產生結構描述**TypedPolling**作業。  
  
## <a name="define-messages-and-message-types"></a>定義訊息和訊息類型  
 您稍早產生的結構描述會描述協調流程中的訊息所需的 「 類型 」。 訊息通常是一個變數，要為其類型會定義對應的結構。 一旦產生結構描述時，您必須訊息從 BizTalk 專案的協調流程檢視以將它的連結。  
  
 本主題中，您必須建立一則訊息來接收 SQL Server 資料庫中的訊息。  
  
 執行下列步驟來建立訊息，並將它們連結至結構描述。  
  
#### <a name="create-messages-and-link-to-schema"></a>建立訊息，並連結至結構描述  
  
1.  BizTalk 專案中新增協調流程。 從 [方案總管] 中，以滑鼠右鍵按一下 BizTalk 專案名稱，指向**新增**，然後按一下**新項目**。 輸入 BizTalk 協調流程的名稱，然後按一下**新增**。  
  
2.  如果它尚未開啟，請開啟 BizTalk 專案中，[協調流程檢視] 視窗。 按一下 **檢視**，指向**其他 Windows**，然後按一下**協調流程檢視**。  
  
3.  在 **協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。  
  
4.  以滑鼠右鍵按一下新建立的訊息，然後按**屬性 視窗**。  
  
5.  在 [**屬性**] 窗格**Message_1**，執行下列動作：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |識別碼|型別**PollingMessage**。|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*Typed_Polling.TypedPolling_Employee.TypedPolling*，其中*Typed_Polling*是 BizTalk 的名稱專案。 *TypedPolling_Employee*是針對產生的結構描述**TypedPolling**作業。|  
  
## <a name="set-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]接收以輪詢為基礎的資料變更訊息從 SQL Server 資料庫。 在此協調流程中，配接器接收的輪詢訊息指定的輪詢陳述式。 BizTalk 對應工具則會對應至 EmployeeDetails.xsd 結構描述的輪詢訊息結構描述。 對應的訊息然後儲存至檔案位置。 典型的協調流程用於接收從 SQL Server 資料庫的強型別輪詢訊息會包含：  
  
- 接收和傳送圖形，從 SQL Server 接收訊息，並分別將傳送至檔案連接埠。  
  
- 單向接收埠以接收來自 SQL Server 的訊息。  
  
  > [!IMPORTANT]
  >  輸入的輪詢案例，您必須一律設定為單向接收埠。 雙向接收埠不支援的輸入作業。  
  
- 單向傳送埠以將輪詢回應從 SQL Server 資料庫傳送到資料夾。  
  
- 輪詢訊息的結構描述對應到任何其他的結構描述的 BizTalk 對應工具 」。  
  
  範例協調流程如下所示。  
  
  ![協調流程的強式&#45;型別輪詢](../../adapters-and-accelerators/adapter-sql/media/1db03859-b7f8-470c-9158-2be4da0b45ae.gif "1db03859-b7f8-470c-9158-2be4da0b45ae")  
  
### <a name="add-message-shapes"></a>新增訊息圖形  
 請確定您針對每個訊息 圖形中指定下列屬性。 剛剛提到的協調流程中所示，圖形資料行中所列的名稱會是訊息 圖形的名稱。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ReceiveMessage|Receive|-設定**名稱**到*ReceiveMessage*<br /><br /> -設定**啟用**到 *，則為 True*|  
|SaveMessage|Send|輪詢間隔後，執行配接器再次**PolledDataAvailableStatement**。|  
  
### <a name="add-ports"></a>新增連接埠  
 請確定您針對每個邏輯連接埠中指定下列屬性。 協調流程中所示，連接埠資料行中所列的名稱會是連接埠的名稱。  
  
|通訊埠|屬性|  
|----------|----------------|  
|SQLReceivePort|-設定**識別碼**到*SQLReceivePort*<br /><br /> -設定**型別**到*SQLReceivePortType*<br /><br /> -設定**通訊模式**到*單向*<br /><br /> -設定**通訊方向**到*接收*|  
|SaveMessagePort|-設定**識別碼**到*SaveMessagePort*<br /><br /> -設定**型別**到*SaveMessagePortType*<br /><br /> -設定**通訊模式**到*單向*<br /><br /> -設定**通訊方向**到*傳送*|  
  
### <a name="enter-messages-for-action-shapes-and-connect-to-ports"></a>輸入動作圖形訊息並連接到連接埠  
 下表指定的屬性和屬性來指定動作圖形的訊息，以及連結至連接埠的訊息，您應該設定的值。 先前所述的協調流程中所示，圖形資料行中所列的名稱會是訊息 圖形的名稱。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveMessage|設定**訊息**到*PollingMessage*<br /><br /> 設定**作業**到*SQLReceivePort.TypedPolling.Request*|  
|SaveMessage|設定**訊息**到*PollingMessage*<br /><br /> 設定**作業**到*SaveMessagePort.TypedPolling.Request*|  
  
 您已指定這些屬性之後，會連接的訊息 圖形和連接埠。  
  
### <a name="add-a-biztalk-mapper"></a>新增 BizTalk 對應工具  
 您必須將 BizTalk 對應工具加入至輪詢訊息結構描述對應至 EmployeeDetails.xsd 結構描述的協調流程。 在 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您將使用此對應工具將輪詢訊息的結構描述對應至 EmployeeDetails.xsd 結構描述。  
  

1. 將 BizTalk 對應工具加入至 BizTalk 專案中。 以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下**新項目**。  
  
    在 **加入新項目**對話方塊中，從左窗格中，選取**對應檔**。 從右窗格中，選取**地圖**。 指定對應名稱，例如`MapSchema.btm`。 按一下 **[加入]**。  
  
2. 從來源結構描述 窗格中，按一下**開啟來源結構描述**。  
  
3. 在  **BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，，然後選取 輪詢訊息的結構描述。 本主題中，選取 [Typed_Polling.TypedPolling_Employee]。 按一下 [確定] 。  
  
4. 在 **來源結構描述的根節點** 對話方塊中，選取 TypedPolling 然後按一下 **確定**。  
  
5. 從目的結構描述 窗格中，按一下**開啟目的結構描述**。  
  
6. 在  **BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，依序展開**結構描述**，和選取的結構描述的 EmployeeDetails。 本主題中，選取 [Typed_Polling.EmployeeDetails]。 按一下 [確定] 。  
  
7. 在輪詢訊息的來源結構描述中，展開 TypedPollingResultSet0 節點和後續的節點，以查看會輪詢訊息中傳回的項目。 在目的結構描述中，展開 EmployeeDetails 節點以查看結構描述中的不同項目。 本主題中，您必須將對應的結構描述的方式，：  
  
   - **Employee_ID**並**名稱**來源中結構描述必須對應至**Employee_Info**目的結構描述中。  
  
   - **指定**並**Job_Description**來源中結構描述必須對應至**Employee_Profile**目的結構描述中。  
  
   - **評等**並**薪資**來源中結構描述必須對應至**Employee_Performance**目的結構描述中。  
  
     若要合併來源結構描述中的多個節點，並將它們對應至目的結構描述中的單一節點，您必須使用**字串串連運算質**。 詳細資料[!INCLUDE[ui-guidance-developers-reference](../../includes/ui-guidance-developers-reference.md)]。
  
8. 若要使用 「 字串串連 」 運算質：  
  
   1.  從**工具箱**，拖曳**字串串連**運算質放在對應工具格線。  
  
   2.  連接**Employee_ID**並**名稱**運算質將來源結構描述中的項目。  
  
   3.  連接到運算質**Employee_Info**目的結構描述中的項目。  
  
   4.  重複上述步驟，針對您想要對應的所有項目。 已完成的對應會如下所示：  
  
        ![將強型別輪詢結構描述對應](../../adapters-and-accelerators/adapter-sql/media/0a4a2608-3b84-4bac-9a16-512cf42c7525.gif "0a4a2608-3b84-4bac-9a16-512cf42c7525")  
  
   5.  儲存對應。  
  
   在您建立 「 對應工具 」 之後，協調流程已完成。 您現在必須建置 BizTalk 方案，並將其部署至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 建置和執行協調流程](../../core/building-and-running-orchestrations.md)。
  
## <a name="configure-the-biztalk-application"></a>設定 BizTalk 應用程式  
 您已部署的 BizTalk 專案之後，您稍早建立的協調流程會列在下**協調流程**在 BizTalk Server 管理主控台 窗格。 您必須使用 BizTalk Server 管理主控台來設定應用程式。 如需逐步解說，請參閱 <<c0> [ 逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。
  
 設定應用程式包含：  
  
- 選取應用程式主機。  
  
- 對應您在您在 BizTalk Server 管理主控台中的實體連接埠的協調流程中建立的連接埠。 此協調流程中，您必須：  
  
  - 不過，因為現在具有狀態為 0，則需要不有任何記錄，所以配接器會取得空的回應，如下列所示。 此連接埠會輪詢 SQL Server 資料庫，以您指定連接埠輪詢陳述式。 如需有關如何建立連接埠的資訊，請參閱 <<c0> [ 手動設定 SQL 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md)。 請確定指定接收埠的下列繫結屬性。  
  
    > [!IMPORTANT]
    >  請確定您指定**InboundID**連線 URI 的一部分。 輸入的識別碼必須是您指定在產生結構描述時相同。  
    > 
    > [!IMPORTANT]
    >  您不需要執行此步驟中，如果您指定在設計階段的繫結屬性。 在此情況下，您可以建立 wcf-custom 或 WCF SQL 接收埠中，設定必要的繫結屬性，藉由匯入所建立的繫結檔[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 如需詳細資訊，請參閱[設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)。  
  
    |繫結屬性|ReplTest1|  
    |----------------------|-----------|  
    |**InboundOperationType**|請確定您將此設**TypedPolling**。|  
    |**PolledDataAvailableStatement**|請確定您指定時產生的結構描述，也就是指定相同的 SQL 陳述式：<br /><br /> `SELECT COUNT(*) FROM Employee`|  
    |**PollingStatement**|請確定您提供相同的輪詢陳述式時產生的結構描述，也就是您指定：<br /><br /> `SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000`|  
  
     如需不同的繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
    > [!NOTE]
    >  我們建議您執行使用的輸入的操作時設定的交易隔離等級和交易等待時間[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 您可以執行加上服務行為設定 Wcf-custom 或 WCF-SQL 時接收埠。 如需有關如何新增服務行為的指示，請參閱[設定交易隔離等級和交易等待時間，使用 SQL](../../adapters-and-accelerators/adapter-sql/configure-transaction-isolation-level-and-transaction-timeout-with-sql.md)。  
  
  - 定義配接器將會卸除訊息的 FILE 傳送埠。 此傳送埠也會使用協調流程，將輪詢訊息對應至訊息符合 EmployeeDetails.xsd 結構描述中建立的對應。 執行下列步驟，以設定 FILE 傳送埠，以使用對應。  
  
    1.  建立 FILE 傳送埠。  
  
    2.  從傳送埠的 [屬性] 對話方塊的左窗格中，按一下**輸出對應**。 從右窗格中，按一下 下的欄位**地圖**資料行，然後從下拉式清單中選取**MapSchema**。 按一下 [確定] 。  
  
         ![FILE 傳送埠上設定輸出對應](../../adapters-and-accelerators/adapter-sql/media/831c9aee-fd97-466f-9270-3b04dbccd9fe.gif "831c9aee-fd97-466f-9270-3b04dbccd9fe")  
  
## <a name="start-the-application"></a>啟動應用程式  
 您必須啟動 SQL Server 資料庫中接收訊息的 BizTalk 應用程式。 如需有關啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。
  
 在這個階段，請確定：  
  
-   Wcf-custom 或 WCF-SQL 單向接收連接埠，就會使用指定的陳述式的 SQL Server 資料庫來輪詢**PollingStatement**繫結屬性，正在執行。  
  
-   FILE 傳送埠，這會對應至 EmployeeDetails 結構描述的輪詢訊息，正在執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
## <a name="execute-the-operation"></a>執行作業  
 執行應用程式之後，下列的一組動作進行，相同的順序：  
  
- 執行配接器**PolledDataAvailableStatement** employee 資料表，並判斷資料表是否有記錄進行輪詢。  
  
- 配接器執行輪詢陳述式。 輪詢陳述式是由 SELECT 陳述式和預存程序所組成，因為配接器會執行所有陳述式一個接著一個。  
  
  - 配接器會先執行 SELECT 陳述式會傳回 Employee 資料表中的所有記錄。  
  
  - 然後執行 MOVE_EMP_DATA 預存程序從 Employee 資料表的所有資料移動至 EmployeeHistory 資料表配接器。 這個預存程序不會傳回任何值。  
  
  - 配接器接著就執行 ADD_EMP_DETAILS 預存程序，將 [員工] 資料表中的一筆記錄。 這個預存程序傳回的員工識別碼插入之資料錄。  
  
    執行輪詢陳述式，並接收訊息之後，輪詢訊息取得傳送至 FILE 傳送埠。 這裡，輸出對應 (**MapSchema**) 設定的傳送埠地圖 EmployeeDetails 結構描述的輪詢訊息，並會捨棄訊息至檔案位置。 訊息如下所示：  
  
  ```  
  <?xml version="1.0" encoding="utf-8" ?>   
  <EmployeeDetails xmlns="http://Typed_Polling.EmployeeDetails">  
    <Employee_Info>10751John</Employee_Info>   
    <Employee_Profile>TesterManagesTesting</Employee_Profile>   
    <Employee_Performance>100000</EmployeePerformance>  
  </EmployeeDetails>  
  ```  
  
   在上述的回應中，您可以注意到 Employee_Info 項目包含員工識別碼 (10751) 和員工的姓名 （名字） 的組合。 其他項目也會包含對應的協調流程所建立的對應工具中的組合。  
  
> [!NOTE]
>  [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]將繼續輪詢，直到您明確停用接收埠從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以匯出至 XML 檔案，稱為繫結檔案的組態設定。 一旦您產生繫結檔案時，您可以匯入的組態設定檔案，，讓您不需要建立傳送埠和接收相同的協調流程的連接埠。 如需有關繫結檔案的詳細資訊，請參閱 <<c0> [ 重複使用配接器繫結](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md)。
  
## <a name="see-also"></a>另請參閱  
 [使用 SQL 配接器與 BizTalk Server 輪詢 SQL Server](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-biztalk-server.md)