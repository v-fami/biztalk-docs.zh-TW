---
title: 如何診斷 SOAP 配接器問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 16c93333-cb32-49bc-a1c4-9d726ab41850
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db1d495eb301f93100a6ac9a4e50c8f1c57e5f5a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249470"
---
# <a name="how-to-diagnose-problems-with-the-soap-adapter"></a><span data-ttu-id="c9a0d-102">如何診斷 SOAP 配接器問題</span><span class="sxs-lookup"><span data-stu-id="c9a0d-102">How to Diagnose Problems with the SOAP Adapter</span></span>
<span data-ttu-id="c9a0d-103">本節包含的步驟有助於診斷 SOAP 配接器的問題。</span><span class="sxs-lookup"><span data-stu-id="c9a0d-103">This section contains steps that can be followed to help diagnose problems with the SOAP adapter.</span></span>  
  
### <a name="check-the-iis-log-and-httperr-log-of-the-iis-server-for-errors"></a><span data-ttu-id="c9a0d-104">檢查 IIS 伺服器的 IIS 記錄和 HTTPERR 記錄中是否記載發生的錯誤</span><span class="sxs-lookup"><span data-stu-id="c9a0d-104">Check the IIS log and HTTPERR log of the IIS Server for errors</span></span>  
  
-   <span data-ttu-id="c9a0d-105">來源或目標 IIS 伺服器記錄檔可能包含有助於疑難排解 SOAP 配接器問題的資訊。</span><span class="sxs-lookup"><span data-stu-id="c9a0d-105">The source or target IIS server log files can contain information that is helpful for troubleshooting problems with the SOAP adapter.</span></span> <span data-ttu-id="c9a0d-106">根據預設，[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] 電腦上的 IIS 記錄檔位於下列目錄：</span><span class="sxs-lookup"><span data-stu-id="c9a0d-106">By default the IIS log files on a [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] computer are located in the following directory:</span></span>  
  
     <span data-ttu-id="c9a0d-107">*%Windir%\\*system32\LogFiles\W3SVC1\\</span><span class="sxs-lookup"><span data-stu-id="c9a0d-107">*%WinDir%\\*system32\LogFiles\W3SVC1\\</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c9a0d-108">*%Windir%* 是 IIS 伺服器上的 Windows 目錄位置的預留位置。</span><span class="sxs-lookup"><span data-stu-id="c9a0d-108">*%WinDir%* is a placeholder for the location of the Windows directory on the IIS server.</span></span>  
  
     <span data-ttu-id="c9a0d-109">根據預設，[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] 電腦上的 HTTPERR 記錄檔位於下列目錄：</span><span class="sxs-lookup"><span data-stu-id="c9a0d-109">By default the HTTPERR log files on a [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] based computer are located in the following directory:</span></span>  
  
     <span data-ttu-id="c9a0d-110">*%Windir%\\*system32\LogFiles\HTTPERR\\</span><span class="sxs-lookup"><span data-stu-id="c9a0d-110">*%WinDir%\\*system32\LogFiles\HTTPERR\\</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c9a0d-111">只有在 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 電腦上才能使用 HTTPERR 記錄檔。</span><span class="sxs-lookup"><span data-stu-id="c9a0d-111">The HTTPERR log file is available only on [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] computers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9a0d-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9a0d-112">See Also</span></span>  
 <span data-ttu-id="c9a0d-113">[工具和公用程式來進行疑難排解的使用](../core/tools-and-utilities-to-use-for-troubleshooting.md) </span><span class="sxs-lookup"><span data-stu-id="c9a0d-113">[Tools and Utilities to Use for Troubleshooting](../core/tools-and-utilities-to-use-for-troubleshooting.md) </span></span>  
 [<span data-ttu-id="c9a0d-114">SOAP 配接器疑難排解</span><span class="sxs-lookup"><span data-stu-id="c9a0d-114">Troubleshooting the SOAP Adapter</span></span>](../core/troubleshooting-the-soap-adapter.md)