---
title: "設定 PeopleSoft 傳輸屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- setting transport properties
- transport properties, setting
ms.assetid: 44b5f015-59f1-43a3-9673-a5ba40266843
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ecfd221d28312e84dcbaf7d8c83abc4f5191f54
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="setting-peoplesoft-transport-properties"></a><span data-ttu-id="fc243-102">設定 PeopleSoft 傳輸屬性</span><span class="sxs-lookup"><span data-stu-id="fc243-102">Setting PeopleSoft Transport Properties</span></span>
<span data-ttu-id="fc243-103">PeopleSoft 傳輸屬性用於設計和執行階段。</span><span class="sxs-lookup"><span data-stu-id="fc243-103">The PeopleSoft transport properties are used for design and run time.</span></span> <span data-ttu-id="fc243-104">在**傳輸屬性**對話方塊中，您設定的連接和認證參數特定伺服器系統和您嘗試存取的物件。</span><span class="sxs-lookup"><span data-stu-id="fc243-104">In the **Transport Properties** dialog box, you set the connection and credential parameters specific to the server system and the objects you are trying to access.</span></span>  
  
 ![](../core/media/peop-peoplesofttransportpropertiess.gif "Peop_PeopleSoftTransportPropertiess")  
  
### <a name="to-create-a-send-port"></a><span data-ttu-id="fc243-105">建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="fc243-105">To create a send port</span></span>  
  
1.  <span data-ttu-id="fc243-106">展開 [配接器必要屬性]，並填入連線至 PeopleSoft 伺服器的所有必要資訊。</span><span class="sxs-lookup"><span data-stu-id="fc243-106">Expand the Adapter Required Properties and fill in all required information for connection to the PeopleSoft server.</span></span>  
  
     <span data-ttu-id="fc243-107">您必須設定組態參數，Microsoft BizTalk Adapter for PeopleSoft Enterprise 才能連線至 PeopleSoft Enterprise。</span><span class="sxs-lookup"><span data-stu-id="fc243-107">You must set configuration parameters to connect Microsoft BizTalk Adapter for PeopleSoft Enterprise to PeopleSoft Enterprise.</span></span> <span data-ttu-id="fc243-108">此資料區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="fc243-108">This data is case sensitive.</span></span>  
  
    |<span data-ttu-id="fc243-109">參數</span><span class="sxs-lookup"><span data-stu-id="fc243-109">Parameter</span></span>|<span data-ttu-id="fc243-110">Description</span><span class="sxs-lookup"><span data-stu-id="fc243-110">Description</span></span>|  
    |---------------|-----------------|  
    |`Application Server Path`|<span data-ttu-id="fc243-111">字串，表示執行 PeopleSoft Application Server 的電腦和接聽的連接埠。</span><span class="sxs-lookup"><span data-stu-id="fc243-111">A string representing the computer and port on which the PeopleSoft Application Server is running and listening.</span></span> <span data-ttu-id="fc243-112">PeopleSoft 8 應用程式的 URL 路徑的語法是 / / < 電腦名稱 >:\<連接埠 >。</span><span class="sxs-lookup"><span data-stu-id="fc243-112">The syntax of the URL path to the PeopleSoft 8 Application is //<computer_name>:\<port>.</span></span> <span data-ttu-id="fc243-113">詢問您的 PeopleSoft 系統管理員以\<連接埠 > 值。</span><span class="sxs-lookup"><span data-stu-id="fc243-113">Ask your PeopleSoft administrator for the \<port> value.</span></span> <span data-ttu-id="fc243-114">\<連接埠 > 值是 JOLT 通訊協定接聽程式通訊埠，不應用程式伺服器連接埠。</span><span class="sxs-lookup"><span data-stu-id="fc243-114">The \<port> value is the JOLT protocol listener port, not the App Server port.</span></span> <span data-ttu-id="fc243-115">預設 JOLT 連接埠為 9000。</span><span class="sxs-lookup"><span data-stu-id="fc243-115">The default JOLT port is 9000.</span></span>|  
    |`JAVA_HOME`|<span data-ttu-id="fc243-116">設定 JAVA_HOME 變數以指向 JDK 安裝，例如： **C:\j2sdk1.4.2_08**。</span><span class="sxs-lookup"><span data-stu-id="fc243-116">Set the JAVA_HOME variable to point to your JDK installation, for example: **C:\j2sdk1.4.2_08**.</span></span>|  
    |`Password`|<span data-ttu-id="fc243-117">如果您未選取**使用 SSO**，您必須設定 BizTalk Adapter for PeopleSoft Enterprise 能夠存取伺服器系統的認證參數。</span><span class="sxs-lookup"><span data-stu-id="fc243-117">If you did not select **Use SSO**, you must set credential parameters for the BizTalk Adapter for PeopleSoft Enterprise to access the server system.</span></span><br /><br /> <span data-ttu-id="fc243-118">字串，表示使用者用來登入 PeopleSoft 系統的密碼。</span><span class="sxs-lookup"><span data-stu-id="fc243-118">A string representing the user's password for logon to a PeopleSoft system.</span></span> <span data-ttu-id="fc243-119">字元不會顯示出來，而是以星號 (*) 表示。</span><span class="sxs-lookup"><span data-stu-id="fc243-119">The characters do not appear but are represented by asterisks (*).</span></span>|  
    |`PeopleSoft 8.x Jar Files`|<span data-ttu-id="fc243-120">若要使用 Ccmponent 介面 (僅限 PeopleSoft 8)，您必須更新 CLASSPATH 來包含 PeopleSoft 元件介面 jar 檔案。</span><span class="sxs-lookup"><span data-stu-id="fc243-120">To use Ccmponent interfaces (PeopleSoft 8 only) you must update your CLASSPATH to include the PeopleSoft Component Interface jar file.</span></span> <span data-ttu-id="fc243-121">例如： **< PeopleSoft_Home > \web\PSJOA\psjoa.jar**。</span><span class="sxs-lookup"><span data-stu-id="fc243-121">For example: **<PeopleSoft_Home>\web\PSJOA\psjoa.jar**.</span></span>|  
    |`User Name`|<span data-ttu-id="fc243-122">如果您未選取**使用 SSO**，您必須設定 BizTalk Adapter for PeopleSoft Enterprise 能夠存取伺服器系統的認證參數。</span><span class="sxs-lookup"><span data-stu-id="fc243-122">If you did not select **Use SSO**, you must set credential parameters for the BizTalk Adapter for PeopleSoft Enterprise to access the server system.</span></span><br /><br /> <span data-ttu-id="fc243-123">字串，表示登入 PeopleSoft 系統所需的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="fc243-123">A string representing a user name required for logon to a PeopleSoft system.</span></span>|  
  
