---
title: "CSOM: SharePoint Services 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 334c7f32-4620-4fee-8237-491d3c3ded4e
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 146d4ecb253aca18c0699f526e01b28fd62ff984
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="csom-sharepoint-services-adapter"></a><span data-ttu-id="0e83b-102">CSOM: SharePoint Services 配接器</span><span class="sxs-lookup"><span data-stu-id="0e83b-102">CSOM: SharePoint Services Adapter</span></span>
<span data-ttu-id="0e83b-103">使用 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 配接器，即可從 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 接收訊息及傳送訊息至 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0e83b-103">Using the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] adapter, you can receive messages from [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] and send messages to [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="0e83b-104">[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]配接器會使用[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]Client Side Object Model (CSOM)，也就是***自動***時一併安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="0e83b-104">The [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Adapter uses the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Client Side Object Model (CSOM), which is ***automatically*** installed when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed.</span></span> <span data-ttu-id="0e83b-105">上有任何額外的安裝步驟[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]電腦。</span><span class="sxs-lookup"><span data-stu-id="0e83b-105">There are no additional installation steps on the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] computer.</span></span>  
  
 <span data-ttu-id="0e83b-106">我們建議使用 Client Side Object Model (CSOM) 的[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]配接器。</span><span class="sxs-lookup"><span data-stu-id="0e83b-106">We recommend using the Client Side Object Model (CSOM) of the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Adapter.</span></span>  
  
 <span data-ttu-id="0e83b-107">[附錄 b： 安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)提供更多有關[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="0e83b-107">[Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) provides more information on the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] installation.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0e83b-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="0e83b-108">In This Section</span></span>  
  
-   [<span data-ttu-id="0e83b-109">設定 SharePoint Services 接收位置</span><span class="sxs-lookup"><span data-stu-id="0e83b-109">Configure SharePoint Services Receive Location</span></span>](../core/configure-sharepoint-services-receive-location.md)  
  
-   [<span data-ttu-id="0e83b-110">設定 SharePoint Services 傳送埠</span><span class="sxs-lookup"><span data-stu-id="0e83b-110">Configure SharePoint Services Send Port</span></span>](../core/configure-sharepoint-services-send-port.md)  
  
-   [<span data-ttu-id="0e83b-111">SharePoint Services 配接器疑難排解</span><span class="sxs-lookup"><span data-stu-id="0e83b-111">Troubleshooting SharePoint Services Adapter</span></span>](../core/troubleshooting-sharepoint-services-adapter.md)  
  
## <a name="see-also"></a><span data-ttu-id="0e83b-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e83b-112">See Also</span></span>  
 <span data-ttu-id="0e83b-113">[附錄 B：安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="0e83b-113">[Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) </span></span>  
 [<span data-ttu-id="0e83b-114">BizTalk Server 2013 和 2013 R2 的安裝概觀</span><span class="sxs-lookup"><span data-stu-id="0e83b-114">Installation Overview for BizTalk Server 2013 and 2013 R2</span></span>](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)