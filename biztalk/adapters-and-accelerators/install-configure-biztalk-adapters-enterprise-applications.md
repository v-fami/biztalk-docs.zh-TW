---
title: 安裝 BizTalk Adapters for Enterprise Applications |Microsoft Docs
description: 需求和安裝 JD Edwards OneWorld 中，JD Edwards EnterpriseOne，PeopleSoft Enterprise、 TIBCO Rendezvous 和 TIBCO Enterprise Message Service 中的步驟在 BizTalk Server 上
ms.custom: ''
ms.date: 10/13/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7777b7027e51460e79a6dff6a591d8faa4fe57e3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987519"
---
# <a name="install-and-configure-the-microsoft-biztalk-adapters-for-enterprise-applications"></a><span data-ttu-id="033ef-103">安裝和設定 Microsoft BizTalk Adapters for Enterprise Applications</span><span class="sxs-lookup"><span data-stu-id="033ef-103">Install and configure the Microsoft BizTalk Adapters for Enterprise Applications</span></span> 
  
 <span data-ttu-id="033ef-104">Microsoft BizTalk Adapters for Enterprise Applications 包含下列配接器：</span><span class="sxs-lookup"><span data-stu-id="033ef-104">Microsoft BizTalk Adapters for Enterprise Applications includes the following adapters:</span></span>  
  
-   <span data-ttu-id="033ef-105">Microsoft BizTalk Adapter for JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="033ef-105">Microsoft BizTalk Adapter for JD Edwards OneWorld</span></span>  
  
-   <span data-ttu-id="033ef-106">Microsoft BizTalk Adapter for JD Edwards EnterpriseOne</span><span class="sxs-lookup"><span data-stu-id="033ef-106">Microsoft BizTalk Adapter for JD Edwards EnterpriseOne</span></span>  
  
-   <span data-ttu-id="033ef-107">Microsoft BizTalk Adapter for PeopleSoft Enterprise</span><span class="sxs-lookup"><span data-stu-id="033ef-107">Microsoft BizTalk Adapter for PeopleSoft Enterprise</span></span>  
  
-   <span data-ttu-id="033ef-108">Microsoft BizTalk Adapter for TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="033ef-108">Microsoft BizTalk Adapter for TIBCO Rendezvous</span></span>  
  
-   <span data-ttu-id="033ef-109">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service</span><span class="sxs-lookup"><span data-stu-id="033ef-109">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service</span></span>  


> [!IMPORTANT]
> - <span data-ttu-id="033ef-110">進行任何組態變更之前，先備份所有的資料</span><span class="sxs-lookup"><span data-stu-id="033ef-110">Back up all data before you make any configuration changes</span></span>
> - <span data-ttu-id="033ef-111">您必須先熟悉特定企業應用程式進行任何組態變更</span><span class="sxs-lookup"><span data-stu-id="033ef-111">You must be experienced with the specific enterprise application before you make any configuration changes</span></span>
  
## <a name="supported-versions--requirements"></a><span data-ttu-id="033ef-112">支援的版本與需求</span><span class="sxs-lookup"><span data-stu-id="033ef-112">Supported versions & requirements</span></span>

||<span data-ttu-id="033ef-113">需求</span><span class="sxs-lookup"><span data-stu-id="033ef-113">Requirements</span></span>|  
|---|---|
|<span data-ttu-id="033ef-114">作業系統</span><span class="sxs-lookup"><span data-stu-id="033ef-114">Operating System</span></span>|<span data-ttu-id="033ef-115">配接器支援與 BizTalk Server 相同的作業系統：</span><span class="sxs-lookup"><span data-stu-id="033ef-115">The adapter supports the same OS as BizTalk Server:</span></span><ul><li>[<span data-ttu-id="033ef-116">BizTalk Server 2016 的需求</span><span class="sxs-lookup"><span data-stu-id="033ef-116">BizTalk Server 2016 requirements</span></span>](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)</li><li>[<span data-ttu-id="033ef-117">BizTalk Server 2013 R2 / 2013年需求</span><span class="sxs-lookup"><span data-stu-id="033ef-117">BizTalk Server 2013 R2 / 2013 requirements</span></span>](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md)</li></ul>|
|<span data-ttu-id="033ef-118">支援的企業系統</span><span class="sxs-lookup"><span data-stu-id="033ef-118">Supported enterprise system</span></span>|<span data-ttu-id="033ef-119">[支援的營運 (LOB) 和企業系統](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)列出支援的版本</span><span class="sxs-lookup"><span data-stu-id="033ef-119">[Supported Line-of-Business (LOB) and Enterprise systems](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx) lists the supported versions</span></span> |
|<span data-ttu-id="033ef-120">JD Edwards OneWorld XE</span><span class="sxs-lookup"><span data-stu-id="033ef-120">JD Edwards OneWorld XE</span></span> | <ul><li><span data-ttu-id="033ef-121">在 Windows 上的 JD Edwards 企業伺服器</span><span class="sxs-lookup"><span data-stu-id="033ef-121">JD Edwards Enterprise server on Windows</span></span></li><li><span data-ttu-id="033ef-122">在 Windows 上的 JD Edwards 部署伺服器</span><span class="sxs-lookup"><span data-stu-id="033ef-122">JD Edwards Deployment server on Windows</span></span></li></ul>|
|<span data-ttu-id="033ef-123">JD Edwards EnterpriseOne</span><span class="sxs-lookup"><span data-stu-id="033ef-123">JD Edwards EnterpriseOne</span></span> | <span data-ttu-id="033ef-124">配接器會呼叫 JD Edwards EnterpriseOne API，會使用 JDBC，資料庫都需要驅動程式。</span><span class="sxs-lookup"><span data-stu-id="033ef-124">The adapter calls the JD Edwards EnterpriseOne API that uses JDBC, which needs a driver for the database.</span></span> <span data-ttu-id="033ef-125">如果您使用 SQL 資料庫安裝 JD Edwards EnterpriseOne，則需要 MS-SQL 驅動程式。</span><span class="sxs-lookup"><span data-stu-id="033ef-125">If you install JD Edwards EnterpriseOne with a SQL database, you need MS-SQL drivers.</span></span> <span data-ttu-id="033ef-126">同樣地如果您使用 Oracle 資料庫安裝 JD Edwards EnterpriseOne，您需要 Oracle 驅動程式;或者，您使用 DB2 資料庫安裝，則需要 DB2 驅動程式。</span><span class="sxs-lookup"><span data-stu-id="033ef-126">Similarly if you installed JD Edwards EnterpriseOne with an Oracle database, you need Oracle drivers; or if you installed with a DB2 database, you need DB2 drivers.</span></span> |
|<span data-ttu-id="033ef-127">PeopleSoft Enterprise</span><span class="sxs-lookup"><span data-stu-id="033ef-127">PeopleSoft Enterprise</span></span> | <ul><li><span data-ttu-id="033ef-128">Sun Systems Java Development Kit (JDK)</span><span class="sxs-lookup"><span data-stu-id="033ef-128">Sun Systems Java Development Kit (JDK)</span></span></li><li><span data-ttu-id="033ef-129">PeopleSoft 工具版本</span><span class="sxs-lookup"><span data-stu-id="033ef-129">PeopleSoft Tools release</span></span></li><li><span data-ttu-id="033ef-130">PeopleSoft 應用程式版本</span><span class="sxs-lookup"><span data-stu-id="033ef-130">PeopleSoft Applications release</span></span></li><li><span data-ttu-id="033ef-131">此配接器需要修改 PeopleSoft 應用程式。</span><span class="sxs-lookup"><span data-stu-id="033ef-131">This adapter requires a modification to the PeopleSoft application.</span></span> <span data-ttu-id="033ef-132">若要使用的元件介面，請將自訂元件介面 GET_CI_INFO 上傳至 PeopleSoft。</span><span class="sxs-lookup"><span data-stu-id="033ef-132">To use component interfaces, upload a custom component interface, GET_CI_INFO, into PeopleSoft.</span></span> <span data-ttu-id="033ef-133">GET_CI_INFO.pc 位於 Program Files\Common Files\Microsoft BizTalk Adapters Enterprise Applications\PeopleSoft Enterprise(r) \Config\ 的。</span><span class="sxs-lookup"><span data-stu-id="033ef-133">GET_CI_INFO.pc is in Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\PeopleSoft Enterprise(r)\Config\.</span></span></li></ul>|
|<span data-ttu-id="033ef-134">TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="033ef-134">TIBCO Rendezvous</span></span> | <ul><li><span data-ttu-id="033ef-135">BizTalk Adapter for TIBCO Rendezvous 執行所在的電腦上必須安裝 TIBCO Rendezvous 執行階段元件</span><span class="sxs-lookup"><span data-stu-id="033ef-135">The TIBCO Rendezvous run-time component must be installed on the computer where BizTalk Adapter for TIBCO Rendezvous is running</span></span></li><li><span data-ttu-id="033ef-136">BizTalk Adapter for TIBCO Rendezvous 執行所在電腦上，必須設定 TIBCO Rendezvous 授權。</span><span class="sxs-lookup"><span data-stu-id="033ef-136">The TIBCO Rendezvous license must be configured on the computer where BizTalk Adapter for TIBCO Rendezvous is running.</span></span></li><li><span data-ttu-id="033ef-137">配接器必須能夠看到 TIBCO Rendezvous 二進位檔目錄：在環境變數 PATH 值中，或在 BizTalk Server 中的每個 Rendezvous 連接埠上指定。</span><span class="sxs-lookup"><span data-stu-id="033ef-137">The TIBCO Rendezvous binaries directory must be visible to the adapter: either in the Environment variables PATH value, or specified on each Rendezvous port in BizTalk Server.</span></span> <span data-ttu-id="033ef-138">這對於 Rendezvous 組件尋找其程式庫和可執行檔是必要的。</span><span class="sxs-lookup"><span data-stu-id="033ef-138">This is necessary for the Rendezvous assembly to find its libraries and executable.</span></span></li></ul>|
|<span data-ttu-id="033ef-139">TIBCO Enterprise Message Service</span><span class="sxs-lookup"><span data-stu-id="033ef-139">TIBCO Enterprise Message Service</span></span> | <span data-ttu-id="033ef-140">Enterprise Message Service (EMS) 版本 5.x 及更新版本包含 用戶端 SDK （使用 TIBCO EMS C# API）。</span><span class="sxs-lookup"><span data-stu-id="033ef-140">Enterprise Message Service (EMS) version 5.x and above includes a client SDK (using the TIBCO EMS C# API).</span></span> <span data-ttu-id="033ef-141">BizTalk Adapter for TIBCO EMS 會使用此與伺服器通訊。</span><span class="sxs-lookup"><span data-stu-id="033ef-141">BizTalk Adapter for TIBCO EMS uses this to communicate with the server.</span></span> |


## <a name="jd-edwards-oneworld-xe"></a><span data-ttu-id="033ef-142">JD Edwards OneWorld XE</span><span class="sxs-lookup"><span data-stu-id="033ef-142">JD Edwards OneWorld XE</span></span>

<span data-ttu-id="033ef-143">此章節包含使用 Microsoft BizTalk Adapter for JD Edwards OneWorld XE 與 BizTalk Server 的重要資訊。</span><span class="sxs-lookup"><span data-stu-id="033ef-143">This sections includes key information on using the Microsoft BizTalk Adapter for JD Edwards OneWorld XE with BizTalk Server.</span></span>
  
### <a name="create-the-jar-files"></a><span data-ttu-id="033ef-144">建立的 JAR 檔案</span><span class="sxs-lookup"><span data-stu-id="033ef-144">Create the JAR Files</span></span>
 <span data-ttu-id="033ef-145">本節說明 JD Edwards OneWorld 搭配 Microsoft BizTalk Adapter for JD Edwards OneWorld 使用的需求。</span><span class="sxs-lookup"><span data-stu-id="033ef-145">This section describes the requirements for JD Edwards OneWorld to work with Microsoft BizTalk Adapter for JD Edwards OneWorld.</span></span>  
  
#### <a name="jar-files-and-the-classpath"></a><span data-ttu-id="033ef-146">JAR 檔案和 CLASSPATH</span><span class="sxs-lookup"><span data-stu-id="033ef-146">JAR Files and the CLASSPATH</span></span>  
 <span data-ttu-id="033ef-147">JD Edwards OneWorld JAR 檔案必須是介面卡可用。</span><span class="sxs-lookup"><span data-stu-id="033ef-147">JD Edwards OneWorld JAR files must be available to the adapter.</span></span> <span data-ttu-id="033ef-148">比方說，若要連接到 B7.3.3.3 版，會需要下列 jar 檔案。</span><span class="sxs-lookup"><span data-stu-id="033ef-148">For instance, to connect to B7.3.3.3 Version, the following jar files are required.</span></span> <span data-ttu-id="033ef-149">根據您所連接的伺服器，可能會變更的 jar 檔案清單：</span><span class="sxs-lookup"><span data-stu-id="033ef-149">Depending on the server you connect, the jar file list may change:</span></span>
  
- <span data-ttu-id="033ef-150">Connector.jar</span><span class="sxs-lookup"><span data-stu-id="033ef-150">Connector.jar</span></span>    
- <span data-ttu-id="033ef-151">Kernel.jar</span><span class="sxs-lookup"><span data-stu-id="033ef-151">Kernel.jar</span></span>  
  
  <span data-ttu-id="033ef-152">這些檔案位於 JD Edwards OneWorld 執行所在的電腦上，位置如下：</span><span class="sxs-lookup"><span data-stu-id="033ef-152">These files are located on a computer running JD Edwards OneWorld, at the following locations:</span></span>  
  
- <span data-ttu-id="033ef-153">JD Edwards OneWorld XE_install_Directory\System\classes\Connector.jar</span><span class="sxs-lookup"><span data-stu-id="033ef-153">JD Edwards OneWorld XE_install_Directory\System\classes\Connector.jar</span></span>    
- <span data-ttu-id="033ef-154">JD Edwards OneWorld XE_install_Directory\System\classes\Kernel.jar</span><span class="sxs-lookup"><span data-stu-id="033ef-154">JD Edwards OneWorld XE_install_Directory\System\classes\Kernel.jar</span></span>  
  
  <span data-ttu-id="033ef-155">您可以將這些檔案複製到任何位置；不過，您必須在 CLASSPATH 中指定 JAR 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="033ef-155">You can copy these files to any location; however, you must specify the location of the JAR files in the CLASSPATH.</span></span> <span data-ttu-id="033ef-156">CLASSPATH 必須包含 JAR 檔案的完整檔案路徑和名稱 (以分號分隔)。</span><span class="sxs-lookup"><span data-stu-id="033ef-156">The CLASSPATH must include both the full path of the file and the name of the JAR file (separated by a semicolon).</span></span>  
  
  <span data-ttu-id="033ef-157">BizTalk Adapter for JD Edwards OneWorld 提供與 JD Edwards OneWorld 搭配使用 JDEJAccess JAR 檔案。</span><span class="sxs-lookup"><span data-stu-id="033ef-157">BizTalk Adapter for JD Edwards OneWorld provides the JDEJAccess JAR file for use with JD Edwards OneWorld.</span></span> <span data-ttu-id="033ef-158">根據預設，從參考 JDEJAccess.jar 檔案*Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise applications\j.d.edwards。Edwards OneWorld(r)\classes\JDEJAccess.jar*.</span><span class="sxs-lookup"><span data-stu-id="033ef-158">By default, the JDEJAccess.jar file is referenced from *Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\J.D. Edwards OneWorld(r)\classes\JDEJAccess.jar*.</span></span> 
  
> [!NOTE]
>  <span data-ttu-id="033ef-159">您必須確認已註冊 jdeinterop.ini 檔案，才能使用 BizTalk Adapter for JD Edwards OneWorld。</span><span class="sxs-lookup"><span data-stu-id="033ef-159">You must verify the registration of the jdeinterop.ini file before you can use BizTalk Adapter for JD Edwards OneWorld.</span></span> <span data-ttu-id="033ef-160">請確定您包含在此檔案的路徑**JDE Transport Property**頁面上，當您在 BizTalk Server 中建立的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="033ef-160">Make sure that you include a path to this file in the **JDE Transport Property** page when you create the send port in BizTalk Server.</span></span> <span data-ttu-id="033ef-161">如需完整的說明，請參閱 「 自訂 jdeinterop.ini 檔案。 」</span><span class="sxs-lookup"><span data-stu-id="033ef-161">For a complete explanation, see "Customize the jdeinterop.ini File."</span></span>  
  
#### <a name="create-the-btslibinteropjar-file"></a><span data-ttu-id="033ef-162">建立 BTSLIBinterop.jar 檔案</span><span class="sxs-lookup"><span data-stu-id="033ef-162">Create the BTSLIBinterop.jar File</span></span>  
<span data-ttu-id="033ef-163">建立檔案，並確認 配接器可以存取它。</span><span class="sxs-lookup"><span data-stu-id="033ef-163">Create the file, and confirm it can be accessed by the adapter.</span></span> <span data-ttu-id="033ef-164">您可以使用下列範例做為指南：</span><span class="sxs-lookup"><span data-stu-id="033ef-164">Use the following sample as a guide:</span></span>  
  
1.  <span data-ttu-id="033ef-165">建立包含下列程式碼的 BTSLIB.cmd 檔案：</span><span class="sxs-lookup"><span data-stu-id="033ef-165">Create the BTSLIB.cmd file that contains the following code:</span></span>  
  
    ```  
    define library BTSLIB  
    login  
    library BTSLIB  
    interface JDEAdapter  
    import B5500900  
    build  
    logout  
    ```  
  
2.  <span data-ttu-id="033ef-166">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="033ef-166">Run the following command:</span></span>  
  
    ```  
    GenJava  /cmd  .\BTSLIB.cmd  
    ```  
  
### <a name="verify-your-setup"></a><span data-ttu-id="033ef-167">請確認您的設定</span><span class="sxs-lookup"><span data-stu-id="033ef-167">Verify your setup</span></span>  
  
1.  <span data-ttu-id="033ef-168">使用支援的版本，包括 service pack 號碼 ([支援的營運 (LOB) 和企業系統](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx))。</span><span class="sxs-lookup"><span data-stu-id="033ef-168">Use a supported version, including service pack number ([Supported Line-of-Business (LOB) and Enterprise systems](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)).</span></span> <span data-ttu-id="033ef-169">Service Pack (ESU 和 ASU) 更新系統二進位檔。</span><span class="sxs-lookup"><span data-stu-id="033ef-169">Service packs (ESUs and ASUs) update the system binaries.</span></span> <span data-ttu-id="033ef-170">必要的 Service Pack 提供匯入的 ASU/ESU 功能表選項。</span><span class="sxs-lookup"><span data-stu-id="033ef-170">The prerequisite service pack provides the ASU/ESU menu choice for import.</span></span>  
  
2.  <span data-ttu-id="033ef-171">設定 jdeinterop.ini 檔案以進行記錄，使用正確的磁碟機，如果不同於 c 磁碟機。例如，如果 TEMP 目錄空間不足，可能會失敗 JD Edwards OneWorld 更新。</span><span class="sxs-lookup"><span data-stu-id="033ef-171">Configure the jdeinterop.ini file to use the correct drive for logging, if it differs from drive C. For example, your JD Edwards OneWorld update can fail if the TEMP directory is out of space.</span></span>  
  
3.  <span data-ttu-id="033ef-172">判斷是否必須針對 JD Edwards OneWorld 欄位的左/右邊框距離加入組態檔。</span><span class="sxs-lookup"><span data-stu-id="033ef-172">Determine whether you must add a configuration file for the left/right padding of the JD Edwards OneWorld fields.</span></span>  
  
4.  <span data-ttu-id="033ef-173">確認您的 JAVA_HOME 環境變數指向 Java Development Kit (JDK) 安裝，以便從電腦上的任何程式啟用 javac 和 java 命令。</span><span class="sxs-lookup"><span data-stu-id="033ef-173">Verify that your JAVA_HOME environment variable is pointing to your Java Development Kit (JDK) installation to enable the javac and java commands from any program on the computer.</span></span>  
  
5.  <span data-ttu-id="033ef-174">確認設定 CLASSPATH 環境變數。</span><span class="sxs-lookup"><span data-stu-id="033ef-174">Verify that the CLASSPATH environment variable is set.</span></span> <span data-ttu-id="033ef-175">這可讓 BizTalk Adapter for JD Edwards OneWorld 可以找到 Kernel.jar 和 Connect.jar 檔案。</span><span class="sxs-lookup"><span data-stu-id="033ef-175">This enables BizTalk Adapter for JD Edwards OneWorld to locate the Kernel.jar and Connect.jar files.</span></span>  
  
    <span data-ttu-id="033ef-176">JAR 檔案的路徑會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="033ef-176">The path of the JAR files is case sensitive.</span></span>  
  
6.  <span data-ttu-id="033ef-177">輸入下列區分大小寫的命令來測試環境。</span><span class="sxs-lookup"><span data-stu-id="033ef-177">Test the environment by typing the following command, which is case sensitive.</span></span>  
  
    ```  
    javap -s -p com.microsoft.jde.JDEJAccess  
    ```  
  
7.  <span data-ttu-id="033ef-178">您提供的命令 javap 是 Java 類別檔案解譯器：</span><span class="sxs-lookup"><span data-stu-id="033ef-178">The command you give, javap, is the Java Class File Disassembler:</span></span>  
  
    ```  
    http://java.sun.com/j2se/1.3/docs/tooldocs/solaris/javap.html  
    ```  
  
8.  <span data-ttu-id="033ef-179">`javap`命令解譯類別檔案。</span><span class="sxs-lookup"><span data-stu-id="033ef-179">The `javap` command disassembles a class file.</span></span> <span data-ttu-id="033ef-180">其輸出取決於所使用的選項。</span><span class="sxs-lookup"><span data-stu-id="033ef-180">Its output depends on the options used.</span></span> <span data-ttu-id="033ef-181">如果未不使用任何選項，javap 會列印的封裝、 受保護，和公用欄位和方法傳遞給它的類別。</span><span class="sxs-lookup"><span data-stu-id="033ef-181">If no options are used, javap prints out the package, protected, and public fields and methods of the classes passed to it.</span></span> <span data-ttu-id="033ef-182">javap 會列印其輸出至 stdout。</span><span class="sxs-lookup"><span data-stu-id="033ef-182">javap prints its output to stdout.</span></span>  
  
     <span data-ttu-id="033ef-183">如果沒有任何錯誤，所有 Java 檔案和其相依性會在 CLASSPATH 中。</span><span class="sxs-lookup"><span data-stu-id="033ef-183">If there are no errors, all the Java files and their dependencies are in the CLASSPATH.</span></span>  
  
9. <span data-ttu-id="033ef-184">設定 DNS 解析，藉由設定本機主機檔案 (*C:\WINNT\system32\drivers\etc\hosts*)，使用 JD Edwards OneWorld 系統的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="033ef-184">Set up the DNS resolution by configuring the local host file (*C:\WINNT\system32\drivers\etc\hosts*), with the server name of the JD Edwards OneWorld system.</span></span>  
  
### <a name="create-and-install-the-custom-package"></a><span data-ttu-id="033ef-185">建立並安裝自訂封裝</span><span class="sxs-lookup"><span data-stu-id="033ef-185">Create and install the custom package</span></span>  
<span data-ttu-id="033ef-186">安裝 BTSREL 自訂封裝，才能使用 BizTalk Adapter for JD Edwards OneWorld。</span><span class="sxs-lookup"><span data-stu-id="033ef-186">Install the BTSREL custom package to use BizTalk Adapter for JD Edwards OneWorld.</span></span> <span data-ttu-id="033ef-187">本章節描述：</span><span class="sxs-lookup"><span data-stu-id="033ef-187">This section describes:</span></span>  
  
-   <span data-ttu-id="033ef-188">JD Edwards OneWorld 自訂封裝建立處理程序</span><span class="sxs-lookup"><span data-stu-id="033ef-188">The JD Edwards OneWorld custom package-creation process</span></span>  
-   <span data-ttu-id="033ef-189">如何建立和安裝 BTSREL</span><span class="sxs-lookup"><span data-stu-id="033ef-189">How to create and install BTSREL</span></span>  
-   <span data-ttu-id="033ef-190">JD Edwards OneWorld 中建立的 BTSREL 物件</span><span class="sxs-lookup"><span data-stu-id="033ef-190">The BTSREL objects created in JD Edwards OneWorld</span></span>
  