2.  <span data-ttu-id="fc243-124">輸入**其他參數**時使用日期做為索引鍵的值; 它有不同的格式。</span><span class="sxs-lookup"><span data-stu-id="fc243-124">Enter an **Additional parameters** value when a date is used as a key; it has a different format.</span></span> <span data-ttu-id="fc243-125">YYYY-MM-DD 是預設格式。</span><span class="sxs-lookup"><span data-stu-id="fc243-125">YYYY-MM-DD is the default format.</span></span>  
  
3.  <span data-ttu-id="fc243-126">輸入**並行控制**值中代表的呼叫，例如 200，**同時呼叫數目上限**如有必要。</span><span class="sxs-lookup"><span data-stu-id="fc243-126">Enter a **Concurrency control** value representing the number of calls, for example 200, in **Max Concurrent Calls** if it is required.</span></span>  
  
     <span data-ttu-id="fc243-127">**同時呼叫數目上限**參數啟動的多載保護，如果後端伺服器無法處理的資料量。</span><span class="sxs-lookup"><span data-stu-id="fc243-127">The **Max Concurrent Calls** parameter activates an overload protection if the back-end server cannot process the amount of data.</span></span> <span data-ttu-id="fc243-128">同時呼叫是指配接器尚未回覆的要求。</span><span class="sxs-lookup"><span data-stu-id="fc243-128">A concurrent call is a request for which the adapter does not yet have a reply.</span></span> <span data-ttu-id="fc243-129">設定**同時呼叫數目上限**在輸送量超過後端處理能力。</span><span class="sxs-lookup"><span data-stu-id="fc243-129">Set **Max Concurrent Calls** in instances where the throughput exceeds back-end processing capabilities.</span></span>  
  
     <span data-ttu-id="fc243-130">此欄位 的預設值為 -1，表示不會提供保護 。</span><span class="sxs-lookup"><span data-stu-id="fc243-130">The default value for this field is -1, meaning no protection occurs.</span></span>  
  
     <span data-ttu-id="fc243-131">如果 BizTalk Server 提交要求至傳輸配接器的並行連線數目呼叫等於或超過設定的值**同時呼叫數目上限**、 送出要求會儲存，直到同時呼叫數目的執行緒若要減少設定值以下。</span><span class="sxs-lookup"><span data-stu-id="fc243-131">If BizTalk Server submits a request to the Transmit adapter, and the number of concurrent calls equals or exceeds the value set for **Max Concurrent Calls**, the thread submitting the request is saved until the concurrent calls number decreases to below the set value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc243-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc243-132">See Also</span></span>  
 [<span data-ttu-id="fc243-133">建立 PeopleSoft 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="fc243-133">Creating PeopleSoft Send Handlers</span></span>](../core/creating-peoplesoft-send-handlers.md)