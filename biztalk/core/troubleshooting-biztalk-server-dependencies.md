---
title: "疑難排解 BizTalk Server 相依性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 677b7ef3-9a91-4f1e-bfc5-926bfab23a0f
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a75cf1986c9c7bf66aa48370704ca3569d0db87
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-biztalk-server-dependencies"></a><span data-ttu-id="a3a98-102">BizTalk Server 相依性疑難排解</span><span class="sxs-lookup"><span data-stu-id="a3a98-102">Troubleshooting BizTalk Server Dependencies</span></span>
<span data-ttu-id="a3a98-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 廣泛運用數種其他 Microsoft 產品，以進行設計階段和執行階段作業。</span><span class="sxs-lookup"><span data-stu-id="a3a98-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] makes extensive use of several other Microsoft products for design time and run-time operations.</span></span> <span data-ttu-id="a3a98-104">本節中的疑難排解指導方針可解決在這些基礎技術中可能發生的問題。</span><span class="sxs-lookup"><span data-stu-id="a3a98-104">This section contains troubleshooting guidelines for resolving problems that can occur in these underlying technologies.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a3a98-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="a3a98-105">In This Section</span></span>  
  
-   [<span data-ttu-id="a3a98-106">MSDTC 問題疑難排解</span><span class="sxs-lookup"><span data-stu-id="a3a98-106">Troubleshooting Problems with MSDTC</span></span>](../core/troubleshooting-problems-with-msdtc.md)  
  
-   [<span data-ttu-id="a3a98-107">疑難排解憑證</span><span class="sxs-lookup"><span data-stu-id="a3a98-107">Troubleshooting Certificates</span></span>](../core/troubleshooting-certificates.md)  
  
-   [<span data-ttu-id="a3a98-108">疑難排解企業單一登入</span><span class="sxs-lookup"><span data-stu-id="a3a98-108">Troubleshooting Enterprise Single Sign-On</span></span>](../core/troubleshooting-enterprise-single-sign-on.md)  
  
-   [<span data-ttu-id="a3a98-109">疑難排解 SQL Server</span><span class="sxs-lookup"><span data-stu-id="a3a98-109">Troubleshooting SQL Server</span></span>](../core/troubleshooting-sql-server.md)  
  
-   [<span data-ttu-id="a3a98-110">Web 服務疑難排解</span><span class="sxs-lookup"><span data-stu-id="a3a98-110">Troubleshooting Web Services</span></span>](../core/troubleshooting-web-services.md)  
  
-   [<span data-ttu-id="a3a98-111">疑難排解 Windows Server 叢集</span><span class="sxs-lookup"><span data-stu-id="a3a98-111">Troubleshooting a Windows Server Cluster</span></span>](../core/troubleshooting-a-windows-server-cluster.md)  
  
-   [<span data-ttu-id="a3a98-112">Internet Information Services 疑難排解</span><span class="sxs-lookup"><span data-stu-id="a3a98-112">Troubleshooting Internet Information Services</span></span>](../core/troubleshooting-internet-information-services.md)  
  
-   [<span data-ttu-id="a3a98-113">疑難排解 Windows SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="a3a98-113">Troubleshooting Windows SharePoint Services</span></span>](../core/troubleshooting-windows-sharepoint-services.md)