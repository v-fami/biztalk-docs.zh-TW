---
title: "如何診斷 FTP 配接器問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 499d23d3-b705-4527-9929-147be157e6b3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e66be2e498449b1cdcc70e05c6195ccd8e4395d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-diagnose-problems-with-the-ftp-adapter"></a>如何診斷 FTP 配接器問題
本節包含可供遵循以協助診斷 FTP 配接器問題的步驟。  
  
### <a name="check-the-ftp-log-files-on-the-ftp-server-for-errors"></a>檢查 FTP 伺服器上的 FTP 記錄檔中是否列出錯誤  
  
-   來源或目標 FTP 伺服器記錄檔可能包含了有助於疑難排解 FTP 配接器問題的資訊。 依照預設，Windows Server 或 Windows XP 電腦上的 FTP 記錄檔位於下列目錄：  
  
     *%Windir%\\*system32\LogFiles\MSFTPSVC1\  
  
    > [!NOTE]
    >  *%Windir%*是 FTP 伺服器上的 Windows 目錄位置的預留位置。  
  
### <a name="enable-logging-for-the-ftp-receive-location-or-send-port"></a>啟用 FTP 接收位置或傳送埠的記錄功能  
  
-   設定 FTP 接收位置或傳送埠與**記錄**資料夾。 FTP 配接器會將詳細的記錄資訊儲存在此資料夾中。 **記錄**資料夾選項位於上**FTP 傳輸屬性**時使用 [FTP 傳輸類型設定接收位置或傳送埠] 對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [工具和公用程式來進行疑難排解的使用](../core/tools-and-utilities-to-use-for-troubleshooting.md)