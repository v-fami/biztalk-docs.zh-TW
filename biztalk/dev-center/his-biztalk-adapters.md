---
title: Host Integration Server 所隨附的 BizTalk 配接器 |Microsoft 文件
description: 他附的裝載應用程式、 主控件的檔案、 DB2 和 WebSphere MQ 的 BizTalk 配接器的概觀
author: MandiOhlinger
manager: anneta
ms.date: 10/10/2017
ms.prod: biztalk-server
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.author: mandia
ms.openlocfilehash: 26f2bf48c9a1268aace041776ff3895c8f3b3aa5
ms.sourcegitcommit: 75d35f6f230f0846c29a4b146c6d5b074e60b13c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2017
ms.locfileid: "22645178"
---
# <a name="biztalk-adapters-for-host-systems"></a><span data-ttu-id="e7455-103">主機系統的 BizTalk 配接器</span><span class="sxs-lookup"><span data-stu-id="e7455-103">BizTalk adapters for host systems</span></span>


## <a name="biztalk-adapter-for-host-applications"></a><span data-ttu-id="e7455-104">BizTalk Adapter for 主應用程式</span><span class="sxs-lookup"><span data-stu-id="e7455-104">BizTalk Adapter for Host Applications</span></span>

<span data-ttu-id="e7455-105">Microsoft BizTalk Adapter for 主應用程式可供 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="e7455-105">The Microsoft BizTalk Adapter for Host Applications is designed for BizTalk Server.</span></span> <span data-ttu-id="e7455-106">它基礎技術中 Microsoft 交易整合器 (TI) 對於 Windows-Initiated 處理，可讓現有 IBM 大型主機 zSeries （CICS 與 IMS） 或中階 iSeries (RPG) 伺服器程式的有效用戶端存取。</span><span class="sxs-lookup"><span data-stu-id="e7455-106">It is based on technology in Microsoft Transaction Integrator (TI) for Windows-Initiated Processing, which enables efficient client access to existing IBM mainframe zSeries (CICS and IMS) or midrange iSeries (RPG) server programs.</span></span> 

<span data-ttu-id="e7455-107">TI 設計工具會整合與 Visual Studio 和 BizTalk Server 解決方案，讓 IT 開發人員可以定義用戶端 proxy 時是高生產力，並建立 XSD 結構描述。</span><span class="sxs-lookup"><span data-stu-id="e7455-107">The TI design tools are integrated with Visual Studio and BizTalk Server solutions, enabling IT developers to be highly productive when defining the client proxy and creating the XSD schema.</span></span> <span data-ttu-id="e7455-108">對於 BizTalk Server 系統管理員，已增強現有的 TI 管理員、 Microsoft Management Console (MMC) 嵌入式管理單元，以改善可支援性和支援需要遠端 BizTalk Server 解決方案部署案例。</span><span class="sxs-lookup"><span data-stu-id="e7455-108">For BizTalk Server administrators, the existing TI Manager, Microsoft Management Console (MMC) snap-in, has been enhanced to improve supportability and support the required remote BizTalk Server solution deployment scenarios.</span></span>

