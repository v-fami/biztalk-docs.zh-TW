---
title: "使用配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: adapters
ms.assetid: afdfa70e-5929-4746-99b4-e76274aa5c88
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18ffc3c198cbd6fc26290908dfcc3a90b2c8a62a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-adapters"></a><span data-ttu-id="1ec65-102">使用配接器</span><span class="sxs-lookup"><span data-stu-id="1ec65-102">Using Adapters</span></span>
<span data-ttu-id="1ec65-103">本節包含有關配接器的完整資訊。</span><span class="sxs-lookup"><span data-stu-id="1ec65-103">This section contains comprehensive information about adapters.</span></span> <span data-ttu-id="1ec65-104">描述如何在 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中使用配接器，以及如何為每個配接器設定配接器處理常式、傳送埠以及接收位置。</span><span class="sxs-lookup"><span data-stu-id="1ec65-104">It describes how adapters are used in Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and how to configure adapter handlers, send ports, and receive locations for each adapter.</span></span> <span data-ttu-id="1ec65-105">它提供的批次支援資訊可協助您瞭解與使用 BizTalk 解決方案中的原生配接器。</span><span class="sxs-lookup"><span data-stu-id="1ec65-105">It provides batching support information to help you understand and use the native adapters in your BizTalk solution.</span></span>  
  
 <span data-ttu-id="1ec65-106">使用配接器屬性頁的鍵盤快速鍵的相關資訊，請參閱[配接器屬性頁鍵盤快速鍵](../core/adapter-property-page-keyboard-shortcuts.md)。</span><span class="sxs-lookup"><span data-stu-id="1ec65-106">For information about using the keyboard shortcuts for the adapter property pages, see [Adapter Property Page Keyboard Shortcuts](../core/adapter-property-page-keyboard-shortcuts.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1ec65-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="1ec65-107">In This Section</span></span>  
  
-   [<span data-ttu-id="1ec65-108">在 BizTalk Server 配接器</span><span class="sxs-lookup"><span data-stu-id="1ec65-108">Adapters in BizTalk Server</span></span>](../core/adapters-in-biztalk-server.md)  
  
-   [<span data-ttu-id="1ec65-109">動態傳送埠處理常式是可設定</span><span class="sxs-lookup"><span data-stu-id="1ec65-109">Dynamic Send Port Handler is Configurable</span></span>](../core/dynamic-send-port-handler-is-configurable.md)  
  
-   [<span data-ttu-id="1ec65-110">配接器的安全性考量</span><span class="sxs-lookup"><span data-stu-id="1ec65-110">Security Considerations for Adapters</span></span>](../core/security-considerations-for-adapters.md)  
  
-   [<span data-ttu-id="1ec65-111">SB Messaging 配接器</span><span class="sxs-lookup"><span data-stu-id="1ec65-111">SB-Messaging adapter</span></span>](../core/sb-messaging-adapter.md)  
  
-   [<span data-ttu-id="1ec65-112">File 配接器</span><span class="sxs-lookup"><span data-stu-id="1ec65-112">File adapter</span></span>](../core/file-adapter.md)  
  
-   [<span data-ttu-id="1ec65-113">FTP 配接器</span><span class="sxs-lookup"><span data-stu-id="1ec65-113">FTP adapter</span></span>](../core/ftp-adapter.md)  

- [<span data-ttu-id="1ec65-114">Logic Apps 配接器</span><span class="sxs-lookup"><span data-stu-id="1ec65-114">Logic App adapter</span></span>](../core/logic-app-adapter.md)
  
-   [<span data-ttu-id="1ec65-115">SFTP 配接器</span><span class="sxs-lookup"><span data-stu-id="1ec65-115">SFTP adapter</span></span>](../core/sftp-adapter.md)  
  
-   [<span data-ttu-id="1ec65-116">HTTP 配接器</span><span class="sxs-lookup"><span data-stu-id="1ec65-116">HTTP adapter</span></span>](../core/http-adapter.md)  
  
-   [<span data-ttu-id="1ec65-117">JD Edwards EnterpriseOne 配接器</span><span class="sxs-lookup"><span data-stu-id="1ec65-117">JD Edwards EnterpriseOne adapter</span></span>](../core/jd-edwards-enterpriseone-adapter.md) 
  
-   [<span data-ttu-id="1ec65-118">JD Edwards OneWorld 配接器</span><span class="sxs-lookup"><span data-stu-id="1ec65-118">JD Edwards OneWorld adapter</span></span>](../core/jd-edwards-oneworld-adapter.md)  
  
-   [<span data-ttu-id="1ec65-119">Oracle E-business Suite ODBC 配接器</span><span class="sxs-lookup"><span data-stu-id="1ec65-119">Oracle E-Business Suite ODBC adapter</span></span>](../core/oracle-e-business-suite-odbc-adapter.md)  
  
-   [<span data-ttu-id="1ec65-120">Oracle 資料庫 ODBC 配接器</span><span class="sxs-lookup"><span data-stu-id="1ec65-120">Oracle Database ODBC adapter</span></span>](../core/oracle-database-odbc-adapter.md)  
  
-   [<span data-ttu-id="1ec65-121">PeopleSoft Enterprise 配接器</span><span class="sxs-lookup"><span data-stu-id="1ec65-121">PeopleSoft Enterprise adapter</span></span>](../core/peoplesoft-enterprise-adapter.md)  
  
-   [<span data-ttu-id="1ec65-122">Siebel eBusiness 應用程式配接器</span><span class="sxs-lookup"><span data-stu-id="1ec65-122">Siebel eBusiness Applications adapter</span></span>](../core/siebel-ebusiness-applications-adapter.md)  
  
-   [<span data-ttu-id="1ec65-123">TIBCO Enterprise Message Service 配接器</span><span class="sxs-lookup"><span data-stu-id="1ec65-123">TIBCO Enterprise Message Service adapter</span></span>](../core/tibco-enterprise-message-service-adapter.md)  
  
-   [<span data-ttu-id="1ec65-124">TIBCO Rendezvous 配接器</span><span class="sxs-lookup"><span data-stu-id="1ec65-124">TIBCO Rendezvous adapter</span></span>](../core/tibco-rendezvous-adapter.md)  
  
-   [<span data-ttu-id="1ec65-125">MQSeries 配接器</span><span class="sxs-lookup"><span data-stu-id="1ec65-125">MQSeries adapter</span></span>](../core/mqseries-adapter.md)  
  
-   [<span data-ttu-id="1ec65-126">MSMQ 配接器</span><span class="sxs-lookup"><span data-stu-id="1ec65-126">MSMQ adapter</span></span>](../core/msmq-adapter.md)  
  
-   [<span data-ttu-id="1ec65-127">POP3 配接器</span><span class="sxs-lookup"><span data-stu-id="1ec65-127">POP3 adapter</span></span>](../core/pop3-adapter.md)  
  
-   [<span data-ttu-id="1ec65-128">SAP 配接器</span><span class="sxs-lookup"><span data-stu-id="1ec65-128">SAP adapter</span></span>](../core/sap-adapter.md)  
  
-   [<span data-ttu-id="1ec65-129">SMTP 配接器</span><span class="sxs-lookup"><span data-stu-id="1ec65-129">SMTP adapter</span></span>](../core/smtp-adapter.md)  
  
-   [<span data-ttu-id="1ec65-130">SOAP 配接器</span><span class="sxs-lookup"><span data-stu-id="1ec65-130">SOAP adapter</span></span>](../core/soap-adapter.md)  
  
-   [<span data-ttu-id="1ec65-131">SQL 配接器</span><span class="sxs-lookup"><span data-stu-id="1ec65-131">SQL adapter</span></span>](../core/sql-adapter.md)  
  
-   [<span data-ttu-id="1ec65-132">Windows SharePoint Services 配接器</span><span class="sxs-lookup"><span data-stu-id="1ec65-132">Windows SharePoint Services adapter</span></span>](../core/windows-sharepoint-services-adapter.md)  
  
-   [<span data-ttu-id="1ec65-133">WCF 配接器</span><span class="sxs-lookup"><span data-stu-id="1ec65-133">WCF adapters</span></span>](../core/wcf-adapters.md)  
  
-   [<span data-ttu-id="1ec65-134">建立和刪除配接器處理常式</span><span class="sxs-lookup"><span data-stu-id="1ec65-134">Creating and Deleting Adapter Handlers</span></span>](../core/creating-and-deleting-adapter-handlers.md)  
  
-   [<span data-ttu-id="1ec65-135">影響配接器效能的組態參數</span><span class="sxs-lookup"><span data-stu-id="1ec65-135">Configuration Parameters that Affect Adapter Performance</span></span>](../core/configuration-parameters-that-affect-adapter-performance.md)  
  
-   [<span data-ttu-id="1ec65-136">疑難排解 BizTalk Server 配接器</span><span class="sxs-lookup"><span data-stu-id="1ec65-136">Troubleshooting BizTalk Server Adapters</span></span>](../core/troubleshooting-biztalk-server-adapters.md)  
  
-   [<span data-ttu-id="1ec65-137">其他配接器資訊</span><span class="sxs-lookup"><span data-stu-id="1ec65-137">Additional Adapter Information</span></span>](../core/additional-adapter-information.md)