> [!NOTE]
>  <span data-ttu-id="033ef-191">BTSREL.exe 是自訂封裝 (以 JD Edwards OneWorld 術語表示則為自動軟體更新或 ASU)。</span><span class="sxs-lookup"><span data-stu-id="033ef-191">BTSREL.exe is a custom package (an automated software update, or ASU, in JD Edwards OneWorld terminology).</span></span> <span data-ttu-id="033ef-192">其中包含可擷取中繼資料的商務功能。</span><span class="sxs-lookup"><span data-stu-id="033ef-192">It contains business functions to extract metadata.</span></span> <span data-ttu-id="033ef-193">您應該針對特定的 JD Edwards OneWorld 組態和版本來建立自訂封裝。</span><span class="sxs-lookup"><span data-stu-id="033ef-193">A custom package should be created for a specific configuration and version of JD Edwards OneWorld.</span></span>  
  
#### <a name="define-a-custom-package"></a><span data-ttu-id="033ef-194">定義自訂套件</span><span class="sxs-lookup"><span data-stu-id="033ef-194">Define a custom package</span></span>  
 <span data-ttu-id="033ef-195">自訂封裝是發行後交付項目，針對特定目的提供軟體變更，例如法規變更或增強功能。</span><span class="sxs-lookup"><span data-stu-id="033ef-195">A custom package is a post-release deliverable that provides software changes for specific purposes, such as regulatory changes or enhancements.</span></span> <span data-ttu-id="033ef-196">這些自訂封裝會針對特定功能加以建立。</span><span class="sxs-lookup"><span data-stu-id="033ef-196">These custom packages are created for specific functionality.</span></span> <span data-ttu-id="033ef-197">例如，為了擷取中繼資料而建立 BTSREL。</span><span class="sxs-lookup"><span data-stu-id="033ef-197">For example, BTSREL is created to extract metadata.</span></span> <span data-ttu-id="033ef-198">安裝 BTSREL 自訂封裝之後，該封裝會更新 JD Edwards OneWorld 環境中所選取的模組。</span><span class="sxs-lookup"><span data-stu-id="033ef-198">When the BTSREL custom package is installed, it updates selected modules in the JD Edwards OneWorld environment.</span></span> <span data-ttu-id="033ef-199">若要更新，您必須將 BTSREL 物件併入適當的 JD Edwards OneWorld 環境中。</span><span class="sxs-lookup"><span data-stu-id="033ef-199">To update, BTSREL objects must be merged into the appropriate JD Edwards OneWorld environment.</span></span> <span data-ttu-id="033ef-200">如需 BTSREL 所更新之模組的詳細清單，請參閱模組清單。</span><span class="sxs-lookup"><span data-stu-id="033ef-200">For a detailed list of modules updated by BTSREL, see the list of modules.</span></span>  
  
