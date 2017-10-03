---
title: "閱讀有關資料提供者型別在 SAP 連接字串 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data Provider for SAP, connection string
- ADO, connection string
ms.assetid: 7a46eaae-604f-4bae-924b-9f6d43a6e8a0
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b1a27fa8b09addc7874e6056f0b467c7f874a41e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="read-about-data-provider-types-for-the-sap-connection-string"></a><span data-ttu-id="d322d-102">閱讀有關資料提供者型別在 SAP 連接字串</span><span class="sxs-lookup"><span data-stu-id="d322d-102">Read about Data Provider types for the SAP Connection String</span></span>
<span data-ttu-id="d322d-103">若要建立 SAP 系統的連接能力，ADO.NET 用戶端必須在連接字串的形式指定 SAP 連接屬性。</span><span class="sxs-lookup"><span data-stu-id="d322d-103">To establish connectivity to an SAP system, ADO.NET clients must specify the SAP connection properties in the form of a connection string.</span></span> <span data-ttu-id="d322d-104">在 SAP ADO 連接字串的格式看起來像：</span><span class="sxs-lookup"><span data-stu-id="d322d-104">The format for the SAP ADO connection string looks like:</span></span>  
  
```  
[Property1]=[Value1];[Property2]=[Value2];....  
```  
  
 <span data-ttu-id="d322d-105">連接字串來連接 SAP 系統使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]可以有下列類型：</span><span class="sxs-lookup"><span data-stu-id="d322d-105">The connection string to connect to an SAP system using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] can have the following types:</span></span>  
  
-   <span data-ttu-id="d322d-106">**類型 a:**應用程式主機型的連線所在連接 URI 會指定透過此應用程式伺服器[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]連接到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="d322d-106">**TYPE A:** An application host–based connection in which the connection URI specifies an application server through which the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] connects to the SAP system.</span></span>  
  
-   <span data-ttu-id="d322d-107">**類型 b:**連線 URI 中指定的郵件伺服器的負載平衡的連接[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]連接到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="d322d-107">**TYPE B:** A load-balanced connection in which the connection URI specifies a message server through which the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] connects to the SAP system.</span></span>  
  
-   <span data-ttu-id="d322d-108">**類型 d:**目的地型的連線，連線 URI 中指定包含 SAP 系統的連接參數 saprfc.ini 檔案中的目的地。</span><span class="sxs-lookup"><span data-stu-id="d322d-108">**TYPE D:** A destination-based connection in which the connection URI specifies a destination in the saprfc.ini file that contains the connection parameters for the SAP system.</span></span>  
  
 <span data-ttu-id="d322d-109">下表描述這些連線指定連線 URI 中的方式。</span><span class="sxs-lookup"><span data-stu-id="d322d-109">The following table describes how these connections are specified in the connection URI.</span></span>  
  
