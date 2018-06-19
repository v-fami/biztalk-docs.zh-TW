---
title: 如何診斷 File 配接器問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f06089a5-4747-4879-a796-157088868dba
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0481a3abdf497c093a87d7d74ea0356c7cad0d0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249038"
---
# <a name="how-to-diagnose-problems-with-the-file-adapter"></a><span data-ttu-id="fd82f-102">如何診斷 FILE 配接器問題</span><span class="sxs-lookup"><span data-stu-id="fd82f-102">How to Diagnose Problems with the File Adapter</span></span>
<span data-ttu-id="fd82f-103">本節所包含的步驟可協助您診斷  FILE 配接器的問題。</span><span class="sxs-lookup"><span data-stu-id="fd82f-103">This section contains steps that can be followed to help diagnose problems with the File adapter.</span></span>  
  
### <a name="run-the-filemon-utility-to-diagnose-errors-that-occur-using-the-file-receive-or-file-send-adapter"></a><span data-ttu-id="fd82f-104">執行 FileMon 公用程式來診斷使用檔案接收或檔案傳送配接器時所發生的錯誤</span><span class="sxs-lookup"><span data-stu-id="fd82f-104">Run the FileMon Utility to diagnose errors that occur using the File Receive or File Send Adapter</span></span>  
  
1.  <span data-ttu-id="fd82f-105">下載 FileMon 公用程式從[www.sysinternals.com](http://go.microsoft.com/fwlink/?LinkId=66235)。</span><span class="sxs-lookup"><span data-stu-id="fd82f-105">Download the FileMon utility from [www.sysinternals.com](http://go.microsoft.com/fwlink/?LinkId=66235).</span></span>  
  
2.  <span data-ttu-id="fd82f-106">將 Filemon 公用程式安裝在裝載 FILE 配接器所讀取或寫入之資料夾或共用的伺服器上。</span><span class="sxs-lookup"><span data-stu-id="fd82f-106">Install the Filemon utility on the server that hosts the folder or share that is being read from or written to by the File Adapter.</span></span>  
  
3.  <span data-ttu-id="fd82f-107">啟動 Filemon 公用程式並套用篩選器，僅監視 FILE 配接器處理常式 (如 BTSNTSvc.exe) 在其中執行的 BizTalk 主控件執行個體所進行的檔案存取。</span><span class="sxs-lookup"><span data-stu-id="fd82f-107">Launch the Filemon utility and apply a filter to monitor only file accesses that are being made by the BizTalk Host instance that the file adapter handlers are running in (for example BTSNTSvc.exe).</span></span>  
  
4.  <span data-ttu-id="fd82f-108">執行造成問題的情況。</span><span class="sxs-lookup"><span data-stu-id="fd82f-108">Run the scenario that caused the problem.</span></span>  
  
5.  <span data-ttu-id="fd82f-109">停用 Filemon 公用程式的檔案監視功能，然後將產生的記錄檔儲存至磁碟。</span><span class="sxs-lookup"><span data-stu-id="fd82f-109">Disable file monitoring in the Filemon utility, then save the generated log file to disk.</span></span>  
  
6.  <span data-ttu-id="fd82f-110">檢視產生的記錄檔，看看有無發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="fd82f-110">Review the generated log file for any errors.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fd82f-111">Microsoft 不支援 FileMon，也不保證此程式的適用性。</span><span class="sxs-lookup"><span data-stu-id="fd82f-111">FileMon is not supported by Microsoft, and Microsoft makes no guarantees about the suitability of this program.</span></span> <span data-ttu-id="fd82f-112">請自行承擔使用這個程式的一切風險。</span><span class="sxs-lookup"><span data-stu-id="fd82f-112">Use of this program is entirely at your own risk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd82f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd82f-113">See Also</span></span>  
 <span data-ttu-id="fd82f-114">[工具和公用程式來進行疑難排解的使用](../core/tools-and-utilities-to-use-for-troubleshooting.md) </span><span class="sxs-lookup"><span data-stu-id="fd82f-114">[Tools and Utilities to Use for Troubleshooting](../core/tools-and-utilities-to-use-for-troubleshooting.md) </span></span>  
 [<span data-ttu-id="fd82f-115">檔案配接器疑難排解</span><span class="sxs-lookup"><span data-stu-id="fd82f-115">Troubleshooting the File Adapter</span></span>](../core/troubleshooting-the-file-adapter.md)