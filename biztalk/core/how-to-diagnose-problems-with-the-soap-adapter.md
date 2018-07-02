---
title: 如何診斷 SOAP 配接器的問題 |Microsoft Docs
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
ms.openlocfilehash: 85c585c3fae6c6f49412f00e02276276e9c73b64
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968311"
---
# <a name="how-to-diagnose-problems-with-the-soap-adapter"></a>如何診斷 SOAP 配接器問題
本節包含的步驟有助於診斷 SOAP 配接器的問題。  
  
### <a name="check-the-iis-log-and-httperr-log-of-the-iis-server-for-errors"></a>檢查 IIS 伺服器的 IIS 記錄和 HTTPERR 記錄中是否記載發生的錯誤  
  
- 來源或目標 IIS 伺服器記錄檔可能包含有助於疑難排解 SOAP 配接器問題的資訊。 根據預設，[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] 電腦上的 IIS 記錄檔位於下列目錄：  
  
   <em>%Windir%\\</em>system32\LogFiles\W3SVC1\  
  
  > [!NOTE]
  >  *%Windir%* 是在 IIS 伺服器上的 Windows 目錄位置的預留位置。  
  
   根據預設，[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] 電腦上的 HTTPERR 記錄檔位於下列目錄：  
  
   <em>%Windir%\\</em>system32\LogFiles\HTTPERR\  
  
  > [!NOTE]
  >  只有在 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 電腦上才能使用 HTTPERR 記錄檔。  
  
## <a name="see-also"></a>另請參閱  
 [工具和公用程式來使用，以進行疑難排解](../core/tools-and-utilities-to-use-for-troubleshooting.md)   
 [SOAP 配接器疑難排解](../core/troubleshooting-the-soap-adapter.md)