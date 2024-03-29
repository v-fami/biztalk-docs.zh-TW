---
title: 如何診斷 HTTP 配接器的問題 |Microsoft Docs
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
ms.openlocfilehash: 110ae50f97d89b12b361a14caaac4f0df56989e2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015719"
---
# <a name="how-to-diagnose-problems-with-the-http-adapter"></a>如何診斷 HTTP 配接器問題
本節包含的步驟可幫助您診斷 HTTP 配接器問題。  
  
### <a name="check-the-iis-and-httperr-log-files-of-the-iis-server-for-errors"></a>檢查 IIS 伺服器的 IIS 及 HTTPERR 記錄檔中是否列出錯誤  
  
- 來源或目標 IIS 伺服器記錄檔可能包含有助於疑難排解 HTTP 配接器問題的資訊。 根據預設，Windows Server 上的 IIS 記錄檔位於下列目錄：  
  
   <em>%Windir%\\</em>system32\LogFiles\W3SVC1\  
  
  > [!NOTE]
  >  *%Windir%* 是在 IIS 伺服器上的 Windows 目錄位置的預留位置。  
  
   根據預設，[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] 電腦上的 HTTPERR 記錄檔位於下列目錄：  
  
   <em>%Windir%\\</em>system32\LogFiles\HTTPERR\  
  
  > [!NOTE]
  >  只有在 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 電腦上才能使用 HTTPERR 記錄檔。  
  
### <a name="isolate-problems-with-the-http-send-adapter-by-posting-to-the-destination-url-with-a-client-that-uses-the-systemnethttpwebrequest-class"></a>以使用 System.Net.HttpWebRequest 類別的用戶端公佈到目標 URL，來隔離 HTTP 傳送配接器問題。  
  
1.  如果 HTTP 傳送配接器在公佈到目標 URL 時產生問題，請建立使用 System.Net.HttpWebRequest 和 HttpWebResponse 類別的用戶端來公佈到目標 URL。 此方法有助於判斷問題是針對 HTTP 傳送配接器，或是有一般公佈到目標 URL 的問題。  
  
2.  如需建立使用 System.Net.HttpWebRequest 和 HttpWebResponse 類別的用戶端的詳細資訊，請參閱[如何使用新 System.Net 類別建立 HTTP 用戶端](http://go.microsoft.com/fwlink/?LinkId=66987)。  
  
## <a name="see-also"></a>另請參閱  
 [工具和公用程式來使用，以進行疑難排解](../core/tools-and-utilities-to-use-for-troubleshooting.md)   
 [HTTP 配接器疑難排解](../core/troubleshooting-the-http-adapter.md)