|<span data-ttu-id="d322d-110">TYPE</span><span class="sxs-lookup"><span data-stu-id="d322d-110">TYPE</span></span>|<span data-ttu-id="d322d-111">屬性 1</span><span class="sxs-lookup"><span data-stu-id="d322d-111">Property 1</span></span>|<span data-ttu-id="d322d-112">屬性 2</span><span class="sxs-lookup"><span data-stu-id="d322d-112">Property 2</span></span>|<span data-ttu-id="d322d-113">Description</span><span class="sxs-lookup"><span data-stu-id="d322d-113">Description</span></span>|  
|----------|----------------|----------------|-----------------|  
|<span data-ttu-id="d322d-114">只有在次要複本設定成手動容錯移轉模式，而且至少一個次要複本目前與主要複本 SYNCHRONIZED 時，</span><span class="sxs-lookup"><span data-stu-id="d322d-114">A</span></span>|<span data-ttu-id="d322d-115">ASHOST （應用程式伺服器主控件）</span><span class="sxs-lookup"><span data-stu-id="d322d-115">ASHOST (Application Server Host)</span></span>|<span data-ttu-id="d322d-116">SYSNR （SAP 系統編號）</span><span class="sxs-lookup"><span data-stu-id="d322d-116">SYSNR (SAP System Number)</span></span>|<span data-ttu-id="d322d-117">指定應用程式的主機型連接。</span><span class="sxs-lookup"><span data-stu-id="d322d-117">Specifies an application host-based connection.</span></span>|  
|<span data-ttu-id="d322d-118">B</span><span class="sxs-lookup"><span data-stu-id="d322d-118">B</span></span>|<span data-ttu-id="d322d-119">MSHOST （郵件伺服器主機）</span><span class="sxs-lookup"><span data-stu-id="d322d-119">MSHOST (Message Server Host)</span></span>|<span data-ttu-id="d322d-120">R3NAME （SAP R3 名稱）</span><span class="sxs-lookup"><span data-stu-id="d322d-120">R3NAME (SAP R3 Name)</span></span>|<span data-ttu-id="d322d-121">指定負載平衡到郵件伺服器的連線。</span><span class="sxs-lookup"><span data-stu-id="d322d-121">Specifies a load balancing connection through a message server.</span></span> <span data-ttu-id="d322d-122">對負載平衡連接，您可以指定選用的伺服器群組。</span><span class="sxs-lookup"><span data-stu-id="d322d-122">For a load balancing connection, an optional server group can be specified.</span></span>|  
|<span data-ttu-id="d322d-123">D</span><span class="sxs-lookup"><span data-stu-id="d322d-123">D</span></span>|<span data-ttu-id="d322d-124">目的地 （包含 saprfc.ini 檔案中的連接參數的目的地）</span><span class="sxs-lookup"><span data-stu-id="d322d-124">DEST (Destination that contains the connection parameters in the saprfc.ini file)</span></span>|-|<span data-ttu-id="d322d-125">指定目的地型連線。</span><span class="sxs-lookup"><span data-stu-id="d322d-125">Specifies a destination-based connection.</span></span> <span data-ttu-id="d322d-126">SAP 連接參數會包含在 saprfc.ini 檔案中指定的目的地。</span><span class="sxs-lookup"><span data-stu-id="d322d-126">The SAP connection parameters are contained in the specified destination in the saprfc.ini file.</span></span> <span data-ttu-id="d322d-127">目的地中，可以指定只有類型 A 和 B 類型的連線。</span><span class="sxs-lookup"><span data-stu-id="d322d-127">Only TYPE A and TYPE B connections can be specified in the destination.</span></span> <span data-ttu-id="d322d-128">**注意：**如果 saprfc.ini 檔案中指定連接值，請確定此檔案位於相同的資料夾以存取檔案的.exe 或所需的 SAP 系統的標準位置。</span><span class="sxs-lookup"><span data-stu-id="d322d-128">**Note:**  If you specify connection values in the saprfc.ini file, make sure the file is located in the same folder as the .exe that accesses the file or at a standard location as required by the SAP system.</span></span> <span data-ttu-id="d322d-129">如需詳細資訊，請參閱 SAP 文件集。</span><span class="sxs-lookup"><span data-stu-id="d322d-129">For more information, see the SAP documentation.</span></span>|  
  
 <span data-ttu-id="d322d-130">根據連接字串來連接 SAP 系統使用的連接類型[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]可以包含下列屬性。</span><span class="sxs-lookup"><span data-stu-id="d322d-130">Based on the type of connection, the connection string to connect to an SAP system using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] can contain the following properties.</span></span>  
  
