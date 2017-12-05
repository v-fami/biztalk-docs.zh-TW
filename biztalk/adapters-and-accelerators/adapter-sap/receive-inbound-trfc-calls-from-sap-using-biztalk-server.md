---
title: "從 SAP 使用 BizTalk Server 接收輸入的 tRFC 呼叫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tRFC calls, receiving using BizTalk Server
- tRFCs, sample
ms.assetid: 500eedea-3d27-478c-a64c-903a1fa2b02f
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 588e135507a2d186d9d8006836f5bdfb2940eb32
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="receive-inbound-trfc-calls-from-sap-using-biztalk-server"></a><span data-ttu-id="d017e-102">從 SAP 使用 BizTalk Server 接收輸入的 tRFC 呼叫</span><span class="sxs-lookup"><span data-stu-id="d017e-102">Receive Inbound tRFC Calls from SAP using BizTalk Server</span></span>
<span data-ttu-id="d017e-103">TRFC 伺服器呼叫是對交易式 RFC 伺服器呼叫。</span><span class="sxs-lookup"><span data-stu-id="d017e-103">A tRFC server call is a transactional RFC server call.</span></span> <span data-ttu-id="d017e-104">與協調流程接收從 SAP 系統傳送任何其他輸入的 RFC 相似接收 RFC 交易內容中所需的協調流程。</span><span class="sxs-lookup"><span data-stu-id="d017e-104">The orchestration required to receive an RFC in a transactional context is similar to the orchestration to receive any other inbound RFC sent from an SAP system.</span></span> <span data-ttu-id="d017e-105">不過，您需要執行某些其他工作，以確定 Rfc 接收交易內容中。</span><span class="sxs-lookup"><span data-stu-id="d017e-105">However, you need to perform certain additional tasks to make sure the RFCs are received in a transactional context.</span></span> <span data-ttu-id="d017e-106">如需有關從 SAP 系統使用接收傳入的 RFC [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱[從 SAP 使用 BizTalk Server 接收傳入的 RFC 呼叫](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-from-sap-using-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d017e-106">For more information about receiving an inbound RFC from the SAP system using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], see [Receive Inbound RFC Calls from SAP by using BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-from-sap-using-biztalk-server.md).</span></span> <span data-ttu-id="d017e-107">如需有關如何[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援接收輸入的 tRFC 呼叫從 SAP 系統，請參閱[tRFCs SAP 中的作業](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="d017e-107">For more information about how the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports receiving inbound tRFC calls from an SAP system, see [Operations on tRFCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md).</span></span>  
  
 <span data-ttu-id="d017e-108">接收從 SAP 系統傳送輸入的 tRFC 是相似接收傳入的 RFC，除了下列幾點差異以外：</span><span class="sxs-lookup"><span data-stu-id="d017e-108">Receiving an inbound tRFC sent from an SAP system is similar to receiving an inbound RFC, with the following differences:</span></span>  
  
1.  <span data-ttu-id="d017e-109">在設計階段，在產生結構描述中，確定您選取下的一個 tRFC **TRFC**節點。</span><span class="sxs-lookup"><span data-stu-id="d017e-109">At design time, while generating the schema, make sure you select the tRFC from under the **TRFC** node.</span></span>  
  
2.  <span data-ttu-id="d017e-110">在執行階段，確定您設定的繫結屬性**TidDatabaseConnectionString**。</span><span class="sxs-lookup"><span data-stu-id="d017e-110">At run time, make sure you set the binding property **TidDatabaseConnectionString**.</span></span> <span data-ttu-id="d017e-111">此屬性會接受連接字串以連接到 SQL 資料庫來存放 TID。</span><span class="sxs-lookup"><span data-stu-id="d017e-111">This property takes the connection string to connect to a SQL database to store the TID.</span></span> <span data-ttu-id="d017e-112">範例連接字串應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="d017e-112">A sample connection string would look like:</span></span>  
  
    ```  
    Data Source=<myServerAddress>;Initial Catalog=<myDataBase>;User Id=<myUsername>;Password=<myPassword>;  
    ```  
  
     <span data-ttu-id="d017e-113">如需繫結屬性和設定方式的詳細資訊，請參閱[了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="d017e-113">For more information about the binding property and how to set it, see [Read about BizTalk Adapter for mySAP Business Suite Binding Properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="d017e-114">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝精靈正在安裝的 SQL 指令碼、 SapAdapter-DbScript-Install.sql，必須執行 SQL Server 系統管理員可以在 SQL Server 中建立資料庫和資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="d017e-114">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup wizard installs a SQL script, SapAdapter-DbScript-Install.sql, which must be run by the SQL Server administrator to create a database and the database objects in SQL Server.</span></span> <span data-ttu-id="d017e-115">指令碼通常會安裝在*\<安裝磁碟機\>： 程式 FilesMicrosoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]* 。</span><span class="sxs-lookup"><span data-stu-id="d017e-115">The script is typically installed at *\<installation drive\>:Program FilesMicrosoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]*.</span></span>  
    >   
    >  <span data-ttu-id="d017e-116">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]保存 TIDs 會使用這些物件。</span><span class="sxs-lookup"><span data-stu-id="d017e-116">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses these objects to persist the TIDs.</span></span> <span data-ttu-id="d017e-117">因此，SQL Server 系統管理員必須確定使用者名稱提供連接字串的一部分有足夠的權限可以執行預存程序。</span><span class="sxs-lookup"><span data-stu-id="d017e-117">So, the SQL Server administrator must ensure that the user name provide as part of the connection string has sufficient privileges to execute the stored procedures.</span></span> <span data-ttu-id="d017e-118">提供 Windows 使用者具有足夠的權限的資料庫中執行預存程序，您也可以選擇 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="d017e-118">You can also opt for Windows authentication provided the Windows user has sufficient permissions to execute stored procedures in the database.</span></span>  
  
3.  <span data-ttu-id="d017e-119">請確定安裝配接器的電腦上啟用 MSDTC。</span><span class="sxs-lookup"><span data-stu-id="d017e-119">Make sure MSDTC is enabled on the computer where the adapter is installed.</span></span> <span data-ttu-id="d017e-120">執行下列步驟來啟用 MSDTC。</span><span class="sxs-lookup"><span data-stu-id="d017e-120">Perform the following steps to enable MSDTC.</span></span>  
  
    1.  <span data-ttu-id="d017e-121">啟動 [元件服務] MMC 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="d017e-121">Start the Component Services MMC snap-in.</span></span>  
  
    2.  <span data-ttu-id="d017e-122">在 [元件服務] MMC 嵌入式管理單元，從左窗格展開**元件服務**，展開**電腦**，以滑鼠右鍵按一下**我的電腦**，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="d017e-122">In the Component Services MMC snap-in, from the left pane expand **Component Services**, expand **Computers**, right-click **My Computer**, and click **Properties**.</span></span>  
  
    3.  <span data-ttu-id="d017e-123">在**我的電腦內容**對話方塊中，按一下 [ **MSDTC** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d017e-123">In the **My Computer Properties** dialog box, click the **MSDTC** tab.</span></span>  
  
    4.  <span data-ttu-id="d017e-124">在**交易設定**區段中，按一下**安全性組態** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d017e-124">In the **Transaction Configuration** section, click the **Security Configuration** button.</span></span>  
  
    5.  <span data-ttu-id="d017e-125">在**安全性組態**對話方塊中，選取**網路 DTC 存取**核取方塊，並在內，選取**允許遠端用戶端**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d017e-125">In the **Security Configuration** dialog box, select the **Network DTC Access** check box and within that, select the **Allow Remote Clients** check box.</span></span>  
  
    6.  <span data-ttu-id="d017e-126">在**交易管理員通訊**區段中，選取**允許輸入**和**允許輸出**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d017e-126">In the **Transaction Manager Communication** section, select the **Allow Inbound** and **Allow Outbound** check boxes.</span></span>  
  
    7.  <span data-ttu-id="d017e-127">在**安全性組態**對話方塊中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="d017e-127">In the **Security Configuration** dialog box, click **OK**.</span></span>  
  
    8.  <span data-ttu-id="d017e-128">按一下**是**中對話方塊方塊中，通知將會重新啟動 MSDTC 服務。</span><span class="sxs-lookup"><span data-stu-id="d017e-128">Click **Yes** in the dialog box informing that the MSDTC service will be restarted.</span></span> <span data-ttu-id="d017e-129">重新啟動 MSDTC 服務之後，請按一下**確定**在對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="d017e-129">After the MSDTC service is restarted, click **OK** on the dialog box.</span></span>  
  
    9. <span data-ttu-id="d017e-130">在**我的電腦內容**對話方塊中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="d017e-130">In the **My Computer Properties** dialog box, click **OK**.</span></span>  
  
4.  <span data-ttu-id="d017e-131">MSDTC Windows 防火牆例外清單中，如果未新增已新增。</span><span class="sxs-lookup"><span data-stu-id="d017e-131">Add MSDTC to the Windows Firewall exception list, if not already added.</span></span> <span data-ttu-id="d017e-132">執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="d017e-132">Run the following command.</span></span>  
  
    ```  
    netsh firewall set allowedprogram %windir%\system32\msdtc.exe MSDTC enable  
    ```  
  
> [!IMPORTANT]
>  <span data-ttu-id="d017e-133">輸入的 tRFC 呼叫是從 「 交易 」 的內容中的 SAP 系統接收 Idoc 時使用。</span><span class="sxs-lookup"><span data-stu-id="d017e-133">An inbound tRFC call is used while receiving IDOCs from the SAP system in a "transactional" context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d017e-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="d017e-134">See Also</span></span>  
[<span data-ttu-id="d017e-135">開發 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="d017e-135">Develop BizTalk applications</span></span>](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)