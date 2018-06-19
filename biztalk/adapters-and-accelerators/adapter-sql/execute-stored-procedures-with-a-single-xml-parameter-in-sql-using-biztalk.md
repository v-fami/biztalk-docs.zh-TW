---
title: 使用 BizTalk Server 的 SQL Server 中執行具有單一 XML 參數的預存程序 |Microsoft 文件
description: 預存程序使用中 BizTalk WCF 自訂連接埠和 SQL 配接器中傳遞單一參數
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
ms.openlocfilehash: 02c5f239300140022b1d26f35664add744b630c2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25964596"
---
# <a name="execute-stored-procedures-with-a-single-xml-parameter-in-sql-server-using-biztalk-server"></a><span data-ttu-id="a0c38-103">使用 BizTalk Server 的 SQL Server 中執行具有單一 XML 參數的預存程序</span><span class="sxs-lookup"><span data-stu-id="a0c38-103">Execute stored procedures with a single XML parameter in SQL Server using BizTalk Server</span></span>
<span data-ttu-id="a0c38-104">執行採用單一參數的預存程序是類似於執行任何其他預存程序中所述[使用 BizTalk Server 的 SQL Server 中執行預存程序](execute-stored-procedures-in-sql-server-using-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="a0c38-104">Executing a stored procedure that takes a single parameter is similar to executing any other stored procedure as described in [Execute Stored Procedures in SQL Server using BizTalk Server](execute-stored-procedures-in-sql-server-using-biztalk-server.md).</span></span> <span data-ttu-id="a0c38-105">不過，如上述的連結中所述的方法，您要在設計階段產生預存程序的中繼資料和建立協調流程執行階段叫用程序。</span><span class="sxs-lookup"><span data-stu-id="a0c38-105">However, for the approach described in the preceding link, you need to generate metadata for the stored procedure at design time and create an orchestration to invoke the procedure at run time.</span></span>  
  
 <span data-ttu-id="a0c38-106">假設您只想將一個單一值傳遞給預存程序，而不進行任何處理該值。</span><span class="sxs-lookup"><span data-stu-id="a0c38-106">Consider a scenario where you just want to pass one single value to a stored procedure without doing any processing on that value.</span></span> <span data-ttu-id="a0c38-107">在這種情況下，您不希望產生中繼資料、 建立協調流程、 部署協調流程，以及執行作業的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="a0c38-107">In such cases, you don't want the overhead of generating metadata, creating an orchestration, deploying the orchestration, and executing the operation.</span></span> <span data-ttu-id="a0c38-108">相反地，您可以設定 WCF 自訂或 WCF SQL 傳送埠來直接叫用預存程序。</span><span class="sxs-lookup"><span data-stu-id="a0c38-108">Rather, you can configure a WCF-Custom or WCF-SQL send port to directly invoke the stored procedure.</span></span> <span data-ttu-id="a0c38-109">本主題示範如何使用來執行這些工作[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="a0c38-109">This topic demonstrates how to perform these tasks using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0c38-110">本主題提供有關如何設定 Wcf-custom 傳送埠執行採用單一參數的預存程序。</span><span class="sxs-lookup"><span data-stu-id="a0c38-110">This topic provides instructions on how to configure a WCF-Custom send port for executing stored procedure that takes a single parameter.</span></span> <span data-ttu-id="a0c38-111">您可以設定 WCF SQL 連接埠來執行相同的步驟。</span><span class="sxs-lookup"><span data-stu-id="a0c38-111">You can perform the same steps by configuring a WCF-SQL port.</span></span> <span data-ttu-id="a0c38-112">如需設定 WCF SQL 連接埠的指示，請參閱[設定使用 WCF-SQL 配接器的連接埠](configure-a-port-using-the-wcf-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="a0c38-112">For instructions on configuring WCF-SQL port, see [Configure a Port using the WCF-SQL Adapter](configure-a-port-using-the-wcf-sql-adapter.md).</span></span>  
  
## <a name="invoke-stored-procedures-without-orchestration"></a><span data-ttu-id="a0c38-113">叫用預存程序沒有協調流程</span><span class="sxs-lookup"><span data-stu-id="a0c38-113">Invoke stored procedures without orchestration</span></span>  
 <span data-ttu-id="a0c38-114">若要示範如何執行與不用協調流程的單一參數的預存程序，本主題會使用 ADD_LAST_EMP_XML_INFO 預存程序。</span><span class="sxs-lookup"><span data-stu-id="a0c38-114">To demonstrate how to execute stored procedures with single parameters without an orchestration, this topic uses the ADD_LAST_EMP_XML_INFO stored procedure.</span></span> <span data-ttu-id="a0c38-115">這個程序會使用 XML 做為參數值，並將它插入至**位址**資料行**員工**資料表。</span><span class="sxs-lookup"><span data-stu-id="a0c38-115">This procedure takes an XML value as a parameter and inserts it into the **Address** column of the **Employee** table.</span></span> <span data-ttu-id="a0c38-116">您必須在您將會傳遞至預存程序的 XML 值。</span><span class="sxs-lookup"><span data-stu-id="a0c38-116">You must have the XML value that you will pass to the stored procedure.</span></span> <span data-ttu-id="a0c38-117">不過，若要執行預存程序中使用配接器，您必須傳送要求訊息符合之結構描述的程序，和值包含 XML 的**位址**欄位中，SQL server。</span><span class="sxs-lookup"><span data-stu-id="a0c38-117">However, to execute the stored procedure using the adapter, you must send a request message conforming to the schema of the procedure, and containing the XML value for the **Address** field, to the SQL Server.</span></span> <span data-ttu-id="a0c38-118">因此，您必須建立該要求訊息：</span><span class="sxs-lookup"><span data-stu-id="a0c38-118">So, you must create that request message by:</span></span>  
  
-   <span data-ttu-id="a0c38-119">使用**範本**中使用您可以建立使用訊息範本的要求訊息的傳送埠組態選項。</span><span class="sxs-lookup"><span data-stu-id="a0c38-119">Using the **Template** option in the send port configuration using which you can create a request message using a message template.</span></span>  
  
-   <span data-ttu-id="a0c38-120">將 XML 值**位址**欄位到訊息。</span><span class="sxs-lookup"><span data-stu-id="a0c38-120">Putting the XML value for the **Address** field into the message.</span></span>  
  
 <span data-ttu-id="a0c38-121">在本主題中詳細說明所有這些步驟。</span><span class="sxs-lookup"><span data-stu-id="a0c38-121">All these steps are described in detail in this topic.</span></span> <span data-ttu-id="a0c38-122">您必須執行下列工作集合：</span><span class="sxs-lookup"><span data-stu-id="a0c38-122">You must perform the following set of tasks:</span></span>  
  
1.  <span data-ttu-id="a0c38-123">建立檔案接收的埠，您將會卸除的 XML 檔案，就會插入到**位址**XML 欄位的**員工**資料表。</span><span class="sxs-lookup"><span data-stu-id="a0c38-123">Create a FILE receive port where you will drop the XML file that will be inserted into the **Address** XML field of the **Employee** table.</span></span> <span data-ttu-id="a0c38-124">假設此連接埠稱為**MessageIn**連接埠。</span><span class="sxs-lookup"><span data-stu-id="a0c38-124">Suppose this port is called **MessageIn** port.</span></span>  
  
2.  <span data-ttu-id="a0c38-125">建立 Wcf-custom 單向傳送埠取用 XML 檔案從檔案接收埠、 建構訊息使用訊息的範本，並將它傳送到 SQL Server 來執行預存程序。</span><span class="sxs-lookup"><span data-stu-id="a0c38-125">Create a WCF-Custom one-way send port that picks the XML file from the FILE receive port, constructs the message using the message template, and sends it to SQL Server to execute the stored procedure.</span></span>  
  
 <span data-ttu-id="a0c38-126">這一部分的主題提供指示設定 Wcf-custom 傳送郵件範本的通訊埠。</span><span class="sxs-lookup"><span data-stu-id="a0c38-126">This part of the topic provides instructions on configuring a WCF-Custom send port with the message template.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0c38-127">雖然本主題中的資訊會示範如何執行與單一的 XML 參數的預存程序，您可以執行要執行的任何作業，使用單一參數的任何資料類型的工作。</span><span class="sxs-lookup"><span data-stu-id="a0c38-127">Even though the information in this topic demonstrates how to execute a stored procedure with a single XML parameter, you can perform the tasks to perform any operation that takes a single parameter of any data type.</span></span> <span data-ttu-id="a0c38-128">唯一的差異會在您建立訊息的範本，針對特定作業的方式。</span><span class="sxs-lookup"><span data-stu-id="a0c38-128">The only difference will be in the way you create a message template for a specific operation.</span></span> <span data-ttu-id="a0c38-129">您可以擷取您要用於執行作業的要求訊息，藉此建立訊息範本使用協調流程與參數的值取代 BizTalk 訊息內文。</span><span class="sxs-lookup"><span data-stu-id="a0c38-129">You can create a message template by taking the request message you would use to execute the operation using an orchestration and replacing the value of the parameter with the BizTalk message body.</span></span>  
  
##  <a name="BKMK_OneWay"></a><span data-ttu-id="a0c38-130">設定 Wcf-custom 傳送埠</span><span class="sxs-lookup"><span data-stu-id="a0c38-130">Configure a WCF-Custom send port</span></span>  
 <span data-ttu-id="a0c38-131">之前建立 Wcf-custom 傳送埠時，請確定您建立檔案接收埠， **MessageIn**。</span><span class="sxs-lookup"><span data-stu-id="a0c38-131">Before creating the WCF-Custom send port, make sure you created the FILE receive port, **MessageIn**.</span></span>  
  
1.  <span data-ttu-id="a0c38-132">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="a0c38-132">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="a0c38-133">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="a0c38-133">In the console tree, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="a0c38-134">展開想要部署您的應用程式[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a0c38-134">Expand the application under which you want to deploy the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
4.  <span data-ttu-id="a0c38-135">以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後指向**靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="a0c38-135">Right-click **Send Ports**, point to **New**, and then point to **Static One-way Send Port**.</span></span>  
  
5.  <span data-ttu-id="a0c38-136">在**傳送埠屬性**對話方塊**一般**索引標籤上，輸入傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="a0c38-136">In the **Send Port Properties** dialog box, on the **General** tab, type a name for the send port.</span></span>  
  
6.  <span data-ttu-id="a0c38-137">設定連接埠接收所有檔案在卸除的訊息接收埠， **MessageIn**。</span><span class="sxs-lookup"><span data-stu-id="a0c38-137">Configure the port to receive all messages dropped at the FILE receive port, **MessageIn**.</span></span>  
  
    1.  <span data-ttu-id="a0c38-138">在**傳送埠屬性**對話方塊中的，從左窗格中，按一下**篩選**。</span><span class="sxs-lookup"><span data-stu-id="a0c38-138">In the **Send Port Properties** dialog box, from the left pane, click **Filters**.</span></span>  
  
    2.  <span data-ttu-id="a0c38-139">在右窗格中，在**屬性**資料行中，按一下方格中，然後選取**BTS。ReceivePortName**屬性。</span><span class="sxs-lookup"><span data-stu-id="a0c38-139">In the right pane, under the **Property** column, click the grid, and then select **BTS.ReceivePortName** property.</span></span>  
  
    3.  <span data-ttu-id="a0c38-140">如**運算子**欄中，選取 「**==**"。</span><span class="sxs-lookup"><span data-stu-id="a0c38-140">For the **Operator** column, select “**==**”.</span></span>  
  
    4.  <span data-ttu-id="a0c38-141">如**值**資料行中，指定的檔案名稱的接收埠， `MessageIn`。</span><span class="sxs-lookup"><span data-stu-id="a0c38-141">For the **Value** column, specify the name of the FILE receive port, `MessageIn`.</span></span>  
  
7.  <span data-ttu-id="a0c38-142">在**傳送埠屬性**對話方塊**一般**索引標籤上，從**類型**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="a0c38-142">In the **Send Port Properties** dialog box, on the **General** tab, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
8.  <span data-ttu-id="a0c38-143">在**Wcf-custom 傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a0c38-143">In the **WCF-Custom Transport Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="a0c38-144">按一下**一般** 索引標籤，然後在**位址 (URI)** 欄位中，指定 SQL Server 的連線 URI。</span><span class="sxs-lookup"><span data-stu-id="a0c38-144">Click the **General** tab, and in the **Address (URI)** field, specify the connection URI for SQL Server.</span></span> <span data-ttu-id="a0c38-145">如需連線 URI 的詳細資訊，請參閱[建立 SQL Server 連接 URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="a0c38-145">For more information about the connection URI, see [Create the SQL Server Connection URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).</span></span>  
  
    2.  <span data-ttu-id="a0c38-146">在**一般**索引標籤的**動作**文字方塊中，輸入作業的動作。</span><span class="sxs-lookup"><span data-stu-id="a0c38-146">On the **General** tab, in the **Action** text box, type the action for the operation.</span></span> <span data-ttu-id="a0c38-147">請參閱[訊息與訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)的每個作業的動作清單。</span><span class="sxs-lookup"><span data-stu-id="a0c38-147">See [Messages and message schemas](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md) for a list of actions for each operation.</span></span> <span data-ttu-id="a0c38-148">例如，叫用 ADD_LAST_EMP_XML_INFO 的動作是：</span><span class="sxs-lookup"><span data-stu-id="a0c38-148">For example, the action to invoke the ADD_LAST_EMP_XML_INFO is:</span></span>  
  
        ```  
        Procedure/dbo/ADD_LAST_EMP_XML_INFO  
        ```  
  
    3.  <span data-ttu-id="a0c38-149">按一下**繫結** 索引標籤，並從**繫結的型別**清單中，選取**sqlBinding**。</span><span class="sxs-lookup"><span data-stu-id="a0c38-149">Click the **Binding** tab, and from the **Binding Type** list, select **sqlBinding**.</span></span> <span data-ttu-id="a0c38-150">您可以指定不同的繫結屬性所公開[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a0c38-150">You can specify the different binding properties exposed by the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="a0c38-151">如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="a0c38-151">For more information about binding properties, see [Read about the BizTalk Adapter for SQL Server adapter Binding Properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span>  
  
    4.  <span data-ttu-id="a0c38-152">按一下**認證**索引標籤，然後再執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="a0c38-152">Click the **Credentials** tab, and then do one of the following:</span></span>  
  
        -   <span data-ttu-id="a0c38-153">選取**不會使用單一登入**選項，以及指定的使用者名稱和密碼來連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="a0c38-153">Select the **Do not use Single Sign-On** option, and the specify the user name and password to connect to SQL Server.</span></span> <span data-ttu-id="a0c38-154">請注意使用者名稱和密碼會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="a0c38-154">Note that the user name and password are case-sensitive.</span></span>  
  
            > [!NOTE]
            >  <span data-ttu-id="a0c38-155">如果您想要連接到 SQL Server 使用 Windows 驗證，請指定空白的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="a0c38-155">If you want to connect to SQL Server using Windows authentication, specify a blank user name and password.</span></span>  
  
        -   <span data-ttu-id="a0c38-156">選取**使用單一登入**選項，然後再指定分支機構企業單一登入 (SSO) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0c38-156">Select the **Use Single Sign-On** option, and then specify an affiliate Enterprise Single Sign-on (SSO) application.</span></span>  
  
             <span data-ttu-id="a0c38-157">如需相對於 BizTalk Server 安全性的詳細資訊，請參閱[使用 SQL 配接器和 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="a0c38-157">For more information about security with respect to BizTalk Server, see [Security with the SQL adapter and BizTalk Server](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md).</span></span>
  
    5.  <span data-ttu-id="a0c38-158">按一下**訊息** 索引標籤，然後在**輸出 WCF 訊息內文**區段中，選擇**範本**選項。</span><span class="sxs-lookup"><span data-stu-id="a0c38-158">Click the **Messages** tab, and in the **Outbound WCF message body** section, choose the **Template** option.</span></span>  
  
    6.  <span data-ttu-id="a0c38-159">在**XML**文字方塊中，指定將用來建構 WCF 訊息的範本。</span><span class="sxs-lookup"><span data-stu-id="a0c38-159">In the **XML** text box, specify the template that will be used to construct the WCF message.</span></span> <span data-ttu-id="a0c38-160">如此一來，您會建立訊息，以 WCF 為基礎的 ADD_LAST_EMP_XML_INFO 作業符合[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a0c38-160">By doing so, you create a message that conforms to the ADD_LAST_EMP_XML_INFO operation for the WCF-based [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
         <span data-ttu-id="a0c38-161">![指定輸出 WCF 訊息的範本](../../adapters-and-accelerators/adapter-sql/media/012e9ff0-b78f-4a1d-8a3a-a7b8e3850d55.gif "012e9ff0-b78f-4a1d-8a3a-a7b8e3850d55")</span><span class="sxs-lookup"><span data-stu-id="a0c38-161">![Specify template for outbound WCF message](../../adapters-and-accelerators/adapter-sql/media/012e9ff0-b78f-4a1d-8a3a-a7b8e3850d55.gif "012e9ff0-b78f-4a1d-8a3a-a7b8e3850d55")</span></span>  
  
         <span data-ttu-id="a0c38-162">ADD_LAST_EMP_XML_INFO 預存程序中，您必須指定下列範本：</span><span class="sxs-lookup"><span data-stu-id="a0c38-162">For the ADD_LAST_EMP_XML_INFO stored procedure, you must specify the following template:</span></span>  
  
        ```  
        <ADD_LAST_EMP_XML_INFO xmlns="http://schemas.microsoft.com/Sql/2008/05/Procedures/dbo">  
        <xml_info>  
        <bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="string"/>  
        </xml_info>  
        </ADD_LAST_EMP_XML_INFO>  
        ```  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="a0c38-163">訊息範本中的編碼方式必須一律為 「 字串 」，不論作業將會使用傳送埠時叫用參數的型別。</span><span class="sxs-lookup"><span data-stu-id="a0c38-163">The encoding in the message template must always be “string” irrespective of the type of the parameter for the operation that will be invoked using the send port.</span></span> <span data-ttu-id="a0c38-164">例如，ADD_LAST_EMP_XML_INFO 接受的參數類型的 XML，但訊息範本中的編碼方式為字串。</span><span class="sxs-lookup"><span data-stu-id="a0c38-164">For example, the ADD_LAST_EMP_XML_INFO takes a parameter of type XML, but the encoding in the message template is string.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="a0c38-165">您可以複製預存程序的要求訊息和 < xml_info > 標記內的值取代 BizTalk 訊息內文，以建立這個郵件範本。</span><span class="sxs-lookup"><span data-stu-id="a0c38-165">You can create this message template by copying the request message for the stored procedure and replacing the value within the <xml_info> tags with the BizTalk message body.</span></span> <span data-ttu-id="a0c38-166">您也可以產生結構描述的程序使用預存程序取得要求訊息[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，然後產生取得要求 XML 結構描述的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a0c38-166">You can get the request message for the stored procedure by generating the schema for the procedure using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], and then generating an instance of the schema to get the request XML.</span></span>  
  
    7.  <span data-ttu-id="a0c38-167">若要返回**傳送埠屬性**對話方塊中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="a0c38-167">To return to the **Send Port Properties** dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="a0c38-168">從**傳送處理常式**清單中，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="a0c38-168">From the **Send handler** list, select **BizTalkServerApplication**.</span></span>  
  
10. <span data-ttu-id="a0c38-169">從**傳送管線**清單中，選取管線以對應至**PassThruTransmit**。</span><span class="sxs-lookup"><span data-stu-id="a0c38-169">From the **Send pipeline** list, select the pipeline that corresponds to **PassThruTransmit**.</span></span>  
  
11. <span data-ttu-id="a0c38-170">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="a0c38-170">Click **OK**.</span></span>  
  
## <a name="start-the-application"></a><span data-ttu-id="a0c38-171">啟動應用程式</span><span class="sxs-lookup"><span data-stu-id="a0c38-171">Start the Application</span></span>  
 <span data-ttu-id="a0c38-172">若要啟動 BizTalk 應用程式，您可以啟動這兩個檔案接收位置和 WCF 自訂個別傳送埠。</span><span class="sxs-lookup"><span data-stu-id="a0c38-172">To start the BizTalk application, you can start both the FILE receive location and the WCF-Custom send port individually.</span></span> <span data-ttu-id="a0c38-173">您必須現在複製 XML 檔案的資料夾對應到檔案接收位置。</span><span class="sxs-lookup"><span data-stu-id="a0c38-173">You must now copy an XML file to the folder mapped to the FILE receive location.</span></span> <span data-ttu-id="a0c38-174">BizTalk 應用程式會使用檔，並在員工資料表的 [位址] 欄插入的 XML 值。</span><span class="sxs-lookup"><span data-stu-id="a0c38-174">The BizTalk application consumes the file, and the XML value is inserted in the Address column of the Employee table.</span></span> <span data-ttu-id="a0c38-175">您可以驗證，請使用 SQL Server 用戶端，並選取從 Employee 資料表的記錄。</span><span class="sxs-lookup"><span data-stu-id="a0c38-175">You can verify this by using a SQL Server client and selecting records from the Employee table.</span></span>  
  
## <a name="using-a-two-way-wcf-custom-send-port"></a><span data-ttu-id="a0c38-176">使用雙向 WCF 自訂傳送連接埠</span><span class="sxs-lookup"><span data-stu-id="a0c38-176">Using a Two-way WCF-Custom Send Port</span></span>  
 <span data-ttu-id="a0c38-177">本主題中下一節, 中的指示[如何設定 Wcf-custom 傳送埠](../../core/how-to-configure-a-wcf-custom-send-port.md)，示範如何設定單向的 WCF 自訂傳送連接埠，具有單一參數的預存程序執行而不需使用 BizTalk協調流程。</span><span class="sxs-lookup"><span data-stu-id="a0c38-177">The instructions in this topic, under the section [How to Configure a WCF-Custom Send Port](../../core/how-to-configure-a-wcf-custom-send-port.md), demonstrate how to configure a one-way WCF-Custom send port to execute a stored procedure with a single parameter without using a BizTalk orchestration.</span></span> <span data-ttu-id="a0c38-178">不過，在這種情況下，若要確認是否要執行預存程序成功您必須確認 SQL Server 資料庫中是否已經更新 Employee 資料表中的 [位址] 欄。</span><span class="sxs-lookup"><span data-stu-id="a0c38-178">However, in such a case, to verify whether the stored procedure is executed successfully you will have to verify in the SQL Server database whether the Address column in the Employee table is updated.</span></span>  
  
 <span data-ttu-id="a0c38-179">相反地，您可以建立也取得從 SQL Server 的回應，如果預存程序執行成功的雙向 Wcf-custom 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="a0c38-179">Instead, you can create a two-way WCF-Custom send port that also gets the response from SQL Server if the stored procedure is executed successfully.</span></span> <span data-ttu-id="a0c38-180">如果您要建立雙向 WCF 自訂連接埠，您必須執行一些額外的步驟。</span><span class="sxs-lookup"><span data-stu-id="a0c38-180">You must perform a few additional steps if you create a two-way WCF-Custom port.</span></span> <span data-ttu-id="a0c38-181">請注意，您仍然需要的檔案接收位置，如前述的指示中所述。</span><span class="sxs-lookup"><span data-stu-id="a0c38-181">Note that you will still need a FILE receive location, as mentioned in the preceding instructions.</span></span>  
  
1.  <span data-ttu-id="a0c38-182">例如，建立雙向 Wcf-custom 傳送埠， **ExecProcedure**。</span><span class="sxs-lookup"><span data-stu-id="a0c38-182">Create a two-way WCF-Custom send port, for example, **ExecProcedure**.</span></span> <span data-ttu-id="a0c38-183">若要設定傳送埠的步驟是類似的單向傳送埠。</span><span class="sxs-lookup"><span data-stu-id="a0c38-183">The steps to configure the send port are similar to those for the one-way send port.</span></span> <span data-ttu-id="a0c38-184">唯一的差異在於，如雙向連接埠，您也必須指定接收管線。</span><span class="sxs-lookup"><span data-stu-id="a0c38-184">The only difference is that for the two-way port you must also specify a receive pipeline.</span></span> <span data-ttu-id="a0c38-185">請確定您選取**PassThruReceive**接收管線。</span><span class="sxs-lookup"><span data-stu-id="a0c38-185">Make sure you select **PassThruReceive** for the receive pipeline.</span></span>  
  
2.  <span data-ttu-id="a0c38-186">建立 FILE 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="a0c38-186">Create a FILE send port.</span></span> <span data-ttu-id="a0c38-187">此連接埠會從卸除的回應訊息的 SQL Server 資料庫的資料夾。</span><span class="sxs-lookup"><span data-stu-id="a0c38-187">This port will drop the response message from the SQL Server database to a folder.</span></span> <span data-ttu-id="a0c38-188">使用**篩選** 索引標籤的 連接埠屬性 對話方塊中，設定 Wcf-custom 傳送埠從接收所有回應訊息的 FILE 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="a0c38-188">Using the **Filters** tab of the port properties dialog box, configure the FILE send port to receive all response messages from the WCF-Custom send port.</span></span>  
  
    1.  <span data-ttu-id="a0c38-189">在**傳送埠屬性**對話方塊中的，從左窗格中，按一下**篩選**。</span><span class="sxs-lookup"><span data-stu-id="a0c38-189">In the **Send Port Properties** dialog box, from the left pane, click **Filters**.</span></span>  
  
    2.  <span data-ttu-id="a0c38-190">在右窗格中，在**屬性**資料行中，按一下方格中，然後選取**BTS。SPName**屬性。</span><span class="sxs-lookup"><span data-stu-id="a0c38-190">In the right pane, under the **Property** column, click the grid, and then select **BTS.SPName** property.</span></span>  
  
    3.  <span data-ttu-id="a0c38-191">如**運算子**欄中，選取 「**==**"。</span><span class="sxs-lookup"><span data-stu-id="a0c38-191">For the **Operator** column, select “**==**”.</span></span>  
  
    4.  <span data-ttu-id="a0c38-192">如**值**資料行中，指定名稱的 「 WCF 自訂傳送連接埠， `ExecProcedure`。</span><span class="sxs-lookup"><span data-stu-id="a0c38-192">For the **Value** column, specify the name of the WCF-Custom send port, `ExecProcedure`.</span></span>  
  
 <span data-ttu-id="a0c38-193">啟動所有的三個連接埠。</span><span class="sxs-lookup"><span data-stu-id="a0c38-193">Start all the three ports.</span></span> <span data-ttu-id="a0c38-194">複製 XML 檔案的資料夾對應到檔案接收位置。</span><span class="sxs-lookup"><span data-stu-id="a0c38-194">Copy an XML file to the folder mapped to the FILE receive location.</span></span> <span data-ttu-id="a0c38-195">尋找對應到檔案的資料夾中的回應傳送埠。</span><span class="sxs-lookup"><span data-stu-id="a0c38-195">Look for the response in the folder mapped to the FILE send port.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0c38-196">請參閱</span><span class="sxs-lookup"><span data-stu-id="a0c38-196">See Also</span></span>  
[<span data-ttu-id="a0c38-197">使用 SQL 配接器開發 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="a0c38-197">Develop BizTalk applications using the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)