<span data-ttu-id="e7455-109">請參閱[主應用程式的 BizTalk 配接器](https://msdn.microsoft.com/library/dn148497(BTS.80).aspx)。</span><span class="sxs-lookup"><span data-stu-id="e7455-109">See [BizTalk Adapter for Host Applications](https://msdn.microsoft.com/library/dn148497(BTS.80).aspx).</span></span> 

## <a name="biztalk-adapter-for-host-files"></a><span data-ttu-id="e7455-110">BizTalk Adapter for 主機檔案</span><span class="sxs-lookup"><span data-stu-id="e7455-110">BizTalk Adapter for Host Files</span></span>
<span data-ttu-id="e7455-111">Microsoft BizTalk Adapter for 主機檔案是可讓 IT 組織存取，並將資訊儲存在主機檔案系統，包括大型主機 zSeries VSAM 資料集和中階 iSeries 實體檔案中整合的進階的資料配接器。</span><span class="sxs-lookup"><span data-stu-id="e7455-111">The Microsoft BizTalk Adapter for Host Files is an advanced data adapter that enables IT organizations to access and integrate information stored in host file systems, including mainframe zSeries VSAM datasets and midrange iSeries physical files.</span></span> 

<span data-ttu-id="e7455-112">Visual Studio 設計工具用於 BizTalk Server 方案中定義中繼資料的對應主機程式說明檔案，然後匯出 BizTalk 配接器搭配使用以 XSD。</span><span class="sxs-lookup"><span data-stu-id="e7455-112">Visual Studio design tools are used within a BizTalk Server solution to define a metadata map of the host program-described files, which is then exported as XSD for use with the BizTalk adapter.</span></span> <span data-ttu-id="e7455-113">精靈已整合到 BizTalk Server 管理工具的組態，讓 IT 專業人員，來定義動態傳送埠和靜態和請求回應接收埠，根據一組精簡的 SQL 命令 (SELECT、 INSERT、 UPDATE、 DELETE).</span><span class="sxs-lookup"><span data-stu-id="e7455-113">The configuration wizards are integrated into the BizTalk Server administration tools, allowing IT professionals to define dynamic send ports and static and solicit response receive ports, based on a simplified set of SQL commands (SELECT, INSERT, UPDATE, DELETE).</span></span> 

<span data-ttu-id="e7455-114">此 BizTalk 配接器根據 SQL 會對應至非關聯式主機資料集和成員的主機檔案的 Microsoft.NET Framework 資料提供者。</span><span class="sxs-lookup"><span data-stu-id="e7455-114">This BizTalk adapter is based on the Microsoft .NET Framework Data Provider for Host Files that maps SQL to non-relational host datasets and members.</span></span> <span data-ttu-id="e7455-115">這項功能可更容易讀取和寫入主機檔案資料來源的非程式設計。</span><span class="sxs-lookup"><span data-stu-id="e7455-115">This makes it easier for non-programmers to read and write host file data sources.</span></span>

<span data-ttu-id="e7455-116">請參閱[BizTalk Adapter for 主機檔案](https://msdn.microsoft.com/library/dn150042(BTS.80).aspx)。</span><span class="sxs-lookup"><span data-stu-id="e7455-116">See [BizTalk Adapter for Host Files](https://msdn.microsoft.com/library/dn150042(BTS.80).aspx).</span></span>

## <a name="biztalk-adapter-for-db2"></a><span data-ttu-id="e7455-117">BizTalk Adapter for DB2</span><span class="sxs-lookup"><span data-stu-id="e7455-117">BizTalk Adapter for DB2</span></span>
<span data-ttu-id="e7455-118">Microsoft BizTalk Adapter for DB2 是可讓 IT 專業人員能夠存取儲存在 IBM DB2 資料庫伺服器平台、 IBM 大型主機 zSeries 和中階 iSeries (DB2/400)，以及 IBM DB2 電腦的遠端主機上的重要資料的關聯式資料庫介面卡Universal Database (UDB) 開啟的平台上。</span><span class="sxs-lookup"><span data-stu-id="e7455-118">The Microsoft BizTalk Adapter for DB2 is a relational database adapter that enables IT professionals to access vital data stored in IBM DB2 database servers on remote host computing platforms, IBM mainframe zSeries and midrange iSeries (DB2/400), and also IBM DB2 Universal Database (UDB) on open platforms.</span></span> 

<span data-ttu-id="e7455-119">使用標準 SQL 命令和內建於 BizTalk Server 管理工具設定精靈，IT 專業人員可以建立解決方案會讀取和寫入至 DB2，而不需要資料庫程式設計。</span><span class="sxs-lookup"><span data-stu-id="e7455-119">Using standard SQL commands and a configuration wizard built into BizTalk Server administration tools, IT professionals can create solutions that read and write to DB2 without any need for database programming.</span></span> <span data-ttu-id="e7455-120">DB2 配接器，這根據 Microsoft.NET Framework Data Provider for DB2，支援廣泛的功能，包括動態傳送埠或靜態請求回應接收埠。</span><span class="sxs-lookup"><span data-stu-id="e7455-120">The DB2 adapter, which is based on the Microsoft .NET Framework Data Provider for DB2, supports a broad range of functions, including dynamic send ports, and static and solicit response receive ports.</span></span>

<span data-ttu-id="e7455-121">請參閱[BizTalk Adapter for DB2](https://msdn.microsoft.com/library/dn150160(BTS.80).aspx)。</span><span class="sxs-lookup"><span data-stu-id="e7455-121">See [BizTalk Adapter for DB2](https://msdn.microsoft.com/library/dn150160(BTS.80).aspx).</span></span>

## <a name="biztalk-adapter-for-websphere-mq"></a><span data-ttu-id="e7455-122">WebSphere MQ 的 BizTalk 配接器</span><span class="sxs-lookup"><span data-stu-id="e7455-122">BizTalk Adapter for WebSphere MQ</span></span>
<span data-ttu-id="e7455-123">Microsoft BizTalk Adapter for WebSphere MQ （用戶端為基礎） 使用 IBM WebSphere MQ Client （基底用戶端） 和 IBM WebSphere MQ 擴充交易用戶端 （擴充用戶端） 應用程式開發介面來與遠端 MQSeries 佇列管理員通訊。</span><span class="sxs-lookup"><span data-stu-id="e7455-123">The Microsoft BizTalk Adapter for WebSphere MQ (Client-Based) uses IBM WebSphere MQ Client (Base-Client) and IBM WebSphere MQ Extended Transactional Client (Extended-Client) APIs to communicate with remote MQSeries Queue Managers.</span></span> <span data-ttu-id="e7455-124">配接器可以讓 BizTalk Server 會直接與 MQSeries 佇列管理員在非 Windows 作業系統上部署而不需要部署和管理 WebSphere MQ Server for Windows，有效率地與交換訊息的業務通訊整個企業的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e7455-124">The adapter enables BizTalk Server to communicate directly with MQSeries Queue Managers deployed on non-Windows operating systems, without needing to deploy and manage WebSphere MQ Server for Windows, to efficiently exchange messages with line-of-business applications across the enterprise.</span></span> 

<span data-ttu-id="e7455-125">基底用戶端搭配使用時，配接器會提供非交易式訊息處理保證的訊息傳遞。</span><span class="sxs-lookup"><span data-stu-id="e7455-125">When used with the Base-Client, the adapter provides non-transactional message processing, guaranteeing only the delivery of messages.</span></span> <span data-ttu-id="e7455-126">負責接收端上之應用程式，來處理重複的訊息。</span><span class="sxs-lookup"><span data-stu-id="e7455-126">It is the responsibility of the application on the receiving end to handle any duplicate messages.</span></span> <span data-ttu-id="e7455-127">延伸用戶端搭配使用時，配接器會提供交易式訊息處理，以保證訊息傳遞一次和-僅限-一次。</span><span class="sxs-lookup"><span data-stu-id="e7455-127">When used with the Extended-Client, the adapter provides transactional message processing to guarantee once-and-only-once delivery of messages.</span></span>

<span data-ttu-id="e7455-128">請參閱[WebSphere MQ 的 BizTalk 配接器](https://msdn.microsoft.com/library/dn191830(BTS.80).aspx)。</span><span class="sxs-lookup"><span data-stu-id="e7455-128">See [BizTalk Adapter for WebSphere MQ](https://msdn.microsoft.com/library/dn191830(BTS.80).aspx).</span></span>
