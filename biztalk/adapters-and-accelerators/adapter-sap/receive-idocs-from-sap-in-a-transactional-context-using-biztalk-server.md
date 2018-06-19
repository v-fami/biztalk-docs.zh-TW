---
title: 從交易內容，使用 BizTalk Server 中的 SAP 接收 Idoc |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- transactional context
- IDOCs, receiving in a transactional context using BizTalk Server
ms.assetid: 6a01bb82-7292-4b70-8ad7-996d389a9365
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a8903b6010555b3c7c6aba9a07e12c9204bcf19c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25962740"
---
# <a name="receive-idocs-from-sap-in-a-transactional-context-using-biztalk-server"></a><span data-ttu-id="02ec2-102">從交易內容，使用 BizTalk Server 中的 SAP 接收 Idoc</span><span class="sxs-lookup"><span data-stu-id="02ec2-102">Receive IDOCs from SAP in a Transactional Context using BizTalk Server</span></span>
<span data-ttu-id="02ec2-103">交易內容中接收 IDOC 是相似接收 tRFCs 交易內容中。</span><span class="sxs-lookup"><span data-stu-id="02ec2-103">Receiving IDOC in a transactional context is similar to receiving tRFCs in a transactional context.</span></span> <span data-ttu-id="02ec2-104">在這種情況下，從 SAP 系統接收的 IDOC 包含 TID 一部分 *\<TransactionalRfcOperationIdentifier\>* 項目。</span><span class="sxs-lookup"><span data-stu-id="02ec2-104">In such a case, the IDOC received from the SAP system contains a TID as part of the *\<TransactionalRfcOperationIdentifier\>* element.</span></span> <span data-ttu-id="02ec2-105">此 TID 保存於 SQL 資料庫中的配接器。</span><span class="sxs-lookup"><span data-stu-id="02ec2-105">This TID is persisted in a SQL database by the adapter.</span></span> <span data-ttu-id="02ec2-106">如果 ABAP 程式碼會傳送 IDOC 之 SAP 系統中的有 「 認可工作 」 陳述式，TID 會刪除從 SQL database，將回應傳送到 SAP 系統之後。</span><span class="sxs-lookup"><span data-stu-id="02ec2-106">If the ABAP code in the SAP system that sends the IDOC has a "COMMIT WORK" statement, the TID is deleted from the SQL database after a response is sent back to the SAP system.</span></span>  
  
 <span data-ttu-id="02ec2-107">無論是否 IDOC 收到交易內容中不相似的需要來接收 IDOC 的協調流程。</span><span class="sxs-lookup"><span data-stu-id="02ec2-107">The orchestration required to receive an IDOC is similar irrespective of whether the IDOC is received in a transactional context or not.</span></span> <span data-ttu-id="02ec2-108">請參閱[從 SAP 接收 Idoc，使用 BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-idocs-from-sap-using-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="02ec2-108">See [Receive IDOCs from SAP by Using BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-idocs-from-sap-using-biztalk-server.md).</span></span> <span data-ttu-id="02ec2-109">不過，您需要執行某些其他工作，以確定交易內容中接收 Idoc。</span><span class="sxs-lookup"><span data-stu-id="02ec2-109">However, you need to perform certain additional tasks to make sure the IDOCs are received in a transactional context.</span></span>  
  
1.  <span data-ttu-id="02ec2-110">在設計階段產生您想要接收的 IDOC 的結構描述。</span><span class="sxs-lookup"><span data-stu-id="02ec2-110">At design time, generate the schema for an IDOC that you want to receive.</span></span>  
  
2.  <span data-ttu-id="02ec2-111">在執行階段，確定您設定的繫結屬性**TidDatabaseConnectionString**。</span><span class="sxs-lookup"><span data-stu-id="02ec2-111">At run time, make sure you set the binding property **TidDatabaseConnectionString**.</span></span> <span data-ttu-id="02ec2-112">此屬性會接受連接字串以連接到 SQL 資料庫來存放 TID。</span><span class="sxs-lookup"><span data-stu-id="02ec2-112">This property takes the connection string to connect to a SQL database to store the TID.</span></span> <span data-ttu-id="02ec2-113">範例連接字串應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="02ec2-113">A sample connection string would look like:</span></span>  
  
    ```  
    Data Source=<myServerAddress>;Initial Catalog=<myDataBase>;User Id=<myUsername>;Password=<myPassword>;  
    ```  
  
     <span data-ttu-id="02ec2-114">如需繫結屬性和設定方式的詳細資訊，請參閱[了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="02ec2-114">For more information about the binding property and how to set it, see [Read about BizTalk Adapter for mySAP Business Suite Binding Properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="02ec2-115">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝精靈正在安裝的 SQL 指令碼、 SapAdapter-DbScript-Install.sql，必須執行 SQL Server 系統管理員可以在 SQL Server 中建立資料庫和資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="02ec2-115">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup wizard installs a SQL script, SapAdapter-DbScript-Install.sql, which must be run by the SQL Server administrator to create a database and the database objects in SQL Server.</span></span> <span data-ttu-id="02ec2-116">指令碼通常會安裝在*\<安裝磁碟機\>*： 程式 FilesMicrosoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="02ec2-116">The script is typically installed at *\<installation drive\>*:Program FilesMicrosoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span>  
    >   
    >  <span data-ttu-id="02ec2-117">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]保存 TIDs 會使用這些物件。</span><span class="sxs-lookup"><span data-stu-id="02ec2-117">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses these objects to persist the TIDs.</span></span> <span data-ttu-id="02ec2-118">因此，SQL Server 系統管理員必須確定使用者名稱提供連接字串的一部分有足夠的權限可以執行預存程序。</span><span class="sxs-lookup"><span data-stu-id="02ec2-118">So, the SQL Server administrator must ensure that the user name provide as part of the connection string has sufficient privileges to execute the stored procedures.</span></span> <span data-ttu-id="02ec2-119">提供 Windows 使用者具有足夠的權限的資料庫中執行預存程序，您也可以選擇 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="02ec2-119">You can also opt for Windows authentication provided the Windows user has sufficient permissions to execute stored procedures in the database.</span></span>  
  
3.  <span data-ttu-id="02ec2-120">請確定安裝配接器的電腦上啟用 MSDTC。</span><span class="sxs-lookup"><span data-stu-id="02ec2-120">Make sure MSDTC is enabled on the computer where the adapter is installed.</span></span> <span data-ttu-id="02ec2-121">執行下列步驟來啟用 MSDTC。</span><span class="sxs-lookup"><span data-stu-id="02ec2-121">Perform the following steps to enable MSDTC.</span></span>  
  
    1.  <span data-ttu-id="02ec2-122">啟動 [元件服務] MMC 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="02ec2-122">Start the Component Services MMC snap-in.</span></span>  
  
    2.  <span data-ttu-id="02ec2-123">在 [元件服務] MMC 嵌入式管理單元，從左窗格展開**元件服務**，展開**電腦**，以滑鼠右鍵按一下**我的電腦**，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="02ec2-123">In the Component Services MMC snap-in, from the left pane expand **Component Services**, expand **Computers**, right-click **My Computer**, and click **Properties**.</span></span>  
  
    3.  <span data-ttu-id="02ec2-124">在**我的電腦內容**對話方塊中，按一下 [ **MSDTC** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="02ec2-124">In the **My Computer Properties** dialog box, click the **MSDTC** tab.</span></span>  
  
    4.  <span data-ttu-id="02ec2-125">在**交易設定**區段中，按一下**安全性組態** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="02ec2-125">In the **Transaction Configuration** section, click the **Security Configuration** button.</span></span>  
  
    5.  <span data-ttu-id="02ec2-126">在**安全性組態**對話方塊中，選取**網路 DTC 存取**核取方塊，並在內，選取**允許遠端用戶端**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="02ec2-126">In the **Security Configuration** dialog box, select the **Network DTC Access** check box and within that, select the **Allow Remote Clients** check box.</span></span>  
  
    6.  <span data-ttu-id="02ec2-127">在**交易管理員通訊**區段中，選取**允許輸入**和**允許輸出**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="02ec2-127">In the **Transaction Manager Communication** section, select the **Allow Inbound** and **Allow Outbound** check boxes.</span></span>  
  
    7.  <span data-ttu-id="02ec2-128">在**安全性組態**對話方塊中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="02ec2-128">In the **Security Configuration** dialog box, click **OK**.</span></span>  
  
    8.  <span data-ttu-id="02ec2-129">按一下**是**中對話方塊方塊中，通知將會重新啟動 MSDTC 服務。</span><span class="sxs-lookup"><span data-stu-id="02ec2-129">Click **Yes** in the dialog box informing that the MSDTC service will be restarted.</span></span> <span data-ttu-id="02ec2-130">重新啟動 MSDTC 服務之後，請按一下**確定**在對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="02ec2-130">After the MSDTC service is restarted, click **OK** on the dialog box.</span></span>  
  
    9. <span data-ttu-id="02ec2-131">在**我的電腦內容**對話方塊中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="02ec2-131">In the **My Computer Properties** dialog box, click **OK**.</span></span>  
  
4.  <span data-ttu-id="02ec2-132">MSDTC Windows 防火牆例外清單中，如果未新增已新增。</span><span class="sxs-lookup"><span data-stu-id="02ec2-132">Add MSDTC to the Windows Firewall exception list, if not already added.</span></span> <span data-ttu-id="02ec2-133">執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="02ec2-133">Run the following command.</span></span>  
  
    ```  
    netsh firewall set allowedprogram %windir%\system32\msdtc.exe MSDTC enable  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="02ec2-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="02ec2-134">See Also</span></span>  
[<span data-ttu-id="02ec2-135">開發 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="02ec2-135">Develop BizTalk applications</span></span>](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)