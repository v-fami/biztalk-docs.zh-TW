---
title: 如何診斷問題使用 Windows SharePoint Services 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55c29569-3814-43a7-93f8-a39c3464a831
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fd328b8e68b90b5afb23a49fc7412156fc85de91
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981007"
---
# <a name="how-to-diagnose-problems-with-the-windows-sharepoint-services-adapter"></a>如何診斷 Windows SharePoint Services 配接器問題
本節所包含的步驟可協助您診斷 Windows Sharepoint Services 配接器的問題。  
  
### <a name="check-the-iis-and-httperr-log-files-of-the-iis-server-for-errors"></a>檢查 IIS 伺服器的 IIS 及 HTTPERR 記錄檔中是否列出錯誤  
  
- 來源或目標 IIS 伺服器記錄檔可能包含了有助於疑難排解 Windows Sharepoint Services 配接器問題的資訊。 根據預設，[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] 電腦上的 IIS 記錄檔位於下列目錄：  
  
   <em>%Windir%\\</em>system32\LogFiles\W3SVC1\  
  
  > [!NOTE]
  >  *%Windir%* 是在 IIS 伺服器上的 Windows 目錄位置的預留位置。  
  
- 根據預設，[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] 電腦上的 HTTPERR 記錄檔位於下列目錄：  
  
   <em>%Windir%\\</em>system32\LogFiles\HTTPERR\  
  
  > [!NOTE]
  >  只有在 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 電腦上才能使用 HTTPERR 記錄檔。  
  
## <a name="see-also"></a>另請參閱  
 [工具和公用程式來使用，以進行疑難排解](../core/tools-and-utilities-to-use-for-troubleshooting.md)   
 [Windows SharePoint Services 配接器疑難排解](../core/troubleshooting-the-windows-sharepoint-services-adapter.md)