---
title: 如何診斷 HTTP 配接器問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 91f818dd-11fa-4ea4-b904-e8e00b3e49b4
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 545e095624c30b4611c74dcfbdead13d685164ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249838"
---
# <a name="how-to-diagnose-problems-with-the-http-adapter"></a><span data-ttu-id="0bb39-102">如何診斷 HTTP 配接器問題</span><span class="sxs-lookup"><span data-stu-id="0bb39-102">How to Diagnose Problems with the HTTP Adapter</span></span>
<span data-ttu-id="0bb39-103">本節包含的步驟可幫助您診斷 HTTP 配接器問題。</span><span class="sxs-lookup"><span data-stu-id="0bb39-103">This section contains steps that can be followed to help diagnose problems with the HTTP adapter.</span></span>  
  
### <a name="check-the-iis-and-httperr-log-files-of-the-iis-server-for-errors"></a><span data-ttu-id="0bb39-104">檢查 IIS 伺服器的 IIS 及 HTTPERR 記錄檔中是否列出錯誤</span><span class="sxs-lookup"><span data-stu-id="0bb39-104">Check the IIS and HTTPERR log files of the IIS Server for errors</span></span>  
  
-   <span data-ttu-id="0bb39-105">來源或目標 IIS 伺服器記錄檔可能包含有助於疑難排解 HTTP 配接器問題的資訊。</span><span class="sxs-lookup"><span data-stu-id="0bb39-105">The source or target IIS server log files can contain information that is helpful for troubleshooting problems with the HTTP adapter.</span></span> <span data-ttu-id="0bb39-106">根據預設，Windows Server 上的 IIS 記錄檔位於下列目錄：</span><span class="sxs-lookup"><span data-stu-id="0bb39-106">By default the IIS log files on a Windows Server are located in the following directory:</span></span>  
  
     <span data-ttu-id="0bb39-107">*%Windir%\\*system32\LogFiles\W3SVC1\\</span><span class="sxs-lookup"><span data-stu-id="0bb39-107">*%WinDir%\\*system32\LogFiles\W3SVC1\\</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0bb39-108">*%Windir%* 是 IIS 伺服器上的 Windows 目錄位置的預留位置。</span><span class="sxs-lookup"><span data-stu-id="0bb39-108">*%WinDir%* is a placeholder for the location of the Windows directory on the IIS server.</span></span>  
  
     <span data-ttu-id="0bb39-109">根據預設，[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] 電腦上的 HTTPERR 記錄檔位於下列目錄：</span><span class="sxs-lookup"><span data-stu-id="0bb39-109">By default the HTTPERR log files on a [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] based computer are located in the following directory:</span></span>  
  
     <span data-ttu-id="0bb39-110">*%Windir%\\*system32\LogFiles\HTTPERR\\</span><span class="sxs-lookup"><span data-stu-id="0bb39-110">*%WinDir%\\*system32\LogFiles\HTTPERR\\</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0bb39-111">只有在 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 電腦上才能使用 HTTPERR 記錄檔。</span><span class="sxs-lookup"><span data-stu-id="0bb39-111">The HTTPERR log file is available only on [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] computers.</span></span>  
  
### <a name="isolate-problems-with-the-http-send-adapter-by-posting-to-the-destination-url-with-a-client-that-uses-the-systemnethttpwebrequest-class"></a><span data-ttu-id="0bb39-112">以使用 System.Net.HttpWebRequest 類別的用戶端公佈到目標 URL，來隔離 HTTP 傳送配接器問題。</span><span class="sxs-lookup"><span data-stu-id="0bb39-112">Isolate problems with the HTTP send adapter by posting to the destination URL with a client that uses the System.Net.HttpWebRequest class</span></span>  
  
1.  <span data-ttu-id="0bb39-113">如果 HTTP 傳送配接器在公佈到目標 URL 時產生問題，請建立使用 System.Net.HttpWebRequest 和 HttpWebResponse 類別的用戶端來公佈到目標 URL。</span><span class="sxs-lookup"><span data-stu-id="0bb39-113">If the HTTP send adapter is generating errors when posting to the destination URL, create a client that uses the System.Net.HttpWebRequest and HttpWebResponse classes to post to the destination URL.</span></span> <span data-ttu-id="0bb39-114">此方法有助於判斷問題是針對 HTTP 傳送配接器，或是有一般公佈到目標 URL 的問題。</span><span class="sxs-lookup"><span data-stu-id="0bb39-114">This approach will help determine if the problem is specific to the HTTP send adapter or if there is a problem posting to the destination URL in general.</span></span>  
  
2.  <span data-ttu-id="0bb39-115">如需有關建立使用 System.Net.HttpWebRequest 和 HttpWebResponse 類別的用戶端，請參閱[如何使用新 System.Net 類別來建立 HTTP 用戶端](http://go.microsoft.com/fwlink/?LinkId=66987)。</span><span class="sxs-lookup"><span data-stu-id="0bb39-115">For more information about creating a client that uses the System.Net.HttpWebRequest and HttpWebResponse classes see [How to use the new System.Net classes to create an HTTP client](http://go.microsoft.com/fwlink/?LinkId=66987).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bb39-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0bb39-116">See Also</span></span>  
 <span data-ttu-id="0bb39-117">[工具和公用程式來進行疑難排解的使用](../core/tools-and-utilities-to-use-for-troubleshooting.md) </span><span class="sxs-lookup"><span data-stu-id="0bb39-117">[Tools and Utilities to Use for Troubleshooting](../core/tools-and-utilities-to-use-for-troubleshooting.md) </span></span>  
 [<span data-ttu-id="0bb39-118">HTTP 配接器疑難排解</span><span class="sxs-lookup"><span data-stu-id="0bb39-118">Troubleshooting the HTTP Adapter</span></span>](../core/troubleshooting-the-http-adapter.md)