|<span data-ttu-id="d322d-131">屬性</span><span class="sxs-lookup"><span data-stu-id="d322d-131">Property</span></span>|<span data-ttu-id="d322d-132">用於型別</span><span class="sxs-lookup"><span data-stu-id="d322d-132">Used for TYPE</span></span>|<span data-ttu-id="d322d-133">Description</span><span class="sxs-lookup"><span data-stu-id="d322d-133">Description</span></span>|  
|--------------|-------------------|-----------------|  
|<span data-ttu-id="d322d-134">應用程式伺服器主機 (ASHOST)</span><span class="sxs-lookup"><span data-stu-id="d322d-134">Application Server Host (ASHOST)</span></span>|<span data-ttu-id="d322d-135">只有在次要複本設定成手動容錯移轉模式，而且至少一個次要複本目前與主要複本 SYNCHRONIZED 時，</span><span class="sxs-lookup"><span data-stu-id="d322d-135">A</span></span>|<span data-ttu-id="d322d-136">SAP 應用程式伺服器主機名稱。</span><span class="sxs-lookup"><span data-stu-id="d322d-136">Name of the SAP application server host.</span></span>|  
|<span data-ttu-id="d322d-137">系統編號 (SYSNR)</span><span class="sxs-lookup"><span data-stu-id="d322d-137">System Number (SYSNR)</span></span>|<span data-ttu-id="d322d-138">只有在次要複本設定成手動容錯移轉模式，而且至少一個次要複本目前與主要複本 SYNCHRONIZED 時，</span><span class="sxs-lookup"><span data-stu-id="d322d-138">A</span></span>|<span data-ttu-id="d322d-139">SAP 系統編號</span><span class="sxs-lookup"><span data-stu-id="d322d-139">The SAP system number</span></span>|  
|<span data-ttu-id="d322d-140">應用程式伺服器群組名稱 （群組）</span><span class="sxs-lookup"><span data-stu-id="d322d-140">Application Server Group Name (GROUP)</span></span>|<span data-ttu-id="d322d-141">B</span><span class="sxs-lookup"><span data-stu-id="d322d-141">B</span></span>|<span data-ttu-id="d322d-142">SAP 伺服器群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="d322d-142">Name of the SAP server group.</span></span> <span data-ttu-id="d322d-143">這是選用的應用程式在負載平衡連接的伺服器群組。</span><span class="sxs-lookup"><span data-stu-id="d322d-143">This is an optional group of application servers in a load balancing connection.</span></span>|  
|<span data-ttu-id="d322d-144">訊息伺服器主機 (MSHOST)</span><span class="sxs-lookup"><span data-stu-id="d322d-144">Message Server Host (MSHOST)</span></span>|<span data-ttu-id="d322d-145">B</span><span class="sxs-lookup"><span data-stu-id="d322d-145">B</span></span>|<span data-ttu-id="d322d-146">SAP 訊息伺服器主機名稱</span><span class="sxs-lookup"><span data-stu-id="d322d-146">Name of the SAP message server host</span></span>|  
|<span data-ttu-id="d322d-147">訊息伺服器服務 (MSSERV)</span><span class="sxs-lookup"><span data-stu-id="d322d-147">Message Server Service (MSSERV)</span></span>|<span data-ttu-id="d322d-148">B</span><span class="sxs-lookup"><span data-stu-id="d322d-148">B</span></span>|<span data-ttu-id="d322d-149">SAP 訊息伺服器服務中所指定的名稱\<系統磁碟機 >: \WINDOWS\system32\drivers\etc\services 檔案。</span><span class="sxs-lookup"><span data-stu-id="d322d-149">Name of the SAP message server service as specified in the \<system drive>:\WINDOWS\system32\drivers\etc\services file.</span></span> <span data-ttu-id="d322d-150">如果您未指定值，[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]假設這是 「 sapms\</ 3 系統名稱 >"。</span><span class="sxs-lookup"><span data-stu-id="d322d-150">If you do not specify a value, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] assumes this to be "sapms\<R/3 system name>".</span></span> <span data-ttu-id="d322d-151">例如，如果 DV1 / 3 系統名稱，此配接器會假設訊息伺服器服務名稱是"sapmsDV1"。</span><span class="sxs-lookup"><span data-stu-id="d322d-151">For example, if the R/3 system name is DV1, the adapter assumes the message server service name to be "sapmsDV1".</span></span><br /><br /> <span data-ttu-id="d322d-152">不過，如果服務檔案中的項目不同，您必須指定該值。</span><span class="sxs-lookup"><span data-stu-id="d322d-152">However, if the entry in the services file is different, you must specify that value.</span></span>|  
|<span data-ttu-id="d322d-153">/ 3 系統名稱 (R3NAME)</span><span class="sxs-lookup"><span data-stu-id="d322d-153">R/3 System Name (R3NAME)</span></span>|<span data-ttu-id="d322d-154">B</span><span class="sxs-lookup"><span data-stu-id="d322d-154">B</span></span>|<span data-ttu-id="d322d-155">SAP / 3 的名稱。</span><span class="sxs-lookup"><span data-stu-id="d322d-155">The SAP R/3 name.</span></span>|  
|<span data-ttu-id="d322d-156">目的地 （目的地）</span><span class="sxs-lookup"><span data-stu-id="d322d-156">Destination (DEST)</span></span>|<span data-ttu-id="d322d-157">D</span><span class="sxs-lookup"><span data-stu-id="d322d-157">D</span></span>|<span data-ttu-id="d322d-158">從 saprfc.ini 檔案中挑選的連接參數。</span><span class="sxs-lookup"><span data-stu-id="d322d-158">Picks the connection parameters from the saprfc.ini file.</span></span>|  
|<span data-ttu-id="d322d-159">用戶端 （用戶端）</span><span class="sxs-lookup"><span data-stu-id="d322d-159">Client (CLIENT)</span></span>|<span data-ttu-id="d322d-160">A、 B、 D</span><span class="sxs-lookup"><span data-stu-id="d322d-160">A,B,D</span></span>|<span data-ttu-id="d322d-161">SAP 用戶端數目</span><span class="sxs-lookup"><span data-stu-id="d322d-161">The SAP client number</span></span>|  
|<span data-ttu-id="d322d-162">語言 (l a n g)</span><span class="sxs-lookup"><span data-stu-id="d322d-162">Language (Lang)</span></span>|<span data-ttu-id="d322d-163">A、 B、 D</span><span class="sxs-lookup"><span data-stu-id="d322d-163">A,B,D</span></span>|<span data-ttu-id="d322d-164">語言</span><span class="sxs-lookup"><span data-stu-id="d322d-164">Language</span></span>|  
|<span data-ttu-id="d322d-165">密碼 （密碼）</span><span class="sxs-lookup"><span data-stu-id="d322d-165">Password (PASSWD)</span></span>|<span data-ttu-id="d322d-166">A、 B、 D</span><span class="sxs-lookup"><span data-stu-id="d322d-166">A,B,D</span></span>|<span data-ttu-id="d322d-167">SAP 使用者密碼</span><span class="sxs-lookup"><span data-stu-id="d322d-167">The SAP user password</span></span>|  
|<span data-ttu-id="d322d-168">使用者名稱 （使用者）</span><span class="sxs-lookup"><span data-stu-id="d322d-168">Username (USER)</span></span>|<span data-ttu-id="d322d-169">A、 B、 D</span><span class="sxs-lookup"><span data-stu-id="d322d-169">A,B,D</span></span>|<span data-ttu-id="d322d-170">要連接至 SAP 系統的使用者名稱</span><span class="sxs-lookup"><span data-stu-id="d322d-170">The user name to connect to an SAP system</span></span>|  
|<span data-ttu-id="d322d-171">啟用偵錯 (AbapDebug) 的 SAP GUI</span><span class="sxs-lookup"><span data-stu-id="d322d-171">Enable SAP GUI debugging (AbapDebug)</span></span>|<span data-ttu-id="d322d-172">A、 B、 D</span><span class="sxs-lookup"><span data-stu-id="d322d-172">A,B,D</span></span>|<span data-ttu-id="d322d-173">選擇性參數，指定是否從偵錯 ABAP[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]已啟用和配接器是否使用 SAP GUI 偵錯。</span><span class="sxs-lookup"><span data-stu-id="d322d-173">Optional parameter that specifies whether ABAP debugging from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] is enabled and whether the adapter uses the SAP GUI for debugging.</span></span> <span data-ttu-id="d322d-174">這個值可以是 True 或 False。如果為 True，ABAP 偵錯已啟用，而且 SAP GUI 會開啟。</span><span class="sxs-lookup"><span data-stu-id="d322d-174">The value can be True or False; if True, ABAP debugging is enabled and the SAP GUI is opened.</span></span> <span data-ttu-id="d322d-175">預設值是 False。</span><span class="sxs-lookup"><span data-stu-id="d322d-175">The default is False.</span></span>|  
|<span data-ttu-id="d322d-176">追蹤 RFC SDK(RfcSdkTrace)</span><span class="sxs-lookup"><span data-stu-id="d322d-176">Trace RFC SDK(RfcSdkTrace)</span></span>|<span data-ttu-id="d322d-177">A、 B、 D</span><span class="sxs-lookup"><span data-stu-id="d322d-177">A,B,D</span></span>|<span data-ttu-id="d322d-178">選擇性參數，指定是否要啟用 RFC 程式庫的追蹤。</span><span class="sxs-lookup"><span data-stu-id="d322d-178">Optional parameter that specifies whether RFC library tracing is enabled.</span></span> <span data-ttu-id="d322d-179">這個值可以是 True 或 False。如果為 True，則會啟用 RFC 程式庫追蹤。</span><span class="sxs-lookup"><span data-stu-id="d322d-179">The value can be True or False; if True, RFC Library tracing is enabled.</span></span> <span data-ttu-id="d322d-180">預設值是 False。</span><span class="sxs-lookup"><span data-stu-id="d322d-180">The default is False.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="d322d-181">屬性資料行中的括號內提供的值是必須同時提供連線 URI，透過程式設計的解決方案指定的連接屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="d322d-181">The values provided within parentheses in the Property column are the name of the connection properties that must be specified while providing the connection URI through a programming solution.</span></span> <span data-ttu-id="d322d-182">不過，如果您使用的 DDEX 外掛程式或 SQL Server 匯入和匯出精靈將 ADO 介面，連接屬性會列為好記的名稱。</span><span class="sxs-lookup"><span data-stu-id="d322d-182">However, if you are using the DDEX plug-in or SQL Server Import and Export wizard to use the ADO interface, the connection properties are listed as friendly names.</span></span>  
  
