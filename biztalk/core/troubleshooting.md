---
title: "疑難排解和已知問題 |Microsoft 文件"
description: "已知問題、 zombie，效能進行疑難排解、 疑難排解配接器、 疑難排解權限、 EDI 和 AS2 和多個 BizTalk Server 中的疑難排解"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecb934c6-3efa-40b6-949b-a04a73e60b07
caps.latest.revision: "32"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df13438e641d55de91096b690a8e5e95e26cbfa4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting"></a><span data-ttu-id="3cec0-103">疑難排解</span><span class="sxs-lookup"><span data-stu-id="3cec0-103">Troubleshooting</span></span>

## <a name="overview"></a><span data-ttu-id="3cec0-104">概觀</span><span class="sxs-lookup"><span data-stu-id="3cec0-104">Overview</span></span>
<span data-ttu-id="3cec0-105">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 運用及依賴數種不同的 Microsoft 技術，包含但不限於 Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]、Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]、Microsoft [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)]、Internet Information Services (IIS)、Microsoft Windows 伺服器叢集、Microsoft 企業單一登入和 Windows [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3cec0-105">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] makes use of or may depend on several different Microsoft technologies including but not limited to Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], the Microsoft [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)], Internet Information Services (IIS), Microsoft Windows Server Cluster, Enterprise Single Sign-On, and Windows [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)].</span></span> <span data-ttu-id="3cec0-106">因為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 所利用的技術繁多，所以在針對 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 進行疑難排解時，經常涉及基礎技術或所使用之相依性的疑難排解。</span><span class="sxs-lookup"><span data-stu-id="3cec0-106">Because [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is used with so many other technologies, troubleshooting a problem with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] often involves troubleshooting the underlying technology or dependency that is being used.</span></span> <span data-ttu-id="3cec0-107">本節針對特定的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 問題以及可能發生於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 相依性軟體的問題提供疑難排解的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3cec0-107">This section provides information about troubleshooting specific [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] problems and information about troubleshooting problems that can occur in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dependency software.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="3cec0-108">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="3cec0-108">Next steps</span></span> 
  
-   [<span data-ttu-id="3cec0-109">BizTalk Server 的已知的問題</span><span class="sxs-lookup"><span data-stu-id="3cec0-109">Known Issues with BizTalk Server</span></span>](../core/known-issues-with-biztalk-server.md)  

-   [<span data-ttu-id="3cec0-110">BizTalk Server 中的 zombie</span><span class="sxs-lookup"><span data-stu-id="3cec0-110">Zombies in BizTalk Server</span></span>](zombies-in-biztalk-server.md)
  
-   [<span data-ttu-id="3cec0-111">疑難排解 BizTalk Server 管理</span><span class="sxs-lookup"><span data-stu-id="3cec0-111">Troubleshoot BizTalk Server Administration</span></span>](../core/troubleshooting-biztalk-server-administration.md)  
  
-   [<span data-ttu-id="3cec0-112">啟用 System.Net 記錄功能</span><span class="sxs-lookup"><span data-stu-id="3cec0-112">Enabling System.Net Logging</span></span>](../core/enabling-system-net-logging.md)  
  
-   [<span data-ttu-id="3cec0-113">疑難排解 BizTalk Server 權限</span><span class="sxs-lookup"><span data-stu-id="3cec0-113">Troubleshoot BizTalk Server Permissions</span></span>](../core/troubleshooting-biztalk-server-permissions.md)  
  
-   [<span data-ttu-id="3cec0-114">BizTalk Server 效能進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="3cec0-114">Troubleshoot BizTalk Server Performance</span></span>](../core/troubleshooting-biztalk-server-performance.md)  
  
-   [<span data-ttu-id="3cec0-115">疑難排解 BizTalk Server 配接器</span><span class="sxs-lookup"><span data-stu-id="3cec0-115">Troubleshoot BizTalk Server Adapters</span></span>](../core/troubleshooting-biztalk-server-adapters.md)  
  
-   [<span data-ttu-id="3cec0-116">疑難排解 EDI 和 AS2 解決方案</span><span class="sxs-lookup"><span data-stu-id="3cec0-116">Troubleshoot EDI and AS2 Solutions</span></span>](../core/troubleshooting-edi-and-as2-solutions.md)  
  
-   [<span data-ttu-id="3cec0-117">疑難排解 BizTalk Server 相依性</span><span class="sxs-lookup"><span data-stu-id="3cec0-117">Troubleshoot BizTalk Server Dependencies</span></span>](../core/troubleshooting-biztalk-server-dependencies.md)  
  
-   [<span data-ttu-id="3cec0-118">針對組態進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="3cec0-118">Troubleshoot Configuration</span></span>](../core/troubleshooting-configuration.md)  
  
-   [<span data-ttu-id="3cec0-119">取得 BizTalk 處理序的記憶體傾印</span><span class="sxs-lookup"><span data-stu-id="3cec0-119">Get a Memory Dump of a BizTalk Process</span></span>](../core/how-to-capture-a-memory-dump-of-a-biztalk-process.md)  
  
-   [<span data-ttu-id="3cec0-120">工具和公用程式</span><span class="sxs-lookup"><span data-stu-id="3cec0-120">Tools and Utilities</span></span>](../core/tools-and-utilities-to-use-for-troubleshooting.md)  
  
-   [<span data-ttu-id="3cec0-121">使用十六進位內容的擱置訊息的訊息驗證錯誤進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="3cec0-121">Troubleshoot Message Validation Failures using the Hexadecimal Contents of Suspended Messages</span></span>](../core/troubleshoot-message-validation-failures-using-the-hexadecimal-contents.md)

- [<span data-ttu-id="3cec0-122">事件和錯誤</span><span class="sxs-lookup"><span data-stu-id="3cec0-122">Events and Errors</span></span>](events-and-errors2.md)