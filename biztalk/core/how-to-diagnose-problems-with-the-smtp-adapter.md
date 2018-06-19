---
title: 如何診斷 SMTP 配接器問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eaf39fd8-b662-4b0c-b5e8-1af02cb4f79b
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a41a347534c07b522de5fc073933758870bf8a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249670"
---
# <a name="how-to-diagnose-problems-with-the-smtp-adapter"></a><span data-ttu-id="73828-102">如何診斷 SMTP 配接器問題</span><span class="sxs-lookup"><span data-stu-id="73828-102">How to Diagnose Problems with the SMTP Adapter</span></span>
<span data-ttu-id="73828-103">本節包含的步驟可協助您診斷 SMTP 配接器的問題。</span><span class="sxs-lookup"><span data-stu-id="73828-103">This section contains steps that can be followed to help diagnose problems with the SMTP adapter.</span></span>  
  
### <a name="check-the-smtp-log-files-of-the-smtp-server-for-errors"></a><span data-ttu-id="73828-104">檢查 SMTP 伺服器的 SMTP 記錄檔是否出現錯誤</span><span class="sxs-lookup"><span data-stu-id="73828-104">Check the SMTP log files of the SMTP Server for errors</span></span>  
  
-   <span data-ttu-id="73828-105">SMTP 伺服器記錄檔包含的資訊，可協助您疑難排解 SMTP 配接器的問題。</span><span class="sxs-lookup"><span data-stu-id="73828-105">The target SMTP server log files can contain information that is helpful for troubleshooting problems with the SMTP adapter.</span></span> <span data-ttu-id="73828-106">根據預設，[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] 上的 SMTP 記錄檔位於下列目錄：</span><span class="sxs-lookup"><span data-stu-id="73828-106">By default the SMTP log files on [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] are located in the following directory:</span></span>  
  
     <span data-ttu-id="73828-107">*%Windir%\\*system32\LogFiles\SMTPSVC1\\</span><span class="sxs-lookup"><span data-stu-id="73828-107">*%WinDir%\\*system32\LogFiles\SMTPSVC1\\</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="73828-108">*%Windir%* 是 SMTP 伺服器上的 Windows 目錄位置的預留位置。</span><span class="sxs-lookup"><span data-stu-id="73828-108">*%WinDir%* is a placeholder for the location of the Windows directory on the SMTP server.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="73828-109">SMTP 記錄功能預設為停用上[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="73828-109">SMTP logging is disabled by default on [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)].</span></span> <span data-ttu-id="73828-110">如需啟用 SMTP 記錄功能的詳細資訊，請參閱 Windows Server 文件。</span><span class="sxs-lookup"><span data-stu-id="73828-110">For information about enabling logging for SMTP, see the Windows Server documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73828-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73828-111">See Also</span></span>  
 <span data-ttu-id="73828-112">[工具和公用程式來進行疑難排解的使用](../core/tools-and-utilities-to-use-for-troubleshooting.md) </span><span class="sxs-lookup"><span data-stu-id="73828-112">[Tools and Utilities to Use for Troubleshooting](../core/tools-and-utilities-to-use-for-troubleshooting.md) </span></span>  
 [<span data-ttu-id="73828-113">SMTP 配接器疑難排解</span><span class="sxs-lookup"><span data-stu-id="73828-113">Troubleshooting the SMTP Adapter</span></span>](../core/troubleshooting-the-smtp-adapter.md)