## <a name="example-connection-string-for-type-a"></a><span data-ttu-id="d322d-183">類型的範例連接字串的</span><span class="sxs-lookup"><span data-stu-id="d322d-183">Example Connection String for TYPE A</span></span>  
 <span data-ttu-id="d322d-184">輸入的範例連接字串應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="d322d-184">An example connection string for TYPE A would look like:</span></span>  
  
```  
TYPE=A; ASHOST=SAPSERVER; SYSNR=00; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=YourPassword;  
```  
  
> [!NOTE]
>  <span data-ttu-id="d322d-185">根據預設[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]一律會考慮類型 a 的連接字串</span><span class="sxs-lookup"><span data-stu-id="d322d-185">By default the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] always considers the connection string to be of TYPE A.</span></span>  
  
## <a name="example-connection-string-for-type-b"></a><span data-ttu-id="d322d-186">型別 B 的範例連接字串</span><span class="sxs-lookup"><span data-stu-id="d322d-186">Example Connection String for TYPE B</span></span>  
 <span data-ttu-id="d322d-187">型別 B 的範例連接字串應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="d322d-187">An example connection string for TYPE B would look like:</span></span>  
  
```  
TYPE=B; R3NAME=NAME1; GROUP=ADAPTER; MSHOST=MSSERVER; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=YourPassword;  
```  
  
