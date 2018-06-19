---
title: SOA BizTalk 管理點的概觀 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0d4c3a30-c50e-4c1c-9f59-d9a364078388
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60f73834a9bc02e371d4050115b1eccf5e88e02f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294926"
---
# <a name="overview-of-the-soa-biztalk-management-point"></a><span data-ttu-id="05fb0-102">SOA BizTalk 管理點的概觀</span><span class="sxs-lookup"><span data-stu-id="05fb0-102">Overview of the SOA BizTalk Management Point</span></span>
<span data-ttu-id="05fb0-103">SOA 服務管理員和工作臺產品與原生整合，BizTalk 管理點。</span><span class="sxs-lookup"><span data-stu-id="05fb0-103">The BizTalk Management Point natively integrates with SOA Service Manager and Workbench products.</span></span> <span data-ttu-id="05fb0-104">不同於一般的 Web 服務管理點，這項實作都與 Microsoft BizTalk Server 環境，以表示 BizTalk Server 所提供的服務接收位置和傳送埠。</span><span class="sxs-lookup"><span data-stu-id="05fb0-104">Unlike the typical Web Services Management Point, this implementation is associated with services provided by the Microsoft BizTalk Server environment, expressed in terms of BizTalk Server receive locations and send ports.</span></span> <span data-ttu-id="05fb0-105">因為任意本質的接收位置和傳送埠 （針對各種不同的 BizTalk Server 配接器設定），這些服務不一定與 Web 服務相關聯，但它們可以被視為方面 SOA Service Manager 中的 Web 服務和 SOA Workbench。</span><span class="sxs-lookup"><span data-stu-id="05fb0-105">Because of the arbitrary nature of receive locations and send ports (configured against a variety of BizTalk Server adapters), these services are not necessarily associated with Web services, but they can be treated as Web services in terms of the SOA Service Manager and SOA Workbench.</span></span>  
  
 <span data-ttu-id="05fb0-106">圖 1 顯示 SOA 服務管理員 Web 應用程式顯示的範例應用程式的 [Workbench] 頁面。</span><span class="sxs-lookup"><span data-stu-id="05fb0-106">Figure 1 shows the SOA Service Manager Web application displaying the Workbench page for an example application.</span></span> <span data-ttu-id="05fb0-107">左側的樹狀檢視可讓使用者瀏覽應用程式和服務安裝 BizTalk Server 中，右邊窗格可讓使用者檢視應用程式詳細資料、 作業、 存取連接埠、 類別、 規則和監視資訊。</span><span class="sxs-lookup"><span data-stu-id="05fb0-107">The left-side tree view allows users to navigate through the applications and services installed within BizTalk Server, and the right-side pane allows users to view application details, operations, access ports, categories, rules, and monitoring information.</span></span>  
  
 <span data-ttu-id="05fb0-108">![Ch9 &#45;SOAServiceManager](../esb-toolkit/media/ch9-soaservicemanager.jpg "Ch9 SOAServiceManager")</span><span class="sxs-lookup"><span data-stu-id="05fb0-108">![Ch9&#45;SOAServiceManager](../esb-toolkit/media/ch9-soaservicemanager.jpg "Ch9-SOAServiceManager")</span></span>  
  
 <span data-ttu-id="05fb0-109">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="05fb0-109">**Figure 1**</span></span>  
  
 <span data-ttu-id="05fb0-110">**SOA 服務管理員 [Workbench] 頁面上顯示可用的監視功能**</span><span class="sxs-lookup"><span data-stu-id="05fb0-110">**The SOA Service Manager showing the monitoring features available on the Workbench page**</span></span>  
  
 <span data-ttu-id="05fb0-111">您可以監視所有作業，在應用程式 （所有傳送埠和接收位置） 或特定的作業。Workbench 通過所選的訊息清單會顯示傳送埠和接收位置。</span><span class="sxs-lookup"><span data-stu-id="05fb0-111">You can monitor all the operations within an application (all send ports and receive locations), or specific operations; the Workbench shows a list of the messages passing through the selected send ports and receive locations.</span></span> <span data-ttu-id="05fb0-112">當您按兩下清單中的訊息時，Workbench （如果已啟用記錄），就會顯示訊息和其內容屬性的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="05fb0-112">When you double-click a message in the list, the Workbench displays details of the message, and its context properties (if recording is enabled).</span></span> <span data-ttu-id="05fb0-113">或者，您可以在通過該服務的即時訊息中選取特定的服務和監視。</span><span class="sxs-lookup"><span data-stu-id="05fb0-113">Alternatively, you can select a specific service and monitor in real-time messages passing through that service.</span></span>