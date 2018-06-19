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
# <a name="how-to-diagnose-problems-with-the-file-adapter"></a>如何診斷 FILE 配接器問題
本節所包含的步驟可協助您診斷  FILE 配接器的問題。  
  
### <a name="run-the-filemon-utility-to-diagnose-errors-that-occur-using-the-file-receive-or-file-send-adapter"></a>執行 FileMon 公用程式來診斷使用檔案接收或檔案傳送配接器時所發生的錯誤  
  
1.  下載 FileMon 公用程式從[www.sysinternals.com](http://go.microsoft.com/fwlink/?LinkId=66235)。  
  
2.  將 Filemon 公用程式安裝在裝載 FILE 配接器所讀取或寫入之資料夾或共用的伺服器上。  
  
3.  啟動 Filemon 公用程式並套用篩選器，僅監視 FILE 配接器處理常式 (如 BTSNTSvc.exe) 在其中執行的 BizTalk 主控件執行個體所進行的檔案存取。  
  
4.  執行造成問題的情況。  
  
5.  停用 Filemon 公用程式的檔案監視功能，然後將產生的記錄檔儲存至磁碟。  
  
6.  檢視產生的記錄檔，看看有無發生錯誤。  
  
    > [!NOTE]
    >  Microsoft 不支援 FileMon，也不保證此程式的適用性。 請自行承擔使用這個程式的一切風險。  
  
## <a name="see-also"></a>另請參閱  
 [工具和公用程式來進行疑難排解的使用](../core/tools-and-utilities-to-use-for-troubleshooting.md)   
 [檔案配接器疑難排解](../core/troubleshooting-the-file-adapter.md)