## <a name="example-connection-string-for-type-d"></a><span data-ttu-id="d322d-188">類型 D 的範例連接字串</span><span class="sxs-lookup"><span data-stu-id="d322d-188">Example Connection String for TYPE D</span></span>  
 <span data-ttu-id="d322d-189">類型 D 的範例連接字串應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="d322d-189">An example connection string for TYPE D would look like:</span></span>  
  
```  
TYPE=D; DEST=TESTSAPSRV; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=YourPassword;  
```  
  
 <span data-ttu-id="d322d-190">範例 saprfc.ini 檔案類似：</span><span class="sxs-lookup"><span data-stu-id="d322d-190">A sample saprfc.ini file resembles:</span></span>  
  
```  
DEST=TESTSAPSRV  
TYPE=A  
ASHOST=ADAPSAP47  
SYSNR=00  
```  
  
 <span data-ttu-id="d322d-191">如需 saprfc.ini 檔案的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=91457](http://go.microsoft.com/fwlink/?LinkId=91457)。</span><span class="sxs-lookup"><span data-stu-id="d322d-191">For more information about the saprfc.ini file, see [http://go.microsoft.com/fwlink/?LinkId=91457](http://go.microsoft.com/fwlink/?LinkId=91457).</span></span>  
  
 <span data-ttu-id="d322d-192">所有這三種連線類型的密碼必須包含雙引號。</span><span class="sxs-lookup"><span data-stu-id="d322d-192">The password for all three connection types must not contain double quotation marks.</span></span> <span data-ttu-id="d322d-193">不過，如果密碼會包含任何特殊字元，密碼必須括在雙引號內。</span><span class="sxs-lookup"><span data-stu-id="d322d-193">However, if the password contains any other special characters, the password must be enclosed within double quotation marks.</span></span> <span data-ttu-id="d322d-194">例如：</span><span class="sxs-lookup"><span data-stu-id="d322d-194">For example:</span></span>  
  
```  
ASHOST=SAPSERVER; SYSNR=00; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=",@/:;_ \\";  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="d322d-195">您必須指定連接參數只能有一個連線類型 A、 B 或 d。例如，如果您在連接字串中指定的應用程式伺服器主機，您必須指定郵件伺服器主機名稱或 R3NAME。</span><span class="sxs-lookup"><span data-stu-id="d322d-195">You must specify the connection parameters for only one connection TYPE A, B, or D. For example, if you specify the Application Server Host in the connection string, you must not specify a Message Server Host name or the R3NAME.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d322d-196">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d322d-196">See Also</span></span>  
 [<span data-ttu-id="d322d-197">使用.NET Framework Data Provider for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="d322d-197">Use the .NET Framework Data Provider for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md)