#### <a name="install-the-btsrel-custom-package"></a><span data-ttu-id="033ef-201">安裝 BTSREL 自訂封裝</span><span class="sxs-lookup"><span data-stu-id="033ef-201">Install the BTSREL custom package</span></span>   
<span data-ttu-id="033ef-202">下載[BTSREL](https://www.microsoft.com/download/details.aspx?id=56113)。</span><span class="sxs-lookup"><span data-stu-id="033ef-202">Download [BTSREL](https://www.microsoft.com/download/details.aspx?id=56113).</span></span> <span data-ttu-id="033ef-203">將它安裝在部署伺服器上，然後再將它設為部署到企業伺服器。</span><span class="sxs-lookup"><span data-stu-id="033ef-203">Install it on the deployment server, and then deploy it to the enterprise server.</span></span>  
  
 <span data-ttu-id="033ef-204">現有的 BTSREL.exe 封裝可直接用於 B7333 版本。</span><span class="sxs-lookup"><span data-stu-id="033ef-204">The existing BTSREL.exe package directly works with the B7333 version.</span></span> <span data-ttu-id="033ef-205">針對封裝用於 B7334 版本，然後：</span><span class="sxs-lookup"><span data-stu-id="033ef-205">For the package to work with the B7334 version, then:</span></span>  
  
1. <span data-ttu-id="033ef-206">下載並將 BTSREL.exe 的內容解壓縮到工作資料夾。</span><span class="sxs-lookup"><span data-stu-id="033ef-206">Download and extract the contents of BTSREL.exe to your working folder.</span></span>  
  
2. <span data-ttu-id="033ef-207">修改**ReleaseLevelRequired**並**發行**B7334 Deployment.Inf 檔案中的值。</span><span class="sxs-lookup"><span data-stu-id="033ef-207">Modify both the **ReleaseLevelRequired** and the **Release** values to B7334 in the Deployment.Inf file.</span></span>  
  
3. <span data-ttu-id="033ef-208">執行安裝程式。</span><span class="sxs-lookup"><span data-stu-id="033ef-208">Run the Setup.</span></span>  
  
   <span data-ttu-id="033ef-209">若要安裝 BTSREL，需要下列條件：</span><span class="sxs-lookup"><span data-stu-id="033ef-209">To install BTSREL, the following are required:</span></span>  
  
-   <span data-ttu-id="033ef-210">部署伺服器安裝</span><span class="sxs-lookup"><span data-stu-id="033ef-210">Deployment server installation</span></span>    
-   <span data-ttu-id="033ef-211">Workbench 安裝</span><span class="sxs-lookup"><span data-stu-id="033ef-211">Installation Workbench</span></span>  
  
#### <a name="install-btsrel-on-the-deployment-server"></a><span data-ttu-id="033ef-212">在 部署伺服器上安裝 BTSREL</span><span class="sxs-lookup"><span data-stu-id="033ef-212">Install BTSREL on the deployment server</span></span>  
 <span data-ttu-id="033ef-213">自訂封裝僅適用於 Windows 的作業系統，並使用與部署伺服器。</span><span class="sxs-lookup"><span data-stu-id="033ef-213">The custom package only works on a Windows operating system, and is used with the deployment server.</span></span> <span data-ttu-id="033ef-214">它必須建置在部署伺服器，並接著部署至企業伺服器。</span><span class="sxs-lookup"><span data-stu-id="033ef-214">It must be built on the deployment server, and then deployed to the enterprise server.</span></span> <span data-ttu-id="033ef-215">企業伺服器通常是實際執行伺服器，可以位於 Windows 或 UNIX 作業系統上。</span><span class="sxs-lookup"><span data-stu-id="033ef-215">The enterprise server is usually a production server, and can be on either a Windows or UNIX operating system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="033ef-216">當將 ASU 套用至 JD Edwards OneWorld 部署伺服器，請確認您是在**更新**模式。</span><span class="sxs-lookup"><span data-stu-id="033ef-216">When applying the ASU to the JD Edwards OneWorld deployment server, verify that you are in **Update** mode.</span></span> <span data-ttu-id="033ef-217">**證明**模式可確認 ASU 中沒有任何錯誤而**更新**模式 」 被指定在套用 ASU 時。</span><span class="sxs-lookup"><span data-stu-id="033ef-217">The **Proof** mode verifies that there are no bugs in the ASU, whereas **Update** mode is designated for when you apply the ASU.</span></span>  
  
1.  <span data-ttu-id="033ef-218">登入部署伺服器，以使用者身分**JDE**。</span><span class="sxs-lookup"><span data-stu-id="033ef-218">Sign in to the deployment server as user **JDE**.</span></span>  
  
2.  <span data-ttu-id="033ef-219">在部署伺服器 (根目錄) 的 /B7 資料夾中，建立新的資料夾 BTSREL。</span><span class="sxs-lookup"><span data-stu-id="033ef-219">Create a new folder, named BTSREL, on the Deployment Server (root) /B7 folder.</span></span>  
  
3.  <span data-ttu-id="033ef-220">將 BTSREL.exe 複製到新建立的 BTSREL 資料夾。</span><span class="sxs-lookup"><span data-stu-id="033ef-220">Copy BTSREL.exe to the newly created BTSREL folder.</span></span>  
  
4.  <span data-ttu-id="033ef-221">從 .../B7/BTSREL 資料夾執行 BTSREL.exe。</span><span class="sxs-lookup"><span data-stu-id="033ef-221">Run BTSREL.exe from the.../B7/BTSREL folder.</span></span> <span data-ttu-id="033ef-222">安裝管理員會自動啟動。</span><span class="sxs-lookup"><span data-stu-id="033ef-222">The installation manager automatically starts.</span></span>  
  
5.  <span data-ttu-id="033ef-223">在 [設定] 視窗中，選取**下一步**，然後選取**完成**。</span><span class="sxs-lookup"><span data-stu-id="033ef-223">In the setup window, select **Next**, and then select **Finish**.</span></span> <span data-ttu-id="033ef-224">如果已成功安裝，則會顯示一則訊息。</span><span class="sxs-lookup"><span data-stu-id="033ef-224">A message displays if the installation is successful.</span></span>  
  
6.  <span data-ttu-id="033ef-225">登入 JDEPLAN 環境做**JDE** JD Edwards OneWorld 部署伺服器上的使用者。</span><span class="sxs-lookup"><span data-stu-id="033ef-225">Sign to the JDEPLAN environment as the**JDE** user on the JD Edwards OneWorld deployment server.</span></span>  
  
    1.  <span data-ttu-id="033ef-226">如果系統上未安裝含有 SAR # 4533357 的電子軟體更新 (ESU)，選取**Software Updates**從**系統安裝工具**功能表 (GH9612)。</span><span class="sxs-lookup"><span data-stu-id="033ef-226">If the electronic software update (ESU) that includes SAR #4533357 is not installed on the system, select **Software Updates** from the **System Installation Tools** menu (GH9612).</span></span>  
  
    2.  <span data-ttu-id="033ef-227">選項 1 中，輸入 02**處理選項**面板。</span><span class="sxs-lookup"><span data-stu-id="033ef-227">Enter 02 for option 1 in the **Processing Options** panel.</span></span>  
  
    3.  <span data-ttu-id="033ef-228">如果已安裝含有 SAR # 4533357 ESU 系統上，選取**應用程式的軟體更新**從**系統安裝工具**功能表 (GH9612)。</span><span class="sxs-lookup"><span data-stu-id="033ef-228">If the ESU that includes SAR #4533357 has been installed on the system, select **Application Software Update** from the **System Installation Tools** menu (GH9612).</span></span>  
  
#### <a name="install-btsrel-on-the-jd-edwards-oneworld-workbench"></a><span data-ttu-id="033ef-229">JD Edwards OneWorld WorkBench 上安裝 BTSREL</span><span class="sxs-lookup"><span data-stu-id="033ef-229">Install BTSREL on the JD Edwards OneWorld WorkBench</span></span>  
   
1.  <span data-ttu-id="033ef-230">在 [**使用應用程式更新**畫面中，按兩下 BTSREL 更新，並選取**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="033ef-230">On the **Work with Application Update** screen, double-click the BTSREL update, and then select **Next**.</span></span>  
  
2.  <span data-ttu-id="033ef-231">按兩下您想要安裝、 更新的環境，然後選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="033ef-231">Double-click the environments where you want the update installed, and then select **Next**.</span></span>  
  
    1.  <span data-ttu-id="033ef-232">請檢查**Unattended Workbench**如果您想要在自動安裝模式中執行的軟體更新。</span><span class="sxs-lookup"><span data-stu-id="033ef-232">Check **Unattended Workbench** if you want the software update to run in unattended mode.</span></span>  
  
    2.  <span data-ttu-id="033ef-233">選取 **備份**如果您想備份規格 （如此才能還原原始規格）。</span><span class="sxs-lookup"><span data-stu-id="033ef-233">Select **Backup** if you want the backup of the specifications (so that the original specifications can be restored).</span></span>  
  
3.  <span data-ttu-id="033ef-234">在上**處理安裝計劃**畫面上，選取您要安裝的更新的計劃，然後**選取**。</span><span class="sxs-lookup"><span data-stu-id="033ef-234">On the **Work with Installation Plan** screen, select the plan for the update you are installing, and then **Select**.</span></span>  
  
4.  <span data-ttu-id="033ef-235">安裝完成之後，請查看自動產生的 PDF 是否有任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="033ef-235">See the automatically generated PDFs for errors after the installation is finished.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="033ef-236">如果發生錯誤，請參閱「JD Edwards OneWorld 軟體更新指南」中的疑難排解秘訣，或直接連絡 JD Edwards OneWorld。</span><span class="sxs-lookup"><span data-stu-id="033ef-236">If errors occur, look in the JD Edwards OneWorld Software Update Guide for troubleshooting tips, or contact JD Edwards OneWorld directly.</span></span>  
  
5.  <span data-ttu-id="033ef-237">手動註冊商務功能程式庫，使用包含在 「 手動註冊商務功能程式庫 」 這一節的步驟。</span><span class="sxs-lookup"><span data-stu-id="033ef-237">Manually register the business function library using the steps included in "Manually register the business function library" in this section.</span></span>  
  
#### <a name="uninstall-the-custom-package"></a><span data-ttu-id="033ef-238">解除安裝自訂封裝</span><span class="sxs-lookup"><span data-stu-id="033ef-238">Uninstall the custom package</span></span>  
 <span data-ttu-id="033ef-239">解除安裝自訂封裝沒有任何需求。</span><span class="sxs-lookup"><span data-stu-id="033ef-239">There is no requirement to uninstall the custom package.</span></span> <span data-ttu-id="033ef-240">不過，如果您想要清理系統，您可以使用不同的方式來解除安裝。</span><span class="sxs-lookup"><span data-stu-id="033ef-240">However, if you want to clean the system, you can uninstall in different ways.</span></span> <span data-ttu-id="033ef-241">解除安裝之後，重建套件使用下列方法之一：</span><span class="sxs-lookup"><span data-stu-id="033ef-241">After you uninstall, rebuild the package using one of the following methods:</span></span>  
  
- <span data-ttu-id="033ef-242">使用 JD Edwards OneWorld 部署伺服器 Gh8612-P96470，在**資料列**功能表上，選取**更新**，然後選取**解除安裝**。</span><span class="sxs-lookup"><span data-stu-id="033ef-242">Use the JD Edwards OneWorld Deployment Server, Gh8612—P96470, on the **ROW** menu, select **Update**, and then select **Uninstall**.</span></span>    
- <span data-ttu-id="033ef-243">核取並刪除用戶端電腦上的所有自訂物件 (BTSREL)。</span><span class="sxs-lookup"><span data-stu-id="033ef-243">Check out all the custom objects (BTSREL) to a client computer and delete them.</span></span>    
- <span data-ttu-id="033ef-244">套用先前的資料庫快照集。</span><span class="sxs-lookup"><span data-stu-id="033ef-244">Apply a previous snapshot of database.</span></span>  
  
  <span data-ttu-id="033ef-245">在清除期間，確認 JD Edwards OneWorld 的其他物件是否有任何其他修改。</span><span class="sxs-lookup"><span data-stu-id="033ef-245">During the clean-up, verify any other modifications to the other objects of JD Edwards OneWorld.</span></span>  
  
#### <a name="manually-register-the-business-function-library"></a><span data-ttu-id="033ef-246">手動註冊商務功能程式庫</span><span class="sxs-lookup"><span data-stu-id="033ef-246">Manually register the business function library</span></span>  
 <span data-ttu-id="033ef-247">由於 JD Edwards OneWorld 產品封裝程序的限制，您必須向 JD Edwards OneWorld 手動註冊 BizTalk Adapter for JD Edwards OneWorld 的自訂商務功能程式庫 DLL。</span><span class="sxs-lookup"><span data-stu-id="033ef-247">Because of a limitation of the JD Edwards OneWorld product packaging process, the custom Business Function Library DLL for BizTalk Adapter for JD Edwards OneWorld must be manually registered with JD Edwards OneWorld.</span></span> <span data-ttu-id="033ef-248">此程序是由下列步驟所組成。</span><span class="sxs-lookup"><span data-stu-id="033ef-248">This process consists of the following steps.</span></span>
  
##### <a name="step-1-create-the-custom-business-function-library"></a><span data-ttu-id="033ef-249">步驟 1： 建立自訂的商務功能程式庫</span><span class="sxs-lookup"><span data-stu-id="033ef-249">Step 1: Create the custom business function library</span></span>  
 <span data-ttu-id="033ef-250">使用 JD Edwards OneWorld Object Management Workbench (OMW) 建立自訂商務功能程式庫。</span><span class="sxs-lookup"><span data-stu-id="033ef-250">Using JD Edwards OneWorld Object Management Workbench (OMW), create the Custom Business Function Library.</span></span> <span data-ttu-id="033ef-251">下列程序必須在初始設定、 執行，並套用至所有平台。</span><span class="sxs-lookup"><span data-stu-id="033ef-251">The following procedure must be performed on initial setup, and applies to all platforms.</span></span>  
  
1.  <span data-ttu-id="033ef-252">啟動 Object Management Workbench (快速路徑:"OMW"或功能表選項： GH902 物件： P98220)。</span><span class="sxs-lookup"><span data-stu-id="033ef-252">Start the Object Management Workbench (fast path: "OMW" or menu selection: GH902 Object: P98220).</span></span>  
  
2.  <span data-ttu-id="033ef-253">選取 **新增**，然後選取的選項**商務功能程式庫**。</span><span class="sxs-lookup"><span data-stu-id="033ef-253">Select **Add**, and select the option for **Business Function Library**.</span></span>  
  
3.  <span data-ttu-id="033ef-254">輸入新商務功能程式庫物件的下列資訊：</span><span class="sxs-lookup"><span data-stu-id="033ef-254">Enter the following information for the New Business Function Library Object:</span></span>  
  
    -   <span data-ttu-id="033ef-255">**名稱：** ACBLIB</span><span class="sxs-lookup"><span data-stu-id="033ef-255">**Name:** ACBLIB</span></span>    
    -   <span data-ttu-id="033ef-256">**描述：** Microsoft DLL</span><span class="sxs-lookup"><span data-stu-id="033ef-256">**Description:** Microsoft DLL</span></span>    
    -   <span data-ttu-id="033ef-257">**產品代碼：** 55</span><span class="sxs-lookup"><span data-stu-id="033ef-257">**Product Code:** 55</span></span>    
    -   <span data-ttu-id="033ef-258">**產品系統程式碼：** 55</span><span class="sxs-lookup"><span data-stu-id="033ef-258">**Product System Code:** 55</span></span>  
  
4.  <span data-ttu-id="033ef-259">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="033ef-259">Select **OK**.</span></span>  
  
##### <a name="step-2-rebuild-libraries-from-the-deployment-server"></a><span data-ttu-id="033ef-260">步驟 2： 重建程式庫，從部署伺服器</span><span class="sxs-lookup"><span data-stu-id="033ef-260">Step 2: Rebuild libraries from the deployment server</span></span>  
<span data-ttu-id="033ef-261">完成下列步驟在每個平台的初始設定。</span><span class="sxs-lookup"><span data-stu-id="033ef-261">Complete the following steps on initial setup for each platform.</span></span>  
  
1.  <span data-ttu-id="033ef-262">若要在獨立模式下啟動 BusBuild 程式，請選取**開始**，選取**執行**，然後選取**busbuild.exe**。</span><span class="sxs-lookup"><span data-stu-id="033ef-262">To start the BusBuild program in a standalone mode, select **Start**, select  **Run**, and then select **busbuild.exe**.</span></span>
  
2.  <span data-ttu-id="033ef-263">以 pathcode （PY7333，PD7333 或 DV7333） 登入 JD Edwards OneWorld。</span><span class="sxs-lookup"><span data-stu-id="033ef-263">Sign in to JD Edwards OneWorld in the pathcode (PY7333, PD7333, or DV7333).</span></span>  
  
3.  <span data-ttu-id="033ef-264">在 **重建程式庫**清單中，選取**建置**。</span><span class="sxs-lookup"><span data-stu-id="033ef-264">In the **Rebuild Libraries** list, select the **Build**.</span></span>  
  
##### <a name="step-3-copy-the-custom-dll"></a><span data-ttu-id="033ef-265">步驟 3： 複製自訂 DLL</span><span class="sxs-lookup"><span data-stu-id="033ef-265">Step 3: Copy the Custom DLL</span></span>  
 <span data-ttu-id="033ef-266">將自訂 DLL 從 pathcode 目錄複製到 JD Edwards OneWorld 部署伺服器和 JD Edwards OneWorld 企業伺服器上的父封裝目錄。</span><span class="sxs-lookup"><span data-stu-id="033ef-266">Copy the custom DLL from the pathcode directory to the parent package directories on the JD Edwards OneWorld deployment server and on the JD Edwards OneWorld Enterprise Server.</span></span>
  
<span data-ttu-id="033ef-267">**JD Edwards OneWorld XE 部署伺服器上**</span><span class="sxs-lookup"><span data-stu-id="033ef-267">**On the JD Edwards OneWorld XE Deployment Server**</span></span>  
  
1.  <span data-ttu-id="033ef-268">將 ACBLIB.dll 從 DV7333\bin32 複製到 DV7333\Packages\DV7333FA\bin32。</span><span class="sxs-lookup"><span data-stu-id="033ef-268">Copy ACBLIB.dll from DV7333\bin32 to DV7333\Packages\DV7333FA\bin32.</span></span>  
  
2.  <span data-ttu-id="033ef-269">將 ACBLIB.def、ACBLIB.dmp 和 ACBLIB.mak 從 DV7333\obj 資料夾複製到 DV7333\Packages\DV7333FA\obj 資料夾。</span><span class="sxs-lookup"><span data-stu-id="033ef-269">Copy ACBLIB.def, ACBLIB.dmp, and ACBLIB.mak from DV7333\obj folder to DV7333\Packages\DV7333FA\obj folder.</span></span>  
  
3.  <span data-ttu-id="033ef-270">ACBLIB.exp、 ACBLIB.lib 和 sACBLIB.lib DV7333\lib32 資料夾複製 DV7333\Packages\DV7333FA\lib32 資料夾。</span><span class="sxs-lookup"><span data-stu-id="033ef-270">Copy ACBLIB.exp, ACBLIB.lib, and sACBLIB.lib from DV7333\lib32 folder to DV7333\Packages\DV7333FA\lib32 folder.</span></span>  
  
<span data-ttu-id="033ef-271">**JD Edwards OneWorld 企業伺服器上**</span><span class="sxs-lookup"><span data-stu-id="033ef-271">**On the JD Edwards OneWorld Enterprise Server**</span></span>  
  
<span data-ttu-id="033ef-272">建立每個目錄和檔案之後，確認授權。</span><span class="sxs-lookup"><span data-stu-id="033ef-272">After each directory and file is created, verify the authorization.</span></span>  
  
1.  <span data-ttu-id="033ef-273">建立目錄 ACBLIB 在 DV7333FA\obj\\。</span><span class="sxs-lookup"><span data-stu-id="033ef-273">Create a directory ACBLIB under DV7333FA\obj\\.</span></span>  
  
2.  <span data-ttu-id="033ef-274">建立目錄 ACBLIB DV7333FA\source 底下。</span><span class="sxs-lookup"><span data-stu-id="033ef-274">Create a directory ACBLIB under DV7333FA\source.</span></span>  
  
3.  <span data-ttu-id="033ef-275">將 b5500900.c 從部署伺服器的 DV7333\source 目錄傳送至 DV7333FA\source\ACBLIB 目錄。</span><span class="sxs-lookup"><span data-stu-id="033ef-275">FTP b5500900.c from Deployment Server DV7333\source directory to DV7333FA\source\ACBLIB directory.</span></span>  
  
4.  <span data-ttu-id="033ef-276">從部署伺服器 DV7333\include 目錄 FTP b5500900.h DV7333FA\include 目錄。</span><span class="sxs-lookup"><span data-stu-id="033ef-276">FTP b5500900.h from Deployment Server DV7333\include directory to DV7333FA\include directory.</span></span>  
  
##### <a name="step-4-build-a-full-package"></a><span data-ttu-id="033ef-277">步驟 4： 建置完整封裝</span><span class="sxs-lookup"><span data-stu-id="033ef-277">Step 4: Build a Full Package</span></span>  
 <span data-ttu-id="033ef-278">由於 JD Edwards 封裝建置程序的限制，建置完整封裝的環境中要套用 BTSREL 更新，或更新封裝組建無法正常運作。</span><span class="sxs-lookup"><span data-stu-id="033ef-278">Because of a limitation of the JD Edwards package-build process, build a full package for the environments to which you applied the BTSREL update, or the update package build does not work correctly.</span></span> <span data-ttu-id="033ef-279">請參閱 JD Edwards 說明，以了解如何建置完整封裝組建。</span><span class="sxs-lookup"><span data-stu-id="033ef-279">See the JD Edwards documentation on how to build a full package build.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="033ef-280">當您套用 JD Edwards OneWorld ASU/ESU 時，ASU/ESU 通常不會建立新的程式庫和商務功能。</span><span class="sxs-lookup"><span data-stu-id="033ef-280">When you apply JD Edwards OneWorld ASU/ESUs, the ASU/ESU does not typically create new library and business functions.</span></span> <span data-ttu-id="033ef-281">因此，此程序很簡單： 但是，BizTalk Adapter for JD Edwards OneWorld 自訂封裝會建立新的程式庫。</span><span class="sxs-lookup"><span data-stu-id="033ef-281">Therefore, the process is simple: however, the BizTalk Adapter for JD Edwards OneWorld custom package creates a new library.</span></span> <span data-ttu-id="033ef-282">因此，您必須執行額外的步驟，例如，手動建立目錄，並執行完整封裝組建。</span><span class="sxs-lookup"><span data-stu-id="033ef-282">Therefore, you must perform extra steps, such as manually create a directory and run a full package build.</span></span>  
  
#### <a name="modules-list"></a><span data-ttu-id="033ef-283">模組清單</span><span class="sxs-lookup"><span data-stu-id="033ef-283">Modules list</span></span>  
 <span data-ttu-id="033ef-284">BTSREL 自訂封裝會在 JD Edwards OneWorld 中建立下列物件。</span><span class="sxs-lookup"><span data-stu-id="033ef-284">The BTSREL custom package creates the following objects in JD Edwards OneWorld.</span></span> <span data-ttu-id="033ef-285">BTSREL 包含可擷取中繼資料的商務功能，以及可測試資料類型的自訂功能。</span><span class="sxs-lookup"><span data-stu-id="033ef-285">BTSREL contains business functions to extract metadata and custom functions to test the data types.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="033ef-286">JD Edwards OneWorld 更新有一個 Bug。</span><span class="sxs-lookup"><span data-stu-id="033ef-286">There is a bug in the JD Edwards OneWorld update.</span></span> <span data-ttu-id="033ef-287">如果您不需要所有的商務和自訂函式，請確認完整封裝組建已完成，而不是更新封裝組建。</span><span class="sxs-lookup"><span data-stu-id="033ef-287">If you don't have all the business and custom functions, verify that a full package build was completed, rather than an update package build.</span></span>  
>  
>  <span data-ttu-id="033ef-288">如果您遺漏清單中的檔案，例如，如果您具有 ACBTEST 下方的所有檔案但遺漏上方的檔案，則可能遺漏「資料字典」(DD) 項目。</span><span class="sxs-lookup"><span data-stu-id="033ef-288">If you are missing files from the list, for example, if you have everything below ACBTEST but nothing above it, you might be missing the Data Dictionary (DD) items.</span></span> <span data-ttu-id="033ef-289">您可以前往**Work With Data Items**並尋找遺漏的檔案。</span><span class="sxs-lookup"><span data-stu-id="033ef-289">You can go to **Work With Data Items** and look for missing files.</span></span>  
>   
>  <span data-ttu-id="033ef-290">如果您遺漏其他項目，例如 ACBCHAR01、 ACBDATE01、 ADBINT01、 ACBMATH01 和 ACBSTR01，這些是*主要的資料元素*。</span><span class="sxs-lookup"><span data-stu-id="033ef-290">If you are missing other items, such as ACBCHAR01, ACBDATE01, ADBINT01, ACBMATH01, and ACBSTR01, these are the *Primary Data Elements*.</span></span> <span data-ttu-id="033ef-291">當您合併從規劃到開發的物件時，會在背景執行許多報表。</span><span class="sxs-lookup"><span data-stu-id="033ef-291">When you merge objects from planner to DEV, many reports run in the background.</span></span> <span data-ttu-id="033ef-292">您可以開啟合併報表並尋找是否有任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="033ef-292">You can open the merge reports and look for errors.</span></span> <span data-ttu-id="033ef-293">報表應該列出所有項目，並指出已完成且沒有任何錯誤或警告。</span><span class="sxs-lookup"><span data-stu-id="033ef-293">The reports should list all the items and indicate that they were completed without errors or warnings.</span></span> <span data-ttu-id="033ef-294">透過這項驗證，由於所有項目都已計入，因此您可以繼續進行。</span><span class="sxs-lookup"><span data-stu-id="033ef-294">With this verification, you can continue because all items are accounted for.</span></span>  
  
-   <span data-ttu-id="033ef-295">ACBCHAR01 - 測試 CHAR 類型 01</span><span class="sxs-lookup"><span data-stu-id="033ef-295">ACBCHAR01 - TEST CHAR TYPE 01</span></span>  
  
-   <span data-ttu-id="033ef-296">ACBCUST - ACB 客戶識別碼</span><span class="sxs-lookup"><span data-stu-id="033ef-296">ACBCUST - ACB CUSTOMER ID</span></span>  
  
-   <span data-ttu-id="033ef-297">ACBDATE01 - 測試日期類型 01</span><span class="sxs-lookup"><span data-stu-id="033ef-297">ACBDATE01 - TEST DATE TYPE 01</span></span>  
  
-   <span data-ttu-id="033ef-298">ACBDEF - ACB 功能類型定義</span><span class="sxs-lookup"><span data-stu-id="033ef-298">ACBDEF - ACB FUNCTION TYPE DEFINITION</span></span>  
  
-   <span data-ttu-id="033ef-299">ACBFCNT - ACB 功能名稱清單計數</span><span class="sxs-lookup"><span data-stu-id="033ef-299">ACBFCNT - ACB FUNCTION NAME LIST COUNT</span></span>  
  
-   <span data-ttu-id="033ef-300">ACBFUNC-ACB 函式名稱清單</span><span class="sxs-lookup"><span data-stu-id="033ef-300">ACBFUNC - ACB FUNCTION NAME LIST</span></span>  
  
-   <span data-ttu-id="033ef-301">ACBFUNCN-ACB 函式名稱</span><span class="sxs-lookup"><span data-stu-id="033ef-301">ACBFUNCN - ACB FUNCTION NAME</span></span>  
  
-   <span data-ttu-id="033ef-302">ACBINT01 - 測試整數類型 01</span><span class="sxs-lookup"><span data-stu-id="033ef-302">ACBINT01 - TEST INTEGER TYPE 01</span></span>  
  
-   <span data-ttu-id="033ef-303">ACBLIB - 控制 BROKER 程式庫</span><span class="sxs-lookup"><span data-stu-id="033ef-303">ACBLIB - CONTROL BROKER LIBRARY</span></span>  
  
-   <span data-ttu-id="033ef-304">ACBMATH01 - 測試數學類型 01</span><span class="sxs-lookup"><span data-stu-id="033ef-304">ACBMATH01 - TEST MATH TYPE 01</span></span>  
  
-   <span data-ttu-id="033ef-305">ACBNEWS - ACB 新狀態</span><span class="sxs-lookup"><span data-stu-id="033ef-305">ACBNEWS - ACB NEW STATUS</span></span>  
  
-   <span data-ttu-id="033ef-306">ACBORDER - ACB 訂單號碼</span><span class="sxs-lookup"><span data-stu-id="033ef-306">ACBORDER - ACB ORDER NUMBER</span></span>  
  
-   <span data-ttu-id="033ef-307">ACBPRC - ACB 項目價格</span><span class="sxs-lookup"><span data-stu-id="033ef-307">ACBPRC - ACB ITEM PRICE</span></span>  
  
-   <span data-ttu-id="033ef-308">ACBPROD - ACB 產品識別碼</span><span class="sxs-lookup"><span data-stu-id="033ef-308">ACBPROD - ACB PRODUCT ID</span></span>  
  
-   <span data-ttu-id="033ef-309">ACBQTY - ACB 項目數量</span><span class="sxs-lookup"><span data-stu-id="033ef-309">ACBQTY - ACB ITEM QUANTITY</span></span>  
  
-   <span data-ttu-id="033ef-310">ACBRES - ACB 結果指標</span><span class="sxs-lookup"><span data-stu-id="033ef-310">ACBRES - ACB RESULT INDICATOR</span></span>  
  
-   <span data-ttu-id="033ef-311">ACBSTAT - ACB 狀態</span><span class="sxs-lookup"><span data-stu-id="033ef-311">ACBSTAT - ACB STATUS</span></span>  
  
-   <span data-ttu-id="033ef-312">ACBSTR01 - 測試字串類型 01</span><span class="sxs-lookup"><span data-stu-id="033ef-312">ACBSTR01 - TEST STRING TYPE 01</span></span>  
  
-   <span data-ttu-id="033ef-313">ACBTEST - ACB 測試畫面</span><span class="sxs-lookup"><span data-stu-id="033ef-313">ACBTEST - ACB TEST SCREEN</span></span>  
  
-   <span data-ttu-id="033ef-314">ACBTEST2-ACB 測試畫面 2</span><span class="sxs-lookup"><span data-stu-id="033ef-314">ACBTEST2 - ACB TEST SCREEN 2</span></span>  
  
-   <span data-ttu-id="033ef-315">ACBTEST3-ACB 測試畫面 3</span><span class="sxs-lookup"><span data-stu-id="033ef-315">ACBTEST3 - ACB TEST SCREEN 3</span></span>  
  
-   <span data-ttu-id="033ef-316">B5500900 - 控制 BROKER 支援模組</span><span class="sxs-lookup"><span data-stu-id="033ef-316">B5500900 - CONTROL BROKER SUPPORT MODULE</span></span>  
  
-   <span data-ttu-id="033ef-317">D5500900-控制 BROKER 資料結構</span><span class="sxs-lookup"><span data-stu-id="033ef-317">D5500900 - CONTROL BROKER DATA STRUCTURE</span></span>  
  
-   <span data-ttu-id="033ef-318">D5500900A-控制 BROKER 資料結構</span><span class="sxs-lookup"><span data-stu-id="033ef-318">D5500900A - CONTROL BROKER DATA STRUCTURE</span></span>  
  
-   <span data-ttu-id="033ef-319">D5500900B-擷取價格資料結構</span><span class="sxs-lookup"><span data-stu-id="033ef-319">D5500900B - FETCH PRICE DATA STRUCTURE</span></span>  
  
-   <span data-ttu-id="033ef-320">D5500900C - 取得客戶狀態資料結構</span><span class="sxs-lookup"><span data-stu-id="033ef-320">D5500900C - GET CUSTOMER STATUS DATA STRUCTURE</span></span>  
  
-   <span data-ttu-id="033ef-321">D5500900D-集合的客戶狀態資料結構</span><span class="sxs-lookup"><span data-stu-id="033ef-321">D5500900D - SET CUSTOMER STATUS DATA STRUCTURE</span></span>  
  
-   <span data-ttu-id="033ef-322">D5500900E-更新銷售訂單狀態資料結構</span><span class="sxs-lookup"><span data-stu-id="033ef-322">D5500900E - UPDATE SALES ORDER STATUS DATA STRUCTURE</span></span>  
  
-   <span data-ttu-id="033ef-323">D5500900F - 測試整數</span><span class="sxs-lookup"><span data-stu-id="033ef-323">D5500900F - TEST INTEGER</span></span>  
  
-   <span data-ttu-id="033ef-324">D5500900G-測試字串</span><span class="sxs-lookup"><span data-stu-id="033ef-324">D5500900G - TEST STRING</span></span>  
  
-   <span data-ttu-id="033ef-325">D5500900H-測試日期</span><span class="sxs-lookup"><span data-stu-id="033ef-325">D5500900H - TEST DATE</span></span>  
  
-   <span data-ttu-id="033ef-326">D5500900I-測試 CHAR</span><span class="sxs-lookup"><span data-stu-id="033ef-326">D5500900I - TEST CHAR</span></span>  
  
-   <span data-ttu-id="033ef-327">D5500900J - 測試數學數值</span><span class="sxs-lookup"><span data-stu-id="033ef-327">D5500900J - TEST MATH NUMERIC</span></span>  
  
-   <span data-ttu-id="033ef-328">D5500900K-測試日期 2</span><span class="sxs-lookup"><span data-stu-id="033ef-328">D5500900K - TEST DATE 2</span></span>  
  
#### <a name="customize-the-jdeinteropini-file"></a><span data-ttu-id="033ef-329">自訂 jdeinterop.ini 檔案</span><span class="sxs-lookup"><span data-stu-id="033ef-329">Customize the jdeinterop.ini file</span></span>  
 <span data-ttu-id="033ef-330">Connector.jar 和 Kernel.jar 中的 JD Edwards OneWorld XE 連接器類別會要求您必須使用 jdeinterop.ini 的組態檔。</span><span class="sxs-lookup"><span data-stu-id="033ef-330">The JD Edwards OneWorld XE connector classes in Connector.jar and Kernel.jar require that you use the jdeinterop.ini configuration file.</span></span> <span data-ttu-id="033ef-331">這個檔案由 JD Edwards OneWorld 軟體所定義，並使用其術語。</span><span class="sxs-lookup"><span data-stu-id="033ef-331">This file is defined by the JD Edwards OneWorld software and uses its terminology.</span></span> <span data-ttu-id="033ef-332">JD Edwards 互通性指南版本 OneWorld 可能提供之用途和術語，此檔案的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="033ef-332">The JD Edwards Interoperability Guide Release OneWorld may provide more information about the purpose and terminology of this file.</span></span> <span data-ttu-id="033ef-333">沒有範例 jdeinterop.ini 檔案 *< 可 > \config\jde*。</span><span class="sxs-lookup"><span data-stu-id="033ef-333">There is a sample jdeinterop.ini file in *<Adapter_Installation>\config\jde*.</span></span>  
  
<span data-ttu-id="033ef-334">更新以符合您在中定義的參數值的 jdeinterop.ini**傳輸屬性**螢幕。</span><span class="sxs-lookup"><span data-stu-id="033ef-334">Update jdeinterop.ini to match the parameter values that you defined in the **Transport Properties** screen.</span></span> <span data-ttu-id="033ef-335">如果其參數相容，則多個 JD Edwards OneWorld 邏輯系統可以共用同一個 jdeinterop.ini 檔案。</span><span class="sxs-lookup"><span data-stu-id="033ef-335">Multiple JD Edwards OneWorld logical systems can share the same jdeinterop.ini file if their parameters are compatible.</span></span> <span data-ttu-id="033ef-336">一般而言，如果兩個邏輯系統指向兩部不同的 JD Edwards OneWorld 電腦，則他們需要兩個不同的 jdeinterop.ini 複本。</span><span class="sxs-lookup"><span data-stu-id="033ef-336">Generally, if two logical systems point to two different JD Edwards OneWorld computers, they need two different copies of jdeinterop.ini.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="033ef-337">Jdeinterop.ini 中的記錄應該關閉，而且可以放心地忽略各種記錄檔的參數。</span><span class="sxs-lookup"><span data-stu-id="033ef-337">The logging in jdeinterop.ini should be turned off, and the parameters for the various log files can safely be ignored.</span></span>  
  
 <span data-ttu-id="033ef-338">下表逐項列出位於 jdeinterop.ini 檔案中的設定，</span><span class="sxs-lookup"><span data-stu-id="033ef-338">The following table itemizes the settings found in the jdeinterop.ini file.</span></span> <span data-ttu-id="033ef-339">並依區段分組其資訊。</span><span class="sxs-lookup"><span data-stu-id="033ef-339">The information is organized by section.</span></span> <span data-ttu-id="033ef-340">例如，[JDENET] 等區段會依其在 JD Edwards OneWorld 軟體中出現的順序列出。</span><span class="sxs-lookup"><span data-stu-id="033ef-340">For example [JDENET] and the sections are listed in the order that they appear in the JD Edwards OneWorld software.</span></span>  
  
#### <a name="jdeinteropini-file-settings"></a><span data-ttu-id="033ef-341">jdeinterop.ini 檔案設定</span><span class="sxs-lookup"><span data-stu-id="033ef-341">jdeinterop.ini file settings</span></span>
  
|<span data-ttu-id="033ef-342">章節</span><span class="sxs-lookup"><span data-stu-id="033ef-342">Section</span></span>|<span data-ttu-id="033ef-343">參數和描述</span><span class="sxs-lookup"><span data-stu-id="033ef-343">Parameter and Description</span></span>|  
|-------------|-------------------------------|  
|<span data-ttu-id="033ef-344">[JDENET]</span><span class="sxs-lookup"><span data-stu-id="033ef-344">[JDENET]</span></span>|<span data-ttu-id="033ef-345">**EnterpriseServerTimeout.**</span><span class="sxs-lookup"><span data-stu-id="033ef-345">**EnterpriseServerTimeout.**</span></span> <span data-ttu-id="033ef-346">企業伺服器要求的逾時值，以毫秒為單位。</span><span class="sxs-lookup"><span data-stu-id="033ef-346">The time-out value for a request to the enterprise server in milliseconds.</span></span> <span data-ttu-id="033ef-347">預設大小是 120000。</span><span class="sxs-lookup"><span data-stu-id="033ef-347">The default size is 120000.</span></span><br /><br /> <span data-ttu-id="033ef-348">**maxPoolSize.**</span><span class="sxs-lookup"><span data-stu-id="033ef-348">**maxPoolSize.**</span></span> <span data-ttu-id="033ef-349">JDENET 通訊端連接集區大小。</span><span class="sxs-lookup"><span data-stu-id="033ef-349">The JDENET socket connection pool size.</span></span> <span data-ttu-id="033ef-350">預設大小為 30。</span><span class="sxs-lookup"><span data-stu-id="033ef-350">The default size is 30.</span></span>|  
|<span data-ttu-id="033ef-351">[SERVER]</span><span class="sxs-lookup"><span data-stu-id="033ef-351">[SERVER]</span></span>|<span data-ttu-id="033ef-352">**glossaryTextServer.**</span><span class="sxs-lookup"><span data-stu-id="033ef-352">**glossaryTextServer.**</span></span> <span data-ttu-id="033ef-353">提供詞彙文字資訊的企業伺服器和連接埠。</span><span class="sxs-lookup"><span data-stu-id="033ef-353">The enterprise server and port that provide glossary text information.</span></span> <span data-ttu-id="033ef-354">這是傳回錯誤文字描述的伺服器。</span><span class="sxs-lookup"><span data-stu-id="033ef-354">This is the server that returns text descriptions for errors.</span></span> <span data-ttu-id="033ef-355">通常是與 JD Edwards OneWorld 應用程式伺服器相同的主機和連接埠。</span><span class="sxs-lookup"><span data-stu-id="033ef-355">This is frequently the same host and port as the JD Edwards OneWorld application server.</span></span> <span data-ttu-id="033ef-356">為了支援不同的語言編碼，可能會有多個詞彙伺服器。</span><span class="sxs-lookup"><span data-stu-id="033ef-356">There may be more than one glossary server for different supported language encodings.</span></span> <span data-ttu-id="033ef-357">例如，JDED:6010 或 actsrv1:6009。</span><span class="sxs-lookup"><span data-stu-id="033ef-357">For example, JDED:6010 or actsrv1:6009.</span></span> <span data-ttu-id="033ef-358">這些值必須符合在 [系統定義] 中設定的值。</span><span class="sxs-lookup"><span data-stu-id="033ef-358">The values must match those set in System Definition.</span></span><br /><br /> <span data-ttu-id="033ef-359">**codePage.**</span><span class="sxs-lookup"><span data-stu-id="033ef-359">**codePage.**</span></span> <span data-ttu-id="033ef-360">編碼配置中。</span><span class="sxs-lookup"><span data-stu-id="033ef-360">The encoding scheme.</span></span> <span data-ttu-id="033ef-361">預設值是 1252年。</span><span class="sxs-lookup"><span data-stu-id="033ef-361">The default is 1252.</span></span><br /><br /> <span data-ttu-id="033ef-362">1252 英文和西歐語系</span><span class="sxs-lookup"><span data-stu-id="033ef-362">- 1252 English and Western European</span></span><br /><br /> <span data-ttu-id="033ef-363">-932 日文</span><span class="sxs-lookup"><span data-stu-id="033ef-363">- 932 Japanese</span></span><br /><br /> <span data-ttu-id="033ef-364">-950 繁體中文</span><span class="sxs-lookup"><span data-stu-id="033ef-364">- 950 Traditional Chinese</span></span><br /><br /> <span data-ttu-id="033ef-365">-936 簡體中文</span><span class="sxs-lookup"><span data-stu-id="033ef-365">- 936 Simplified Chinese</span></span><br /><br /> <span data-ttu-id="033ef-366">-949 韓文</span><span class="sxs-lookup"><span data-stu-id="033ef-366">- 949 Korean</span></span>|  
|<span data-ttu-id="033ef-367">[LOGS]</span><span class="sxs-lookup"><span data-stu-id="033ef-367">[LOGS]</span></span>|<span data-ttu-id="033ef-368">**log = c:\jas.log。**</span><span class="sxs-lookup"><span data-stu-id="033ef-368">**log= c:\jas.log.**</span></span> <span data-ttu-id="033ef-369">記錄檔的位置。</span><span class="sxs-lookup"><span data-stu-id="033ef-369">Location of the log file.</span></span> <span data-ttu-id="033ef-370">您可以放心地略過這個參數。</span><span class="sxs-lookup"><span data-stu-id="033ef-370">You can safely ignore this parameter.</span></span><br /><br /> <span data-ttu-id="033ef-371">**debuglog = c:\jasdebug.log。**</span><span class="sxs-lookup"><span data-stu-id="033ef-371">**debuglog= c:\jasdebug.log.**</span></span> <span data-ttu-id="033ef-372">偵錯記錄檔的位置。</span><span class="sxs-lookup"><span data-stu-id="033ef-372">Location of debug log file.</span></span> <span data-ttu-id="033ef-373">您可以放心地略過這個參數。</span><span class="sxs-lookup"><span data-stu-id="033ef-373">You can safely ignore this parameter.</span></span><br /><br /> <span data-ttu-id="033ef-374">**偵錯。**</span><span class="sxs-lookup"><span data-stu-id="033ef-374">**Debug.**</span></span> <span data-ttu-id="033ef-375">判斷是否開啟 JDENET 偵錯功能。</span><span class="sxs-lookup"><span data-stu-id="033ef-375">Determines whether JDENET debugging is on.</span></span> <span data-ttu-id="033ef-376">預設值為 FALSE。</span><span class="sxs-lookup"><span data-stu-id="033ef-376">The default is FALSE.</span></span>|  
|<span data-ttu-id="033ef-377">[DEBUG]</span><span class="sxs-lookup"><span data-stu-id="033ef-377">[DEBUG]</span></span>|<span data-ttu-id="033ef-378">**JobFile = c:\Interop.log。**</span><span class="sxs-lookup"><span data-stu-id="033ef-378">**JobFile= c:\Interop.log.**</span></span> <span data-ttu-id="033ef-379">錯誤檔的位置。</span><span class="sxs-lookup"><span data-stu-id="033ef-379">Location of error file.</span></span> <span data-ttu-id="033ef-380">您可以放心地略過這個參數。</span><span class="sxs-lookup"><span data-stu-id="033ef-380">You can safely ignore this parameter.</span></span><br /><br /> <span data-ttu-id="033ef-381">**DebugFile = c:\InteropDebug.log。**</span><span class="sxs-lookup"><span data-stu-id="033ef-381">**DebugFile= c:\InteropDebug.log.**</span></span> <span data-ttu-id="033ef-382">偵錯檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="033ef-382">Location of debug file.</span></span> <span data-ttu-id="033ef-383">您可以放心地略過這個參數。</span><span class="sxs-lookup"><span data-stu-id="033ef-383">You can safely ignore this parameter.</span></span><br /><br /> <span data-ttu-id="033ef-384">**log = c:\net.log。**</span><span class="sxs-lookup"><span data-stu-id="033ef-384">**log= c:\net.log.**</span></span> <span data-ttu-id="033ef-385">記錄檔的位置。</span><span class="sxs-lookup"><span data-stu-id="033ef-385">Location of log file.</span></span> <span data-ttu-id="033ef-386">您可以放心地略過這個參數。</span><span class="sxs-lookup"><span data-stu-id="033ef-386">You can safely ignore this parameter.</span></span><br /><br /> <span data-ttu-id="033ef-387">**debugLevel = 0-12。**</span><span class="sxs-lookup"><span data-stu-id="033ef-387">**debugLevel= 0 - 12.**</span></span> <span data-ttu-id="033ef-388">偵錯層級。</span><span class="sxs-lookup"><span data-stu-id="033ef-388">Debug levels.</span></span> <span data-ttu-id="033ef-389">您可以放心地略過這個參數。</span><span class="sxs-lookup"><span data-stu-id="033ef-389">You can safely ignore this parameter.</span></span> <span data-ttu-id="033ef-390">這會定義指定記錄檔中 COM 連接器和 Callobject 元件所提供的追蹤層級，僅適用於 COM 伺服器。</span><span class="sxs-lookup"><span data-stu-id="033ef-390">This defines the level of tracing provided by the COM Connector and the Callobject component in the specified log file, in the COM server only.</span></span><br /><br /> <span data-ttu-id="033ef-391">-0 none。</span><span class="sxs-lookup"><span data-stu-id="033ef-391">- 0 None.</span></span> <span data-ttu-id="033ef-392">關閉記錄功能並僅將錯誤寫入 JobFile。</span><span class="sxs-lookup"><span data-stu-id="033ef-392">Logging is turned off and only errors are written to the JobFile.</span></span><br /><br /> <span data-ttu-id="033ef-393">-2 的錯誤 （錯誤訊息）</span><span class="sxs-lookup"><span data-stu-id="033ef-393">- 2 Errors (error messages)</span></span><br /><br /> <span data-ttu-id="033ef-394">-4 系統錯誤 （例外狀況訊息）</span><span class="sxs-lookup"><span data-stu-id="033ef-394">- 4 System Errors (exception messages)</span></span><br /><br /> <span data-ttu-id="033ef-395">-6 警告資訊</span><span class="sxs-lookup"><span data-stu-id="033ef-395">- 6 Warning Information</span></span><br /><br /> <span data-ttu-id="033ef-396">-8 最小追蹤 （索引鍵作業。</span><span class="sxs-lookup"><span data-stu-id="033ef-396">- 8 Min Trace (Key operations.</span></span> <span data-ttu-id="033ef-397">例如登入、 登出、商務功能呼叫)。</span><span class="sxs-lookup"><span data-stu-id="033ef-397">For example, Logon, Logoff, Business Function calls.)</span></span><br /><br /> <span data-ttu-id="033ef-398">-10 的疑難排解資訊 （說明）。</span><span class="sxs-lookup"><span data-stu-id="033ef-398">- 10 Troubleshooting Information (Help).</span></span><br /><br /> <span data-ttu-id="033ef-399">12 完整的偵錯資訊 （記錄檔的所有項目）</span><span class="sxs-lookup"><span data-stu-id="033ef-399">- 12 Complete Debug Information (Logs everything)</span></span><br /><br /> <span data-ttu-id="033ef-400">-根據預設，您不必開啟追蹤功能，，但您在偵錯您的程式碼時，追蹤就很有用。</span><span class="sxs-lookup"><span data-stu-id="033ef-400">- By default, you do not have to turn on tracing, but tracing is useful when you are debugging your code.</span></span><br /><br /> <span data-ttu-id="033ef-401">-NetTraceLevel = 0。</span><span class="sxs-lookup"><span data-stu-id="033ef-401">- NetTraceLevel=0.</span></span> <span data-ttu-id="033ef-402">追蹤層級。</span><span class="sxs-lookup"><span data-stu-id="033ef-402">Trace levels.</span></span> <span data-ttu-id="033ef-403">您可以放心地略過這個參數。</span><span class="sxs-lookup"><span data-stu-id="033ef-403">You can safely ignore this parameter.</span></span> <span data-ttu-id="033ef-404">定義中指定的記錄檔，在僅限 COM 伺服器 ThinNet 元件所提供的追蹤層級。</span><span class="sxs-lookup"><span data-stu-id="033ef-404">Defines the level of tracing provided by the ThinNet component in the specified log file, in the COM server only.</span></span> <span data-ttu-id="033ef-405">奇數值則保留給未來要加入的層級。</span><span class="sxs-lookup"><span data-stu-id="033ef-405">The odd values are reserved for future levels to be added.</span></span><br /><br /> <span data-ttu-id="033ef-406">-下列清單說明更多的偵錯層級：</span><span class="sxs-lookup"><span data-stu-id="033ef-406">-  The following list describes debug levels even more:</span></span><br /><br /> <span data-ttu-id="033ef-407">-0 無追蹤</span><span class="sxs-lookup"><span data-stu-id="033ef-407">-     0 No trace</span></span><br /><br /> <span data-ttu-id="033ef-408">-1 表示記錄處理序識別碼、 執行緒 ID，以及新增新的連接，並搜尋通訊端集區時可用的通訊端狀態。</span><span class="sxs-lookup"><span data-stu-id="033ef-408">- 1 Refers to the Record process ID, thread ID, and the available socket status when a new connection is added and the socket pool is searched.</span></span><br /><br /> <span data-ttu-id="033ef-409">-2 包含追蹤層級 1 中的資訊，也會追蹤每個連接管理員類別中所做的呼叫。</span><span class="sxs-lookup"><span data-stu-id="033ef-409">- 2 Includes the information in trace level 1 and also traces every call made in the connection manager class.</span></span><br /><br /> <span data-ttu-id="033ef-410">-3 包含追蹤層級 2，以及追蹤 getport （） 呼叫和 gethost （） 呼叫中的所有資訊。</span><span class="sxs-lookup"><span data-stu-id="033ef-410">- 3 Includes all information in trace level 2, and also traces getPort() calls and getHost() calls.</span></span>|  
|<span data-ttu-id="033ef-411">[INTEROP]</span><span class="sxs-lookup"><span data-stu-id="033ef-411">[INTEROP]</span></span>|<span data-ttu-id="033ef-412">**enterpriseServer.**</span><span class="sxs-lookup"><span data-stu-id="033ef-412">**enterpriseServer.**</span></span> <span data-ttu-id="033ef-413">這個值是主機伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="033ef-413">This value is the name of the host server.</span></span> <span data-ttu-id="033ef-414">請確定此值是相同的值，您在中輸入**主機名稱**欄位中**JDE [Credentials**一節中**系統定義**在**傳輸屬性**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="033ef-414">Make sure that this value is the same value that you enter in the **Host Name** field in the **JDE Credentials** section in **System Definition** in the **Transport Properties** dialog box.</span></span> <span data-ttu-id="033ef-415">預設為 JDED。</span><span class="sxs-lookup"><span data-stu-id="033ef-415">The default is JDED.</span></span><br /><br /> <span data-ttu-id="033ef-416">**連接埠。**</span><span class="sxs-lookup"><span data-stu-id="033ef-416">**port.**</span></span> <span data-ttu-id="033ef-417">這個值是用來交換資料的連接埠編號。</span><span class="sxs-lookup"><span data-stu-id="033ef-417">This value is the port number that is used to exchange data.</span></span> <span data-ttu-id="033ef-418">請確定此值是相同的值，您在中輸入**連接埠號碼**欄位中 [JD Edwards**認證**一節中**傳輸屬性] 系統定義**.</span><span class="sxs-lookup"><span data-stu-id="033ef-418">Make sure that this value is the same value that you enter in the **Port Number** field in the JD Edwards **Credentials** section in the **Transport Properties, System Definition**.</span></span> <span data-ttu-id="033ef-419">比方說，6010 或 6009。</span><span class="sxs-lookup"><span data-stu-id="033ef-419">For example, 6010 or 6009.</span></span> <span data-ttu-id="033ef-420">在中設定這些值必須符合**系統定義**。</span><span class="sxs-lookup"><span data-stu-id="033ef-420">The values must match those set in **System Definition**.</span></span><br /><br /> <span data-ttu-id="033ef-421">**inactive_timeout**。</span><span class="sxs-lookup"><span data-stu-id="033ef-421">**inactive_timeout**.</span></span> <span data-ttu-id="033ef-422">自動認可模式下的交易逾時值，以毫秒為單位。</span><span class="sxs-lookup"><span data-stu-id="033ef-422">The time-out value in milliseconds for a transaction in auto-commit mode.</span></span> <span data-ttu-id="033ef-423">如果使用者在這段時間 (毫秒) 內沒有活動，interop 伺服器會將使用者登出。</span><span class="sxs-lookup"><span data-stu-id="033ef-423">If the user is inactive for this period of time (in milliseconds), the interop server logs off the user.</span></span> <span data-ttu-id="033ef-424">您可以將這個值變更為更短的時間。</span><span class="sxs-lookup"><span data-stu-id="033ef-424">You can change this value to a shorter period of time.</span></span> <span data-ttu-id="033ef-425">預設為 1200000。</span><span class="sxs-lookup"><span data-stu-id="033ef-425">The default is 1200000.</span></span><br /><br /> <span data-ttu-id="033ef-426">**manual_timeout。**</span><span class="sxs-lookup"><span data-stu-id="033ef-426">**manual_timeout.**</span></span> <span data-ttu-id="033ef-427">以毫秒為單位，在手動認可模式下的交易逾時值。</span><span class="sxs-lookup"><span data-stu-id="033ef-427">The time-out value in milliseconds for a transaction in manual commit mode.</span></span> <span data-ttu-id="033ef-428">預設為 120000。</span><span class="sxs-lookup"><span data-stu-id="033ef-428">The default is 120000.</span></span><br /><br /> <span data-ttu-id="033ef-429">**存放庫。**</span><span class="sxs-lookup"><span data-stu-id="033ef-429">**Repository.**</span></span> <span data-ttu-id="033ef-430">指向包含 Connector.jar 和 Kernel.jar 的目錄位置。</span><span class="sxs-lookup"><span data-stu-id="033ef-430">Points to the location of the directory that contains Connector.jar and Kernel.jar.</span></span> <span data-ttu-id="033ef-431">在 UNIX 上，這是完整路徑。</span><span class="sxs-lookup"><span data-stu-id="033ef-431">On UNIX, this is a full path.</span></span>|  
|<span data-ttu-id="033ef-432">[CORBA]</span><span class="sxs-lookup"><span data-stu-id="033ef-432">[CORBA]</span></span>|<span data-ttu-id="033ef-433">您可以放心地略過這個參數。</span><span class="sxs-lookup"><span data-stu-id="033ef-433">You can safely ignore this parameter.</span></span><br /><br /> <span data-ttu-id="033ef-434">**多執行緒。**</span><span class="sxs-lookup"><span data-stu-id="033ef-434">**Multithread.**</span></span> <span data-ttu-id="033ef-435">您可以忽略此設定。</span><span class="sxs-lookup"><span data-stu-id="033ef-435">The setting can be ignored.</span></span> <span data-ttu-id="033ef-436">設定為 1 表示提供多執行緒支援給 CORBA。</span><span class="sxs-lookup"><span data-stu-id="033ef-436">Set to 1 for multithread support for CORBA.</span></span><br /><br /> <span data-ttu-id="033ef-437">Objects= CORBA::Connector;CORBA::OneWorldVersion</span><span class="sxs-lookup"><span data-stu-id="033ef-437">Objects= CORBA::Connector;CORBA::OneWorldVersion</span></span><br /><br /> <span data-ttu-id="033ef-438">為 CORBA 伺服器定義要在啟動時建立的物件。</span><span class="sxs-lookup"><span data-stu-id="033ef-438">Defines the objects for the CORBA server to create at startup.</span></span> <span data-ttu-id="033ef-439">也取代了-DIORFILENAME = 命令列選項，例如： CORBA::Connector=connector.ior。</span><span class="sxs-lookup"><span data-stu-id="033ef-439">Also replaces the -DIORFILENAME = command-line option, for example: CORBA::Connector=connector.ior.</span></span>|  
  
## <a name="jd-edwards-enterpriseone"></a><span data-ttu-id="033ef-440">JD Edwards EnterpriseOne</span><span class="sxs-lookup"><span data-stu-id="033ef-440">JD Edwards EnterpriseOne</span></span>  
<span data-ttu-id="033ef-441">此章節包含有關使用 Microsoft BizTalk Adapter for JD Edwards EnterpriseOne 的 BizTalk Server 的重要資訊。</span><span class="sxs-lookup"><span data-stu-id="033ef-441">This sections includes key information on using the Microsoft BizTalk Adapter for JD Edwards EnterpriseOne with BizTalk Server.</span></span>
  
### <a name="execute-a-jd-edwards-enterpriseone-master-business-function"></a><span data-ttu-id="033ef-442">執行 JD Edwards EnterpriseOne 主要商務功能</span><span class="sxs-lookup"><span data-stu-id="033ef-442">Execute a JD Edwards EnterpriseOne master business function</span></span>  
 <span data-ttu-id="033ef-443">您可以使用 BizTalk Adapter for JD Edwards EnterpriseOne 來叫用 JD Edwards EnterpriseOne 主要商務功能，例如通訊錄、 採購單或銷售訂單。</span><span class="sxs-lookup"><span data-stu-id="033ef-443">You can use the BizTalk Adapter for JD Edwards EnterpriseOne to invoke a JD Edwards EnterpriseOne master business function, such as Address Book, Purchase Order, or Sales Order.</span></span> <span data-ttu-id="033ef-444">您也可以使用這個配接器來連接 JD Edwards EnterpriseOne 和 BizTalk Server，以進行整合。</span><span class="sxs-lookup"><span data-stu-id="033ef-444">You can also use the adapter as part of an integration effort to connect JD Edwards EnterpriseOne with BizTalk Server.</span></span>  
  
##### <a name="access-data-stored-in-jd-edwards-enterpriseone"></a><span data-ttu-id="033ef-445">存取儲存在 JD Edwards EnterpriseOne 中的資料</span><span class="sxs-lookup"><span data-stu-id="033ef-445">Access data stored in JD Edwards EnterpriseOne</span></span>  
 <span data-ttu-id="033ef-446">此配接器接受 XML 訊息，讓 BizTalk Server 應用程式進行通訊並交換的交易與 JD Edwards EnterpriseOne 使用下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="033ef-446">The adapter accepts XML messages to enable BizTalk Server applications to communicate and exchange transactions with JD Edwards EnterpriseOne using one of the following:</span></span>  
  
-   <span data-ttu-id="033ef-447">**傳輸配接器**，其中使用靜態請求-回應傳送埠將訊息傳送至 JD Edwards EnterpriseOne 並預期回應。</span><span class="sxs-lookup"><span data-stu-id="033ef-447">**Transmit Adapter**, which uses a Static Solicit-Response Send port to send a message to JD Edwards EnterpriseOne and expects a response.</span></span>    
-   <span data-ttu-id="033ef-448">**接收配接器**，使用靜態單向接收埠來接收 JD Edwards EnterpriseOne 的訊息。</span><span class="sxs-lookup"><span data-stu-id="033ef-448">**Receive Adapter**, which uses a Static One-Way Receive port to receive messages from JD Edwards EnterpriseOne.</span></span>  
  
### <a name="interoperability-framework"></a><span data-ttu-id="033ef-449">互通性架構</span><span class="sxs-lookup"><span data-stu-id="033ef-449">Interoperability framework</span></span>  
 <span data-ttu-id="033ef-450">JD Edwards EnterpriseOne 透過其互通性架構提供與系統的整合。</span><span class="sxs-lookup"><span data-stu-id="033ef-450">JD Edwards EnterpriseOne provides for integration with systems through its interoperability framework.</span></span> <span data-ttu-id="033ef-451">配接器使用 JD Edwards EnterpriseOne 架構，並利用各種整合存取方法，以提供最大的彈性和功能。</span><span class="sxs-lookup"><span data-stu-id="033ef-451">The adapter uses the JD Edwards EnterpriseOne framework, and takes advantage of various integration access methods to provide the greatest amount of flexibility and functionality.</span></span>  
  
 <span data-ttu-id="033ef-452">BizTalk Adapter for JD Edwards EnterpriseOne 支援下列整合存取方法：</span><span class="sxs-lookup"><span data-stu-id="033ef-452">BizTalk Adapter for JD Edwards EnterpriseOne supports the following integration access methods:</span></span>  
  
- <span data-ttu-id="033ef-453">JD Edwards EnterpriseOne ThinNet API</span><span class="sxs-lookup"><span data-stu-id="033ef-453">JD Edwards EnterpriseOne ThinNet API</span></span>    
- <span data-ttu-id="033ef-454">JD Edwards EnterpriseOne XML</span><span class="sxs-lookup"><span data-stu-id="033ef-454">JD Edwards EnterpriseOne XML</span></span>    
- <span data-ttu-id="033ef-455">JD Edwards EnterpriseOne 未編輯的交易資料表 (Z 資料表)</span><span class="sxs-lookup"><span data-stu-id="033ef-455">JD Edwards EnterpriseOne unedited transaction tables (Z tables)</span></span>  
  
  <span data-ttu-id="033ef-456">這個配接器使用 JD Edwards EnterpriseOne ThinNet API 與 JD Edwards EnterpriseOne 應用程式通訊。</span><span class="sxs-lookup"><span data-stu-id="033ef-456">The adapter uses the JD Edwards EnterpriseOne ThinNet API to communicate with the JD Edwards EnterpriseOne application.</span></span> <span data-ttu-id="033ef-457">透過 ThinNet API，這個配接器可以在單一工作單元 (UOW) 中叫用一個主要商務功能 (MBF)。</span><span class="sxs-lookup"><span data-stu-id="033ef-457">By using the ThinNet API, the adapter can invoke one master business function (MBF) in a single unit of work (UOW).</span></span> <span data-ttu-id="033ef-458">當 MBF 失敗時，整個 UOW 都會失敗。</span><span class="sxs-lookup"><span data-stu-id="033ef-458">When an MBF fails, the whole UOW fails.</span></span> <span data-ttu-id="033ef-459">如此可防止部分更新。</span><span class="sxs-lookup"><span data-stu-id="033ef-459">This prevents partial updates.</span></span> <span data-ttu-id="033ef-460">JD Edwards EnterpriseOne 應用程式會處理基礎資料庫的資料、商務規則和通訊的驗證。</span><span class="sxs-lookup"><span data-stu-id="033ef-460">The validation of data, business rules, and communications to the underlying database are handled by the JD Edwards EnterpriseOne application.</span></span>  
  
#### <a name="jd-edwards-outbound-processing-framework"></a><span data-ttu-id="033ef-461">JD Edwards 輸出處理架構</span><span class="sxs-lookup"><span data-stu-id="033ef-461">JD Edwards Outbound Processing Framework</span></span>  
 <span data-ttu-id="033ef-462">在輸出程序中，當特定 MBF 在 JD Edwards EnterpriseOne 環境中執行時，便會啟動這個事件。</span><span class="sxs-lookup"><span data-stu-id="033ef-462">In the outbound process, the event starts when a specific MBF is executed in the JD Edwards EnterpriseOne environment.</span></span> <span data-ttu-id="033ef-463">MBF 會將事件的必要資訊寫入適當的介面資料表，然後通知子系統批次功能 (BF) 有此事件發生。</span><span class="sxs-lookup"><span data-stu-id="033ef-463">The MBF writes the required information for the event into the appropriate interface table and then notifies the subsystem batch function (BF) that an event occurred.</span></span> <span data-ttu-id="033ef-464">子系統 BF 接著會在子系統資料佇列中加入該事件的項目。</span><span class="sxs-lookup"><span data-stu-id="033ef-464">The subsystem BF then includes an entry about the event on the subsystem data queue.</span></span>  
  
 <span data-ttu-id="033ef-465">輸出子系統會擷取資料佇列項目，並查詢「資料匯出控制」資料表中是否有需要通知的外部處理序。</span><span class="sxs-lookup"><span data-stu-id="033ef-465">The outbound subsystem retrieves the data queue entry and looks in the Data Export Control table for the external processes to notify.</span></span> <span data-ttu-id="033ef-466">輸出子系統接著會呼叫 BizTalk Adapter for JD Edwards EnterpriseOne 接聽程式，並提供通知。</span><span class="sxs-lookup"><span data-stu-id="033ef-466">The outbound subsystem then calls the BizTalk Adapter for JD Edwards EnterpriseOne listener with notification.</span></span> <span data-ttu-id="033ef-467">接聽程式會將通知傳遞給產生器。</span><span class="sxs-lookup"><span data-stu-id="033ef-467">The listener passes the notification to the generator.</span></span> <span data-ttu-id="033ef-468">產生器接著會使用 JD Edwards EnterpriseOne ThinNet API 來擷取介面資料表中的適當資訊。</span><span class="sxs-lookup"><span data-stu-id="033ef-468">The generator then uses the JD Edwards EnterpriseOne ThinNet API to retrieve the appropriate information from the interface table.</span></span>  
  
### <a name="set-string-justification-in-jdearglist"></a><span data-ttu-id="033ef-469">在 Jdearglist 中設定字串左右對齊</span><span class="sxs-lookup"><span data-stu-id="033ef-469">Set string justification in Jdearglist</span></span>  
 <span data-ttu-id="033ef-470">若要將一些字串引數設定為靠右對齊和左側填補中 J.D.</span><span class="sxs-lookup"><span data-stu-id="033ef-470">To configure certain string arguments as right-justified and left padded in the J.D.</span></span> <span data-ttu-id="033ef-471">Edwards EnterpriseOne jdearglist.txt 檔案中，您必須知道您想要存取; 商務功能具體來說，您必須知道您想要呼叫的商務功能中的哪些欄位。</span><span class="sxs-lookup"><span data-stu-id="033ef-471">Edwards EnterpriseOne jdearglist.txt file, you must know what business function you want to access; specifically, you must know which fields in the business function you want to call.</span></span>  
  
 <span data-ttu-id="033ef-472">您必須先更新 jdearglist.txt，然後才能在協調流程中產生繫結 (結構描述)。</span><span class="sxs-lookup"><span data-stu-id="033ef-472">You must update the jdearglist.txt before you generate the bindings (schemas) in the orchestration.</span></span> <span data-ttu-id="033ef-473">更新 jdearglist.txt 檔案中 < 處理字串值 > 一節所述的指示。</span><span class="sxs-lookup"><span data-stu-id="033ef-473">The instructions for updating the jdearglist.txt file outlined in the "Handling String Values" section.</span></span>  
  
 <span data-ttu-id="033ef-474">如果您在記錄檔中收到 jdearglist.txt 警告訊息，其目的是通知您 jdearglist.txt 遺漏。</span><span class="sxs-lookup"><span data-stu-id="033ef-474">If you receive a jdearglist.txt warning message in the log, its purpose is to inform you that the jdearglist.txt is missing.</span></span> <span data-ttu-id="033ef-475">不過，如果您執行 SalesOrder 或 PurchaseOrder 商務功能，您必須擁有該檔案在您的路徑，或無法運作。</span><span class="sxs-lookup"><span data-stu-id="033ef-475">However, if you are running the SalesOrder or PurchaseOrder business function, you must have that file in your PATH or it does not work.</span></span>  
  
### <a name="understand-jdeinteropini"></a><span data-ttu-id="033ef-476">了解 jdeinterop.ini</span><span class="sxs-lookup"><span data-stu-id="033ef-476">Understand jdeinterop.ini</span></span>  
 <span data-ttu-id="033ef-477">Connector.jar 和 Kernel.jar 中的 JD Edwards EnterpriseOne 連接器類別會要求您使用名為 jdeinterop.ini 的組態檔。</span><span class="sxs-lookup"><span data-stu-id="033ef-477">The JD Edwards EnterpriseOne connector classes in Connector.jar and Kernel.jar require that you use a configuration file named jdeinterop.ini.</span></span> <span data-ttu-id="033ef-478">這個檔案是由 JD Edwards EnterpriseOne 軟體所定義，並使用其術語。</span><span class="sxs-lookup"><span data-stu-id="033ef-478">This file is defined by the JD Edwards EnterpriseOne software and uses its terminology.</span></span> <span data-ttu-id="033ef-479">如需這個檔案之用途和術語的詳細資訊，請參閱 "JD Edwards Interoperability Guide"。</span><span class="sxs-lookup"><span data-stu-id="033ef-479">For more information about the purpose and terminology of this file, see the JD Edwards Interoperability Guide.</span></span> <span data-ttu-id="033ef-480">沒有範例 jdeinterop.ini 檔案： Program Files\ Microsoft BizTalk Adapters for Enterprise applications\{4cdcdb2c J.D.</span><span class="sxs-lookup"><span data-stu-id="033ef-480">There is a sample jdeinterop.ini file in: Program Files\ Microsoft BizTalk Adapters for Enterprise Applications\ J.D.</span></span> <span data-ttu-id="033ef-481">Edwards EnterpriseOne(r) \config。</span><span class="sxs-lookup"><span data-stu-id="033ef-481">Edwards EnterpriseOne(r)\config.</span></span>  
  
 <span data-ttu-id="033ef-482">不建議您先手動編輯此檔案因為與它互動**傳輸屬性**傳送埠，例如在標示的欄位 對話方塊中 **< by Biztalk>\>**.</span><span class="sxs-lookup"><span data-stu-id="033ef-482">It is not recommended that you edit this file manually because it interacts with the **Transport Properties** dialog box for the send port -- for example those fields marked as **<configured by BizTalk\>**.</span></span>  
  
## <a name="peoplesoft-enterprise"></a><span data-ttu-id="033ef-483">PeopleSoft Enterprise</span><span class="sxs-lookup"><span data-stu-id="033ef-483">PeopleSoft Enterprise</span></span>  
<span data-ttu-id="033ef-484">本節包含有關使用 Microsoft BizTalk Adapter for PeopleSoft Enterprise 與 BizTalk Server 的重要資訊。</span><span class="sxs-lookup"><span data-stu-id="033ef-484">This section includes key information on using the Microsoft BizTalk Adapter for PeopleSoft Enterprise with BizTalk Server.</span></span>
  
### <a name="receive-handler-peoplesoft-requirements"></a><span data-ttu-id="033ef-485">接收處理常式 PeopleSoft 需求</span><span class="sxs-lookup"><span data-stu-id="033ef-485">Receive handler PeopleSoft requirements</span></span>  
 <span data-ttu-id="033ef-486">PeopleSoft Integration Broker 必須能夠與 BizTalk Server 通訊。</span><span class="sxs-lookup"><span data-stu-id="033ef-486">The PeopleSoft Integration Broker must be able to communicate with BizTalk Server.</span></span> <span data-ttu-id="033ef-487">現有的 PeopleSoft 環境中可能已發生下列情況，而且您可能會重複使用現有的節點；因此，除了向 PeopleSoft 系統管理員取得 HTTP 規格，您不必執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="033ef-487">The following could have already occurred in an existing PeopleSoft environment and you could reuse an existing node; therefore, you would not have to do anything except obtain the HTTP specifications from a PeopleSoft System Administrator.</span></span> <span data-ttu-id="033ef-488">如需詳細資訊，請參閱 PeopleSoft 文件。</span><span class="sxs-lookup"><span data-stu-id="033ef-488">For detailed information, see the PeopleSoft documentation.</span></span>  

<span data-ttu-id="033ef-489">下列步驟將概述在 PeopleSoft 中完成：</span><span class="sxs-lookup"><span data-stu-id="033ef-489">The following steps provide an overview to complete in PeopleSoft:</span></span>  
  
1.  <span data-ttu-id="033ef-490">設定訊息，並讓它成為透過應用程式的設計工具。</span><span class="sxs-lookup"><span data-stu-id="033ef-490">Set up the message, and make it active through the Application Designer.</span></span>  
  
2.  <span data-ttu-id="033ef-491">對 PeopleSoft integration.gateway.properties 檔案進行一次性變更。</span><span class="sxs-lookup"><span data-stu-id="033ef-491">Make a one-time change to the PeopleSoft integration.gateway.properties file.</span></span>  
  
3.  <span data-ttu-id="033ef-492">建立並設定閘道和節點，以啟用 HTTP:</span><span class="sxs-lookup"><span data-stu-id="033ef-492">Create and configure the gateway and nodes to activate HTTP:</span></span>
  
    -   <span data-ttu-id="033ef-493">這個節點必須使用一些觸發方法，例如 LOCATION_SYNC 機制。</span><span class="sxs-lookup"><span data-stu-id="033ef-493">The node must be using some triggering method, for example, the LOCATION_SYNC mechanism.</span></span>   
    -   <span data-ttu-id="033ef-494">這個節點必須使用 HTTP。</span><span class="sxs-lookup"><span data-stu-id="033ef-494">The node must use HTTP.</span></span>    
    -   <span data-ttu-id="033ef-495">這個節點必須指向傳送事件的目標主機和連接埠。</span><span class="sxs-lookup"><span data-stu-id="033ef-495">The node must point to the host and port to which you are sending the event.</span></span>  
  
### <a name="send-handler-peoplesoft-requirements"></a><span data-ttu-id="033ef-496">傳送處理常式 PeopleSoft 需求</span><span class="sxs-lookup"><span data-stu-id="033ef-496">Send handler PeopleSoft requirements</span></span>  
 <span data-ttu-id="033ef-497">BizTalk Adapter for PeopleSoft Enterprise 包含自訂元件介面 (CI) 可透過 Java API 的存取。</span><span class="sxs-lookup"><span data-stu-id="033ef-497">BizTalk Adapter for PeopleSoft Enterprise consists of a custom component interface (CI) that provides access through a Java API.</span></span> <span data-ttu-id="033ef-498">自訂 CI 物件**GET_CI_INFO**，部署在 PeopleSoft 系統提供的中繼資料資訊所需的 BizTalk Adapter for PeopleSoft Enterprise 使用 PeopleSoft 工具。</span><span class="sxs-lookup"><span data-stu-id="033ef-498">A custom CI object, **GET_CI_INFO**, is deployed in the PeopleSoft system using PeopleSoft Tools, to provide metadata information that is required by BizTalk Adapter for PeopleSoft Enterprise.</span></span> <span data-ttu-id="033ef-499">如需詳細資訊，請參閱 PeopleSoft 文件。</span><span class="sxs-lookup"><span data-stu-id="033ef-499">For more information, refer to PeopleSoft documentation.</span></span>  
  
 <span data-ttu-id="033ef-500">上載自訂元件介面的動作只發生一次。</span><span class="sxs-lookup"><span data-stu-id="033ef-500">Uploading of the custom component interface is a one-time occurrence.</span></span> <span data-ttu-id="033ef-501">GET_CI_INFO.pc 這個檔案隨附於產品，必須安裝在 PeopleSoft 系統中，才能使用配接器瀏覽 CI。</span><span class="sxs-lookup"><span data-stu-id="033ef-501">This file, GET_CI_INFO.pc, is provided with the product and must be installed in the PeopleSoft system before you can use the adapter to browse CIs.</span></span> <span data-ttu-id="033ef-502">您必須能夠存取 PeopleSoft 應用程式設計工具 中;不過，應用程式設計師不必是 BizTalk Server 電腦附近的任何位置。</span><span class="sxs-lookup"><span data-stu-id="033ef-502">You must have access to the PeopleSoft Application Designer; however, the Application Designer does not have to be anywhere near the BizTalk Server computer.</span></span> <span data-ttu-id="033ef-503">您可以使用應用程式設計工具來將自訂 CI 上傳到您瀏覽的 PeopleSoft 電腦。</span><span class="sxs-lookup"><span data-stu-id="033ef-503">You use the Application Designer to upload the custom CI into the PeopleSoft computer that you browse.</span></span>  
  
 <span data-ttu-id="033ef-504">您必須有 PeopleSoft 電腦的存取權，因為您必須設定環境變數 CLASSPATH (或設定資訊**傳輸屬性**視窗) 以指向 PeopleSoft PSJOA/psjoa.jar 檔案。</span><span class="sxs-lookup"><span data-stu-id="033ef-504">You must have access to the PeopleSoft computer because you must set the environment variable CLASSPATH (or set the information in the **Transport Properties** window) to point to the PeopleSoft PSJOA/psjoa.jar file.</span></span>  
  
### <a name="set-environment-variable-and-use-component-interface"></a><span data-ttu-id="033ef-505">設定環境變數，並使用元件介面</span><span class="sxs-lookup"><span data-stu-id="033ef-505">Set environment variable and use component interface</span></span>  
<span data-ttu-id="033ef-506">如需有關 PeopleSoft 的詳細資訊，請參閱 PeopleSoft 文件。</span><span class="sxs-lookup"><span data-stu-id="033ef-506">For more information about PeopleSoft, see the PeopleSoft documentation.</span></span>  
  
#### <a name="set-classpath-environment-variable"></a><span data-ttu-id="033ef-507">設定 ClassPath 環境變數</span><span class="sxs-lookup"><span data-stu-id="033ef-507">Set ClassPath environment variable</span></span>  

<span data-ttu-id="033ef-508">**更新 JAVA_HOME**</span><span class="sxs-lookup"><span data-stu-id="033ef-508">**Update JAVA_HOME**</span></span>    
  
 <span data-ttu-id="033ef-509">請將 JAVA_HOME 變數設定為指向 JDK 安裝，例如：</span><span class="sxs-lookup"><span data-stu-id="033ef-509">Set the JAVA_HOME variable to point to your JDK installation, for example:</span></span>  
  
```  
set JAVA_HOME=C:\j2sdk1.4.2_06  
```  
  
 <span data-ttu-id="033ef-510">**更新 CLASSPATH**</span><span class="sxs-lookup"><span data-stu-id="033ef-510">**Update CLASSPATH**</span></span>  
  
<span data-ttu-id="033ef-511">若要使用元件介面 (PeopleSoft 8) 您必須更新 CLASSPATH 來包含 PeopleSoft 元件介面 jar 檔案：</span><span class="sxs-lookup"><span data-stu-id="033ef-511">To use component interfaces (PeopleSoft 8 only) you must update your CLASSPATH to include the PeopleSoft component interface jar file:</span></span>
  
1. <span data-ttu-id="033ef-512">在 **控制台中**，開啟**系統**。</span><span class="sxs-lookup"><span data-stu-id="033ef-512">In **Control Panel**, open **System**.</span></span>  
  
2. <span data-ttu-id="033ef-513">在 **進階**索引標籤上，選取**環境變數**，然後選取**CLASSPATH**。</span><span class="sxs-lookup"><span data-stu-id="033ef-513">On the **Advanced** tab, select **Environment Variables**, and then select **CLASSPATH**.</span></span>  
  
3. <span data-ttu-id="033ef-514">加入的路徑。</span><span class="sxs-lookup"><span data-stu-id="033ef-514">Add the path.</span></span> <span data-ttu-id="033ef-515">例如，輸入：</span><span class="sxs-lookup"><span data-stu-id="033ef-515">For example, enter:</span></span>  
  
   ```  
   <PeopleSoft_Home>\web\PSJOA\psjoa.jar  
   ```  
  
   <span data-ttu-id="033ef-516">BizTalk Adapter for PeopleSoft Enterprise 需要 psjoa.jar 檔案。</span><span class="sxs-lookup"><span data-stu-id="033ef-516">BizTalk Adapter for PeopleSoft Enterprise requires the psjoa.jar file.</span></span> <span data-ttu-id="033ef-517">當您建立傳送埠時會執行這項作業。</span><span class="sxs-lookup"><span data-stu-id="033ef-517">This is performed when you create a send port.</span></span> <span data-ttu-id="033ef-518">如需詳細資訊，請參閱配接器文件中的 "Setting Transport Properties in PeopleSoft System"。</span><span class="sxs-lookup"><span data-stu-id="033ef-518">For more information, see "Setting Transport Properties in PeopleSoft System" in the adapter documentation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="033ef-519">僅在您的 PATH 中使用其中一個目錄，以確保 BizTalk Adapter for PeopleSoft Enterprise 選取正確的 DLL。</span><span class="sxs-lookup"><span data-stu-id="033ef-519">Only have one of these directories in your PATH to make sure that BizTalk Adapter for PeopleSoft Enterprise picks up the correct DLLs.</span></span> <span data-ttu-id="033ef-520">未能正確設定所需 PeopleSoft 版本的環境，可能會導致錯誤很難追蹤。</span><span class="sxs-lookup"><span data-stu-id="033ef-520">Failure to set up your environment correctly for the desired version of PeopleSoft could lead to errors that are difficult to trace.</span></span>  
  
#### <a name="use-component-interfaces"></a><span data-ttu-id="033ef-521">使用元件介面</span><span class="sxs-lookup"><span data-stu-id="033ef-521">Use component interfaces</span></span>  
  
<a name="BKMK_CustomCI"></a>   
##### <a name="upload-a-custom-ci-into-peoplesoft"></a><span data-ttu-id="033ef-522">將自訂 CI 上傳至 PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="033ef-522">Upload a Custom CI into PeopleSoft</span></span>  
 <span data-ttu-id="033ef-523">BizTalk Adapter for PeopleSoft Enterprise 需要修改 PeopleSoft 應用程式。</span><span class="sxs-lookup"><span data-stu-id="033ef-523">BizTalk Adapter for PeopleSoft Enterprise requires a modification to the PeopleSoft application.</span></span> <span data-ttu-id="033ef-524">若要使用元件介面，您必須將自訂元件介面 GET_CI_INFO 上傳至 PeopleSoft。</span><span class="sxs-lookup"><span data-stu-id="033ef-524">To use component interfaces, you must upload a custom component interface, GET_CI_INFO, into PeopleSoft.</span></span> <span data-ttu-id="033ef-525">您只需要在初始設定期間匯入 GET_CI_INFO，即可使用配接器。</span><span class="sxs-lookup"><span data-stu-id="033ef-525">You only have to import GET_CI_INFO during initial setup to use the adapter.</span></span> <span data-ttu-id="033ef-526">這個配接器使用 GET_CI_INFO 來取得 PeopleSoft 中其他現有元件介面的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="033ef-526">The adapter uses GET_CI_INFO to obtain information about other existing component interfaces in PeopleSoft.</span></span>  
  
 <span data-ttu-id="033ef-527">本節說明如何以手動方式匯入自訂元件介面，可讓您瀏覽 PeopleSoft 中的元件介面。</span><span class="sxs-lookup"><span data-stu-id="033ef-527">This section explains how to manually import a custom component interface that let you browse component interfaces in PeopleSoft.</span></span> <span data-ttu-id="033ef-528">請注意，不使用或修改任何屬性，它會安裝在元件介面的自訂方法。</span><span class="sxs-lookup"><span data-stu-id="033ef-528">Note that the custom methods do not use or modify any properties of the component interface that it is installed in.</span></span> <span data-ttu-id="033ef-529">若要匯入自訂元件介面，您可以使用下列其中一個方法：</span><span class="sxs-lookup"><span data-stu-id="033ef-529">To import the custom component interface, you can use one of the following methods:</span></span>  
  
- <span data-ttu-id="033ef-530">建立新的元件以匯入自訂方法。</span><span class="sxs-lookup"><span data-stu-id="033ef-530">Create a new component to import the custom methods.</span></span>  
  
- <span data-ttu-id="033ef-531">使用不含索引鍵的現有元件，例如 INSTALLATION_RS。</span><span class="sxs-lookup"><span data-stu-id="033ef-531">Use an existing component that contains no keys, for example, INSTALLATION_RS.</span></span>  
  
  <span data-ttu-id="033ef-532">簡單的元件介面不能包含索引鍵。</span><span class="sxs-lookup"><span data-stu-id="033ef-532">The simple component interface must not contain keys.</span></span> <span data-ttu-id="033ef-533">如果您不確定特定元件介面是否包含索引鍵，您可以使用 SQL 查詢工具執行這個簡單的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="033ef-533">If you are not sure whether a particular component interface contains keys, you can run this simple SQL statement using your SQL Query tool.</span></span> <span data-ttu-id="033ef-534">它可讓您的應用程式中所有不含索引鍵的元件介面清單。</span><span class="sxs-lookup"><span data-stu-id="033ef-534">It gives you a list of all the component interfaces in your application that have no keys.</span></span>  
  
```  
select distinct BCNAME  
from PSBCITEM bc1  
where not exists  
(select 1  
from PSBCITEM bc2  
where bc1.BCNAME = bc2.BCNAME  
and bc2.BCTYPE in (1, 2))  
```  
  
 <span data-ttu-id="033ef-535">您可以遵循 PeopleSoft 文件，建立唯一的簡單元件來儲存 BizTalk Adapter for PeopleSoft Enterprise 的自訂方法。</span><span class="sxs-lookup"><span data-stu-id="033ef-535">You can follow PeopleSoft documentation to create a unique simple component for storing BizTalk Adapter for PeopleSoft Enterprise custom methods.</span></span> <span data-ttu-id="033ef-536">您也可以複製其中一個已存在的元件介面，並使用它來儲存自訂方法。</span><span class="sxs-lookup"><span data-stu-id="033ef-536">You can also clone one of the pre-existing component interfaces and use it to store the custom methods.</span></span>  
  
 <span data-ttu-id="033ef-537">若要確認您的 GET_CI_INFO 不含索引鍵，請執行 PeopleTools Application Designer 元件介面測試工具。</span><span class="sxs-lookup"><span data-stu-id="033ef-537">To verify that your GET_CI_INFO has no keys, run the PeopleTools Application Designer Component Interface Test tool.</span></span>  
  
<a name="BKMK_NewCom"></a>   
##### <a name="create-a-new-component-interface"></a><span data-ttu-id="033ef-538">建立新的元件介面</span><span class="sxs-lookup"><span data-stu-id="033ef-538">Create a new component interface</span></span>  
 <span data-ttu-id="033ef-539">請遵循下列步驟來建立新的元件介面，使用 PeopleSoft 應用程式設計工具 中：</span><span class="sxs-lookup"><span data-stu-id="033ef-539">Follow these steps to create a new component interface using the PeopleSoft, Application Designer:</span></span>
  
1. <span data-ttu-id="033ef-540">開啟**PeopleSoft 應用程式設計工具**。</span><span class="sxs-lookup"><span data-stu-id="033ef-540">Open the **PeopleSoft Application Designer**.</span></span>  
  
2. <span data-ttu-id="033ef-541">輸入三層式連接類型，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="033ef-541">Enter a three-tier connection type, and then click **OK**.</span></span> <span data-ttu-id="033ef-542">例如，從清單中選取 [Application Server]。</span><span class="sxs-lookup"><span data-stu-id="033ef-542">For example, select Application Server from the list.</span></span>  
  
3. <span data-ttu-id="033ef-543">在 應用程式設計工具中，在**檔案**功能表上，選取**新增**。</span><span class="sxs-lookup"><span data-stu-id="033ef-543">In the Application Designer, on the **File** menu, select **New**.</span></span>  
  
4. <span data-ttu-id="033ef-544">在 **新增**對話方塊中，選取**元件介面**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="033ef-544">In the **New** dialog box, select **Component Interface**, and then click **OK**.</span></span>  
  
5. <span data-ttu-id="033ef-545">按一下 [選取]。</span><span class="sxs-lookup"><span data-stu-id="033ef-545">Click **Select**.</span></span>  
  
6. <span data-ttu-id="033ef-546">從所有元件清單中選取任何簡單的元件。</span><span class="sxs-lookup"><span data-stu-id="033ef-546">From the list of all components, select any simple component.</span></span> <span data-ttu-id="033ef-547">例如，選取 INSTALLATION_RS 或您建立的新 PeopleSoft 元件。</span><span class="sxs-lookup"><span data-stu-id="033ef-547">For example, select INSTALLATION_RS, or a new PeopleSoft component that you created.</span></span>  
  
   <span data-ttu-id="033ef-548">自訂方法不會使用或修改安裝所在之元件介面的任何屬性。</span><span class="sxs-lookup"><span data-stu-id="033ef-548">The custom methods do not use or modify any properties of the component interface that it is installed in.</span></span>  
  
   <span data-ttu-id="033ef-549">這個簡單的元件介面不能包含索引鍵。</span><span class="sxs-lookup"><span data-stu-id="033ef-549">This simple component interface must not contain keys.</span></span> <span data-ttu-id="033ef-550">如果您不確定特定元件介面是否包含索引鍵，您可以使用 SQL 查詢工具執行這個簡單的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="033ef-550">If you are not sure whether a particular component interface contains keys, you can run this simple SQL statement using your SQL Query tool.</span></span> <span data-ttu-id="033ef-551">它可讓您的應用程式中所有不含索引鍵的元件介面清單：</span><span class="sxs-lookup"><span data-stu-id="033ef-551">It gives you a list of all the component interfaces in your application that have no keys:</span></span>  
  
```  
select distinct BCNAME from PSBCITEM bc1 where not exists (select 1 from PSBCITEM bc2 where bc1.BCNAME = bc2.BCNAME and bc2.BCTYPE in (1, 2))  
```  
  
> [!NOTE]
>  <span data-ttu-id="033ef-552">您也可以遵循 PeopleSoft 文件，建立唯一的簡單元件來儲存 BizTalk Adapter for PeopleSoft Enterprise 的自訂方法。</span><span class="sxs-lookup"><span data-stu-id="033ef-552">You can also follow PeopleSoft documentation to create a unique simple component for storing custom methods for BizTalk Adapter for PeopleSoft Enterprise.</span></span>  
  
 <span data-ttu-id="033ef-553">若要確認您的 GET_CI_INFO 不含索引鍵，請執行 PeopleTools Application Designer 元件介面測試工具。</span><span class="sxs-lookup"><span data-stu-id="033ef-553">To verify that your GET_CI_INFO has no keys, run the PeopleTools Application Designer Component Interface Test tool.</span></span>  
  
##### <a name="check-component-interface"></a><span data-ttu-id="033ef-554">檢查元件介面</span><span class="sxs-lookup"><span data-stu-id="033ef-554">Check component interface</span></span>  
 <span data-ttu-id="033ef-555">您已完成將 Microsoft BizTalk Adapter for PeopleSoft GET_CI_INFO 上傳至 PeopleSoft 系統。</span><span class="sxs-lookup"><span data-stu-id="033ef-555">You have completed uploading the Microsoft BizTalk Adapter for PeopleSoft GET_CI_INFO into your PeopleSoft System.</span></span> <span data-ttu-id="033ef-556">GET_CI_INFO 是使用者定義的自訂元件介面，</span><span class="sxs-lookup"><span data-stu-id="033ef-556">The GET_CI_INFO is a user-defined custom component interface.</span></span> <span data-ttu-id="033ef-557">它包含使用者定義的方法。</span><span class="sxs-lookup"><span data-stu-id="033ef-557">It contains user-defined methods.</span></span> <span data-ttu-id="033ef-558">GET_CI_INFO 元件介面可讓您使用 Microsoft Adapter 精靈瀏覽 PeopleSoft 系統中的元件介面。</span><span class="sxs-lookup"><span data-stu-id="033ef-558">The GET_CI_INFO component interface lets you browse component interfaces in your PeopleSoft system using the Microsoft Adapter Wizard.</span></span> <span data-ttu-id="033ef-559">您可以尋找並展開 GET_CI_INFO，以檢視其使用者定義的方法。</span><span class="sxs-lookup"><span data-stu-id="033ef-559">You can locate and expand GET_CI_INFO to view its user-defined methods.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="033ef-560">如需有關使用者定義方法的詳細資訊，請參閱配接器文件中的 「 PeopleSoft:: 元件介面使用者定義方法 」。</span><span class="sxs-lookup"><span data-stu-id="033ef-560">For more information about user-defined methods, see "PeopleSoft: Component Interface User-Defined Methods" in the adapter documentation.</span></span>  
  
##### <a name="set-the-component-interface-security"></a><span data-ttu-id="033ef-561">設定元件介面安全性</span><span class="sxs-lookup"><span data-stu-id="033ef-561">Set the component interface security</span></span>  
 <span data-ttu-id="033ef-562">在 PeopleSoft 上安裝自訂 GET_CI_INFO PeopleSoft 元件介面之後，設定的安全性設定**GetCINamespace**， **GetDetails**，和**GetCollections**BizTalk adapter for PeopleSoft Enterprise 的方法。</span><span class="sxs-lookup"><span data-stu-id="033ef-562">After you install the custom GET_CI_INFO PeopleSoft component interface on PeopleSoft, set the security settings for **GetCINamespace**, **GetDetails**, and **GetCollections** methods for BizTalk Adapter for PeopleSoft Enterprise.</span></span> <span data-ttu-id="033ef-563">這是建立自訂元件或使用者定義方法時的標準作法。</span><span class="sxs-lookup"><span data-stu-id="033ef-563">This is standard practice when you create custom components or user-defined methods.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="033ef-564">下列程序說明如何在所有支援的模式下，為所有支援的 PeopleSoft 版本設定安全性。</span><span class="sxs-lookup"><span data-stu-id="033ef-564">The following procedure describes how to configure security for all supported releases of PeopleSoft in all supported modes.</span></span>  
>   
>  <span data-ttu-id="033ef-565">設定元件介面的安全性</span><span class="sxs-lookup"><span data-stu-id="033ef-565">To configure security for the component interface</span></span>  
  
1.  <span data-ttu-id="033ef-566">指向**PeopleTools**，指向**安全性**，指向**Permissions & Roles**，然後選取**Permission Lists**。</span><span class="sxs-lookup"><span data-stu-id="033ef-566">Point to **PeopleTools**, point to **Security**, point to **Permissions & Roles**, and then select **Permission Lists**.</span></span>  
  
2.  <span data-ttu-id="033ef-567">在 [ **Maintain Security** ] 視窗中，按一下**搜尋**，選取相關**權限清單**，然後按一下適當的清單超連結。</span><span class="sxs-lookup"><span data-stu-id="033ef-567">In the **Maintain Security** window, click **Search**, select the relevant **Permission List**, and then click the appropriate list hyperlink.</span></span>  
  
3.  <span data-ttu-id="033ef-568">在**權限清單**右邊的窗格中按一下向右箭號旁**登入次數**索引標籤，顯示**元件介面** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="033ef-568">In the **Permission List** pane on the right, click the right arrow next to the **Sign-on Times** tab to display the **Component Interfaces** tab.</span></span>  
  
4.  <span data-ttu-id="033ef-569">按一下 [**元件介面**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="033ef-569">Click the **Component Interfaces** tab.</span></span>  
  
5.  <span data-ttu-id="033ef-570">按一下加號 （+），以加入新的資料列即可**元件介面**清單。</span><span class="sxs-lookup"><span data-stu-id="033ef-570">Click the plus sign (+) to add a new row to the **Component Interfaces** list.</span></span>  
  
6.  <span data-ttu-id="033ef-571">選取  **GET_CI_INFO**元件介面，然後按一下**編輯**。</span><span class="sxs-lookup"><span data-stu-id="033ef-571">Select the **GET_CI_INFO** component interface, and then click **Edit**.</span></span>  
  
7.  <span data-ttu-id="033ef-572">將方法設定為**完整存取權**，按一下 **（全部） 的完整存取**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="033ef-572">To set the methods to **Full Access**, click **Full Access (All)**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="033ef-573">捲動至底部**Component Interfaces**視窗中，然後再按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="033ef-573">Scroll to the bottom of the **Component Interfaces** window, and then click **Save**.</span></span>  
  
##### <a name="test-the-component-interface"></a><span data-ttu-id="033ef-574">測試元件介面</span><span class="sxs-lookup"><span data-stu-id="033ef-574">Test the component interface</span></span>  
 <span data-ttu-id="033ef-575">您已完成設定 BizTalk Adapter for PeopleSoft Enterprise 所提供之 GET_CI_INFO 元件介面的安全性。</span><span class="sxs-lookup"><span data-stu-id="033ef-575">You have finished configuring security for the GET_CI_INFO component interface delivered with BizTalk Adapter for PeopleSoft Enterprise.</span></span> <span data-ttu-id="033ef-576">您的 PeopleSoft 元件介面已就緒，可供您瀏覽 PeopleSoft 元件介面。</span><span class="sxs-lookup"><span data-stu-id="033ef-576">Your PeopleSoft component interface is ready, and you can browse PeopleSoft component interfaces.</span></span>  
  
 <span data-ttu-id="033ef-577">請執行下列步驟，在 Application Designer 中測試元件介面。</span><span class="sxs-lookup"><span data-stu-id="033ef-577">Follow these steps to test the component interface in the Application Designer.</span></span>  
  
 <span data-ttu-id="033ef-578">若要測試元件介面</span><span class="sxs-lookup"><span data-stu-id="033ef-578">To test the component interface</span></span>  
  
1.  <span data-ttu-id="033ef-579">開始**PeopleSoft 應用程式設計工具**。</span><span class="sxs-lookup"><span data-stu-id="033ef-579">Start the **PeopleSoft Application Designer**.</span></span>  
  
2.  <span data-ttu-id="033ef-580">在 **檔案**功能表上，指向**開啟**，然後選取**定義 = Component Interface**。</span><span class="sxs-lookup"><span data-stu-id="033ef-580">On the **File** menu, point to **Open**, and then select **Definition = Component Interface**.</span></span>  
  
3.  <span data-ttu-id="033ef-581">從元件介面清單中，選取**GET_CI_INFO CI**。</span><span class="sxs-lookup"><span data-stu-id="033ef-581">From the list of component interfaces, select **GET_CI_INFO CI**.</span></span>  
  
4.  <span data-ttu-id="033ef-582">開啟 GET_CI_INFO 之後，請以滑鼠右鍵按一下您的元件介面定義右窗格中的任何位置，然後按**測試元件介面**。</span><span class="sxs-lookup"><span data-stu-id="033ef-582">After you open GET_CI_INFO, right-click anywhere in the right pane of your component interface definition, and then select **Test Component Interface**.</span></span>  
  
<span data-ttu-id="033ef-583">**Component Interface Tester**視窗隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="033ef-583">The **Component Interface Tester** window opens.</span></span> <span data-ttu-id="033ef-584">並且應該不會列出任何索引鍵。</span><span class="sxs-lookup"><span data-stu-id="033ef-584">There should be no keys listed.</span></span> <span data-ttu-id="033ef-585">如果您的 GET_CI_INFO 包含索引鍵，或如果沒有選取範圍的另一個選項，返回 應用程式設計工具中，並消除 GET_CI_INFO 中的所有索引鍵。</span><span class="sxs-lookup"><span data-stu-id="033ef-585">If your GET_CI_INFO contains keys, or if there is another option for selection, return to the Application Designer, and eliminate all keys from GET_CI_INFO.</span></span>  
  
## <a name="install-steps"></a><span data-ttu-id="033ef-586">安裝步驟</span><span class="sxs-lookup"><span data-stu-id="033ef-586">Install steps</span></span>
 <span data-ttu-id="033ef-587">在安裝之前，可確定 BizTalk Server，並已安裝配接器的所有軟體必要條件。</span><span class="sxs-lookup"><span data-stu-id="033ef-587">Before you install, be sure BizTalk Server and all the software prerequisites for the adapters are installed.</span></span> <span data-ttu-id="033ef-588">建議您關閉所有應用程式，再執行安裝程式。</span><span class="sxs-lookup"><span data-stu-id="033ef-588">It is recommended that you close all applications before running Setup.</span></span>  
  
1.  <span data-ttu-id="033ef-589">執行 BizTalk Server **Setup.exe**，選取**安裝 Microsoft BizTalk Adapters**，然後選取**安裝 Microsoft BizTalk Adapters for Enterprise Applications**。</span><span class="sxs-lookup"><span data-stu-id="033ef-589">Run the BizTalk Server **Setup.exe**, select **Install Microsoft BizTalk Adapters**, and select **Install Microsoft BizTalk Adapters for Enterprise Applications**.</span></span>  
  
    > [!NOTE]
    >  - <span data-ttu-id="033ef-590">您也可以執行無訊息安裝中使用下列命令： msiexec /i < msi\> /qn /l\* < 記錄檔\>，其中 < 記錄檔\>是選擇性的但適合安裝失敗。</span><span class="sxs-lookup"><span data-stu-id="033ef-590">You can also run a silent installation using the following command: msiexec /i <msi\> /qn /l\* <logfile\> -- where <logfile\> is optional, but is useful in the event of a failed installation.</span></span>  
    >  - <span data-ttu-id="033ef-591">安裝會更新 PATH 環境變數。</span><span class="sxs-lookup"><span data-stu-id="033ef-591">The installation updates the PATH environment variable.</span></span> <span data-ttu-id="033ef-592">若要確定您使用的變數正確，請關閉安裝命令視窗以更新變數。</span><span class="sxs-lookup"><span data-stu-id="033ef-592">To make sure that you are using the correct variables, close the installation command window to update your variables.</span></span>  
  
2.  <span data-ttu-id="033ef-593">接受**授權合約**，然後選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="033ef-593">Accept the **License Agreement**, and select **Next**.</span></span>
  
3.  <span data-ttu-id="033ef-594">輸入您**客戶資訊**，然後選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="033ef-594">Enter your **Customer Information**, and select **Next**.</span></span>  
  
4.  <span data-ttu-id="033ef-595">選取  **Complete**或是**自訂**安裝：</span><span class="sxs-lookup"><span data-stu-id="033ef-595">Select a **Complete** or **Custom** installation:</span></span> 
  
    -   <span data-ttu-id="033ef-596">**完成**： 安裝 Microsoft BizTalk Adapters for Enterprise Applications，所有的程式功能，而且用於開發和執行階段。</span><span class="sxs-lookup"><span data-stu-id="033ef-596">**Complete**: Installs all the Microsoft BizTalk Adapters for Enterprise Applications, all the program features, and is used for development and run time.</span></span>  
  
    -   <span data-ttu-id="033ef-597">**自訂**： 您選擇的介面卡和功能，您要安裝，並安裝它們。</span><span class="sxs-lookup"><span data-stu-id="033ef-597">**Custom**: You choose the adapters and features that you want to install, and where they are installed.</span></span>  
  
    <span data-ttu-id="033ef-598">若要設定目的地，請選取**瀏覽**，並設定安裝路徑。</span><span class="sxs-lookup"><span data-stu-id="033ef-598">To set the destination, select **Browse**, and set the installation path.</span></span>  
  
    <span data-ttu-id="033ef-599">選取 [**下一步]** 以繼續。</span><span class="sxs-lookup"><span data-stu-id="033ef-599">Select **Next** to continue.</span></span>  
  
5. <span data-ttu-id="033ef-600">**安裝**，然後選取**完成**完成時。</span><span class="sxs-lookup"><span data-stu-id="033ef-600">**Install**, and select **Finish** when complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="033ef-601">在安裝期間，您可能會遇到下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="033ef-601">You may encounter the following error during installation:</span></span>  
>   
>  `Error 1609. An error occurred while applying security settings. CREATOR OWNER is not a valid user or group`  
>   
>  <span data-ttu-id="033ef-602">若要解決這個錯誤，執行下列作業，並再次執行安裝程式：</span><span class="sxs-lookup"><span data-stu-id="033ef-602">To work around this error, do the following, and run the installation again:</span></span>  
>   
>  1. <span data-ttu-id="033ef-603">開啟命令提示字元</span><span class="sxs-lookup"><span data-stu-id="033ef-603">Open a command prompt</span></span>
>  2. <span data-ttu-id="033ef-604">類型： `net user "CREATOR OWNER" /add`。</span><span class="sxs-lookup"><span data-stu-id="033ef-604">Type: `net user "CREATOR OWNER" /add`.</span></span> <span data-ttu-id="033ef-605">這會建立新的使用者 CREATOR owner。</span><span class="sxs-lookup"><span data-stu-id="033ef-605">This creates a new user called CREATOR OWNER.</span></span>
>  3. <span data-ttu-id="033ef-606">類型： `net localgroup Users /add`。</span><span class="sxs-lookup"><span data-stu-id="033ef-606">Type: `net localgroup Users /add`.</span></span> <span data-ttu-id="033ef-607">這會建立名為使用者的新群組。</span><span class="sxs-lookup"><span data-stu-id="033ef-607">This creates a new group called Users.</span></span>
  
<span data-ttu-id="033ef-608">若要新增的配接器至 BizTalk Server，請參閱 「 新增配接器給 BizTalk 系統管理員 」 在本主題中。</span><span class="sxs-lookup"><span data-stu-id="033ef-608">To add the adapters to BizTalk Server, see "Add adapters to BizTalk Admin" in this topic.</span></span>

## <a name="add-adapters-to-biztalk-admin"></a><span data-ttu-id="033ef-609">將配接器新增至 BizTalk 系統管理員</span><span class="sxs-lookup"><span data-stu-id="033ef-609">Add adapters to BizTalk Admin</span></span>
  
> [!NOTE]
>  <span data-ttu-id="033ef-610">如果您在多重電腦環境 （僅限執行階段的某部電腦上，安裝和管理僅限工具安裝在另一部電腦上） 中安裝 BizTalk，您應該安裝 for Enterprise Applications 的 BizTalk 配接器在電腦上。</span><span class="sxs-lookup"><span data-stu-id="033ef-610">If you install BizTalk in a multicomputer environment (runtime-only installation on one computer, and an administration tools-only installation on another computer),  you should install the BizTalk Adapters for Enterprise Applications on both the computers.</span></span>  
  
1.  <span data-ttu-id="033ef-611">開啟 BizTalk Server 管理主控台中，展開**Microsoft BizTalk Server**，然後展開**平台設定**。</span><span class="sxs-lookup"><span data-stu-id="033ef-611">Open the BizTalk Server Administration Console, expand **Microsoft BizTalk Server**, and then expand **Platform Settings**.</span></span>  
  
2.  <span data-ttu-id="033ef-612">以滑鼠右鍵按一下**配接器**，選取**新增**，然後選取**配接器**。</span><span class="sxs-lookup"><span data-stu-id="033ef-612">Right-click **Adapters**, select **New**, and then select **Adapter**.</span></span>  
  
3.  <span data-ttu-id="033ef-613">輸入名稱，例如**PeopleSoft**。</span><span class="sxs-lookup"><span data-stu-id="033ef-613">Enter a name, such as **PeopleSoft**.</span></span>  
  
4.  <span data-ttu-id="033ef-614">選取您從輸入的名稱**配接器**清單，然後選取**確定**。</span><span class="sxs-lookup"><span data-stu-id="033ef-614">Select the name you entered from the **Adapter** list, and select **OK**.</span></span>  
   
## <a name="post-install---jd-edwards-oneworld"></a><span data-ttu-id="033ef-615">後續安裝-JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="033ef-615">Post-install - JD Edwards OneWorld</span></span>  
 <span data-ttu-id="033ef-616">Microsoft BizTalk Adapter for JD Edwards OneWorld 介面支援的資料庫和伺服器系統連接到 Microsoft BizTalk Server 傳輸配接器所組成。</span><span class="sxs-lookup"><span data-stu-id="033ef-616">Microsoft BizTalk Adapter for JD Edwards OneWorld consists of a transmit adapter that interfaces supported databases and server systems to Microsoft BizTalk Server.</span></span> <span data-ttu-id="033ef-617">傳輸配接器可讓您叫用從 BizTalk Server 的伺服器系統的呼叫。</span><span class="sxs-lookup"><span data-stu-id="033ef-617">The transmit adapter enables you to invoke a server system's call from BizTalk Server.</span></span> <span data-ttu-id="033ef-618">傳輸配接器 (BizTalk Server 管理傳送處理常式) 組態會指定 SQL 資料庫的位置。</span><span class="sxs-lookup"><span data-stu-id="033ef-618">The transmit adapter (the BizTalk Server Administration Send Handler) configuration specifies the location of the SQL database.</span></span>  
  
 <span data-ttu-id="033ef-619">請參閱有關如何使用 BizTalk Adapter for JD Edwards OneWorld 以及其模型與 BizTalk Server 模型之間的對應資訊的配接器文件。</span><span class="sxs-lookup"><span data-stu-id="033ef-619">See the adapter documentation for information about how to use BizTalk Adapter for JD Edwards OneWorld and about the mapping between its model and the BizTalk Server model.</span></span>  
  
### <a name="single-sign-on"></a><span data-ttu-id="033ef-620">單一登入 (SSO)</span><span class="sxs-lookup"><span data-stu-id="033ef-620">Single Sign-On</span></span>  
 <span data-ttu-id="033ef-621">BizTalk Adapter for JD Edwards OneWorld 提供支援的企業單一登入 (SSO)。</span><span class="sxs-lookup"><span data-stu-id="033ef-621">BizTalk Adapter for JD Edwards OneWorld provides support for Enterprise Single Sign-On (SSO).</span></span> <span data-ttu-id="033ef-622">如果您選取使用中的 SSO**傳輸屬性**頁面上，認證會使用 SSO 認證資料庫中的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="033ef-622">If you select to use SSO in the **Transport Properties** page, the credentials for the affiliate application in the SSO Credentials database are used.</span></span> <span data-ttu-id="033ef-623">分支機構應用程式代表需要認證的後端應用程式。</span><span class="sxs-lookup"><span data-stu-id="033ef-623">An affiliate application represents an application—a back-end that requires credentials.</span></span>  
  
### <a name="installed-components"></a><span data-ttu-id="033ef-624">已安裝的元件</span><span class="sxs-lookup"><span data-stu-id="033ef-624">Installed components</span></span>  

* <span data-ttu-id="033ef-625">配接器安裝會安裝並註冊在全域組件快取 (GAC) 中的下列元件。</span><span class="sxs-lookup"><span data-stu-id="033ef-625">The adapter installation installs and registers the following components in the global assembly cache (GAC).</span></span> <span data-ttu-id="033ef-626">您可以在總管中開啟組件 資料夾，以確認註冊 (< %WINDIR%> \assembly)，或使用`gacutil /l`從 Visual Studio 命令提示字元：</span><span class="sxs-lookup"><span data-stu-id="033ef-626">You can verify the registration by opening the assembly folder in your explorer (<%WINDIR%>\assembly), or use the `gacutil /l` from the Visual Studio command prompt:</span></span>

    -   <span data-ttu-id="033ef-627">Microsoft.BizTalk.Adapters.BizUtil.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-627">Microsoft.BizTalk.Adapters.BizUtil.dll</span></span>    
    -   <span data-ttu-id="033ef-628">Microsoft.BizTalk.Adapters.JDEProperties.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-628">Microsoft.BizTalk.Adapters.JDEProperties.dll</span></span>    
    -   <span data-ttu-id="033ef-629">Microsoft.BizTalk.Adapters.CoreManagement.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-629">Microsoft.BizTalk.Adapters.CoreManagement.dll</span></span>    
    -   <span data-ttu-id="033ef-630">Microsoft.BizTalk.Adapters.CoreReceiver.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-630">Microsoft.BizTalk.Adapters.CoreReceiver.dll</span></span>    
    -   <span data-ttu-id="033ef-631">Microsoft.BizTalk.Adapters.CoreTransmitter.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-631">Microsoft.BizTalk.Adapters.CoreTransmitter.dll</span></span>  

  
* <span data-ttu-id="033ef-632">btsTask.exe 會安裝和部署`Microsoft.BizTalk.Adapters.JDEProperties.dll`至 GAC 的檔案。</span><span class="sxs-lookup"><span data-stu-id="033ef-632">btsTask.exe installs and deploys the `Microsoft.BizTalk.Adapters.JDEProperties.dll` file to the GAC.</span></span> <span data-ttu-id="033ef-633">BizTalk Server 部署記錄結果位於*\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\jdeDeploy.html*並**jdeDeploy.xml**。</span><span class="sxs-lookup"><span data-stu-id="033ef-633">The BizTalk Server deployment log results are in *\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\jdeDeploy.html* and **jdeDeploy.xml**.</span></span>
  
* <span data-ttu-id="033ef-634">配接器專屬檔案會安裝在*Program Files*並*Program Files\Common Files*。</span><span class="sxs-lookup"><span data-stu-id="033ef-634">Adapter-specific files are installed in *Program Files* and *Program Files\Common Files*.</span></span>  
  
* <span data-ttu-id="033ef-635">`sdk\`安裝在*Program Files\Microsoft BizTalk Adapters for Enterprise applications\{4cdcdb2c J.D.Edwards OneWorld(r)*。</span><span class="sxs-lookup"><span data-stu-id="033ef-635">The `sdk\` is installed in *Program Files\Microsoft BizTalk Adapters for Enterprise Applications\ J.D. Edwards OneWorld(r)*.</span></span>
  
* <span data-ttu-id="033ef-636">* 程式 Files\Microsoft BizTalk Adapters for Enterprise Applications\JD Edwards OneWorld(r)\*包含下列檔案：</span><span class="sxs-lookup"><span data-stu-id="033ef-636">*Program Files\Microsoft BizTalk Adapters for Enterprise Applications\JD Edwards OneWorld(r)\* contains the following files:</span></span>  
  
    -   <span data-ttu-id="033ef-637">classes\JDEJAccess.jar</span><span class="sxs-lookup"><span data-stu-id="033ef-637">classes\JDEJAccess.jar</span></span>    
    -   <span data-ttu-id="033ef-638">Config\ J.D.</span><span class="sxs-lookup"><span data-stu-id="033ef-638">Config\ J.D.</span></span> <span data-ttu-id="033ef-639">Edwards OneWorld(r) \BTSREL.exe</span><span class="sxs-lookup"><span data-stu-id="033ef-639">Edwards OneWorld(r) \BTSREL.exe</span></span>    
    -   <span data-ttu-id="033ef-640">Config\ J.D.</span><span class="sxs-lookup"><span data-stu-id="033ef-640">Config\ J.D.</span></span> <span data-ttu-id="033ef-641">Edwards OneWorld(r) \jdearglist.txt</span><span class="sxs-lookup"><span data-stu-id="033ef-641">Edwards OneWorld(r) \jdearglist.txt</span></span>    
    -   <span data-ttu-id="033ef-642">Config\ J.D.</span><span class="sxs-lookup"><span data-stu-id="033ef-642">Config\ J.D.</span></span> <span data-ttu-id="033ef-643">Edwards OneWorld(r) \jdeinterop.ini</span><span class="sxs-lookup"><span data-stu-id="033ef-643">Edwards OneWorld(r) \jdeinterop.ini</span></span>  
  
* <span data-ttu-id="033ef-644">* 程式 Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\Bin\*包含下列檔案：</span><span class="sxs-lookup"><span data-stu-id="033ef-644">*Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\Bin\* contains the following files:</span></span>  
  
    -   <span data-ttu-id="033ef-645">Microsoft.BizTalk.Adapters.JDEProperties.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-645">Microsoft.BizTalk.Adapters.JDEProperties.dll</span></span>    
    -   <span data-ttu-id="033ef-646">jdecba.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-646">jdecba.dll</span></span>  
  
## <a name="post-install---jd-edwards-enterpriseone"></a><span data-ttu-id="033ef-647">後續安裝-JD Edwards EnterpriseOne</span><span class="sxs-lookup"><span data-stu-id="033ef-647">Post-install - JD Edwards EnterpriseOne</span></span>  
 <span data-ttu-id="033ef-648">Microsoft BizTalk Adapter for JD Edwards EnterpriseOne 包含傳輸配接器，可支援的資料庫與伺服器系統連接到 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="033ef-648">Microsoft BizTalk Adapter for JD Edwards EnterpriseOne contains a transmit adapter that interfaces with supported databases and server systems to BizTalk Server.</span></span> <span data-ttu-id="033ef-649">傳輸配接器可讓您叫用從 BizTalk Server 的伺服器系統的呼叫。</span><span class="sxs-lookup"><span data-stu-id="033ef-649">The transmit adapter enables you to invoke a server system’s call from BizTalk Server.</span></span>  
  
 <span data-ttu-id="033ef-650">BizTalk Adapter for JD Edwards EnterpriseOne 提供支援的企業單一登入 (SSO)。</span><span class="sxs-lookup"><span data-stu-id="033ef-650">BizTalk Adapter for JD Edwards EnterpriseOne provides support for Enterprise Single Sign-On (SSO).</span></span> <span data-ttu-id="033ef-651">如果您選取使用中的 SSO**傳輸屬性**頁面上，認證會使用 SSO 認證資料庫中的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="033ef-651">If you select to use SSO in the **Transport Properties** page, the credentials for the affiliate application in the SSO Credentials database are used.</span></span> <span data-ttu-id="033ef-652">分支機構應用程式代表需要認證的後端應用程式。</span><span class="sxs-lookup"><span data-stu-id="033ef-652">An affiliate application represents an application—a back-end that requires credentials.</span></span>  
  
### <a name="installed-components"></a><span data-ttu-id="033ef-653">已安裝的元件</span><span class="sxs-lookup"><span data-stu-id="033ef-653">Installed components</span></span>  
* <span data-ttu-id="033ef-654">配接器安裝會安裝並註冊在全域組件快取 (GAC) 中的下列元件。</span><span class="sxs-lookup"><span data-stu-id="033ef-654">The adapter installation installs and registers the following components in the global assembly cache (GAC).</span></span> <span data-ttu-id="033ef-655">您可以在總管中開啟組件 資料夾，以確認註冊 (< %WINDIR%> \assembly)，或使用`gacutil /l`從 Visual Studio 命令提示字元：</span><span class="sxs-lookup"><span data-stu-id="033ef-655">You can verify the registration by opening the assembly folder in your explorer (<%WINDIR%>\assembly), or use the `gacutil /l` from the Visual Studio command prompt:</span></span>
  
    -   <span data-ttu-id="033ef-656">Microsoft.BizTalk.Adapters.BizUtil.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-656">Microsoft.BizTalk.Adapters.BizUtil.dll</span></span>    
    -   <span data-ttu-id="033ef-657">Microsoft.BizTalk.Adapters.JDEProperties.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-657">Microsoft.BizTalk.Adapters.JDEProperties.dll</span></span>    
    -   <span data-ttu-id="033ef-658">Microsoft.BizTalk.Adapters.CoreManagement.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-658">Microsoft.BizTalk.Adapters.CoreManagement.dll</span></span>    
    -   <span data-ttu-id="033ef-659">Microsoft.BizTalk.Adapters.CoreReceiver.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-659">Microsoft.BizTalk.Adapters.CoreReceiver.dll</span></span>    
    -   <span data-ttu-id="033ef-660">Microsoft.BizTalk.Adapters.CoreTransmitter.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-660">Microsoft.BizTalk.Adapters.CoreTransmitter.dll</span></span>    

* <span data-ttu-id="033ef-661">配接器專屬檔案會安裝在*Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\Bin*資料夾。</span><span class="sxs-lookup"><span data-stu-id="033ef-661">The adapter-specific files are installed in the *Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\Bin* folder.</span></span> <span data-ttu-id="033ef-662">這個資料夾包含下列檔案：</span><span class="sxs-lookup"><span data-stu-id="033ef-662">This folder contains the following files:</span></span>  
  
    -   <span data-ttu-id="033ef-663">Jdecba.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-663">Jdecba.dll</span></span>    
    -   <span data-ttu-id="033ef-664">Microsoft.BizTalk.Adapters.JDEProperties.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-664">Microsoft.BizTalk.Adapters.JDEProperties.dll</span></span>  
  
* <span data-ttu-id="033ef-665">下列檔案會安裝在*Program Files\Microsoft BizTalk Adapters for Enterprise applications\j.d.edwards。Edwards EnterpriseOne(r)*:</span><span class="sxs-lookup"><span data-stu-id="033ef-665">The following files are installed in *Program Files\Microsoft BizTalk Adapters for Enterprise Applications\J.D. Edwards EnterpriseOne(r)*:</span></span>  
  
    -   <span data-ttu-id="033ef-666">Bin\BTAJDEEnterpriseOneTrace.cmd</span><span class="sxs-lookup"><span data-stu-id="033ef-666">Bin\BTAJDEEnterpriseOneTrace.cmd</span></span>    
    -   <span data-ttu-id="033ef-667">Classes\JDEDynAccess.jar</span><span class="sxs-lookup"><span data-stu-id="033ef-667">Classes\JDEDynAccess.jar</span></span>    
    -   <span data-ttu-id="033ef-668">Config\btaJDEEnterpriseOneTrace.mof</span><span class="sxs-lookup"><span data-stu-id="033ef-668">Config\btaJDEEnterpriseOneTrace.mof</span></span>    
    -   <span data-ttu-id="033ef-669">Config\jdearglist.txt</span><span class="sxs-lookup"><span data-stu-id="033ef-669">Config\jdearglist.txt</span></span>    
    -   <span data-ttu-id="033ef-670">Config\jdeinterop.ini</span><span class="sxs-lookup"><span data-stu-id="033ef-670">Config\jdeinterop.ini</span></span>    
    -   <span data-ttu-id="033ef-671">Config\jdelog.properties</span><span class="sxs-lookup"><span data-stu-id="033ef-671">Config\jdelog.properties</span></span>    
    -   <span data-ttu-id="033ef-672">Sdk</span><span class="sxs-lookup"><span data-stu-id="033ef-672">Sdk</span></span>  
  
 
## <a name="post-install---peoplesoft-enterprise"></a><span data-ttu-id="033ef-673">後續安裝-PeopleSoft Enterprise</span><span class="sxs-lookup"><span data-stu-id="033ef-673">Post-install - PeopleSoft Enterprise</span></span>  
 <span data-ttu-id="033ef-674">Microsoft BizTalk Adapter for PeopleSoft Enterprise 包含傳輸配接器，可將支援的資料庫和伺服器系統連接到 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="033ef-674">Microsoft BizTalk Adapter for PeopleSoft Enterprise contains a transmit adapter that interfaces supported databases and server systems to BizTalk Server.</span></span> <span data-ttu-id="033ef-675">傳輸配接器可讓您叫用從 BizTalk Server 的伺服器系統的呼叫。</span><span class="sxs-lookup"><span data-stu-id="033ef-675">The transmit adapter enables you to invoke a server system’s call from BizTalk Server.</span></span> <span data-ttu-id="033ef-676">傳輸配接器 (BizTalk Server 管理傳送處理常式) 組態會指定 SQL 資料庫的位置。</span><span class="sxs-lookup"><span data-stu-id="033ef-676">The transmit adapter (the BizTalk Server Administration Send Handler) configuration specifies the location of the SQL database.</span></span>  
  
 <span data-ttu-id="033ef-677">BizTalk Adapter for PeopleSoft Enterprise 提供支援的企業單一登入 (SSO)。</span><span class="sxs-lookup"><span data-stu-id="033ef-677">BizTalk Adapter for PeopleSoft Enterprise provides support for Enterprise Single Sign-On (SSO).</span></span> <span data-ttu-id="033ef-678">如果您選取使用中的 SSO**傳輸屬性**頁面上，認證會使用 SSO 認證資料庫中的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="033ef-678">If you select to use SSO in the **Transport Properties** page, the credentials for the affiliate application in the SSO Credentials database are used.</span></span> <span data-ttu-id="033ef-679">分支機構應用程式代表需要認證的後端應用程式。</span><span class="sxs-lookup"><span data-stu-id="033ef-679">An affiliate application represents an application—a back-end that requires credentials.</span></span>  
  
 <span data-ttu-id="033ef-680">配接器安裝包含 \sdk 目錄中的範例。</span><span class="sxs-lookup"><span data-stu-id="033ef-680">The adapter installation includes samples in the \sdk directory.</span></span>  
  
### <a name="installed-components"></a><span data-ttu-id="033ef-681">已安裝的元件</span><span class="sxs-lookup"><span data-stu-id="033ef-681">Installed components</span></span>  
* <span data-ttu-id="033ef-682">配接器安裝會安裝並註冊在全域組件快取 (GAC) 中的下列元件。</span><span class="sxs-lookup"><span data-stu-id="033ef-682">The adapter installation installs and registers the following components in the global assembly cache (GAC).</span></span> <span data-ttu-id="033ef-683">您可以在總管中開啟組件 資料夾，以確認註冊 (< %WINDIR%> \assembly)，或使用`gacutil /l`從 Visual Studio 命令提示字元：</span><span class="sxs-lookup"><span data-stu-id="033ef-683">You can verify the registration by opening the assembly folder in your explorer (<%WINDIR%>\assembly), or use the `gacutil /l` from the Visual Studio command prompt:</span></span>
  
    -   <span data-ttu-id="033ef-684">Microsoft.BizTalk.Adapters.BizUtil.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-684">Microsoft.BizTalk.Adapters.BizUtil.dll</span></span>    
    -   <span data-ttu-id="033ef-685">Microsoft.BizTalk.Adapters.CoreManagement.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-685">Microsoft.BizTalk.Adapters.CoreManagement.dll</span></span>    
    -   <span data-ttu-id="033ef-686">Microsoft.BizTalk.Adapters.CoreReceiver.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-686">Microsoft.BizTalk.Adapters.CoreReceiver.dll</span></span>    
    -   <span data-ttu-id="033ef-687">Microsoft.BizTalk.Adapters.CoreTransmitter.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-687">Microsoft.BizTalk.Adapters.CoreTransmitter.dll</span></span>    

* <span data-ttu-id="033ef-688">配接器專屬檔案會安裝在*Program Files*並*Program Files\Common Files*。</span><span class="sxs-lookup"><span data-stu-id="033ef-688">Adapter-specific files are installed in *Program Files* and *Program Files\Common Files*.</span></span> <span data-ttu-id="033ef-689">下列檔案會安裝在*Program Files\Microsoft BizTalk Adapters for Enterprise Applications\PeopleSoft Enterprise (r)*:</span><span class="sxs-lookup"><span data-stu-id="033ef-689">The following files are installed in *Program Files\Microsoft BizTalk Adapters for Enterprise Applications\PeopleSoft Enterprise (r)*:</span></span>
  
    -   <span data-ttu-id="033ef-690">bin\BTAPeopleSoftTrace.cmd</span><span class="sxs-lookup"><span data-stu-id="033ef-690">bin\BTAPeopleSoftTrace.cmd</span></span>    
    -   <span data-ttu-id="033ef-691">config\btaPeopleSoftTrace.mof</span><span class="sxs-lookup"><span data-stu-id="033ef-691">config\btaPeopleSoftTrace.mof</span></span>    
    -   <span data-ttu-id="033ef-692">config\GET_CI_INFO.pc</span><span class="sxs-lookup"><span data-stu-id="033ef-692">config\GET_CI_INFO.pc</span></span>    
    -   <span data-ttu-id="033ef-693">config\GET_CI_INFO.pc</span><span class="sxs-lookup"><span data-stu-id="033ef-693">config\GET_CI_INFO.pc</span></span>    
    -   <span data-ttu-id="033ef-694">sdk\<sdk</span><span class="sxs-lookup"><span data-stu-id="033ef-694">sdk\\</span></span>  
  
* <span data-ttu-id="033ef-695">*程式 Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications*包含下列檔案：</span><span class="sxs-lookup"><span data-stu-id="033ef-695">*Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications* contains the following files:</span></span>  
  
    -   <span data-ttu-id="033ef-696">bin\psosa.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-696">bin\psosa.dll</span></span>    
    -   <span data-ttu-id="033ef-697">bin\Microsoft.BizTalk.Adapters.CoreManagement.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-697">bin\Microsoft.BizTalk.Adapters.CoreManagement.dll</span></span>    
    -   <span data-ttu-id="033ef-698">bin\Microsoft.BizTalk.Adapters.CoreReceiver.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-698">bin\Microsoft.BizTalk.Adapters.CoreReceiver.dll</span></span>    
    -   <span data-ttu-id="033ef-699">bin\Microsoft.BizTalk.Adapters.CoreTransmitter.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-699">bin\Microsoft.BizTalk.Adapters.CoreTransmitter.dll</span></span>  
  
## <a name="post-install-overview---tibco-rendezvous"></a><span data-ttu-id="033ef-700">後續安裝概觀-TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="033ef-700">Post-install overview - TIBCO Rendezvous</span></span>  
 <span data-ttu-id="033ef-701">Microsoft BizTalk Adapter for TIBCO Rendezvous 包含接收和傳輸功能，可支援的資料庫與伺服器系統連接到 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="033ef-701">Microsoft BizTalk Adapter for TIBCO Rendezvous contains receive and transmit functionality that interface with supported databases and server systems to BizTalk Server.</span></span>  
  
- <span data-ttu-id="033ef-702">接收端會接聽來自伺服器系統的輸出呼叫。</span><span class="sxs-lookup"><span data-stu-id="033ef-702">The receive side listens for calls that are outbound from the server system.</span></span>  
  
- <span data-ttu-id="033ef-703">傳輸端可讓您從 BizTalk Server 叫用伺服器系統的呼叫。</span><span class="sxs-lookup"><span data-stu-id="033ef-703">The transmit side enables you to invoke a server system’s call from BizTalk Server.</span></span>  
  
  <span data-ttu-id="033ef-704">請參閱有關如何使用 Microsoft BizTalk Adapter for TIBCO Rendezvous 以及其模型與 BizTalk Server 模型之間的對應資訊的配接器文件。</span><span class="sxs-lookup"><span data-stu-id="033ef-704">See the adapter documentation for information about how to use Microsoft BizTalk Adapter for TIBCO Rendezvous and about the mapping between its model and the BizTalk Server model.</span></span>  
  
### <a name="installed-components"></a><span data-ttu-id="033ef-705">已安裝的元件</span><span class="sxs-lookup"><span data-stu-id="033ef-705">Installed components</span></span>  
* <span data-ttu-id="033ef-706">配接器安裝會安裝並註冊在全域組件快取 (GAC) 中的下列元件。</span><span class="sxs-lookup"><span data-stu-id="033ef-706">The adapter installation installs and registers the following components in the global assembly cache (GAC).</span></span> <span data-ttu-id="033ef-707">您可以在總管中開啟組件 資料夾，以確認註冊 (< %WINDIR%> \assembly)，或使用`gacutil /l`從 Visual Studio 命令提示字元：</span><span class="sxs-lookup"><span data-stu-id="033ef-707">You can verify the registration by opening the assembly folder in your explorer (<%WINDIR%>\assembly), or use the `gacutil /l` from the Visual Studio command prompt:</span></span> 
  
    -   <span data-ttu-id="033ef-708">Microsoft.BizTalk.Adapters.TibcoRV</span><span class="sxs-lookup"><span data-stu-id="033ef-708">Microsoft.BizTalk.Adapters.TibcoRV</span></span>    
    -   <span data-ttu-id="033ef-709">Microsoft.BizTalk.Adapters.TibcoRV.Common</span><span class="sxs-lookup"><span data-stu-id="033ef-709">Microsoft.BizTalk.Adapters.TibcoRV.Common</span></span>    
    -   <span data-ttu-id="033ef-710">Microsoft.BizTalk.Adapters.TibcoRV.Service</span><span class="sxs-lookup"><span data-stu-id="033ef-710">Microsoft.BizTalk.Adapters.TibcoRV.Service</span></span>    
    -   <span data-ttu-id="033ef-711">Microsoft.BizTalk.Adapters.TibRV.Properties</span><span class="sxs-lookup"><span data-stu-id="033ef-711">Microsoft.BizTalk.Adapters.TibRV.Properties</span></span>    
    -   <span data-ttu-id="033ef-712">Microsoft.BizTalk.Adapters.TibcoEMS</span><span class="sxs-lookup"><span data-stu-id="033ef-712">Microsoft.BizTalk.Adapters.TibcoEMS</span></span>    
    -   <span data-ttu-id="033ef-713">Microsoft.BizTalk.Adapters.TibcoEMS.Properties</span><span class="sxs-lookup"><span data-stu-id="033ef-713">Microsoft.BizTalk.Adapters.TibcoEMS.Properties</span></span>    
    -   <span data-ttu-id="033ef-714">Microsoft.BizTalk.Adapters.TibcoRVManagement</span><span class="sxs-lookup"><span data-stu-id="033ef-714">Microsoft.BizTalk.Adapters.TibcoRVManagement</span></span>    
    -   <span data-ttu-id="033ef-715">Microsoft.BizTalk.Adapters.TibcoRVReceiver</span><span class="sxs-lookup"><span data-stu-id="033ef-715">Microsoft.BizTalk.Adapters.TibcoRVReceiver</span></span>  
    -   <span data-ttu-id="033ef-716">Microsoft.BizTalk.Adapters.TibcoRVTransmitter</span><span class="sxs-lookup"><span data-stu-id="033ef-716">Microsoft.BizTalk.Adapters.TibcoRVTransmitter</span></span>  
  
* <span data-ttu-id="033ef-717">配接器專屬檔案會安裝在*Program Files 與 Program Files\Common Files*。</span><span class="sxs-lookup"><span data-stu-id="033ef-717">Adapter-specific files are installed in *Program Files and Program Files\Common Files*.</span></span> <span data-ttu-id="033ef-718">下列檔案會安裝在*Program Files\Microsoft BizTalk Adapters for Enterprise applications\{4cdcdb2c TIBCO(r) Rendezvous(r)*:</span><span class="sxs-lookup"><span data-stu-id="033ef-718">The following files are installed in *Program Files\Microsoft BizTalk Adapters for Enterprise Applications\ TIBCO(r) Rendezvous(r)*:</span></span>  
  
    -   <span data-ttu-id="033ef-719">bin\BTATibcoRVTrace.cmd</span><span class="sxs-lookup"><span data-stu-id="033ef-719">bin\BTATibcoRVTrace.cmd</span></span>    
    -   <span data-ttu-id="033ef-720">bin\mbaRV.exe</span><span class="sxs-lookup"><span data-stu-id="033ef-720">bin\mbaRV.exe</span></span>    
    -   <span data-ttu-id="033ef-721">bin\Microsoft.BizTalk.Adapters.TibcoRV.Common.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-721">bin\Microsoft.BizTalk.Adapters.TibcoRV.Common.dll</span></span>    
    -   <span data-ttu-id="033ef-722">bin\Microsoft.BizTalk.Adapters.TibcoRV.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-722">bin\Microsoft.BizTalk.Adapters.TibcoRV.dll</span></span>    
    -   <span data-ttu-id="033ef-723">bin\Microsoft.BizTalk.Adapters.TibcoRV.Service.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-723">bin\Microsoft.BizTalk.Adapters.TibcoRV.Service.dll</span></span>    
    -   <span data-ttu-id="033ef-724">bin\Microsoft.BizTalk.Adapters.BizUtil.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-724">bin\Microsoft.BizTalk.Adapters.BizUtil.dll</span></span>    
    -   <span data-ttu-id="033ef-725">bin\Microsoft.BizTalk.Adapters.CoreManagement.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-725">bin\Microsoft.BizTalk.Adapters.CoreManagement.dll</span></span>    
    -   <span data-ttu-id="033ef-726">bin\Microsoft.BizTalk.Adapters.CoreReceiver.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-726">bin\Microsoft.BizTalk.Adapters.CoreReceiver.dll</span></span>    
    -   <span data-ttu-id="033ef-727">bin\Microsoft.BizTalk.Adapters.CoreTransmitter.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-727">bin\Microsoft.BizTalk.Adapters.CoreTransmitter.dll</span></span>    
    -   <span data-ttu-id="033ef-728">bin\Microsoft.BizTalk.Adapters.TibRV.Properties.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-728">bin\Microsoft.BizTalk.Adapters.TibRV.Properties.dll</span></span>    
    -   <span data-ttu-id="033ef-729">Config\btaTibcoRVTrace.mof</span><span class="sxs-lookup"><span data-stu-id="033ef-729">Config\btaTibcoRVTrace.mof</span></span>    
    -   <span data-ttu-id="033ef-730">sdk\<sdk</span><span class="sxs-lookup"><span data-stu-id="033ef-730">sdk\\</span></span>  
  
* <span data-ttu-id="033ef-731">*程式 Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications*包含下列檔案：</span><span class="sxs-lookup"><span data-stu-id="033ef-731">*Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications* contains the following files:</span></span>  
  
    -   <span data-ttu-id="033ef-732">bin\tibcorvcba.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-732">bin\tibcorvcba.dll</span></span>    
    -   <span data-ttu-id="033ef-733">Microsoft.BizTalk.Adapters.CoreManagement.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-733">Microsoft.BizTalk.Adapters.CoreManagement.dll</span></span>    
    -   <span data-ttu-id="033ef-734">Microsoft.BizTalk.Adapters.CoreReceiver.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-734">Microsoft.BizTalk.Adapters.CoreReceiver.dll</span></span>    
    -   <span data-ttu-id="033ef-735">Microsoft.BizTalk.Adapters.CoreTransmitter.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-735">Microsoft.BizTalk.Adapters.CoreTransmitter.dll</span></span>  
  
### <a name="add-tibcorendezvousdll-to-the-gac"></a><span data-ttu-id="033ef-736">將 TIBCO。Rendezvous.dll gac</span><span class="sxs-lookup"><span data-stu-id="033ef-736">Add TIBCO.Rendezvous.dll to the GAC</span></span>  
 <span data-ttu-id="033ef-737">BizTalk Adapter for TIBCO Rendezvous 需要**TIBCO。Rendezvous.dll**檔案。</span><span class="sxs-lookup"><span data-stu-id="033ef-737">BizTalk Adapter for TIBCO Rendezvous requires the **TIBCO.Rendezvous.dll** file.</span></span> <span data-ttu-id="033ef-738">所需的最低版本是 1.0.3036.23330 FileVersion，隨附於該產品 8.1 版。</span><span class="sxs-lookup"><span data-stu-id="033ef-738">The minimum version that is required is 1.0.3036.23330 FileVersion, which is shipped with the product version 8.1.</span></span> <span data-ttu-id="033ef-739">配接器會觸發例外狀況，並記錄適當的訊息，如果未安裝此組件。</span><span class="sxs-lookup"><span data-stu-id="033ef-739">The adapter triggers an exception and logs an appropriate message if this assembly is not installed.</span></span>  
  
 <span data-ttu-id="033ef-740">您必須使用晚期繫結來載入組件，以便當特定版本的 TIBCO，TIBCO Rendezvous 組件不會失敗。Rendezvous.dll 和 TIBCO。Rendezvous.net 模組不在目標電腦上。</span><span class="sxs-lookup"><span data-stu-id="033ef-740">You must use late binding to load assemblies so that the TIBCO Rendezvous assemblies don't fail when a particular version of the TIBCO.Rendezvous.dll and TIBCO.Rendezvous.net module aren't on the target computer.</span></span>
  
 <span data-ttu-id="033ef-741">**執行階段元件**</span><span class="sxs-lookup"><span data-stu-id="033ef-741">**Runtime Component**</span></span>  
  
 <span data-ttu-id="033ef-742">確認您的電腦上已安裝 TIBCO Rendezvous 執行階段元件。</span><span class="sxs-lookup"><span data-stu-id="033ef-742">Verify you have the TIBCO Rendezvous Runtime Component installed on your computer.</span></span> <span data-ttu-id="033ef-743">執行階段元件是安裝 TIBCO Rendezvous 時唯一必須安裝的元件。</span><span class="sxs-lookup"><span data-stu-id="033ef-743">The Runtime Component is the only component that you must install when you install TIBCO Rendezvous.</span></span>  

1. <span data-ttu-id="033ef-744">在 Visual Studio 命令提示字元中，將目錄變更至 TIBCO 的位置。Rendezvous.dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="033ef-744">In a Visual Studio command prompt, change directories to the location of the TIBCO.Rendezvous.dll file.</span></span> <span data-ttu-id="033ef-745">TIBCO Rendezvous 的預設安裝中，這個 DLL 的路徑是**C:\TIBCO\TIBRV\BIN\TIBCO。Rendezvous.dll**。</span><span class="sxs-lookup"><span data-stu-id="033ef-745">The path of this DLL in the default installation of TIBCO Rendezvous is **C:\TIBCO\TIBRV\BIN\TIBCO.Rendezvous.dll**.</span></span>  
  
2. <span data-ttu-id="033ef-746">在命令提示字元中，請輸入下列項目：</span><span class="sxs-lookup"><span data-stu-id="033ef-746">At the command prompt, type the following:</span></span>  
  
```
C:\TIBCO\TIBRV\BIN > gacutil /i TIBCO.Rendezvous.dll
```
  
 <span data-ttu-id="033ef-747">TIBCO.Rendezvous.dll 現在會顯示 GAC 清單。</span><span class="sxs-lookup"><span data-stu-id="033ef-747">The TIBCO.Rendezvous.dll now shows GAC list.</span></span> <span data-ttu-id="033ef-748">若要檢視清單中，在控制台中，開啟**系統管理工具**，開啟**Microsoft.NET Framework 組態**，然後開啟**組件快取**。</span><span class="sxs-lookup"><span data-stu-id="033ef-748">To view the list, in Control Panel, open **Administrator Tools**, open **Microsoft .NET Framework Configuration**, and then open **Assembly Cache**.</span></span>  
  
## <a name="post-install---tibco-enterprise-message-service"></a><span data-ttu-id="033ef-749">後置 install-TIBCO Enterprise Message Service</span><span class="sxs-lookup"><span data-stu-id="033ef-749">Post-install - TIBCO Enterprise Message Service</span></span>  
 <span data-ttu-id="033ef-750">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) 包含接收和傳輸功能，可將支援的資料庫和伺服器系統連接到 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="033ef-750">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) contains receive and transmit functionality that interface with supported databases and server systems to BizTalk Server.</span></span>  
  
- <span data-ttu-id="033ef-751">接收端會接聽來自伺服器系統的輸出呼叫。</span><span class="sxs-lookup"><span data-stu-id="033ef-751">The receive side listens for calls that are outbound from the server system.</span></span>  

- <span data-ttu-id="033ef-752">傳輸端可讓您從 BizTalk Server 叫用伺服器系統的呼叫。</span><span class="sxs-lookup"><span data-stu-id="033ef-752">The transmit side enables you to invoke a server system’s call from BizTalk Server.</span></span>  
  
  <span data-ttu-id="033ef-753">請參閱有關如何使用 BizTalk Adapter for TIBCO EMS 以及其模型與 BizTalk Server 模型之間的對應資訊的配接器文件。</span><span class="sxs-lookup"><span data-stu-id="033ef-753">See the adapter documentation for information about how to use BizTalk Adapter for TIBCO EMS and about the mapping between its model and the BizTalk Server model.</span></span>  
  
### <a name="installed-components"></a><span data-ttu-id="033ef-754">已安裝的元件</span><span class="sxs-lookup"><span data-stu-id="033ef-754">Installed components</span></span>  
* <span data-ttu-id="033ef-755">配接器安裝會安裝並註冊`Microsoft.BizTalk.Adapters.TibcoEMS.dll`全域組件快取 (GAC) 中的檔案。</span><span class="sxs-lookup"><span data-stu-id="033ef-755">The adapter installation installs and registers the `Microsoft.BizTalk.Adapters.TibcoEMS.dll` file in the global assembly cache (GAC).</span></span> <span data-ttu-id="033ef-756">您可以在總管中開啟組件 資料夾，以確認註冊 (< %WINDIR%> \assembly)，或使用`gacutil /l`從 Visual Studio 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="033ef-756">You can verify the registration by opening the assembly folder in your explorer (<%WINDIR%>\assembly), or use the `gacutil /l` from the Visual Studio command prompt.</span></span>
  
* <span data-ttu-id="033ef-757">配接器專屬檔案會安裝在*Program Files*並*Program Files\Common Files*。</span><span class="sxs-lookup"><span data-stu-id="033ef-757">Adapter-specific files are installed in *Program Files* and *Program Files\Common Files*.</span></span> <span data-ttu-id="033ef-758">下列檔案會安裝下*Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) 企業訊息 Service(TM)*:</span><span class="sxs-lookup"><span data-stu-id="033ef-758">The following files are installed under *Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Enterprise Message Service(TM)*:</span></span>  
  
    -   <span data-ttu-id="033ef-759">bin\BTATibcoEMSTrace.cmd</span><span class="sxs-lookup"><span data-stu-id="033ef-759">bin\BTATibcoEMSTrace.cmd</span></span>    
    -   <span data-ttu-id="033ef-760">Microsoft.BizTalk.Adapters.TibcoEMS.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-760">Microsoft.BizTalk.Adapters.TibcoEMS.dll</span></span>    
    -   <span data-ttu-id="033ef-761">Config\btaTibcoEMSTrace.mof</span><span class="sxs-lookup"><span data-stu-id="033ef-761">Config\btaTibcoEMSTrace.mof</span></span>    
    -   <span data-ttu-id="033ef-762">sdk\<sdk</span><span class="sxs-lookup"><span data-stu-id="033ef-762">sdk\\</span></span>  
  
* <span data-ttu-id="033ef-763">*程式 Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\bin*資料夾包含下列檔案：</span><span class="sxs-lookup"><span data-stu-id="033ef-763">*Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\bin* folder contains the following files:</span></span>  
  
  - <span data-ttu-id="033ef-764">Microsoft.BizTalk.Adapters.CoreManagement.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-764">Microsoft.BizTalk.Adapters.CoreManagement.dll</span></span>    
  - <span data-ttu-id="033ef-765">Microsoft.BizTalk.Adapters.CoreReceiver.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-765">Microsoft.BizTalk.Adapters.CoreReceiver.dll</span></span>    
  - <span data-ttu-id="033ef-766">Microsoft.BizTalk.Adapters.CoreTransmitter.dll</span><span class="sxs-lookup"><span data-stu-id="033ef-766">Microsoft.BizTalk.Adapters.CoreTransmitter.dll</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="033ef-767">您必須使用晚期繫結來載入組件，如此一來，當目標電腦上沒有特定版本的 TIBCO.EMS.dll 時，TIBCO EMS 組件才不會失敗。</span><span class="sxs-lookup"><span data-stu-id="033ef-767">You must use late binding to load assemblies so that the TIBCO EMS assemblies do not fail when a particular version of the TIBCO.EMS.dll is not present on the target computer.</span></span>  
  
### <a name="add-tibcoemsdll-api-to-the-gac"></a><span data-ttu-id="033ef-768">將 TIBCO。EMS.dll API 加入 GAC</span><span class="sxs-lookup"><span data-stu-id="033ef-768">Add TIBCO.EMS.dll API to the GAC</span></span>  
 <span data-ttu-id="033ef-769">BizTalk Adapter for TIBCO EMS 會要求您將 TIBCO.EMS.dll 加入 GAC。</span><span class="sxs-lookup"><span data-stu-id="033ef-769">BizTalk Adapter for TIBCO EMS requires that you add the TIBCO.EMS.dll to the GAC.</span></span> <span data-ttu-id="033ef-770">如果未安裝這個組件，BizTalk Adapter for TIBCO EMS 會觸發例外狀況並記錄適當的訊息。</span><span class="sxs-lookup"><span data-stu-id="033ef-770">BizTalk Adapter for TIBCO EMS triggers an exception and logs an appropriate message if this assembly is not installed.</span></span>  
  
1. <span data-ttu-id="033ef-771">將 TIBCO EMS C#API 複製到您的 BizTalk 電腦。</span><span class="sxs-lookup"><span data-stu-id="033ef-771">Copy the TIBCO EMS C#API to your BizTalk computer.</span></span>  
  
2. <span data-ttu-id="033ef-772">在 Visual Studio 命令提示字元中，將目錄變更為 C# API 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="033ef-772">In a Visual Studio command prompt, change directories to the location of the C# API file.</span></span>  
  
3. <span data-ttu-id="033ef-773">在 Visual Studio 命令提示字元中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="033ef-773">In a Visual Studio command prompt, type the following:</span></span>  
  
   ```
   C:\\<TIBCO EMS Folder\>bin> gacutil /i TIBCO.EMS.dll
   ```
  
   <span data-ttu-id="033ef-774">TIBCO.EMS.dll 現在會顯示在 C:\Windows\assembly 清單中。</span><span class="sxs-lookup"><span data-stu-id="033ef-774">The TIBCO.EMS.dll now shows in the C:\Windows\assembly listing.</span></span> <span data-ttu-id="033ef-775">或者，您也可以在控制台中，開啟**系統管理工具**，開啟**Microsoft.NET Framework**，然後開啟**組件快取**若要檢視 GAC 清單。</span><span class="sxs-lookup"><span data-stu-id="033ef-775">Or, in Control Panel, open **Administrator Tools**, open **Microsoft .NET Framework**, and open **Assembly Cache** to view the GAC list.</span></span>  
  
   <span data-ttu-id="033ef-776">**限制**</span><span class="sxs-lookup"><span data-stu-id="033ef-776">**Limitations**</span></span>  
  
   <span data-ttu-id="033ef-777">BizTalk Adapter for TIBCO EMS 使用 TIBCO.EMS.dll 與伺服器通訊。</span><span class="sxs-lookup"><span data-stu-id="033ef-777">BizTalk Adapter for TIBCO EMS uses TIBCO.EMS.dll to communicate with the server.</span></span> <span data-ttu-id="033ef-778">以下是使用 TIBCO.EMS.dll 的限制：</span><span class="sxs-lookup"><span data-stu-id="033ef-778">The following are limitations when you use the TIBCO.EMS.dll:</span></span>  
  
4. <span data-ttu-id="033ef-779">無法使用訊息壓縮功能，該功能可讓 TIBCO EMS 用戶端將壓縮格式的訊息傳送給 EMS。</span><span class="sxs-lookup"><span data-stu-id="033ef-779">Message compression, which enables the TIBCO EMS client to send messages in a compressed form to EMS, is not available.</span></span>  
  
5. <span data-ttu-id="033ef-780">無法加密配接器和伺服器之間的訊息。</span><span class="sxs-lookup"><span data-stu-id="033ef-780">Encryption of messages between the adapter and the server is not available.</span></span> <span data-ttu-id="033ef-781">TIBCO.EMS.dll 不允許使用 OpenSSL 程式庫進行 SSL 加密，但配接器支援使用 Tibco.EMS.dll 搭配 ProductVersion 5.0 及更新版本的 SLL。</span><span class="sxs-lookup"><span data-stu-id="033ef-781">The TIBCO.EMS.dll does not allow for SSL encryption using the OpenSSL libraries but the Adapters support the SLL with Tibco.EMS.dll with ProductVersion 5.0 and above.</span></span>  
  
6. <span data-ttu-id="033ef-782">不支援 EMS 的系統管理 API。</span><span class="sxs-lookup"><span data-stu-id="033ef-782">Administration API for EMS is not supported.</span></span>  
  
## <a name="adapter-tracing"></a><span data-ttu-id="033ef-783">配接器追蹤</span><span class="sxs-lookup"><span data-stu-id="033ef-783">Adapter tracing</span></span>

### <a name="enable-tracing"></a><span data-ttu-id="033ef-784">啟用追蹤</span><span class="sxs-lookup"><span data-stu-id="033ef-784">Enable tracing</span></span>
 <span data-ttu-id="033ef-785">系統管理員可決定要使用 Windows 追蹤的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="033ef-785">The file name used with Windows tracing is up to the administrator.</span></span> <span data-ttu-id="033ef-786">這個應用程式會寫入至作業系統，並在您需要特定後端系統的記錄檔之前，略過所有記錄檔。</span><span class="sxs-lookup"><span data-stu-id="033ef-786">The application writes to the operating system, which ignores all logs until you want the logs for a particular back-end system.</span></span> <span data-ttu-id="033ef-787">您可以執行個別適用於企業應用程式的 BizTalk Adapter 命令檔，來執行這項作業。</span><span class="sxs-lookup"><span data-stu-id="033ef-787">You do this by running a separate BizTalk Adapters for Enterprise Applications command file.</span></span> <span data-ttu-id="033ef-788">該命令的引數的其中一個是用來擷取追蹤資訊的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="033ef-788">One of the arguments for that command is the name of the file that is used to capture the trace information.</span></span> <span data-ttu-id="033ef-789">如需詳細資訊，請參閱 「 使用 Windows 追蹤事件 」 （在本主題中）。</span><span class="sxs-lookup"><span data-stu-id="033ef-789">For more information, see "Use Windows trace event" (in this topic).</span></span>
  
 <span data-ttu-id="033ef-790">追蹤檔案安裝至 * \Program Files\Microsoft BizTalk Adapters for Enterprise Applications\*。</span><span class="sxs-lookup"><span data-stu-id="033ef-790">Trace files install to *\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\*.</span></span>  
  
-   <span data-ttu-id="033ef-791">bin\BTATrace.cmd</span><span class="sxs-lookup"><span data-stu-id="033ef-791">bin\BTATrace.cmd</span></span>    
-   <span data-ttu-id="033ef-792">config\btaTrace.mof</span><span class="sxs-lookup"><span data-stu-id="033ef-792">config\btaTrace.mof</span></span>  
  
### <a name="use-windows-trace-event"></a><span data-ttu-id="033ef-793">使用 Windows 追蹤事件</span><span class="sxs-lookup"><span data-stu-id="033ef-793">Use Windows trace event</span></span>  
 <span data-ttu-id="033ef-794">配接器會將錯誤、警告和資訊訊息記錄至 Windows 事件檢視器。</span><span class="sxs-lookup"><span data-stu-id="033ef-794">The adapters log error, warning, and information messages to the Windows Event Viewer.</span></span> <span data-ttu-id="033ef-795">您可以使用 Windows 事件追蹤 (ETW) 工具來檢視其他追蹤訊息。</span><span class="sxs-lookup"><span data-stu-id="033ef-795">You can view additional tracing messages by using the Event Tracing for Windows (ETW) tool.</span></span> <span data-ttu-id="033ef-796">當 ETW 啟用時，它會建立 \*.etl 檔案以接收訊息。</span><span class="sxs-lookup"><span data-stu-id="033ef-796">When ETW is enabled, it creates an \*.etl file to receive the messages.</span></span> <span data-ttu-id="033ef-797">這個檔案是二進位格式，必須經過轉換才能讀取。</span><span class="sxs-lookup"><span data-stu-id="033ef-797">This file is in binary format and must be converted to be read.</span></span> <span data-ttu-id="033ef-798">若要這樣做，您必須取用者應用程式可供解譯\*.etl 檔案，比方說，Windows tracerpt.exe 或 tracedmp.exe。</span><span class="sxs-lookup"><span data-stu-id="033ef-798">To do this, you must have a consumer application available to interpret the \*.etl file, for example, Windows tracerpt.exe or tracedmp.exe.</span></span>  
  
### <a name="etw-components"></a><span data-ttu-id="033ef-799">ETW 元件</span><span class="sxs-lookup"><span data-stu-id="033ef-799">ETW components</span></span>
  
 <span data-ttu-id="033ef-800">「Windows 事件追蹤」有三個元件：</span><span class="sxs-lookup"><span data-stu-id="033ef-800">Event Tracing for Windows has three components:</span></span>  
  
* <span data-ttu-id="033ef-801">**控制器應用程式：** 啟動和停用提供者。</span><span class="sxs-lookup"><span data-stu-id="033ef-801">**Controller application:** Activates and deactivates a provider.</span></span> <span data-ttu-id="033ef-802">例如，tracelog.exe 或 logman.exe。</span><span class="sxs-lookup"><span data-stu-id="033ef-802">For example, tracelog.exe or logman.exe.</span></span>  
  
    <span data-ttu-id="033ef-803">您會將 PATH 環境變數設定成指向 tracelog.exe 的位置。</span><span class="sxs-lookup"><span data-stu-id="033ef-803">You set your PATH environment variable to point to the location of tracelog.exe.</span></span> <span data-ttu-id="033ef-804">這可確保該 BTA < 配接器名稱\>追蹤呼叫可在系統中找到 tracelog.exe。</span><span class="sxs-lookup"><span data-stu-id="033ef-804">This makes sure that BTA<Adapter Name\>Trace calls can locate tracelog.exe in the system.</span></span> <span data-ttu-id="033ef-805">根據預設，BTA < 配接器名稱\>追蹤搜尋目前的路徑。</span><span class="sxs-lookup"><span data-stu-id="033ef-805">By default, BTA<Adapter Name\>Trace searches the current path.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="033ef-806">tracelog.exe 可從 Microsoft SDK，而且是由 Microsoft BizTalk Adapters for Enterprise Applications 的命令相容。</span><span class="sxs-lookup"><span data-stu-id="033ef-806">tracelog.exe is available from the Microsoft SDK and is compatible with the commands provided by Microsoft BizTalk Adapters for Enterprise Applications.</span></span> <span data-ttu-id="033ef-807">如果要使用 logman.exe，請參閱 logman 文件。</span><span class="sxs-lookup"><span data-stu-id="033ef-807">To use logman.exe, see the logman documentation.</span></span>  
  
* <span data-ttu-id="033ef-808">**取用者應用程式：** 讀取記錄的事件。</span><span class="sxs-lookup"><span data-stu-id="033ef-808">**Consumer application:** Reads logged events.</span></span>  
  
    <span data-ttu-id="033ef-809">如果要讓取用者應用程式可讀取 .etl 檔案中的事件，「Windows 事件追蹤」必須將它們傾印到該檔案。</span><span class="sxs-lookup"><span data-stu-id="033ef-809">For the consumer application to be able to read the event in the .etl file, Event Tracing for Windows must dump them into that file.</span></span> <span data-ttu-id="033ef-810">此動作通常是在控制器停用追蹤後完成的。</span><span class="sxs-lookup"><span data-stu-id="033ef-810">Typically this is done when the controller deactivates the tracing.</span></span>  
  
    <span data-ttu-id="033ef-811">若要使用的取用者應用程式，而不需要停用追蹤，控制器必須啟用使用即時選項時，追蹤 **< 即時\>=-rt**。</span><span class="sxs-lookup"><span data-stu-id="033ef-811">To use the consumer application without deactivating the trace, the controller must activate the trace with the real-time option, **<Real time\> = -rt**.</span></span>  
  
* <span data-ttu-id="033ef-812">**提供者：** 用以提供事件。</span><span class="sxs-lookup"><span data-stu-id="033ef-812">**Provider:** Used to provide the event.</span></span>  
  
    <span data-ttu-id="033ef-813">每個配接器包含五個不同的提供者。</span><span class="sxs-lookup"><span data-stu-id="033ef-813">Each adapter includes five different providers.</span></span> <span data-ttu-id="033ef-814">它們是在 Windows Management Instrumentation (WMI) 中註冊的。</span><span class="sxs-lookup"><span data-stu-id="033ef-814">They are registered in Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="033ef-815">若要在 root\WMI\EventTrace 路經中尋找已登錄的提供者，您可以使用諸如 WMI CIM Studio 這類的工具。</span><span class="sxs-lookup"><span data-stu-id="033ef-815">To find the registered providers in the root\WMI\EventTrace path, you can use tools such as WMI CIM Studio.</span></span>  
  
    <span data-ttu-id="033ef-816">這五個提供者可讓您記錄不同的訊息類型：</span><span class="sxs-lookup"><span data-stu-id="033ef-816">The five providers enable you to log different kinds of messages:</span></span>  
  
        -   **Receiver Logging Provider**: The <Trace element\> switch is - **receiver**.    
        -   **Receiver CastDetails Provider**: The <Trace element\> switch is - **castDetailsReceive**.    
        -   **Transmitter Logging Provider**: The <Trace element\> switch is - **transmitter**.    
        -   **Transmitter CastDetails Provider**: The <Trace element\> switch is - **castDetailsTransmit**.    
        -   **Management Logging Provider**: The <Trace element\> switch is - **management**.  
  
<span data-ttu-id="033ef-817">若要使用 ETW，請執行 特定的配接器的命令： `BTA<Adapter Name\>Trace.cmd`。</span><span class="sxs-lookup"><span data-stu-id="033ef-817">To use ETW, run the command for the specific adapter: `BTA<Adapter Name\>Trace.cmd`.</span></span> <span data-ttu-id="033ef-818">您可以下列方式使用此命令：</span><span class="sxs-lookup"><span data-stu-id="033ef-818">You use this command as follows:</span></span>  
  
```  
BTA<Adapter Name>Trace <Trace element> -start [-cir <MB>|   
    -seq <MB>] [-rt] logfile  
BTA<Adapter Name>Trace <Trace element> -stop  
  
```  
  
 <span data-ttu-id="033ef-819">其中：</span><span class="sxs-lookup"><span data-stu-id="033ef-819">Where:</span></span>  
  
<span data-ttu-id="033ef-820">**< 追蹤項目\>** （必要） 是一種提供者。</span><span class="sxs-lookup"><span data-stu-id="033ef-820">**<Trace element\>** (required) is the kind of provider.</span></span> <span data-ttu-id="033ef-821">選項包括：</span><span class="sxs-lookup"><span data-stu-id="033ef-821">The options are:</span></span>  
  
 <span data-ttu-id="033ef-822">**-castDetailsTransmit**</span><span class="sxs-lookup"><span data-stu-id="033ef-822">**-castDetailsTransmit**</span></span>  
  
 <span data-ttu-id="033ef-823">**-傳輸器**</span><span class="sxs-lookup"><span data-stu-id="033ef-823">**-transmitter**</span></span>  
  
 <span data-ttu-id="033ef-824">**-castDetailsReceive**</span><span class="sxs-lookup"><span data-stu-id="033ef-824">**-castDetailsReceive**</span></span>  
  
 <span data-ttu-id="033ef-825">**-接收者**</span><span class="sxs-lookup"><span data-stu-id="033ef-825">**-receiver**</span></span>  
  
 <span data-ttu-id="033ef-826">**-管理**</span><span class="sxs-lookup"><span data-stu-id="033ef-826">**-management**</span></span>  
  
 <span data-ttu-id="033ef-827">**-啟動、-停止：** 啟用或停用提供者。</span><span class="sxs-lookup"><span data-stu-id="033ef-827">**-start, -stop:** Activate or deactivate the provider.</span></span>  
  
 <span data-ttu-id="033ef-828">**-cir < MB\>:** 檔案的大小與種類。</span><span class="sxs-lookup"><span data-stu-id="033ef-828">**-cir <MB\>:** Size and kind of file.</span></span> <span data-ttu-id="033ef-829">**-cir**是循環檔案。</span><span class="sxs-lookup"><span data-stu-id="033ef-829">**-cir** is a circular file.</span></span> <span data-ttu-id="033ef-830">**< MB\>:** 大小 （mb）。</span><span class="sxs-lookup"><span data-stu-id="033ef-830">**<MB\>:** Size in megabytes.</span></span>  
  
 <span data-ttu-id="033ef-831">**-seq < MB\>:** 檔案的大小與種類。</span><span class="sxs-lookup"><span data-stu-id="033ef-831">**-seq <MB\>:** Size and kind of file.</span></span> <span data-ttu-id="033ef-832">**-seq**是循序檔案。</span><span class="sxs-lookup"><span data-stu-id="033ef-832">**-seq** is a sequential file.</span></span> <span data-ttu-id="033ef-833">**< MB\>:** 大小 （mb）。</span><span class="sxs-lookup"><span data-stu-id="033ef-833">**<MB\>:** Size in megabytes.</span></span>  
  
 <span data-ttu-id="033ef-834">**-rt:** 上設定的即時模式。</span><span class="sxs-lookup"><span data-stu-id="033ef-834">**-rt:** Set the real-time mode on.</span></span>  
  
 <span data-ttu-id="033ef-835">**記錄檔：** 記錄檔的名稱 （c:\rtlog.etl 是預設值）。</span><span class="sxs-lookup"><span data-stu-id="033ef-835">**Logfile:** Name of the log file (c:\rtlog.etl is the default).</span></span>  
  
 <span data-ttu-id="033ef-836">例如：</span><span class="sxs-lookup"><span data-stu-id="033ef-836">For example:</span></span>  
  
```  
BTAXXXTrace -transmitter -start -cir 10 -rt c:\log\mylog.etl  
BTAXXXTrace -transmitter -stop  
  
```  
  
> [!NOTE]
>  <span data-ttu-id="033ef-837">您可以使用 tracerpt.exe 命令來格式化 .etl 檔案。</span><span class="sxs-lookup"><span data-stu-id="033ef-837">You use the tracerpt.exe command to format the .etl files.</span></span>  

## <a name="next-steps"></a><span data-ttu-id="033ef-838">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="033ef-838">Next steps</span></span>
* [<span data-ttu-id="033ef-839">JD Edwards EnterpriseOne 配接器</span><span class="sxs-lookup"><span data-stu-id="033ef-839">JD Edwards EnterpriseOne adapter</span></span>](../core/jd-edwards-enterpriseone-adapter.md)
* [<span data-ttu-id="033ef-840">JD Edwards OneWorld 配接器</span><span class="sxs-lookup"><span data-stu-id="033ef-840">JD Edwards OneWorld adapter</span></span>](../core/jd-edwards-oneworld-adapter.md)
* [<span data-ttu-id="033ef-841">PeopleSoft Enterprise 配接器</span><span class="sxs-lookup"><span data-stu-id="033ef-841">PeopleSoft Enterprise adapter</span></span>](../core/peoplesoft-enterprise-adapter.md)
* [<span data-ttu-id="033ef-842">TIBCO Enterprise Message Service 配接器</span><span class="sxs-lookup"><span data-stu-id="033ef-842">TIBCO Enterprise Message Service adapter</span></span>](../core/tibco-enterprise-message-service-adapter.md)
* [<span data-ttu-id="033ef-843">TIBCO Rendezvous 配接器</span><span class="sxs-lookup"><span data-stu-id="033ef-843">TIBCO Rendezvous adapter</span></span>](../core/tibco-rendezvous-adapter.md)
