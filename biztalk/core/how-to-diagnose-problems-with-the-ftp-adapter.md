---
title: 如何診斷 FTP 配接器問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 499d23d3-b705-4527-9929-147be157e6b3
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e66be2e498449b1cdcc70e05c6195ccd8e4395d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248766"
---
# <a name="how-to-diagnose-problems-with-the-ftp-adapter"></a><span data-ttu-id="0ccf4-102">如何診斷 FTP 配接器問題</span><span class="sxs-lookup"><span data-stu-id="0ccf4-102">How to Diagnose Problems with the FTP Adapter</span></span>
<span data-ttu-id="0ccf4-103">本節包含可供遵循以協助診斷 FTP 配接器問題的步驟。</span><span class="sxs-lookup"><span data-stu-id="0ccf4-103">This section contains steps that can be followed to help diagnose problems with the FTP adapter.</span></span>  
  
### <a name="check-the-ftp-log-files-on-the-ftp-server-for-errors"></a><span data-ttu-id="0ccf4-104">檢查 FTP 伺服器上的 FTP 記錄檔中是否列出錯誤</span><span class="sxs-lookup"><span data-stu-id="0ccf4-104">Check the FTP log files on the FTP Server for errors</span></span>  
  
-   <span data-ttu-id="0ccf4-105">來源或目標 FTP 伺服器記錄檔可能包含了有助於疑難排解 FTP 配接器問題的資訊。</span><span class="sxs-lookup"><span data-stu-id="0ccf4-105">The source or target FTP server log files can contain information that is helpful for troubleshooting problems with the FTP adapter.</span></span> <span data-ttu-id="0ccf4-106">依照預設，Windows Server 或 Windows XP 電腦上的 FTP 記錄檔位於下列目錄：</span><span class="sxs-lookup"><span data-stu-id="0ccf4-106">By default the FTP log files on a Windows Server or Windows XP computer are located in the following directory:</span></span>  
  
     <span data-ttu-id="0ccf4-107">*%Windir%\\*system32\LogFiles\MSFTPSVC1\\</span><span class="sxs-lookup"><span data-stu-id="0ccf4-107">*%WinDir%\\*system32\LogFiles\MSFTPSVC1\\</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0ccf4-108">*%Windir%* 是 FTP 伺服器上的 Windows 目錄位置的預留位置。</span><span class="sxs-lookup"><span data-stu-id="0ccf4-108">*%WinDir%* is a placeholder for the location of the Windows directory on the FTP server.</span></span>  
  
### <a name="enable-logging-for-the-ftp-receive-location-or-send-port"></a><span data-ttu-id="0ccf4-109">啟用 FTP 接收位置或傳送埠的記錄功能</span><span class="sxs-lookup"><span data-stu-id="0ccf4-109">Enable logging for the FTP Receive location or Send Port</span></span>  
  
-   <span data-ttu-id="0ccf4-110">設定 FTP 接收位置或傳送埠與**記錄**資料夾。</span><span class="sxs-lookup"><span data-stu-id="0ccf4-110">Configure the FTP receive location or send port with a **Log** folder.</span></span> <span data-ttu-id="0ccf4-111">FTP 配接器會將詳細的記錄資訊儲存在此資料夾中。</span><span class="sxs-lookup"><span data-stu-id="0ccf4-111">The FTP adapter will save detailed logging information to this folder.</span></span> <span data-ttu-id="0ccf4-112">**記錄**資料夾選項位於上**FTP 傳輸屬性**時使用 [FTP 傳輸類型設定接收位置或傳送埠] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0ccf4-112">The **Log** folder option is available on the **FTP Transport Properties** dialog box when configuring a receive location or send port with the FTP transport type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ccf4-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ccf4-113">See Also</span></span>  
 [<span data-ttu-id="0ccf4-114">工具和公用程式來進行疑難排解的使用</span><span class="sxs-lookup"><span data-stu-id="0ccf4-114">Tools and Utilities to Use for Troubleshooting</span></span>](../core/tools-and-utilities-to-use-for-troubleshooting.md)